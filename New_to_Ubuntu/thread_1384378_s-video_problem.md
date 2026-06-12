---
title: "s-video problem"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by lewstherin01 on 2010-01-18
I'm using Karmic koala and have been trying to hook a tv up to my laptop.  When I plug the s-video lead in the laptop seems to pick up the screen but the screen says no signal. Here is my xorg.conf:

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Can anyone please help?

---

### Post by lewstherin01 on 2010-01-18
Anyone have any ideas?

---

### Post by warfacegod on 2010-01-18
Put your computer hardware specs up. CPU, RAM, Graphics card, etc.

FYI it's considered bad form to bump a thread much before a day has passed.

---

### Post by lewstherin01 on 2010-01-18
Sorry I was in a bit of a hurry.  
Intel Celeron M Processor 440
    * 1.86GHz, 533MHz FSB, 1MB Cache
    * Genuine Windows Vista Home Basic
    * 512MB Memory
    * 80GB Hard Drive
    *  DVD ReWriter MultiDrive
    * 15.4" Widescreen Display
    * 128MB Intel UMA 950 Shared Graphics
    * Wireless Enabled
    * Upto 1.5 hours battery life
Is that what you are looking for?

---

### Post by warfacegod on 2010-01-18
I checked out your specs online and everything seems capable of doing what you are looking to do. Perhaps more RAM would be a good idea. I've never used Intel graphics so I can't help you there and that would be the direction you will need to take with this, obviously. I can tell you this. My Graphics card driver (nVidia) has a utility in my menu with a Detect Displays function. You may want to look for something like that.

---

### Post by lewstherin01 on 2010-01-18
cheers for your help mate.  I went back to 9.04 but it's not working there either.  It's also not working in vista.  The t.v. just says that there is no signal.  I can't find any detect displays function.

---

### Post by warfacegod on 2010-01-18
Well then (Dragon Reborn) look for something that says enable second monitor or something along those lines.

---

### Post by blackened on 2010-01-18
Plug the S-Video cable into your laptop and post the output of

```
xrandr --prop
```

---

### Post by lewstherin01 on 2010-01-18
Are you a WOT fan too?

Screen 0: minimum 320 x 200, current 1280 x 800, maximum 2080 x 800
VGA disconnected (normal left inverted right x axis y axis)
LVDS connected 1280x800+0+0 (normal left inverted right x axis y axis) 345mm x 223mm
    EDID_DATA:
        00ffffffffffff000e140b1400000000
        0b110103802115780a092d9d564f9027
        21505400000001010101010101010101
        010101010101ea1a0080502010303020
        360059df100000190000000f00000000
        0000000000206e050f00000000fe0043
        543738313031353457423420000000fe
        002d42464e73a4c0ff01012020200078
    PANEL_FITTING:    full_aspect
        supported: center       full_aspect  full        
    BACKLIGHT_CONTROL:    kernel
        supported: native       legacy       combination  kernel      
    BACKLIGHT: 1 (0x00000001)    range:  (0,7)
   1280x800       60.0*+
   1024x768       85.0     75.0     70.1     60.0  
   832x624        74.6  
   800x600        85.1     72.2     75.0     60.3     56.2  
   640x480        85.0     72.8     75.0     59.9  
   720x400        85.0  
   640x400        85.1  
   640x350        85.1  
TV connected (normal left inverted right x axis y axis)
    BOTTOM: 37 (0x00000025)    range:  (0,100)
    RIGHT: 46 (0x0000002e)    range:  (0,100)
    TOP: 36 (0x00000024)    range:  (0,100)
    LEFT: 54 (0x00000036)    range:  (0,100)
    TV_FORMAT:    NTSC-M
        supported: NTSC-M       NTSC-443     NTSC-J       PAL-M       
                   PAL-N        PAL         
   1024x768       30.0  
   800x600        30.0  
   848x480        30.0  
   640x480        30.0

---

### Post by warfacegod on 2010-01-18
> Are you a WOT fan too?

Of course. One cannot be a heavy metal warfacegod and not be a fan. They are mutually incompatible planes of existence. Much like matter/antimatter particle collisions, I would blink myself out of existence if I weren't.

---

### Post by lewstherin01 on 2010-01-18
Excellent!  So what did you think of TGS?

---

### Post by blackened on 2010-01-18
Ok, so try 
```
xrandr --output TV --mode 800x600
```

Because it's an analogue signal, s-video will take some tinkering with on your end to get it just right.

---

### Post by lewstherin01 on 2010-01-18
I will try that tomorrow dude.  I don't have access to the tv right now but cheers for your help.

---

### Post by blackened on 2010-01-18
No sweat, let us know how it works out.

---

### Post by lewstherin01 on 2010-01-19
Nothing happened dude.  The laptop screen flickered a bit but nothing on the tv

---

### Post by lewstherin01 on 2010-01-20
Can anyone help?

---

### Post by blackened on 2010-01-20
As I said before, it will take some tinkering to find exactly the right settings for your hardware and it will be far too involved for anyone to hold your hand through. 

xrandr is going to be your best bet as it gives you very granular control over each interface. That said, you may also check what shows up under System->Preferences->Display, considering your s-video interface is being detected, it might give you something. 

If it doesn't, you'll have to resort to learning how to use xrandr, either via the web or by using the man page.

```
man xrandr
```

Good luck.

---

### Post by warfacegod on 2010-01-20
Greetings Dragon.

Just thought I'd let you know that I'm still here.

Also that I'm currently setting up Mythbuntu (Media Center) on my laptop. I only have S-video output to work with (TVs don't usually have VGA). When I get it to work, I'll post the steps I took. Perhaps that will at least point you in the right direction.

---

### Post by tom.swartz07 on 2010-01-20
> **warfacegod said:**
> Greetings Dragon.

Just thought I'd let you know that I'm still here.

Also that I'm currently setting up Mythbuntu (Media Center) on my laptop. I only have S-video output to work with (TVs don't usually have VGA). When I get it to work, I'll post the steps I took. Perhaps that will at least point you in the right direction.

Hey warface- if you do- could you post a link in your sig or something?

Ive been looking into doing something similar for myself, but never got around to doing it

---

### Post by warfacegod on 2010-01-20
I'll post them in this thread and here:

[http://ubuntuforums.org/showthread.php?t=1379471]("http://ubuntuforums.org/showthread.php?t=1379471")

It's this sort of...well, you see it's...in a way it's a...just read it, you'll know what it is.

---

### Post by lewstherin01 on 2010-01-21
Cheers warfacegod and blackened.  I sort of gave up today and started to blame the t.v. lol.

---

### Post by warfacegod on 2010-01-21
> **lewstherin01 said:**
> Cheers warfacegod and blackened.  I sort of gave up today and started to blame the t.v. lol.

It could very well be that your TV and computer aren't on speaking terms. Did they have a falling out? Sometimes it's best to just get everyone together and voice their gripes. Clear the air so to speak.

---

### Post by lewstherin01 on 2010-01-21
lol Well it is a t.v. that hasn't really been used in a long time so it is most likely screwed.  It seems to be working fine but it seemed to good to be true.

---

### Post by tom.swartz07 on 2010-01-21
Its not completely un-doable. 

Look for a VGA to TV scan converter. I got one EXACTLY like this one for about $20 and I could hook up any computer to any TV [http://www.meritline.com/vga-to-tv-converter---p-40917.aspx?source=nextaghdac](http://www.meritline.com/vga-to-tv-converter---p-40917.aspx?source=nextaghdac)

Its worth a shot- you just plug it in VGA out, and then you could connect it to a tv with whatever you want- s-video, RCA, VGA again?


I currently have a media desktop hooked up to an old CRT tv from 1970. haha. The res is low (640x480) but it still works!


Hope this helps!

---

### Post by warfacegod on 2010-01-21
@tom.swartz07

Are you talking about getting Mythbuntu working or my TV to connect to my laptop?

(It looks like I called you Atom)

---

### Post by tom.swartz07 on 2010-01-21
> **warfacegod said:**
> @tom.swartz07

Are you talking about getting Mythbuntu working or my TV to connect to my laptop?

(It looks like I called you Atom)

HAHA! its all good warface.

I posted that link to the scan sampler just to show that you could get anything hooked up to any TV. 

From what I gathered from the thread- it seems like the OP couldnt get his video card to output to TV. I ran into the same problems when I was going to hook up my laptop to the TV, and even just before when I attempted to hook the desktop to my media center.

---

### Post by warfacegod on 2010-01-21
Allot of this depends on what video cards you are using. In my experience, nVidia is the best Linux card, hands down. Mythbuntu worked out of the box for me. It's just a matter of the TV.

---

### Post by tom.swartz07 on 2010-01-21
> **warfacegod said:**
> Allot of this depends on what video cards you are using. In my experience, nVidia is the best Linux card, hands down. Mythbuntu worked out of the box for me. It's just a matter of the TV.

I agree- In my case, and probably the OP's case, The installed video card doesnt support TV-Out. In such a case, the scan converter is the best bet.


Now that I know about Linux and everything, my next computer will be 1000% ubuntu, complete with nVidia cards and flipping sweet SSD's.


Anywho- lewstherin01- Id say you should look into that scan converter. Its not too expensive, and its small enough you could throw it in your laptop bag and take it with you.

Good luck!

---

### Post by warfacegod on 2010-01-21
I'm going to get one myself. I have gotten TV out working on my laptop before, just not very well, so I know it can be done. I figure little scan doohickeys (<<<<I can't believe spell check didn't mark that) are good to have around. Make my life easier.

---

### Post by lewstherin01 on 2010-01-21
I will definitely try that tom. Thanks!

---

### Post by warfacegod on 2010-01-21
I got it working!

.01 I went into my nVidia X Server Settings.

.02 Lots of fiddling around.

.03 Went into X Server Display configuration, selected TV0, and clicked configure.
.04 Check Separate X Screen (Requires X restart) and clicked OK.

.05 Set resolution to 1024x768 and clicked Apply.

.06 Went through seizure of utter astonishment and shock that it worked.


The picture is barely passable, it doesn't quite fit the screen, a little bright, and it won't save the configuration when I reboot but at least it works.

This is all stuff I've done before (except the working part, that never happened) but the best I ever got was Twinview with half on my screen and half on the TV with the TV in black and white filling only a square in the middle. Here's the key:

I went to Edit Menus> hightlight nVidia X Server Settings> click properties> change Command from: /usr/bin/nvidia-settings to: gksu nvidia-settings

I found out immediately afterwards that you can get the same thing with:

> gksudo nvidia-settings

but it won't stick. You'll need to do that every time you reboot.

I'll post again with improvements like getting it to remember the settings so that I won't have to reenable the TV after every reboot.

With that kids, I leave you now to watch Captain Kirk blow up the ship...again.

---

### Post by lewstherin01 on 2010-03-01
An update on this.  I haven't had a chance to do much with this recently but I got a scart adapter today and it worked straight away :D  Thanks to anyone who gave me help with this.

---

