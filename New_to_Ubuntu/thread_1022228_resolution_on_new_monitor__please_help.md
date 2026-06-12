---
title: "resolution on new monitor ???? please help"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by ||Z0di4C|| on 2008-12-26
i just got an acer 22" widescreen monitor and now the screen has a blur to it and i know on windows there is a way to change your resolution but how do you do it on ubuntu 8.04 please help

---

### Post by overdrank on 2008-12-26
> **||Z0di4C|| said:**
> i just got an acer 22" widescreen monitor and now the screen has a blur to it and i know on windows there is a way to change your resolution but how do you do it on ubuntu 8.04 please help

Hi and you can use the command ```
gksu displayconfig-gtk
``` and adjust.

---

### Post by ELF_O8 on 2008-12-26
Alternatively, you can just go to System->Preferences->Screen Resolution

---

### Post by ugm6hr on 2008-12-26
> **ubuntu-freak said:**
> SCREEN RESOLUTION

To enable the correct display resolution in Ubuntu, you have several options. First of all, there is the fairly useless tool in "System > Preferences", the soon to be dead displayconfig-gtk tool, and finally, RandR - the newest method. There will be a graphical front-end (GUI) for RandR soon (keep an eye out for it in "System > Administration"), but for now you will need to use the command line. Let's say you wanted to change your resolution to 1280x800, you would need to execute the following command:

sudo xrandr -s 1280x800

If that fails, bring up a list of "supported" resolutions with this command:

sudo xrandr -q

Use the first command again and set the highest resolution that RandR claims is supported. Once that is set, try setting the resolution you know is correct, as it may now accept that resolution.

If you're still having issues, press Alt+F2 and type "gksudo displayconfig-gtk" (without "gtk" in Kubuntu), type your password and execute, then select the resolution you want from the list. Some of you may have to select a different screen/monitor in the list before you can successfully change the resolution. Reboot/logout if necessary, then go to Launchpad and report a bug.


From the Multimedia link in my signature.

---

### Post by bibleman on 2008-12-26
> **||Z0di4C|| said:**
> i just got an acer 22" widescreen monitor and now the screen has a blur to it and i know on windows there is a way to change your resolution but how do you do it on ubuntu 8.04 please help

What does a blur mean? This almost sounds like there could be a problem with the monitor itself.

xrandr is always an option to change the resolution on the fly. You can invoke it from the command line.

---

### Post by ||Z0di4C|| on 2008-12-26
when i say blur i mean not monitor but sort of hazey and i did change the resolution to what the monitor is but it still has a haze so maybe it could be the monitor?

---

### Post by DeLaney on 2008-12-26
I also got a new monitor, a 22-inch Philips Brilliance for Christmas, and have spent the past couple hours trying various suggestions on forums to get the resolution to 1680 x 1050. I've tried using xrandrm and it seems to refuse to go anywhere. I also tried *System > Preferences* and it had no options. I tried using displayconfig-gtk, which seemed to work, because I found a place where I could select my monitor (I had thought) and applied it, and restarted my computer so it could work. 

When it re-logged on it said it needed to check something, if I recall correctly, and gave me a list of resolutions I could use, the highest being 800x600. So I applied that and went back at it, trying to figure out first how to switch it back to my original settings, and then I figured I'd take a crack at the higher resolution again tomorrow. However, none of the above-mentioned methods work for even returning it to its original settings, so I seem to be stuck at 800x600. Can anyone help?

---

### Post by DaveHT on 2008-12-26
I also got a new monitor, a 22" samsung widescreen.  The highest resolution available is 1024x768 but the monitor is 1680x1050.  I have tried all the commands in this thread and the highest I can select is 1024x768.  This leaves my monitor looking out of focus (not very sharp) although it looks very crisp when I run Windows with it set to 1680x1050.

Are there any drivers or such to get to full resolution?  I am currently using 6.10 Edgy Eft.  If I upgrade to a newer version of Ubuntu will it have 1680x1050 resolution available?  Thanks in advance.

---

### Post by babyblade on 2008-12-26
I had this problem when I first changed to Ubuntu with my Dell 2005fpw monitor. This is what I used to fix the problem, you'll probably want to substitute your own video driver, etc:

Code:
> Section &#8220;Monitor&#8221;
Identifier &#8220;Generic Monitor&#8221;
Option &#8220;DPMS&#8221;
UseModes &#8220;16:10&#8243;
HorizSync 30-83
VertRefresh 60
EndSection

Section &#8220;Screen&#8221;
Identifier &#8220;Default Screen&#8221;
Device &#8220;NVIDIA Corporation NV34GL [Quadro FX 500/600 PCI]&#8220;
Monitor &#8220;Generic Monitor&#8221;
DefaultDepth 24
SubSection &#8220;Display&#8221;
Depth 24
Modes &#8220;1680×1050&#8243; &#8220;1024×768&#8243; &#8220;800×600&#8243; &#8220;640×480&#8243;
EndSubSection
SubSection &#8220;Display&#8221;
Depth 16
Modes &#8220;1680×1050&#8243; &#8220;1024×768&#8243; &#8220;800×600&#8243; &#8220;640×480&#8243;
EndSubSection
EndSection

Section &#8220;Modes&#8221;
Identifier &#8220;16:10&#8243;
ModeLine &#8220;1680×1050 (GTF)&#8221; 147.14 1680 1784 1968 2256 1050 1051 1054 1087
EndSection


//
Hope this helps!
Cheers, Laurie> 

---

### Post by DaveHT on 2008-12-26
babyblade, I'm a newbie with Ubuntu and am wondering what that means.  Am I supposed to type all that code in terminal?  What part do I need to change for my own video card?

---

### Post by DeLaney on 2008-12-27
Yeah, I don't really understand what you mean either...

---

### Post by babyblade on 2008-12-27
Honestly, I don't know. I'm a Linux-noob myself. I tried the fixes that were suggested above and they didn't work, so in frustration I had my  husband who is a (computer-guru) muck about with it. I believe that he had to make sure my video card was being recognized, and then tell Ubuntu what resolutions to make available to my monitor. I'll get him to explain it to me and let you know what it all means. 

//Laurie

---

### Post by avianbc on 2008-12-29
babyblade's response helped me as well, since I just got a brand new 22 inch widescreen monitor.

What he means is to edit the xorg.conf file to add the new resolutions.

Go to Run (Alt+F2) and type in "gksu gedit /etc/X11/xorg.conf". It will ask you for your password then bring up a config file in the text editor. BE CAREFUL editing this file as it may break your system if you do it incorrectly.

I found a section titled "Screen" and added 1680x1050 under modes. Here is what I added (changes are in bold):

> Section "Screen"
	Identifier "Default Screen"
	Device     "Radeon 9600"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     24
		Modes    **"1680x1050"** "1440x900" "1024x768"
	EndSubSection
EndSection

Save the changes and restart and go to System > Preferences > Screen Resolution to select the new resolution that you added.

---

### Post by DeLaney on 2008-12-29
Hmm... I tried that, but it still won't let me access it. Is it because I'm in low graphics mode? It won't let me into anything else, though. Whenever I boot into Linux it does this, and I tried configuring it but it never would accept it. 

At any rate, I'm still stuck at a 800x600 resolution.

---

