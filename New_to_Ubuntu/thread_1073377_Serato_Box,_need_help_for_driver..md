---
title: "Serato Box, need help for driver."
date: 2009-02-18
forum: New to Ubuntu
---

### Post by djmaniak on 2009-02-18
Hi all, im totally new 2 Ubuntu. 
I litteraly fall in love with this program.

Im a dj and i whant to use my Ubuntu to run Serato Scracht Live.
I have already install Serato Scracht Live with Wine. 
But with my program i have a little usb box to plug by usb to the computer.
That box take the time code signal from my vynils send it to serato programe and after to my sound system.

The only driver i found is for Win or mac os. I saw my serato box in my device manager under : USB UHCI Controller / Hub / Usb device/ usb interfarce/  ? RANE SL-1 Sound Card (with a ? in a box in front of it)

Thank you for the futur help. ](*,)

---

### Post by superprash2003 on 2009-02-18
have you looked at ubuntu studio!!It suits your needs!!

---

### Post by djmaniak on 2009-02-18
Ubuntu Studio is no the same type as serato. A do live performance with serato, Ubuntu studio is more for making and record music .

---

### Post by djmaniak on 2009-02-18
Some picture of the material

How to plug:
[IMG]http://www.rane.com/sslsetup.gif[/IMG]

Program: 
[IMG]http://serato.com/sharedimages/87/1187/1187_product_page_small.jpeg[/IMG]

Hardware:
[IMG]http://www.hip-hop.net/graphics/0000/0060/serato-scratch-live.gif[/IMG]

---

### Post by Gidskid on 2009-05-22
if you install the latest ALSA drivers it should be plug and play.
SSL may not work, but Mixxx which is like SSL's equivalent and supports the Rane SL1 and the time code vinyls. The best part is...........


..........It's FREE!

---

### Post by markus@sparkus.se on 2009-07-14
I've hooked up my Serato SL-1 box to my eeePC 1000 running the netbook remix of Ubuntu 9.04.

The SL-1 is identified correctly by Alsa when I connect it, I can send output to it using **aplay -D plughw:1,[0,1] [file]** but for some reason I can't seem to get any audio input from it. I'm running xwax ([http://xwax.co.uk]("http://xwax.co.uk/")) which detecs some sort of input but judging from the visual representation of this input it's extremely low. 

I've tried to find some way to adjust the mixer settings of the SL-1 but to no avail. The version of Alsa is 1.0.18.

This is what **dmesg** tells me when I plug in the unit:
[FONT=Courier New][18306.910666] usb 5-1: configuration #1 chosen from 1 choice
[18307.108315] cannot find HEADER
[18307.108326] snd-usb-audio: probe of 5-1:1.8 failed with error -5
[18307.108355] usbcore: registered new interface driver snd-usb-audio[/FONT]

**/proc/asound/cards**:
[FONT=Courier New] 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xd6700000 irq 22
 1 [SL1            ]: USB-Audio - SL-1
                      Rane SL-1 at usb-0000:00:1d.0-1, full speed[/FONT]

Trying to do **alsactl init 1**:
[FONT=Courier New]Unknown hardware: "USB-Audio" "USB Mixer" "USB13e5:0001" "" ""
Hardware is initialized using a guess method[/FONT]

Trying to run **alsamixer -c1**:
[FONT=Courier New]alsamixer: function snd_mixer_load failed: Invalid argument
[/FONT]
I would greatly appreciate any help to get this up and running!

---

### Post by monkeyKata on 2009-11-07
> **Gidskid said:**
> if you install the latest ALSA drivers it should be plug and play.
SSL may not work, but Mixxx which is like SSL's equivalent and supports the Rane SL1 and the time code vinyls. The best part is...........


..........It's FREE!

Hey, thanks a lot for this heads up.  I've always wanted to get and experiment with Serato and it's great to see there's some free, linux software to use with it.  

And wait... if I'm looking at this correctly, you don't necessarily need the extra equipment (like Serato's input box thingie).  Wow... thanks again for the tip.

---

