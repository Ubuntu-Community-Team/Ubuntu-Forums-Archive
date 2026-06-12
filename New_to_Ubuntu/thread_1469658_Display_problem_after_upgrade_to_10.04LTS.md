---
title: "Display problem after upgrade to 10.04LTS"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by ehpmail on 2010-05-02
Today, my upgrade manager told me about the new version, so I downloaded the 10.04LTS ISO (alternate install), mounted it (thanks Google for the instructions here) and upgraded. Usually this works well. 

Now, my display is not correct. I googled and found something about dkpg-reconfigure xorg something, but that doesnt seem installed.

I have my computer is totally up to date with all software in the repositories, but is basically unusable due to the display.

I'm sure there was something like this before System -> Preferences -> Screen resolution. Thats not there anymore.

How do I fix my drivers and resolution?

---

### Post by senormoll on 2010-05-02
what kind of graphics card are you using?

---

### Post by sadaruwan12 on 2010-05-02
> **ehpmail said:**
> Today, my upgrade manager told me about the new version, so I downloaded the 10.04LTS ISO (alternate install), mounted it (thanks Google for the instructions here) and upgraded. Usually this works well. 

Now, my display is not correct. I googled and found something about dkpg-reconfigure xorg something, but that doesnt seem installed.

I have my computer is totally up to date with all software in the repositories, but is basically unusable due to the display.

I'm sure there was something like this before System -> Preferences -> Screen resolution. Thats not there anymore.

How do I fix my drivers and resolution?

Need to know what kind of a problem you're having is it no display or a resolution problem just give us clear description. Mention your graphic card make and model if you can that'll help us a grate deal in helping you friend.

the path to adjusting the screen resolution is System -> Preferences -> Monitors that was earlier known as Display.

---

### Post by TheHitman2010 on 2010-05-02
I had the exact same problem (and I think I still have it but need to live with it.)

When it rebooted after install, I got "GPU lockup, switching to software fbcon". After  that, the screen froze, bringing up a scrambled desktop of my Windows 7  install, or just fell to a white screen. What I did was initialized in failsafe  graphics mode, and downloaded NVIDIA driver version 173 (via Hardware Drivers). The startup screen goes into a much lower resolution before hitting  the desktop - but the desktop is running fine. Give it a try.

---

### Post by steverexon on 2010-05-02
> **ehpmail said:**
> Today, my upgrade manager told me about the new version, so I downloaded the 10.04LTS ISO (alternate install), mounted it (thanks Google for the instructions here) and upgraded. Usually this works well. 

Now, my display is not correct. I googled and found something about dkpg-reconfigure xorg something, but that doesnt seem installed.

I have my computer is totally up to date with all software in the repositories, but is basically unusable due to the display.

I'm sure there was something like this before System -> Preferences -> Screen resolution. Thats not there anymore.

How do I fix my drivers and resolution?

Resolution :

Note : I have only tested for Intel Graphics Controller.

1)To know what is your controller open a terminal and execute the following command :
	$ sudo lspci | grep -i vga

It should give message like this:
	00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

2)Make sure that your hardware is not in the blacklist. Modify the script /usr/bin/compiz.Open a terminal and execute the following command :

$ sudo gedit /usr/bin/compiz

	Search in the file the lines about the blacklist. There should be a pair of lines with your (i.e. intel) graphic card. Uncomment them (meaning: put a '#' at the beginning of the line).

It should look like this:

# blacklist based on the pci ids 
# See [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist) for details
#T="   1002:5954 1002:5854 1002:5955" # ati rs480
#T="$T 1002:4153" # ATI Rv350
#T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
#T="$T 8086:2a02 " # Intel GM965
#T="$T 8086:3577 8086:2562 " # Intel 830MG, 845G (LP: #259385)
BLACKLIST_PCIIDS="$T"
unset T

3)In xorg.conf, replace "vesa" with "intel". Open a terminal and execute the following command :
 	
$ sudo gedit /etc/X11/xorg.conf

	Search for “vesa” and replace it with “intel”
 	

4)Restart the computer and hope all should be fine ;-)

---

### Post by sunk8 on 2010-05-02
> **ehpmail said:**
> 
I'm sure there was something like this before System -> Preferences -> Screen resolution. Thats not there anymore.
How do I fix my drivers and resolution?

It's System >> Preferences >> Monitors now...

---

### Post by badandy2021 on 2010-05-02
Im having trouble with my ATI x1950 Pro, which until this update was always a pretty well supported ATI card. Simple 3-d graphics seem to be working fine, and the resolution will hit 1280x1024, but I don't believe that OpenGL rendering is enabled or installed. Anyone have any ideas or other problems with OpenGL on ATI cards? By the way, like I said before, 9.10 had my GPU running flawlessly. What happened????

---

### Post by badandy2021 on 2010-05-02
by the way, the output for the video device is
01:00.0 VGA compatible controller: ATI Technologies Inc RV570 [Radeon X1950 Pro] (rev 9a)
So it recognizes my card and I have full resolution, just no opengl. This is really bugging me...

---

### Post by timwryan on 2010-05-02
I am having a similar problem. Everything worked fine under 9.10.

My graphics card is:

[I]timryan@Tim-Laptop:~$ sudo lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)[/I]

I have found that if I run 10.04 under the kernel version:

[I]timryan@Tim-Laptop:~$ uname -a
Linux Tim-Laptop 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux[/I]

I get lots of errors but eventually the monitor works.

If I boot under the newer kernel, in low graphics mode, then I get lots of errors, but the monitor works. However, the aspect ratio (4:3) is wrong and I do not have the option of changing it in *System -> Preferences -> Monitors*.

If I boot under the newer kernel, in "normal" graphics mode, the the screen goes black a second after the Ubuntu splash screen appears.

I have also tried to boot from a USB using UNetbootin, but so far have been unsuccessful.

Ideas?

---

### Post by timwryan on 2010-05-02
> **timwryan said:**
> I am having a similar problem. Everything worked fine under 9.10.

My graphics card is:

[I]timryan@Tim-Laptop:~$ sudo lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)[/I]

I have found that if I run 10.04 under the kernel version:

[I]timryan@Tim-Laptop:~$ uname -a
Linux Tim-Laptop 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux[/I]

I get lots of errors but eventually the monitor works.

If I boot under the newer kernel, in low graphics mode, then I get lots of errors, but the monitor works. However, the aspect ratio (4:3) is wrong and I do not have the option of changing it in *System -> Preferences -> Monitors*.

If I boot under the newer kernel, in "normal" graphics mode, the the screen goes black a second after the Ubuntu splash screen appears.

I have also tried to boot from a USB using UNetbootin, but so far have been unsuccessful.

Ideas?

found a fix here: [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

---

### Post by ehpmail on 2010-05-02
> **senormoll said:**
> what kind of graphics card are you using?

I booted into Windows and went to Computer management. I can see that the manufacturer of the Graphics card is ATI Technologies. The device type: Display Adapter. I think the type is M24

---

### Post by ehpmail on 2010-05-02
> **senormoll said:**
> what kind of graphics card are you using?

I seem to be using an M24 from ATI Technologies.

---

### Post by ehpmail on 2010-05-02
> **sadaruwan12 said:**
> Need to know what kind of a problem you're having is it no display or a resolution problem just give us clear description. Mention your graphic card make and model if you can that'll help us a grate deal in helping you friend.

the path to adjusting the screen resolution is System -> Preferences -> Monitors that was earlier known as Display.

Graphics card: M24 from ATI technologies.

Problem: The computer starts up. All the applications work, but I cant see much as everything seems to be in 4 colors only. There are stripes across the screen.

Thanks for the path to Monitors. I scratched around, but there did not seem to be anything to fix the problem.

---

### Post by ehpmail on 2010-05-02
> **TrustyTory said:**
> I had the exact same problem (and I think I still have it but need to live with it.)

When it rebooted after install, I got "GPU lockup, switching to software fbcon". After  that, the screen froze, bringing up a scrambled desktop of my Windows 7  install, or just fell to a white screen. What I did was initialized in failsafe  graphics mode, and downloaded NVIDIA driver version 173 (via Hardware Drivers). The startup screen goes into a much lower resolution before hitting  the desktop - but the desktop is running fine. Give it a try.

Not sure - I don't think this is my exact problem. Everything works for me - just that the color is not right. I think its a driver problem too. Basically, I don't have any errors that show up.

---

### Post by ehpmail on 2010-05-02
> **steverexon said:**
> Resolution :

Note : I have only tested for Intel Graphics Controller.

1)To know what is your controller open a terminal and execute the following command :
	$ sudo lspci | grep -i vga

It should give message like this:
	00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

2)Make sure that your hardware is not in the blacklist. Modify the script /usr/bin/compiz.Open a terminal and execute the following command :

$ sudo gedit /usr/bin/compiz

	Search in the file the lines about the blacklist. There should be a pair of lines with your (i.e. intel) graphic card. Uncomment them (meaning: put a '#' at the beginning of the line).

It should look like this:

# blacklist based on the pci ids 
# See [http://wiki.compiz-fusion.org/Hardware/Blacklist](http://wiki.compiz-fusion.org/Hardware/Blacklist) for details
#T="   1002:5954 1002:5854 1002:5955" # ati rs480
#T="$T 1002:4153" # ATI Rv350
#T="$T 8086:2982 8086:2992 8086:29a2 8086:2a02 8086:2a12"  # intel 965
#T="$T 8086:2a02 " # Intel GM965
#T="$T 8086:3577 8086:2562 " # Intel 830MG, 845G (LP: #259385)
BLACKLIST_PCIIDS="$T"
unset T

3)In xorg.conf, replace "vesa" with "intel". Open a terminal and execute the following command :
 	
$ sudo gedit /etc/X11/xorg.conf

	Search for “vesa” and replace it with “intel”
 	

4)Restart the computer and hope all should be fine ;-)

lspci:
04:00.0 VGA compatible controller: ATI Technologies Inc M24 1P {Radeon Mobility X600]

gedit /usr.../compiz:
Could not open the file /usr/bin/compiz
gedit has not been able to detect the character encoding. Please check that you are not trying to open a binary file. Select a character encoding from the menu and try again.

I tried with both options - UTF8 and ISO-8850-15. No luck.

---

### Post by ehpmail on 2010-05-02
> **timwryan said:**
> found a fix here: [https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes](https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes)

Hi,

I looked at your fix. I'm not sure that this will apply to me.
1. I have an ATI Card.
2. I don't know yet what my problem is.
3. I'm a novice Ubuntu user - dont want to wreck my config.

Cheers.

---

### Post by ehpmail on 2010-05-02
> **badandy2021 said:**
> by the way, the output for the video device is
01:00.0 VGA compatible controller: ATI Technologies Inc RV570 [Radeon X1950 Pro] (rev 9a)
So it recognizes my card and I have full resolution, just no opengl. This is really bugging me...

Could you explain what opengl is? I have an ATI card, perhaps it may help me.

---

### Post by ehpmail on 2010-05-02
> **sunk8 said:**
> It's System >> Preferences >> Monitors now...

Thanks.

---

