---
title: "Linksys WPC54GS Install"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by JerseyShoreComputer on 2007-03-29
Hello all-

After much messing around I was finally able to install my Linksys wireless PCMCIA card in my IBM Thinkpad A30 laptop. I am using Edgy Eft for now.. Here is how I did it:

1. Install ndiswrapper
2. Put in the CD that came with the card
3. TYPE: sudo ndiswrapper -i /cdrom/linksys/drivers/w2k/lsbcmnds.inf
   --> NOTE: Check the directory on your CD for the above. You will use the Win 2k or XP driver
4. TYPE: sudo ndiswrapper -m (This will make the driver auto load)
5. TYPE: sudo depmod  -a (If you get no errors, all is fine)
6. TYPE: sudo modprobe ndiswrapper
7. Install WiFi Radar from the Synaptic package manager
8. Turn off the computer.
9. Turn the computer back on WITHOUT the wireless card installed. Make sure that your ETH0 if not hooked up live either.
10. After you logon and Ubuntu loads, insert the wireless card.
11. Run WiFi Radar and configure your card, then click CONNECT
12. Switch the network adapter to WLAN0

Thats it!! It worked for me. The secret was WiFi Radar. I could not get the card to work without it. The other secret was that if I started the computer with the card installed, or with an active wired ethernet connection, it would not work either.

I hope this helps some people out there. So far, I am real happy with the way it is working. I now plan to use this older computer more than my newer Vista PC.

:popcorn:

---

### Post by chili555 on 2007-03-30
Excellent! You might just edit the title of this post to add the word SUCCESS so those searching can see you have the fix.

---

### Post by ubdai on 2007-03-30
Me thinks I will try this with my USB wifi. Trying anything at present to get laptop onto the net.

ubdai

---

### Post by JerseyShoreComputer on 2007-03-30
Thanks everyone. I hope this is successful for everyone. I assume it would probably work with the USB version too. The secret is installing WiFi Radar. Next on my hit list is getting my Bluetooth card to work.

---

### Post by denysy1 on 2007-03-31
I did everything you said, except i had to download the driver from the linksys website, but when i start WiFi radar, it just thinks for a few moment and does nothing.... any idea what i could've done wrong? I seem to have installed the driver correctly because when i tried to follow the instructions the second time it said

"driver lsbcmds already installed" and "module configuration already contains alias directive"

However when I navigate to /etc/ndiswrapper/lsbcmds it appears to be empty. Should it contain any files?
Any ideas on what i could have done wrong?

---

### Post by Artorius on 2007-03-31
I have tried using your solution but I get the following message:  couldnt copy /cdrom0/wpcs54gv3/driver/9x/lsbcmnds.inf at user/sbin/ndiswrapper-1.8 line 144.

Im just hoping that I can get my wireless card working, if not I will go get a different card.

---

