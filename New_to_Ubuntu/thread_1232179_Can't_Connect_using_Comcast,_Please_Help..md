---
title: "Can't Connect using Comcast, Please Help."
date: 2009-08-05
forum: New to Ubuntu
---

### Post by Caboose104 on 2009-08-05
Well I had XP and decided to switch to Ubuntu, but now I can't connect to the internet. My ISP is Comcast, I connect using Ethernet. Can someone please help me connect to the internet?

---

### Post by LunaticHiatus on 2009-08-05
what happens when you click on the network manager icon on the top right?

---

### Post by Caboose104 on 2009-08-05
Auto Eth0 is unticked but i ticked it and it looked like it was going to work but it didn't

---

### Post by Bartender on 2009-08-05
Are you using a router?  
AFAIK Comcast is still being stupid about Linux.  You need to connect from the modem to Comcast with a Windows PC.  Get signed in, connect and disconnect a few times, make sure it's working.  Then disconnect the Windows PC from the modem.  Connect a router.  Wait for it to stabilize.  You should be able to talk to the router via a Linux PC using the manual router address and Firefox, but it might be easier to use the Windows PC again in order to set up encryption, etc.
Once you have Comcast talking to a PC thru a router, Linux PC's will connect to the router wired or wireless no problem.  I have two acquaintances, both using Comcast, and I log in with our laptop to their routers without any hassle whatsoever.

---

### Post by Caboose104 on 2009-08-05
Bartender what you said was confusing since I dont really know computers that well. I have a windows laptop, is that fine in what your telling me to do? What I think your saying is to, connect to the internet via ethernet on my laptop, disconnect and reconnect a couple of times, then connect it to my linux pc and i should be fine?

---

### Post by lvleph on 2009-08-05
I have comcast, and have no issues.

Are you connected through a router? Did you have connection issues under XP?
Please do the following.
alt+f2 > gnome-terminal > enter
This will start a terminal. In the terminal type the following:
```
lspci
```
and past the output here.

---

### Post by Caboose104 on 2009-08-05
im not on my computer with linux, since im on the internet.
so pasting it would be impossible. Do you want me to look for anything specific?

---

### Post by Caboose104 on 2009-08-05
bump

---

### Post by MrWES on 2009-08-05
> **Caboose104 said:**
> bump


If the computer connected via your router and cable modem is physically a different computer; the cable modem will have the MAC address to that network card in its memory. Since the MAC address to your Ubuntu computer is different you will NOT be able to connect. If this is the case, you need to do a hard reset on the cable modem; unplugging the power will not clear the MAC address of the network card from memory. The cable modem should have a small button, and it maybe recessed, so you'll need a pen or paperclip to reset the cable modem. Disconnect the router from the cable modem, and with the cable modem power on, push the reset button in the rear of the cable modem. Reconnect it to the router and power up the router. Should work now.

Bill

---

### Post by lvleph on 2009-08-05
> **Caboose104 said:**
> im not on my computer with linux, since im on the internet.
so pasting it would be impossible. Do you want me to look for anything specific?

You should be looking for ethernet controller or wireless. I was trying to determine what card you have. It you can post the model of your ethernet/wireless card then I could help some more.

Also, you didn't answer to whether or not you are connected through a router.

---

### Post by Caboose104 on 2009-08-05
Thank you it is fixed now.

---

### Post by MrWES on 2009-08-05
> **Caboose104 said:**
> Thank you it is fixed now.

What fixed it? Just wondering....

---

### Post by LewRockwell on 2009-08-05
probably just rebooted the router...

.

---

