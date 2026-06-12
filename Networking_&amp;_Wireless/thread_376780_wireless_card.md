---
title: "wireless card"
date: 2007-03-05
forum: Networking &amp; Wireless
---

### Post by jampeeters on 2007-03-05
I am new with Ubuntu, but installation went fine. However I face huge problems installing my wireles connection to internet. I allready tried for one day but the only success till now is that Ubuntu recognizes my wireles card. The wireless connection is active, and i even have a signal. The only downside is that i cannot connect to the internet.

Is there anyone who can help me?

---

### Post by oilchangeguy on 2007-03-05
to the left of the clock (in version 6.06) you should see a two screened icon. open that, and from the drop down list select wlan0. if you got security settings enabled you'll need to enter that info also. sorry i can't help you more, i'm at my desktop, not my wireless laptop, so this info is from memory.

---

### Post by jampeeters on 2007-03-05
> **oilchangeguy said:**
> to the left of the clock (in version 6.06) you should see a two screened icon. open that, and from the drop down list select wlan0. if you got security settings enabled you'll need to enter that info also. sorry i can't help you more, i'm at my desktop, not my wireless laptop, so this info is from memory.

oilchangeguy,
thanks for replying. Unfortunately I cannot select wlan0. The only choices i have are lo, and eth1.

Are there other possibilities?

---

### Post by oilchangeguy on 2007-03-05
in version 6.06 select system, administration, networking. from there you should probably see your nic card, wireless adapter, and modem. highlight the wireless adapter and select configure (again this is from memory) follow the steps needed to configure it.

---

### Post by whilenski on 2007-03-14
In 6.10, I've noticed that sometimes you need to go into Configure, check off Enable This Connection, and also put in the SSID of the AP you are trying to connect to.

On mine, I had to do this in order to get any connection from my AP, and it was showing up as you explained yours did.  Mine is on Eth1.

Good luck!

---

### Post by SactoBob on 2007-03-14
An easy way to check is to install network-manager-gnome.
When you reboot after installation, you can put the pointer over the network icon at the top of the screen.  If your card is active and working, it will show available networks and prompt you along to connect.

If you don't see any wireless, then you were incorrect about the card working properly.

---

