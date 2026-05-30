const qrcode = require('qrcode-terminal'); const { Client, LocalAuth } = require('whatsapp-web.js');
const client = new Client({ authStrategy: new LocalAuth(), puppeteer: { args: ['--no-sandbox', '--disable-setuid-sandbox'] } });
// CONFIG const PREFIX = '/'; const DONO = '5534984455511';
// QR CODE client.on('qr', qr => { qrcode.generate(qr, { small: true }); });
// ONLINE client.on('ready', () => { console.log('🌙 Hina Bot online!'); });
// BOAS-VINDAS client.on('group_join', async (notification) => {
const chat = await notification.getChat();

chat.sendMessage(`
🌙✨ Bem-vindo(a) ao grupo!
Leia as regras e divirta-se 💕 `); });
// DESPEDIDA client.on('group_leave', async (notification) => {
const chat = await notification.getChat();

chat.sendMessage(`
🥀 Alguém saiu do grupo... Até mais 🌙 `); });
// MENSAGENS client.on('message', async message => {
const msg = message.body.toLowerCase();
const chat = await message.getChat();

// MENU
if(msg === `${PREFIX}menu`) {

    message.reply(`
╭━━━〔 🌙 Hina Bot 🌙 〕━━━╮ ┃ ✨ Oiê, como posso ajudar? ╰━━━━━━━━━━━━━━━━━━╯
╭─❍ 🤖 IA │ /ia │ /texto │ /pergunta ╰───────────
╭─❍ 🎉 Diversão │ /cantada │ /ship │ /meme │ /frase │ /jogo ╰───────────
╭─❍ 🎵 Mídia │ /musica │ /video │ /sticker │ /audio ╰───────────
╭─❍ 🛡️ Moderação │ /antilink │ /avisar │ /admins │ /ban ╰───────────
╭─❍ 👑 Dona │ /broadcast │ /reiniciar │ /membros │ /off ╰───────────
🌙 Cute • Dark • Funny Edition `); }
// OI
if(msg === `${PREFIX}oi`) {
    message.reply('Oiê, como posso ajudar? 🌙✨');
}

// ADMINS
if(msg === `${PREFIX}admins`) {

    let texto = '👑 Chamando admins:\n';
    let mentions = [];

    for(let participant of chat.participants) {

        if(participant.isAdmin) {

            const contato = await client.getContactById(participant.id._serialized);

            mentions.push(contato);

            texto += `@${participant.id.user}\n`;
        }
    }

    chat.sendMessage(texto, { mentions });
}

// ANTI-LINK
if(msg.includes('https://chat.whatsapp.com/')) {

    if(chat.isGroup) {

        await message.delete(true);

        chat.sendMessage(`
🚫 Links não são permitidos aqui. ⚠️ Aviso registrado. `); } }
// FRASES
if(msg === `${PREFIX}frase`) {

    const frases = [
        '🌙 Às vezes o silêncio fala mais.',
        '🖤 Nem todo sorriso é felicidade.',
        '✨ Você é mais forte do que pensa.',
        '😈 O caos também pode ser bonito.'
    ];

    const random = frases[Math.floor(Math.random() * frases.length)];

    message.reply(random);
}

// CANTADAS
if(msg === `${PREFIX}cantada`) {

    const cantadas = [
        '💘 Você não é Wi-Fi, mas senti conexão.',
        '🌙 Seu sorriso bugou meu sistema.',
        '✨ Você parece erro 404... porque não te encontro em ninguém.'
    ];

    const random = cantadas[Math.floor(Math.random() * cantadas.length)];

    message.reply(random);
}

// SHIP
if(msg.startsWith(`${PREFIX}ship`)) {

    const chance = Math.floor(Math.random() * 101);

    message.reply(`
💘 Compatibilidade detectada...
Casal: ${chance}% 😭✨ `); }
// MEME
if(msg === `${PREFIX}meme`) {

    message.reply(`
🗿 "eu vou dormir cedo hoje"
02:47 da manhã: 🤡 `); }
// JOGO
if(msg === `${PREFIX}jogo`) {

    const numero = Math.floor(Math.random() * 10);

    message.reply(`
🎲 Número sorteado: ${numero} `); }
// MEMBROS
if(msg === `${PREFIX}membros`) {

    message.reply(`
👥 Esse grupo possui: ${chat.participants.length} membros `); }
// IA SIMPLES
if(msg.startsWith(`${PREFIX}ia`)) {

    const pergunta = msg.replace('/ia', '');

    message.reply(`
🌙 Hina IA:
Você perguntou: "${pergunta}"
✨ Ainda estou aprendendo... `); }
// TEXTO
if(msg.startsWith(`${PREFIX}texto`)) {

    message.reply(`
✨ Modelo de texto criado pela Hina:
"Oiê! Passando pra desejar uma ótima noite pra você 🌙💕" `); }
// STICKER
if(msg === `${PREFIX}sticker`) {

    message.reply(`
📷 Envie uma imagem com legenda: /sticker `); }
// DONA OFF
if(msg === `${PREFIX}off`) {

    if(message.from.includes(DONO)) {

        message.reply('🌙 Hina está desligando...');
        process.exit();
    }
}
});
// INICIAR client.initialize();
