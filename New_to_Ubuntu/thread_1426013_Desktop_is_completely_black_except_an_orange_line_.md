---
title: "Desktop is completely black except an orange line going down left side of screen"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by mystik_spiral on 2010-03-09
Hi there,

I'm a newbie to Ubuntu and I just got my friend to install the OS system (we have dual operation now with Ubuntu and Windows). Anyway, at work, everything worked fine but now that I've taken my computer home, I've tried to start it up and it is not working. The desktop is not appearing. **It is completely black except an orange line that is going down the far left side of the screen.** I *think* everything might actually be there, you just cannot see it for whatever reason.

If anyone has an idea what the problem is and how to fix that, that would be great!

thanks,

Jason

---

### Post by mystik_spiral on 2010-03-10
please?

---

### Post by halitech on 2010-03-10
did you use the same monitor at work that you are using at home? might be an issue where if you used different monitors it is trying a resolution that your current monitor can't display properly.

---

### Post by MooPi on 2010-03-10
Just to add . Do you hear the start up music? This would indicate that your desktop is starting but not displayed.

---

### Post by Peter09 on 2010-03-10
Try holding the shift key down during boot. This should get you into the Grub menu. From there select the second option down which should read - recovery mode - this will take you to a menu which allows you to reconfigure your display.

---

### Post by mystik_spiral on 2010-03-10
> **halitech said:**
> did you use the same monitor at work that you are using at home? might be an issue where if you used different monitors it is trying a resolution that your current monitor can't display properly.

different monitor. I am using a Samsung sync master 2343BWX. I think it's a monitor issue. I am using an old PC mixed with a newer monitor. I do not know correct terminology but one of the DVI plugs/adapters that came with the monitor does not have an appropriate port at the back of my computer so I only have a single adapter plugged in (RGB IN). 

could that be the problem?

thanks

---

### Post by Peter09 on 2010-03-10
You should still be able to get to recovery mode if you have plugged in the monitor correctly. If you do not see the grub menu then you need to look at the monitor connection.

---

### Post by mystik_spiral on 2010-03-10
> **Peter09 said:**
> Try holding the shift key down during boot. This should get you into the Grub menu. From there select the second option down which should read - recovery mode - this will take you to a menu which allows you to reconfigure your display.
I've been to recovery mode before. How do I access the menu that allows me to reconfigure my display?

---

### Post by Peter09 on 2010-03-10
I'm not infront of my machine but you should see options to reconfigure X in the menu that comes up.

---

### Post by mystik_spiral on 2010-03-10
> **Peter09 said:**
> I'm not infront of my machine but you should see options to reconfigure X in the menu that comes up.
I remember when I went into recovery mode for ubuntu, most of the options were just for attempting to reboot. I will clarify and write down the different options that I can select.

btw, I edited one of my earlier messages that better explains the old PC/new monitor issue. please read that over and tell me if that could be a problem.

thanks...i'll try to go into recovery mode again and provide a sufficient update. with that said, is there a shortcut reboot key that I can hit if it's ineffective? I don't like powering the machine down by pressing the power button on the tower.

---

### Post by halitech on 2010-03-10
the adapter could be preventing Ubuntu from detecting the monitor correctly. While it is booting do you see things normally? Also, what video card is it that you are using?

---

### Post by mystik_spiral on 2010-03-10
> **halitech said:**
> the adapter could be preventing Ubuntu from detecting the monitor correctly. While it is booting do you see things normally? Also, what video card is it that you are using?

To clarify what's plugged in and what isn't for thread's sake:

my RGB IN adapter is plugged in
my DVI IN adapter is not plugged in since no appropriate port at back of computer.


As for your questions, when I am booting, it seems like everything is going to work. The little Ubuntu logo appears at the centre of the screen...then the words Ubuntu appear 3/4 up on the page...but when the desktop is supposed to appear, that's when everything goes black aside from the vertical orange line at the left side of the screen.

I got this computer re-formatted two days ago so I probably have the worst video card imaginable--in fact, I don't know what it is. Looking in my device manager, are any of these my video card?

- Legacy Video Capture Device?
- Intel 82865G Graphics Controller?

My apologies for the limited understanding of video cards and computers in general.

thanks in advance

---

### Post by halitech on 2010-03-10
It's probably the Intel graphics controller. When you get to the messed up screen, press CTRL + F2 to get to a terminal screen. Log in as your normal user then run

lspci

Look for VGA compatible controller and write it down and post it back here. You can also issue 

sudo reboot/shutdown from here to shutdown or reboot without having to use the power button.

---

### Post by mystik_spiral on 2010-03-10
> **MooPi said:**
> Just to add . Do you hear the start up music? This would indicate that your desktop is starting but not displayed.
I will let you know when I do the re-boot.

---

### Post by mystik_spiral on 2010-03-10
> **halitech said:**
> It's probably the Intel graphics controller. When you get to the messed up screen, press CTRL + F2 to get to a terminal screen. Log in as your normal user then run

lspci

Look for VGA compatible controller and write it down and post it back here. You can also issue 

sudo reboot/shutdown from here to shutdown or reboot without having to use the power button.
will try, thanks!

---

### Post by mystik_spiral on 2010-03-10
CTRL + F2 didn't get me anywhere. I was still stuck on the messed up screen. (unless it did take me to the terminal and I just couldn't see it). Of course, I forgot to turn my speakers on so I didn't get to hear if there were any start up music going.

Should I press CTRL + F2 before the messed up screen hits? Like at the Ubuntu logo or when the word Ubuntu appears?

thanks again

---

### Post by halitech on 2010-03-10
opps, sorry it should have been CTRL + ALT + F2 to get to the terminal

---

### Post by mystik_spiral on 2010-03-10
> **halitech said:**
> opps, sorry it should have been CTRL + ALT + F2 to get to the terminal
k, I'll do that. During the messed up screen or before?

---

### Post by halitech on 2010-03-10
when you get to the messed up screen

---

### Post by mystik_spiral on 2010-03-10
slowly making process.

the start up music *did* start so Ubuntu is definitely running. Also, the sudo reboot was a success so I'm not messing up my computer anymore.

as for stuff that I wrote down, this is all that I saw related:

00:02.0 VGA Compatible Controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)

I figure you want more info than that. Above that, there was host bridge information and below it was system peripheral information.

---

### Post by mystik_spiral on 2010-03-10
In the meantime, I will take Peter09's advice and go into recovery mode and see if I can find reconfiguring monitor information. I will report back.

---

### Post by mystik_spiral on 2010-03-10
Peter09:

in recovery mode, there are these options:

resume - resume normal boot
clean - try to make free space
grub - update grub bootloader
netroot - drop to root shell prompt with networking
root - drop to root shell prompt

I tried to update grub bootloader and clean and no errors came up. I tried the resume normal boot and these errors occurred:

150.4 80027 USB 2-1: device descriptor read/64, error 18
times x3

and

different # USB 2-1: device descriptor read/8, error -61
times x3

different # hub 2-0:1.0: unable to enumerate USB device on port 1

---

### Post by Peter09 on 2010-03-10
Well the next thing you could try it do the same again and select the netroot option. This should give you a textual login. Use that to get to the command shell where you could try typing
 
> startx

---

### Post by halitech on 2010-03-10
so you do have an Intel chipset for the onboard video. Try this in the terminal:

```
sudo touch /etc/X11/xorg.conf
```
then
```
sudo nano /etc/X11/xorg.conf
```

then fill it with this info

> 
Section "Monitor"
	Identifier "Monitor0"
	VendorName "AOC"
	ModelName "LM520A"
	HorizSync 30 - 60
	VertRefresh 55 - 75
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
EndSection

Section "Device"
	Identifier "Device0"
	Driver "intel"
	VendorName "Intel 82865G"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device "Device0"
	Monitor "Monitor0"
	DefaultDepth 24
	SubSection "Display"
		Depth 24
		Modes "1024x768"
	EndSubSection
EndSection

Change the monitor to match your info

taken from this post: [http://ubuntuforums.org/showpost.php?p=8793386&postcount=12](http://ubuntuforums.org/showpost.php?p=8793386&postcount=12)

---

### Post by mystik_spiral on 2010-03-10
> **halitech said:**
> so you do have an Intel chipset for the onboard video. Try this in the terminal:

```
sudo touch /etc/X11/xorg.conf
```
then
```
sudo nano /etc/X11/xorg.conf
```

then fill it with this info


Change the monitor to match your info

taken from this post: [http://ubuntuforums.org/showpost.php?p=8793386&postcount=12](http://ubuntuforums.org/showpost.php?p=8793386&postcount=12)
sorry for taking so long. I don't have a printer installed (no installation disc) so i literally had to write all of this out.

when I got to the terminal and went inside the GNU Nano, all I could see was the bar that said the name of the operation (GNU Nano) and the options at the very bottom: GetHelp, WriteOut, ReadFile, etc etc.

I'm gathering that I should have seen a lot of information/numbers in the middle? It was all black.

please advise

---

### Post by mystik_spiral on 2010-03-10
> **Peter09 said:**
> Well the next thing you could try it do the same again and select the netroot option. This should give you a textual login. Use that to get to the command shell where you could try typing
Tried this. Took me to start up page (desktop page but still in all black with orange line). CRTL ALT F2 stopped working for whatever reason so I had to power it down.

---

### Post by mystik_spiral on 2010-03-10
Thanks guys. You guys can keep giving me good advice and stuff going forward but I am literally dead. I worked an overnight shift last night and I have been up for way too long. I'll be back in the evening. Thanks again for your effort...but don't stop now!

---

### Post by halitech on 2010-03-10
> **mystik_spiral said:**
> sorry for taking so long. I don't have a printer installed (no installation disc) so i literally had to write all of this out.

when I got to the terminal and went inside the GNU Nano, all I could see was the bar that said the name of the operation (GNU Nano) and the options at the very bottom: GetHelp, WriteOut, ReadFile, etc etc.

I'm gathering that I should have seen a lot of information/numbers in the middle? It was all black.

please advise

the sudo touch created a blank file for us so when you entered in sudo nano it should have been blank. Simply start typing in what you wrote down. Just make sure you include all the proper indents when typing it in.

CTRL O will save the file, CTRL X will exit

---

### Post by mystik_spiral on 2010-03-10
Hi Halitech,

Thank you very much as I am currently responding using Ubuntu. It is a huge help that I can finally access the desktop but the resolution is definitely wrong. There's maybe two inches of black to the right of the screen and most of all, everything is too enlarged--it's almost like I'm in Windows Safe Mode or something. I've tried manually adjusting monitor and didn't do much, then I went to System > Preferences > Display and played around (detect monitors, the other resolutions, etc) and nothing fits to the proper size of it. 

please advise

---

### Post by halitech on 2010-03-10
so we are half way there then :)

when you were entering the info into xorg.conf, did you change the monitor info to match your monitor? If you have the wrong monitor info it will resort to 800x600 or maybe 640x480.

---

### Post by mystik_spiral on 2010-03-10
> **halitech said:**
> so we are half way there then :)

when you were entering the info into xorg.conf, did you change the monitor info to match your monitor? If you have the wrong monitor info it will resort to 800x600 or maybe 640x480.
Looks like I didn't change the monitor info. I am definitely on 640x480 right now and can't select the 1024x one because I simply cannot scroll down to hit Apply in the preferences haha.

Anyway, the "change your monitor info to match your monitor" part I must have missed. I just copied directly from code to what you've wrote--I'm not sure which areas I should be changing in regards to my computer monitor. What should I written down instead of the code that you've provided me?

here are the exact specs of it:

[http://www.samsung.com/hk_en/consumer/computer-peripherals/monitors/giant-series/LS23MYZAFV/XSH/index.idx?pagetype=prd_detail&tab=spec](http://www.samsung.com/hk_en/consumer/computer-peripherals/monitors/giant-series/LS23MYZAFV/XSH/index.idx?pagetype=prd_detail&tab=spec)

Perhaps you can dumb it down for me to and tell me which numbers to insert instead of what was originally provided. thanks a bunch.

---

### Post by halitech on 2010-03-10
you want to change this section
> Section "Monitor"
Identifier "Monitor0"
VendorName "AOC"
ModelName "LM520A"
HorizSync 30 - 60
VertRefresh 55 - 75
Modeline "1024x768_60.00" 63.50 1024 1072 1176 1328 768 771 775 798 -hsync +vsync
EndSection
Change the vendor name and model name to match yours. You can use
```
gksudo gedit /etc/X11/xorg.conf
```
to open the file to edit. then reboot and cross your fingers :)

---

### Post by mystik_spiral on 2010-03-10
I...don't know what my Vendor Name or Model Name is. In my last message, I edited it and added an URL that showed the specs of what my monitor is. Perhaps you can tell me what they are!

thanks yet again

model name ...2343BWX?
vendor name...?

---

### Post by halitech on 2010-03-10
I missed youy edit, sorry

Model would be SyncMaster 2343BWX and vendor would be Samsung

---

### Post by mystik_spiral on 2010-03-10
Getting better. The resolution isn't killing me anymore as it was set at 640 (now 1024) but it still doesn't look right. Everything is still a bit too enlarged and the 2 inches of black still is apparent on right side of monitor.

hmmm

---

### Post by mystik_spiral on 2010-03-10
I think the problem is that we're entering the wrong resolution in the first place. I went back into Windows and checked my graphics settings and my resolution is set at 2048 x 1152. Can Ubuntu even go into that kind of resolution? It looks perfect in Windows as it fits my screen perfectly.

thanks

---

### Post by halitech on 2010-03-10
ok, edit the file again and change this section
> Section "Screen"
Identifier "Screen0"
Device "Device0"
Monitor "Monitor0"
DefaultDepth 24
SubSection "Display"
Depth 24
Modes "1024x768"
EndSubSection
EndSection 
add the modes of "2048x1152" "1600x1200" in front of "1024x768"

---

### Post by mystik_spiral on 2010-03-10
hi,

tried it and it didn't work. maybe I need to make similar changes for this line as well?

Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

?

---

### Post by halitech on 2010-03-10
If you can't change it in the System - Admin - Resolution then you are probably right. try changing the 1024x768_60.00 to 2048x1115_60.00 then reboot and see what happens.

---

### Post by mystik_spiral on 2010-03-11
Thanks halitech. I am at work now without my computer so this will have to wait untl I return home later this morning.

---

### Post by mystik_spiral on 2010-03-11
Tried what you said and didn't work.

there are a lot of other smaller variables here from "63.50  1024 1072 1176 1328  768 771 775 798", maybe some of those have to be changed as well. I appreciate your help but we're just so close.

---

### Post by halitech on 2010-03-11
I'm not sure on how to set modelines but check out post 4 here: [http://ubuntuforums.org/showthread.php?t=487203](http://ubuntuforums.org/showthread.php?t=487203)

Hopefully it can get us past that final step to working properly

---

### Post by mystik_spiral on 2010-03-11
In the link you gave me, I went to the Modeline Generator link. Check that one out.
[http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)

Any idea where I would find all this information to put input?

---

### Post by halitech on 2010-03-11
try this

Modeline "2048x1115@0" 0.00 2048 2080 2080 2112 1115 1143 1143 1171

---

### Post by mystik_spiral on 2010-03-11
Didn't work. hmmmm

think I should make a new topic for resolution experts to attract other people or can you think of anything else that might do it?

---

### Post by halitech on 2010-03-11
if the modeline didn't do it then I'm out of ideas now.

---

### Post by mystik_spiral on 2010-03-11
Went to a website and found a NVIDIA driver that might need to be installed (supposedly for ubuntu). So I downloaded it...only problem is that now it needs an application to launch with it as doesn't know what to use. any ideas? it's a .run file

---

### Post by halitech on 2010-03-11
you have an Intel card, installing an Nvidia driver won't do any good (unless you've installed an Nvidia card without mentioning it)

---

### Post by mystik_spiral on 2010-03-11
haven't installed anything else.

---

### Post by mystik_spiral on 2010-03-11
this is strange, i'm trying to make a slight adjustment in my terminal and it says:

Error writing /etc/X11/xorg.conf: No such file or directory.

So I cannot save changes.

---

### Post by halitech on 2010-03-11
are you opening it with sudo or gksudo?

---

### Post by mystik_spiral on 2010-03-11
ha, was with sudo but now back with gksudo and changes were saved this time.  no improvements yet to speak of though.

---

