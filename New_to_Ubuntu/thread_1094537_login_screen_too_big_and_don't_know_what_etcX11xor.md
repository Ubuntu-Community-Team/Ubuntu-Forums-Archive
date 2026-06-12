---
title: "login screen too big and don't know what /etc/X11/xorg.conf is"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by ni ni on 2009-03-12
Hello all,

I am so happy with Ubuntu! but I am a newbie.

My login screen is too large for my resolution settings.  I know there is a way to change it using /etc/X11/xorg.conf, but I don't know what that is!!

Can anyone help me?


Thanks x x x x x x x


Ni

---

### Post by ni ni on 2009-03-12
do i go to terminal?

---

### Post by ni ni on 2009-03-14
bump!

---

### Post by impert on 2009-03-14
> do i go to terminal? 

Is it only the login screen that is a problem?
If so, you could edit the /boot/grub/menu.lst
Open a terminal and type:
```
sudo cp /boot/grub/menu.lst /boot/grub/old_menu.lst
```
to back it up. Then
```
sudo gedit /boot/grub/menu.lst
```

find the line that says "end default options".Below it is a line that starts "kernel  /boot/vmlinuz-2.x.xx-x  . . . ." where the x's are numbers. At the end of that line add vga=0x317 (This value seems to work for most people). Save the file and reboot. If it won't boot properly, <Ctrl><Alt><Delete> to force a reboot, then hit 'e' when the boot screen shows, and remove it from the kernel line.

If you want to edit your xorg.conf file (if the screen resolution is wrong after booting)
```
sudo cp /etc/X11/xorg.conf /etc/X11/old_xorg.conf
```
to back up your old configuration.Then:

```
sudo gedit /etc/X11/xorg.conf

```
Before you do this, it would be a good idea to go to the man page:
```
man xorg.conf
```
or [here]("http://http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html")
There is an annotated example of an xorg.conf file [here]("http://http://crowsons.net/puters/txt/xorg.conf.fcm.txt")

One caveat: be careful with the HorizSync and VertRefresh values:
too high a value can supposedly destroy your screen, though fortunately I can't vouch for this.

---

### Post by mvalviar on 2009-03-14
When I was using hardy I followed this guide [http://ubuntuforums.org/archive/index.php/t-920837.html]("http://ubuntuforums.org/archive/index.php/t-920837.html"). I hope this helps you too.

---

### Post by ni ni on 2009-03-15
Thank you!

I followed the guide. however:

```
Scroll down (near the bottom) and you will find a line titled Section “Screen”, tabbed in twice you will find a line that reads Virtual followed by two sets of digits. You should recognize these digits as being common screen resolutions.
Be very careful here! It's better to be safe than sorry.
You may notice a High screen resolution listed here, one your monitor cannot recognize, like 1792 1344 (which defaults to 640 480), or it may be very low, like 640 480 already. My desired screen resolution for the log-in screen is 1024 768 so those are the numbers I chose to replace the numbers.

DO NOT delete the existing numbers yet. They appear to me to be in placeholders is why!

For safety reasons. Place your cursor after the first digit of the first existing number and if different from the first number already listed, type the new single digit then move left one space and delete the first number, then move back right and enter your remaining numbers, then delete the old numbers from behind it. If you are going from 1792 down to 1024, just place your cursor between the 1 and 7 and type 024 then delete the 792 ONLY. I still use this method if I'm going from 640 up to 1024, placing the cursor between the 6 and 4 as my starting point, typing the whole number 1024.
OK, move to the second number, it may be 1344 and you want 768. Use the same method here too! Place your cursor between 1 and 3, type 768, delete the 344, move left and delete the leading 1.

This may be an unnecessary overkill way of doing it. But why take chances when we're only Noob's?

Go to the top of the Screen and Select SAVE, then wait for a bit to make sure it saved before exiting the gedit program.

```

There were no numbers there for me! there was only the following:

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```


any advice????????????????? x x x x x

---

### Post by ni ni on 2009-03-15
I know now what  /etc/X11/xorg.conf is, but i'm still stuck with this.

»----(¯`v´¯)---»

---

### Post by mvalviar on 2009-03-15
I haven't noticed until now but my xorg.conf looks just like yours. I'm no GNU/Linux expert. When I was using hardy changing my screen resolution by editing xorg.conf messes up my log-in screen and I followed that guide to fix it. But when I switched to intrepid everything is perfect as is. I never edited my xorg.conf. I have nvidia and under Applications>System Tools>Nvidia X Server Settings I've noticed that it detected the make and model of my LCD monitor and configured it accordingly. Maybe you should check it there.

---

### Post by S.A.A on 2009-03-15
add these to section "screen"
```

```SubSection "Display"
		        Modes "1024x768"
		        virtual 1024 768```

```

(or any resolution you want)

---

### Post by ni ni on 2009-03-16
Do I want it to look like this??

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	SubSection "Display"
	Modes "1024x768"
	virtual 1024 768
EndSection

---

### Post by S.A.A on 2009-03-16
Yes, Just save the file then reboot.

---

### Post by ni ni on 2009-03-16
I did that and I had awful problems i couldn't even get into the GUI it was all the black screen.... I managed to revert somehow but my HUGE login screen is still huge!

---

### Post by unutbu on 2009-03-16
/etc/X11/xorg.conf is rather finicky about syntax.

What you posted in post #10 might not be completely correct for two reasons:
Your Section "Screen" only has one "EndSection".  There should be two "EndSection"s.
Also, the "virtual" keyword should be capitalized. 

See [http://ohioloco.ubuntuforums.org/showpost.php?p=6847175&postcount=7](http://ohioloco.ubuntuforums.org/showpost.php?p=6847175&postcount=7) for an example of a syntactically correct xorg.conf. You could try copying the "Screen" Section from that post and just changing the Virtual line to whatever resolution you desire.

---

### Post by ni ni on 2009-03-16
Ah, I knew I'd get caught on the sytax, or the spacing, i was so scared of editing anything cos i am new.

Thats a great idea to look at the section of the post you sent me... i'll try it right now!

---

### Post by avtolle on 2009-03-16
> **ni ni said:**
> Do I want it to look like this??

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
    SubSection "Display"
    Modes "1024x768"
    virtual 1024 768
EndSection
After "virtual 1024 768" (without the quotation marks, of course) you need an EndSubSection before EndSection. HTH.

---

### Post by ni ni on 2009-03-16
does the tabbing in, and the skipped lines make a difference?

is this okay?

PS thanks soooo much!

```
Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
SubSection "Display"
	Modes "1024x768"
	Virtual 1024 768
EndSubsection
EndSection
```

---

### Post by ni ni on 2009-03-16
THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU THANK YOU I've been battling with this for two days! i just logged in for the first time ever, being able to see the screen!!!


Thank you!

---

