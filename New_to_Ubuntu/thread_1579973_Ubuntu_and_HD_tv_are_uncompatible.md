---
title: "Ubuntu and HD tv are uncompatible?"
date: 2010-09-22
forum: New to Ubuntu
---

### Post by danielm316 on 2010-09-22
Hello everyone.
I have a HD tv (samsung) and I asked the son of a friend of my mother to create a desktop PC for me.

This are the specifications.

 1 ghz procesor AMD, 1 giga ram, 40 gigas hard disk.
6 usb ports, and a DVD writer. 


Now I want ubuntu and I insert the install CD of ubuntu 9.04 (actually is a DVD), second I reboot the PC,

Third ubuntu instalation process begins,
fourth it asks me the language
fith it asks me what I want to do I say install ubuntu.
sixth the sccreen turns black and on the screen appearas as if the computer is off, this is very weird.
The son of the friend of my mother thinks the problem is the HD tv.

Can anyone help me?

Thank you in advance.

---

### Post by LowSky on 2010-09-22
it isn't the TV... its your computer's hardware. more specifically the video card or chip.

Can you give better details of what computer parts your using. knowing you have 6 USB ports isn't as helpful as what video grahics chipset your running.

---

### Post by e79 on 2010-09-22
I would first try to install Ubuntu with a normal screen (LCD or goo old CRT). Then, if installed correctly, you can try and hook it to your HDtv. As LowSky stated, it is probably related to the graphic (video) card you are using. The default installer might not have the necessary drivers or something related to display in HD.

Hope this helps

---

### Post by Robert Aksland on 2010-09-22
> **danielm316 said:**
> Hello everyone.
I have a HD tv (samsung) and I asked the son of a friend of my mother to create a desktop PC for me.

This are the specifications.

 1 ghz procesor AMD, 1 giga ram, 40 gigas hard disk.
6 usb ports, and a DVD writer. 


Now I want ubuntu and I insert the install CD of ubuntu 9.04 (actually is a DVD), second I reboot the PC,

Third ubuntu instalation process begins,
fourth it asks me the language
fith it asks me what I want to do I say install ubuntu.
sixth the sccreen turns black and on the screen appearas as if the computer is off, this is very weird.
The son of the friend of my mother thinks the problem is the HD tv.

Can anyone help me?

Thank you in advance.

You should try connecting the TV to another graphics port, if there are more than one. You could also try to connect a monitor instead of the TV and adjust the graphic settings before trying to reconnect the TV.

---

### Post by coffeecat on 2010-09-22
A full HD TV has a pixel resolution of 1920 x 1080 which is what is found on 16:9 computer monitors in the 20-24" size range. There should be no problem with that so long as the video card is fairly recent. So I would look at the video card first.

---

### Post by sandyd on 2010-09-22
> **danielm316 said:**
> Hello everyone.
I have a HD tv (samsung) and I asked the son of a friend of my mother to create a desktop PC for me.

This are the specifications.

 1 ghz procesor AMD, 1 giga ram, 40 gigas hard disk.
6 usb ports, and a DVD writer. 


Now I want ubuntu and I insert the install CD of ubuntu 9.04 (actually is a DVD), second I reboot the PC,

Third ubuntu instalation process begins,
fourth it asks me the language
fith it asks me what I want to do I say install ubuntu.
sixth the sccreen turns black and on the screen appearas as if the computer is off, this is very weird.
The son of the friend of my mother thinks the problem is the HD tv.

Can anyone help me?

Thank you in advance.
a) whats the video card.
b) tried nomodeset?

---

### Post by danielm316 on 2010-09-22
> **LowSky said:**
> it isn't the TV... its your computer's hardware. more specifically the video card or chip.

Can you give better details of what computer parts your using. knowing you have 6 USB ports isn't as helpful as what video grahics chipset your running.

lets see, the video card is an MSI R4350
1GB DDR2
low profile design
HDMI output

The motherboard is a Foxconn M61PMV.

Hopefully that helps.
Thank you all for your concern.

---

### Post by coffeecat on 2010-09-23
> **danielm316 said:**
> lets see, the video card is an MSI R4350

That has an ATI Radeon HD 4350 chip. I think your problem is that you are trying to run 9.04 - Jaunty. I have a card with that same chip (different make)  and it runs just fine in 10.04, compiz 3d with the open-source driver too. But the open source driver in Jaunty was less developed. That chip was fairly new when Jaunty came out.

Besides, Jaunty will go end-of-life next month = no more support = no more updates. I suggest you try 10.04, Lucid Lynx. Two advantages: it will support that graphics card - I guarantee it - and it's supported for 3 years.

9.10 (Karmic) will work on that chip too but you won't get 3d acceleration with the open-source chip and the proprietary driver will be a nightmare. Also, I'm testing the Beta of Maverick (10,10) and the HD4350 card is just fine - compiz as well - in that as well

---

### Post by danielm316 on 2010-09-23
> **coffeecat said:**
> That has an ATI Radeon HD 4350 chip. I think your problem is that you are trying to run 9.04 - Jaunty. I have a card with that same chip (different make)  and it runs just fine in 10.04, compiz 3d with the open-source driver too. But the open source driver in Jaunty was less developed. That chip was fairly new when Jaunty came out.

Besides, Jaunty will go end-of-life next month = no more support = no more updates. I suggest you try 10.04, Lucid Lynx. Two advantages: it will support that graphics card - I guarantee it - and it's supported for 3 years.

9.10 (Karmic) will work on that chip too but you won't get 3d acceleration with the open-source chip and the proprietary driver will be a nightmare. Also, I'm testing the Beta of Maverick (10,10) and the HD4350 card is just fine - compiz as well - in that as well
I tried with 10.04 and now I have a little problem, when I reboot the computer and select boot from cd, the screen turns violet and a simbol of a keyboard and a simbol of a CD appear in white on the bottom of the screen.

Maybe I got it wrong when creating the ubuntu boot cd with infra recorder. Who knows.

Any advice?

Thank you in advance coffeecat.

---

### Post by formaldehyde_spoon on 2010-09-23
> **danielm316 said:**
> I tried with 10.04 and now I have a little problem, when I reboot the computer and select boot from cd, the screen turns violet and a simbol of a keyboard and a simbol of a CD appear in white on the bottom of the screen.

Maybe I got it wrong when creating the ubuntu boot cd with infra recorder. Who knows.

Any advice?

Thank you in advance coffeecat.

That sounds good. Does it not boot after that if you wait?

---

### Post by TonyChaos on 2010-09-23
> **danielm316 said:**
> I tried with 10.04 and now I have a little problem, when I reboot the computer and select boot from cd, the screen turns violet and a simbol of a keyboard and a simbol of a CD appear in white on the bottom of the screen.

Maybe I got it wrong when creating the ubuntu boot cd with infra recorder. Who knows.

Any advice?

Thank you in advance coffeecat.

I usually had to hit tab when I saw that logo, bud. I would try that. If that doesn't work then you may want to go from 9.10 to 10.04 and update through the update manager. I had a ton of issues when I updated from 9.10 to 10.04 with a LiveCD/DVD with my video. I went out and bought a new video card, which was needed anyway, just to get it to boot up and start working. I'd give that a try. Be sure to let us know what happens.

---

### Post by coffeecat on 2010-09-24
> **danielm316 said:**
> I tried with 10.04 and now I have a little problem, when I reboot the computer and select boot from cd, the screen turns violet and a simbol of a keyboard and a simbol of a CD appear in white on the bottom of the screen.

Maybe I got it wrong when creating the ubuntu boot cd with infra recorder. 

You didn't get it wrong. That is completely normal. Although I would agree that it could have been designed better.

Either wait (I think about 30 seconds) and it will boot into the installer. Or tap any key, such as the space bar, with those two icons at the bottom of the screen and you will get the normal language selection followed by the older-style boot menu. There always seems to be an appreciable delay after you select whichever menu item - at least for me.

---

