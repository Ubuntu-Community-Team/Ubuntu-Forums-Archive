---
title: "Can't connect wirelessly after upgrade to 8.10"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by Kreuger on 2008-11-07
Okay so I have my computer running to my router. My laptop and my secondary computer that my mom uses are wirelessly connected. For some reason after upgrading my mom's today to Ibex, I can't get it to connect. It comes up saying my network name, asks for the password. I put it in and it says attempting to join. After a minute or so, the box comes back up asking for the password again. If I click to show the password, I see some really long hex looking thing. When I type the password it's supposed to be, and try again the same thing happens. I can't figure out why it's not working. My laptop had no troubles. Actually when I went in to see the settings on it to try them on the second computer, it too had a hex password that was different. I can't understand what's going wrong.

Edit: I realized I had the SSID off by one letter, when I fixed it, the password seems to be the same as on my laptop, however I still can't connect. And also, no connections show when I click on the nm applet, I have to click connect to hidden network.

I also ran nmapplet in the terminal and all it says is:
> ** Message: <info> New secrets for wireless security requested; ask the user.
That's when the box comes up again asking for the password. And when I re enter it, or leave it as the hex password, it happens again

---

### Post by Kreuger on 2008-11-08
Anyone?

---

### Post by Aksu on 2008-11-08
This happens to so many users, including me. Seems like 8.10 does not communicate with wlan cards very well. Windows Vista on the same machine connects to my Apple Airport wlan without problems.. :-(

---

### Post by Kreuger on 2008-11-08
It's just so weird that it worked fine on my laptop and not this other desktop (thats wireless)

---

### Post by moyer_34 on 2008-11-17
I had this problem too with Xubuntu 8.10 on an older Dell laptop connecting through a usb wireless fob. The workaround for me was to make sure the fob was installed at boot. Seems a little like blind luck, but might be worth a shot.

---

### Post by Kreuger on 2008-11-19
Well I ended up putting Windows back on the computer for my mother, but thanks anyways

---

