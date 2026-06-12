---
title: "[SOLVED] Using the samsung blackjack as a modem? I did it on windows."
date: 2007-07-11
forum: Networking &amp; Wireless
---

### Post by ~~Tito~~ on 2007-07-11
**[SIZE="6"]I NEED THIS BECAUSE INFO ASAP PLEASE!! BLACKJACK OWNERS HELP ME OUT TOO[/SIZE]**


I did it before i installed it by tethering it, but I have to have activesync and driver for it from the install cd. I have wine but when I run the cd it doesn't display anything. (I have the Blackjack) If any one successfully did this with their Blackjack please let me know.

(If this is in the improper forum please move it to the right place Mods)

Also can you explain this in more detail? Blackjack owners can you help me 

>    1. Open gnome-ppp as root by either creatinga desktop launcher with "gksudo gnome-ppp" as the command line or typing that into the command line your self.
   2. Enter credentials
         1. [email]ISP@CINGLARGPRS.COM[/email] for the username
         2. CINGULAR1 as the password
         3. *99# as the phone number.
   3. Click setup
         1. Click detect to auto detect your modem (it shoudl find it as ttyACM0)
         2. Click init string andmakemake the following changes:
               1. Init 2 should read: ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
               2. Init 3 should read: AT+CGDCONT=1,"IP","isp.cingular"
   4. Close "setup" and click on connect. After a sort pause at "Waiting for prompt" it should connect you.

---

### Post by t4thfavor on 2007-07-11
Which part do you not understand? That should take care of it.

you must first install gnome-ppp thogh by running this command.

"sudo apt-get install gnome-ppp"

---

### Post by ~~Tito~~ on 2007-07-11
Thanks I resolved it already in another older thread that I found thanks anyways.

---

### Post by t4thfavor on 2007-07-11
Perhaps post a link so that others can benefit from this thread?

---

### Post by ~~Tito~~ on 2007-07-11
Oh ok.

Go [here]("http://ubuntuforums.org/showthread.php?t=496389").

---

