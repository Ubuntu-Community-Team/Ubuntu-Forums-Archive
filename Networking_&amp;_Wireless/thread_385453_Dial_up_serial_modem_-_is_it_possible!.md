---
title: "Dial up serial modem - is it possible??!"
date: 2007-03-15
forum: Networking &amp; Wireless
---

### Post by candtalan on 2007-03-15
I need to use dial up to an isp using my serial modem (external, serial port) from Kubuntu preferably. 

(Yes I *know* adsl is best and I usually use it......., another story)

However, I can get as far as the 56k modem dialling, and appearing to exchange useful sounding squeeks on the line with the isp machine, but then it gives an error.

The error suggests an authentication problem, and a bug seems to exist in kppp sounding a bit similar :-(

Am I wasting my time, or has anyone else found *success* with kppp lately please? If so I would love to compare notes. Anyone please?

(sad note: The same kit has been dialling up with suse for a long time. I now use kubuntu, suse got removed. However, I just had to reinstall suse for the sole reason of using very occasional, but importnt, dialup!)

Help!

---

### Post by sleepingdragon on 2007-03-18
I'm on Kubuntu and I'm using kppp for serial modem dialup, I find it perfectly stable and error free on Edgy.

I did have problems initially with kppp resetting the connection on dial out, but I resolved mine by using the CLI "pppconfig" and using kppp to call that new connection on boot - I'm using mine in an autostart file. The command line for me is:


kppp -c "<pppconfig saved name here>" &

The <pppconfig saved name> is the name you give your connection when setting up pppconfig, it does need to be in quotation marks in the command.

My autostart config file reads like this

[Desktop Entry]
Comment=Autostart Dialup
Exec=kppp -c "<your pppconfig name>" &
Name=KPPP
Type=Application

pppconfig will also allow "persistant connection" just in case your dialup drops the ball and will autoredial for your internet pleasure... Don't forget to set ATZ in your init string for your modem!

Hope that helps, I'll keep an eye on this thread if you need further help.

---

### Post by candtalan on 2007-03-18
Thanks! (There are some things I will need to get to understand from what you have said). I have to be away for a week and I am looking forward to getting it working when I get back.

---

### Post by sleepingdragon on 2007-03-18
No probs. Just reply to this thread and I'll get around to helping ya when I'm relatively sober... :rolleyes: 

Enjoy your week!

---

