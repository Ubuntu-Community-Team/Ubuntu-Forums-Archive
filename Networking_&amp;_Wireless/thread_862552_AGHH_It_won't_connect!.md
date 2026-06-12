---
title: "AGHH It won't connect!"
date: 2008-07-17
forum: Networking &amp; Wireless
---

### Post by Josephp22 on 2008-07-17
So I've been trying to connect to the internet for HOURS. Its not working.... so nwo I moved the computer all the way next to the modem. Heres my problem:

I've tried so many different guides and tutorials.. but nothing worked. I've gotten halfway there though. I can see my router, but it just wont connect. Right now, I've taken out the wep password but it still won't connect.

Can someone help me? I don't wanna give up on linux..

---

### Post by auxis on 2008-07-17
Try this, as it worked for me:

Go to System -> Preferences -> Sessions

Find Network Manager, and uncheck it.  Reboot your computer.

Now go to System -> Administration -> Network.  Click Unlock, enter your root password in.  Look up in the list of devices under Connections tab.  You should see your wireless card in the list, select it, click Properties.

Now un-check roaming mode if it's checked.  Under Network Name (ESSID) you should find the network you'd like to connect to, select it, then select the type of encryption you'd like.  If you require a key, make sure you don't prefix it with 0x (which indicates hex, but it's not needed in this case).

Click OK and a dialog should pop-up saying it's reconfiguring things for you.  Now to reset the connection by un-checking the wireless connection option, then re-checking it.  You may have to do that twice.  If it doesn't work, reboot your computer again.

This worked for me,  it's no guarantee but it's worth a shot.  For me the Network Manager was bugged, the drivers for my wireless card (WG311v2) conflicted with it for some reason, so the first time I tried it I simply right clicked the icon in the task bar and hit Disable Networking, but when I did that, it caused Firefox to start up in offline mode every time (File -> Offline Mode), which is extremely annoying.

Hopefully this bug gets fixed soon.  Hope this helps you!

---

### Post by Josephp22 on 2008-07-17
Sigh.. it didn't work. I forgot to put in my first post the driver and stuff.

I have a WMP54G card and the driver is a BCM4306. this is retarded lol

---

