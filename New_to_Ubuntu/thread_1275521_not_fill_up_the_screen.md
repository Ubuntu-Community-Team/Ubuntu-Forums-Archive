---
title: "not fill up the screen"
date: 2009-09-25
forum: New to Ubuntu
---

### Post by Vik_Sintus on 2009-09-25
new to ubuntu and linux world...format the windows XP and install the ubuntu 9.04 from CD without any problems, eager to start to learn ubuntu but the fisrt window(the box? the desktop?) can not maximised to fill up my screen. Any other window(box) opened inside it able to maximised but nowhere to go because limited by the very first window.

what I have done wrong?

---

### Post by marshmallow1304 on 2009-09-26
Is it possible to take a screenshot?

Applications -> Accessories -> Take Screenshot

Then we might know what's going on.

---

### Post by Vik_Sintus on 2009-09-26
thanks marshmallow
hope this screen shot attached is ok, I am not quite sure what am I doing but I follow your steps

---

### Post by Vik_Sintus on 2009-09-26
the screen shot picture shown on the attachment in my previous post is not showing a full picture of my actual screen, where large area arround the four side of my screen is just black and useless ... no where to be seen an indicator to maximise or minimise the square box(window)... or am I talking a windows language.

---

### Post by wojox on 2009-09-26
You're confusing me too. There is no Max or Min because there is no window to close. Those top and bottom task-bars are called panels. If the screen is showing black around all four edges adjust your monitor. There should be a button to adjust on it somewhere.

Did you activate any graphic drivers? Look in System > Administration > Hardware Drivers.

---

### Post by Vik_Sintus on 2009-09-26
Thank you Wojox....
it says **"no proprietary drivers are in use on this system"** :confused:

---

### Post by 3rdalbum on 2009-09-26
What graphics card do you have? If you don't know, then the results of this command will tell us:

```
lspci
```

You need to copy and paste that into the terminal at Applications > Accessories > Terminal.

---

### Post by mcduck on 2009-09-26
Actually that looks like 640x480 resolution, which the monitor doesn't even try to scale to full screen but simply displays as it is. (not that it would really make any sense to scale such a low resolution to full screen..)

So, the solution is simply to set Ubuntu to use the monitor's native resolution in System/Preferences/Display.

If there are no higher resolutions available then first check System/Adminsitration/Hardware Drivers if there's some driver for your graphics card available, and install it. If there's nothing available then please post more details about your hardware so people can help you to install the correct drivers.

---

### Post by Vik_Sintus on 2009-09-26
> **3rdalbum said:**
> What graphics card do you have? If you don't know, then the results of this command will tell us:

```
lspci
```You need to copy and paste that into the terminal at Applications > Accessories > Terminal.
 Thank you 3rdalbum I'll try that in the minute
> **mcduck said:**
> Actually that looks like 640x480 resolution, which the monitor doesn't even try to scale to full screen but simply displays as it is. (not that it would really make any sense to scale such a low resolution to full screen..)

So, the solution is simply to set Ubuntu to use the monitor's native resolution in System/Preferences/Display.

If there are no higher resolutions available then first check System/Adminsitration/Hardware Drivers if there's some driver for your graphics card available, and install it. If there's nothing available then please post more details about your hardware so people can help you to install the correct drivers.
your diagnosis looks like on the right direction.... I opened the **display preferences **it shows 800 x 600 pixels and when I change it to a smaller resolution(no option for higher)  its works as expected but the main problem is the desktop window, I mean the first square box that open s when I turn my computer on.

I will try my best to find out the details of my computer... I formated the windows XP so at the moment I don't know where should I go to find the details of my hardware.

---

### Post by mcduck on 2009-09-26
The point is that *there is no such thing* as "desktop window" that could be resized. You use too small resolution, you get too small desktop. Simple as that. It only looks like a small window or something like that because your monitor displays the picture sent from the computer as it is without scaling it, so the small-resolution image on a higher resolution display gets black areas around it.

If you really, really want to scale the picture to full screen without using a correct resolution, your display probably has a button to toggle between pixel-perfect and scaled mode (or, if it's a laptop, there's probably some function button in your keyboard to do that). But scaling the small-resolution image to full screen will only give you blurry picture. The only cproper solution is to get the graphics card drivers installed so that you can choose the correct resolution.

---

### Post by Vik_Sintus on 2009-09-26
> **mcduck said:**
> The point is that *there is no such thing* as "desktop window" that could be resized. You use too small resolution, you get too small desktop. Simple as that. It only looks like a small window or something like that because your monitor displays the picture sent from the computer as it is without scaling it, so the small-resolution image on a higher resolution display gets black areas around it.

If you really, really want to scale the picture to full screen without using a correct resolution, your display probably has a button to toggle between pixel-perfect and scaled mode (or, if it's a laptop, there's probably some function button in your keyboard to do that). But scaling the small-resolution image to full screen will only give you blurry picture. The only cproper solution is to get the graphics card drivers installed so that you can choose the correct resolution.

Yes mcduck... very well explained... even I can understand it:) thank you... I am going to put-up with small resolution until I can work out the graphic card part... thank you again

---

### Post by 3rdalbum on 2009-09-26
> **Vik_Sintus said:**
> Yes mcduck... very well explained... even I can understand it:) thank you... I am going to put-up with small resolution until I can work out the graphic card part... thank you again

Post the output of this command:

```
lspci
```

It will tell us (and you) what video card you have, and from there we can make a start toward finding a driver for you.

However, I suspect your computer uses one of the "bad" graphics chipsets like VIA or SiS, where there is minimal Linux support. If this is the case, you might be running the only drivers that are available, and I'd advise installing an ATI or Nvidia graphics card. But anyway, let's see the output of lspci, and we can take it from there.

---

### Post by Vik_Sintus on 2009-09-27
sorry 3rdalbum ,I wasn't sure where to place the code was.... so here is the result from executing the code
[B]To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

lsintus@lsintus-laptop:~$ lspci
00:00.0 Host bridge: ALi Corporation M1644/M1644T Northbridge+Trident (rev 01)
00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:04.0 IDE interface: ALi Corporation M5229 IDE (rev c3)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 01)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:0a.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 0d)
00:11.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
00:11.1 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 32)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82)[/B]

:confused: which one:) I have no idea what so ever

---

### Post by mcduck on 2009-09-27
So, your grphics card is Trident CyberBlade XPAi1.. The good thing is that it's actually supported without installing any additional drivers, and the bad thing is that you'll need to edit the config file manually to gt the correct resolution..

Anyway, this s what you need to do:

1. Open a terminal, and run this command to make a backup of your current config file, just on case something goes wrong:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

2. next, open the config file for editing:
```
gksudo gedit /etc/X11/xorg.conf
```

3. Add the following text into that file:
```
Section "Device"
  Identifier "Trident Microsystems CyberBlade XPAi1"
  Driver "trident"
  BusID "PCI:1:0:0"
EndSection

Section "Monitor"
  Identifier "Configured Monitor"
  Option "DPMS" "true"
  HorizSync 30.0-60.0
  VertRefresh 50.0-70.0
EndSection

Section "Screen"
  Identifier "Default Screen"
  Monitor "Configured Monitor"
  Device "Configured Video Device"
  DefaultDepth 24
  SubSection "Display"
  Depth 24
  Modes "1024x768" "800x600"
EndSubSection

EndSection
```
These should be safe values, assuming your display's native resolution is 1024x768. Although it would be best to use the exact HorizSync and VertRefresh values for your monitor if you manage to find them somewhere (like in the monitor's manual, if you have one).

If you need higher resolution than 1024x768 just tell and I'll give you the correct values for that. Or tell the displays model and I'll see if I can find it's specs somewhere..

4. That should be it, save the file, and restart your computer. You should have 1024x768 resolution, and I understood that the drivers even support some level of 3D acceleration. :)

---

### Post by Vik_Sintus on 2009-09-28
the codes you provide is already exist in the file (xorg.conf) but the screen still not changing it size. I am a happy man though because I learn something else other then trying to fix the screen resolution. Thanks a heaps 
any other suggestion? always welcome

---

### Post by mcduck on 2009-10-01
Maybe you could try leaving out the 800x600 from the options, although having it available shouldn't prevent you from getting 1024x768.

Anyway, if that change doesn't do the trick then I have no idea what you could do.  According to all pages I found discussing your graphics card in Ubuntu 9.04 that should work.

[http://jamie.workingagenda.com/blog/2009/07/19/fixing-screen-resolution-in-toshiba-1405-s-151-in-ubuntu-9-04/]("http://jamie.workingagenda.com/blog/2009/07/19/fixing-screen-resolution-in-toshiba-1405-s-151-in-ubuntu-9-04/")

---

### Post by trenn on 2009-10-18
> **mcduck said:**
> Maybe you could try leaving out the 800x600 from the options, although having it available shouldn't prevent you from getting 1024x768.

Anyway, if that change doesn't do the trick then I have no idea what you could do.  According to all pages I found discussing your graphics card in Ubuntu 9.04 that should work.

[http://jamie.workingagenda.com/blog/2009/07/19/fixing-screen-resolution-in-toshiba-1405-s-151-in-ubuntu-9-04/](http://jamie.workingagenda.com/blog/2009/07/19/fixing-screen-resolution-in-toshiba-1405-s-151-in-ubuntu-9-04/)
Hello mcduck and thanks..The replacement file for xorg.conf worked for me on my old Winbook J1 using Xubuntu 9.0.  I have the Trident Cyberblade i1 driver but I just changed the name where needed and left everything else as you suggested.  I'm a newbie and I've been at this display for close to a week,  and I am so happy to have it resolved.  Now, what do you know about wireless adapters..<g>  different topic.   Thanks again for your time.

---

