---
title: "Dial-Up modem"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by Francis60 on 2009-03-25
What dial-up modem or fax modem, not sure what name it goes by, will work with my desk top. For my laptop I got a card that works. Not sure if eternal modem would work or if have to install an internal modem for desk top that would work with Windows and Ubuntu.
Thanks
Allan St Denis

---

### Post by Francis60 on 2009-03-25
As a P.S. to my question- I cant download any programs until I get on line, so that makes it hard to, unless there is someway to download when on Windows then transfer over to Ubuntu when I reboot. when I got the card for my laptop, Staples did it and they had to go on line first with cable which works right away with Ubuntu. I just have dial-up at home, so I do not have that option with my desktop, unless I bring it where cable is available.
Thanks
Allan

---

### Post by lkraemer on 2009-03-25
Well,
If you have access to a wired LAN (Etherent) or Wifi, you can
upgrade/Download easily.  Other than that you can still use 
a direct connection to LAN from work and use keryx to copy the
files to a USB Memory stick, and then to your computer when you
get home. (Ubuntu ONLY support right now)

[http://keryx.betaserver.org/](http://keryx.betaserver.org/) 

For a modem I'd suggest getting a used External USRobotics Serial
modem from Ebay for $20-$40 and using a Sabrent USB to Serial Converter.
Or, buy the USRobotics USB Modem from Walmart for ~$44.00.
Or if you have a Winmodem, [www.linmodems.org](www.linmodems.org) has good info on how
to try and set them up, but you will sepnd lots of time and emails
on the Winmodem, unless you're mightly lucky.

See the following for how to set the modem up easily.  Shouldn't take
more than ~30 minutes for the first time, and much less after you have
done one setup.

Just scroll down until you see my guide.

[http://ubuntuforums.org/showthread.php?t=1100310](http://ubuntuforums.org/showthread.php?t=1100310)

Also, GOOGLE & SEARCH are your friends too!  Try Google "Howto & Dialup"
from GOOGLE URL and this forum next time and see what it displays.

lkraemer

---

### Post by Radioman991 on 2009-03-25
> **Francis60 said:**
> As a P.S. to my question- I cant download any programs until I get on line, so that makes it hard to, unless there is someway to download when on Windows then transfer over to Ubuntu when I reboot. when I got the card for my laptop, Staples did it and they had to go on line first with cable which works right away with Ubuntu. I just have dial-up at home, so I do not have that option with my desktop, unless I bring it where cable is available.
Thanks
Allan

Well, I can only speak for myself...my father-in-law is on dial-up.  I tried an old Dell internal modem..it was VERY problematic in Ubuntu.  Once I purchased an external serial dial up modem, he has no issues whatsoever.  I highly recommend a decent serial dial up modem...a US Robotics,  for example.

Good luck

---

### Post by Bearly Able on 2009-03-25
I recently configured a dial-up modem for an elderly friend's Xubuntu system.  I had difficulty using the internal modem, although I suspect that was my lack of understanding, rather than the modem not functioning.  However, all the advice said external modems are easier to configure, so I got hold of an old, second-hand Mercury modem - sorry, I don't know the model number.  Anyway, with a bit more help from the forums, I got that set up and she's had no problems with it.  Don't know if that's any help.

---

### Post by Bearly Able on 2009-03-25
Just to add, Ikraemer's the guy who finally solved my problems, so I think you're in good hands there.

---

### Post by stalkingwolf on 2009-03-25
I have never gotten an internal(software) modem to work.  I have had real good luck using Zoom and Dlink externals though.  Both USB and Serial.

---

### Post by jmore9 on 2009-03-25
For several years i used a US Robotics 56k faxmodem sportster 5686.

I used wvdial to set it up or you could use pon and poff.  I have forgotten how to setup the pon and poff maybe google for it or search the forum.

Use was easy just type pon to get on internet and poof to turn off.
If my memory serves me right , you have to also use sudo in front of pon.  Cant remember so long ago.

In wvdial all you have to do is enter your phone #, name used , and password then save .

After that just type wvdial.   Now some folks again , had to use sudo to get on probably a permissions issue.

Hope this helps.

You should be able to get a serial connection modem working faster than a win modem from my own experience.

---

### Post by Francis60 on 2009-03-25
Thanks for all your suggestions. As a follow up, on my laptop I fooled around with it and now the dial-up not working right. Business Staples, as I said put a new fax card in and that worked. They also installed GNOME PPP, instead of using the PPPO that was in there. It all worked real good, then I fooled around with it, now when I dial online, it goes for a few seconds then stops. I think when I re configured GNOME PPP I may have done something wrong-not sure. I see there is a place for manual dial-up configure-maybe I did not do that right either. Is there a step by step for GNOME PPP to configure it right. I may have to just take it back to Staples and let them do it again, and then maybe I will learn not to fool around with things when they are already working right. As far as I my desk top I will try and external Modem as you suggested. Thanks
Allan

---

### Post by Francis60 on 2009-03-25
To IKRAMER- yah when I am windows my internet works, so I will try what you suggested and download to memory stick and then reboot to Ubuntu and install it. I guess that will work that way.
Thanks
Allan

---

### Post by Bearly Able on 2009-03-25
> **Francis60 said:**
> Is there a step by step for GNOME PPP to configure it right.

Gnome PPP uses wvdial to connect, so if you follow Ikraemer's link and the instructions for configuring wvdial, that should sort out your problems.  You might also want to read [this "how to"]("https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-f229b8b898575bbd996c4dac3de0772d430f2a02").

---

