---
title: "An unusual problem with my Keyboard(laptop)"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by Mikael_duke on 2011-01-23
It is a bit of a long story so I’m going to cut I as short as I can.
 

 2½ years ago I bought a laptop from the concern Mybook with windows xp on. 1year passed without problems
 

 but the most annoying thing happened I was encountered by the blue screen of death so I restarted my computer and taught that now my worries was over but no. my keyboard had stopped working and nothing I did made it work (I searched a lot around and didn't get anything solved.. could only use usb keyboard when in windows )
 

 I then thought that maybe the keyboard in my laptop had burned down so I was working on getting new spare parts to my laptop, that was hard sins it apparently it went out of production because mybook laptops went bankrupt.
 

 That aside I thought to my self, that maybe I should change to Ubuntu to see if that made any difference, herd a lot of god stuff about it Ubuntu.
 I then worked a little space for Ubuntu and changed the boot up order file because the keyboard also doesn't work in the start-up fase
 

 and surly when I stated Ubuntu up suddenly I was able to use my keyboard:) hurray.
 There is one but though, and the problem I still cant fix.. my keyboard still doesn't work in the start-up fase and I would like to get in to my bios system to change settings or maybe format my computer at some time.
 

 Hope you have some god advise and direction please note that I'm new in Ubuntu so if you could explain it in step by step :)

---

### Post by [Snc] on 2011-01-23
> **Mikael_duke said:**
> It is a bit of a long story so I’m going to cut I as short as I can.
 

 2½ years ago I bought a laptop from the concern Mybook with windows xp on. 1year passed without problems
 

 but the most annoying thing happened I was encountered by the blue screen of death so I restarted my computer and taught that now my worries was over but no. my keyboard had stopped working and nothing I did made it work (I searched a lot around and didn't get anything solved.. could only use usb keyboard when in windows )
 

 I then thought that maybe the keyboard in my laptop had burned down so I was working on getting new spare parts to my laptop, that was hard sins it apparently it went out of production because mybook laptops went bankrupt.
 

 That aside I thought to my self, that maybe I should change to Ubuntu to see if that made any difference, herd a lot of god stuff about it Ubuntu.
 I then worked a little space for Ubuntu and changed the boot up order file because the keyboard also doesn't work in the start-up fase
 

 and surly when I stated Ubuntu up suddenly I was able to use my keyboard:) hurray.
 There is one but though, and the problem I still cant fix.. my keyboard still doesn't work in the start-up fase and I would like to get in to my bios system to change settings or maybe format my computer at some time.
 

 Hope you have some god advise and direction please note that I'm new in Ubuntu so if you could explain it in step by step :)

OK, here's one from me: last time I updated my BIOS I was stupid enough to disable PS2 (my keyboard), so i went back to BIOS with a PS2 to USB dongle + keyboard and looked for that setting, enabled it again and everything worked.

So try searching through the BIOS and maybe you will find what made your keyboard stop working, it could be some weird setting like ie "Legacy keyboard support" or something.

---

### Post by Mikael_duke on 2011-01-23
my usb keyboard doesn't work in the startup face either so i can't get in to bios.

---

### Post by sandyd on 2011-01-23
> **Mikael_duke said:**
> my usb keyboard doesn't work in the startup face either so i can't get in to bios.
you disabled legacy usb support didnt ya.
some laptops (just like desktops) have a jumper pin to reset the bios.

---

### Post by Mikael_duke on 2011-01-23
since my laptop is a bit old im not sure if  legacy usb support is enable as standard bios setting, but its worth a try how do i find the jumper pin to reset the bios.

---

### Post by [Snc] on 2011-01-23
> **Mikael_duke said:**
> since my laptop is a bit old im not sure if  legacy usb support is enable as standard bios setting, but its worth a try how do i find the jumper pin to reset the bios.

Specify the model and/or check your manuals.

(When i searched for "MyBook" i got a lot of Apple hits on google, they didn't go out of production)

---

### Post by Mikael_duke on 2011-01-23
Just read the manual that came with the laptop, and there wasn't anything on the  jumper pin to reset the bios.(only how to change my cpu, ram and harddisk)
so maybe there's a better manual out there.

my computer is an Mybook ms-1719 i also just lerned from another forum the it is indentical the the MSI MS-1719


If you search mybook on google ou will get a lot of hits on the firm "Western digital my book" not the same firm sadly :(

---

### Post by [Snc] on 2011-01-24
> **Mikael_duke said:**
> Just read the manual that came with the laptop, and there wasn't anything on the  jumper pin to reset the bios.(only how to change my cpu, ram and harddisk)
so maybe there's a better manual out there.

my computer is an Mybook ms-1719 i also just lerned from another forum the it is indentical the the MSI MS-1719


If you search mybook on google ou will get a lot of hits on the firm "Western digital my book" not the same firm sadly :(

You have a MSi GX700 laptop, but MSi doesent (wan't to)  know anything about it, so here is a official MSi "GX701" (MS1719-v1.0) manual (it should be the same).

[http://www.msi.com/product/nb/GX701.html#/?div=Manual](http://www.msi.com/product/nb/GX701.html#/?div=Manual)

and it explicitly says:

> If you want to use USB device, such as mouse, keyboard, portable disk, in
DOS system or boot your system by USB device, you should enable this
function by selecting **Enabled**.


If you are not scared to open the notebook, maybe you can detach and reattach the keyboard pins (that sometimes helps)
[http://www.techfuels.com/homebuilt-systems/52678-break-apart-msi-gx700-laptop.html](http://www.techfuels.com/homebuilt-systems/52678-break-apart-msi-gx700-laptop.html)

---

### Post by Mikael_duke on 2011-01-25
p { margin-bottom: 0.21cm; }  I have know read the manual the manual to MSi "GX701" and unfortunately there wasn’t anything on a *jumper pin to reset the bios. The only bios related stuff was the normal **change settings in bios when your in it :)*

I have looked a bit around inside the laptop to see if I could spot anything looking like a jumper. But sadly without results
 


 I have already detach and reattach the laptops keyboard, and I don't think there's anything wrong with it sins it works fine when Ubuntu has loaded,  but in either the start-up face or in windows it doesn't :S :)

---

### Post by sandyd on 2011-01-25
> **Mikael_duke said:**
> p { margin-bottom: 0.21cm; }  I have know read the manual the manual to MSi "GX701" and unfortunately there wasn’t anything on a *jumper pin to reset the bios. The only bios related stuff was the normal **change settings in bios when your in it :)*

I have looked a bit around inside the laptop to see if I could spot anything looking like a jumper. But sadly without results
 


 I have already detach and reattach the laptops keyboard, and I don't think there's anything wrong with it sins it works fine when Ubuntu has loaded,  but in either the start-up face or in windows it doesn't :S :)
pull out the CMOS battery then, and leave it out for a few hours.
Bios should reset itself after that.

---

### Post by [Snc] on 2011-01-26
> **sandyd said:**
> pull out the CMOS battery then, and leave it out for a few hours.
Bios should reset itself after that.

That's what I was thinking too, but from my point of view its sort of risky, specially with older (2y+) laptops, you never know what the result will be ... 

**I've made a few laptops into nice little bricks that way, so I would** **strongly disencourage doing this!**

Unless, you have experience with it being okay ...

---

### Post by Mikael_duke on 2011-01-29
Hi guys thanks for all the good advise i finaly got it all to work after by unpluggin the cmos battery even thogh i had to Disassemble the whole thing to get to the damn battery :)

but it was worth it thank agin guys.
[]("http://www.youtube.com/watch?v=-64b_5zJ2x8")

---

