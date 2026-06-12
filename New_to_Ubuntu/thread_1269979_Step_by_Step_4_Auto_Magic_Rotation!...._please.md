---
title: "Step by Step 4 Auto Magic Rotation!.... please?"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by R3fr4cti0n on 2009-09-18
i have tryed and tried and tired but i either crash my system or it simply dose not work. please can someone write me a step by step? i just want 2 things to work on my tablet pc, auto rotation and touch. i have touch i just need the other. 
thanks!

---

### Post by Favux on 2009-09-19
Hi R3fr4cti0n,

As I understand it hp-wmi should be installed automatically in Jaunty.  Have you been trying to compile it?  Let's see if it is there.  Enter into a terminal:
```
modprobe -l | grep hp-wmi
```
In Intrepid that returns for me:
```
/lib/modules/2.6.27-14-generic/extra/hp-wmi.ko
```
You should see something similar.  Post the output.

Now let's find out if it is active.  In a terminal enter:
```
lsmod
```
The output will have a list of your current active kernel modules.  Look through it carefully.  You should see these two:  wmi and hp-wmi.  Let me know if you see both.  Or if one is missing, which one.

---

### Post by R3fr4cti0n on 2009-09-19
i get
 ```
kernel/drivers/misc/hp-wmi.ko
```
and neither wmi or hp-wmi. are there

you dont have to look i checked line by linei just thought i put it in case there was something other info you needed

```
julian@laptop:~$ lsmod
Module                  Size  Used by
michael_mic            10880  2 
arc4                   10240  2 
ecb                    11392  2 
binfmt_misc            18572  1 
ppdev                  16904  0 
bridge                 63776  0 
stp                    11140  1 bridge
bnep                   22912  2 
input_polldev          12688  0 
lp                     19588  0 
parport                49584  2 ppdev,lp
snd_hda_intel         557492  4 
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_pcm                99464  4 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
snd_seq_midi           15744  0 
snd_rawmidi            33920  1 snd_seq_midi
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  2 snd_pcm,snd_seq
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fglrx                2376104  34 
snd                    78920  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ieee80211_crypt_tkip    17920  0 
uvcvideo               69640  0 
video                  29204  0 
i2c_piix4              20112  0 
shpchp                 44572  0 
soundcore              16800  1 snd
psmouse                64028  0 
wl                   1286352  0 
pcspkr                 11136  0 
serio_raw              14468  0 
compat_ioctl32         18304  1 uvcvideo
videodev               45184  2 uvcvideo,compat_ioctl32
v4l1_compat            23940  2 uvcvideo,videodev
output                 11648  1 video
joydev                 20992  0 
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
ieee80211_crypt        14596  2 ieee80211_crypt_tkip,wl
usbhid                 47040  0 
usb_storage           115520  0 
r8169                  46596  0 
mii                    14464  1 r8169
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit
julian@laptop:~$ 

```

favux, do you do this stuff for a living? how did you learn all this could you recomend some books?

---

### Post by Favux on 2009-09-19
Hi R3fr4cti0n,

No, I just like messing around.  My hobby was messing around in Windows and I switched to Ubuntu about 10 months ago.

That's interesting.  hp-wmi requires wmi to work.  So let's see if wmi is there too somewhere.  Show me the output of:
```
modprobe -l | grep wmi
```

---

### Post by harisund on 2009-09-19
Not sure if my input is any valuable, but I have an old Toshiba M200 Tablet PC. 

The "auto rotation" feature doesn't work. Meaning the accelerometer is not recognized by the Linux kernel. 

However, if it is just rotation you want, xrandr works just fine. Here are some quirks - 

xrandr rotation needs a line 
Option "RandRRotation" True 
in the Devices section of the /etc/X11/xorg.conf 

xrandr rotation doesn't necessarily rotate the axis / orientation of my stylus. So I need to use xsetwacom to do that. 

I am using the official Nvidia drivers from the Nvidia website directly. The driver in the Ubuntu repos 177.14 or something doesn't work properly, and the website has 177.20. You might also want to check something out as without the proper graphics driver rotation is hard to achieve.

---

### Post by R3fr4cti0n on 2009-09-19
```
julian@laptop:~/Documents$ modprobe -l | grep wmi
kernel/drivers/misc/acer-wmi.ko
kernel/drivers/misc/hp-wmi.ko
kernel/sound/core/snd-rawmidi.ko
julian@laptop:~/Documents$ 
```

favux, will i need to do this all over with kde, i have it so i can choose either gnome or kde befor i "login" its all on the same partition

---

### Post by Favux on 2009-09-19
Hi harisund,

Thanks for chipping in.  Actually he's working off this HOW TO:  [http://ubuntuforums.org/showthread.php?p=6274392#post6274392](http://ubuntuforums.org/showthread.php?p=6274392#post6274392)  So he could use the rotation scripts in Method 1 or Tom Jaegers wacomrotate daemon in Method 3.  What he's trying to do is get rotation based on the switch in his swivel hinge.  We've figured out how to get that event recognized using the above kernel modules.


Hi R3fr4cti0n,

Yes you'll have to do this for KDE to.

I think we've found a problem.  Wmi should have been installed and it doesn't seem to be there.  I don't know why.  But hp-wmi won't work without it.  I know Ayuthia's kernel deb has the patched hp-wmi.

Let's assume it is there and the grep command isn't pulling it up.  So to get the system to start both modules we need to add them to the "modules" file in "/etc/" as described in post #225 here:  [http://ubuntuforums.org/showthread.php?t=996830&page=23](http://ubuntuforums.org/showthread.php?t=996830&page=23)

Add "wmi" and "hp-wmi" (without the quotes) to the end of the "modules" file, each on a separate line, using:
```
gksudo gedit /etc/modules
```
And then reboot.  Then do the "lsmod" command and see if wmi and hp-wmi are now in the output.

Some references/books to look at are:

[http://www.ubuntupocketguide.com/download_main.html](http://www.ubuntupocketguide.com/download_main.html)

[http://ubuntuguide.org/wiki/Ubuntu:Jaunty](http://ubuntuguide.org/wiki/Ubuntu:Jaunty)

[http://www.linuxlinks.com/article/20090405061458383/20oftheBestFreeLinuxBooks-Part1.html](http://www.linuxlinks.com/article/20090405061458383/20oftheBestFreeLinuxBooks-Part1.html)

[http://tldp.org/](http://tldp.org/)

---

### Post by harisund on 2009-09-19
> **Favux said:**
> Hi harisund,

Thanks for chipping in.  Actually he's working off this HOW TO:  [http://ubuntuforums.org/showthread.php?p=6274392#post6274392](http://ubuntuforums.org/showthread.php?p=6274392#post6274392)  So he could use the rotation scripts in Method 1 or Tom Jaegers wacomrotate daemon in Method 3.  What he's trying to do is get rotation based on the switch in his swivel hinge.  We've figured out how to get that event recognized using the above kernel modules.

Ah cool. Actually I use an exactly similar script (xrandr followed by xsetwacom) and I have it bound to the hardware switch on the swivel on the Toshiba M200 as well. Guess it is just easier to identify on Toshiba machines :)

---

### Post by R3fr4cti0n on 2009-09-25
favux,

my modular file looks like this
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
```

so you wany me to put wmi and hp-wmi at the end so it will look like this?
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
wmi
hp-wmi
```

sorry to ask but i dont want to screw up and sorry to take so long to reply i have been getting my butt kicked into submission for my accountting class.

---

### Post by Favux on 2009-09-25
Hi R3fr4cti0n,

It turns out you don't need to add wmi to modules.  I learned the Ubuntu kernel dev.s have added it into the kernel, which is why we couldn't see it in "lsmod".  So instead of being called 'wmi.ko' it's called 'wmi.h'.  And instead of being in "linux-images" it's in "linux-headers", ie the kernel.

So just add 'hp-wmi' like:
```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
hp-wmi
```
After a reboot 'hp-wmi' should show up in "lsmod" entered in a terminal.

This should make the infrastructure available in gnome and KDE.  Then for each you'll need to add the applet.

Hope accounting's going OK.

---

### Post by R3fr4cti0n on 2009-09-25
ok, its there now what?

---

### Post by Favux on 2009-09-25
Hi R3fr4cti0n,

Alright, since hp-wmi is in lsmod you should be set up for Magick.

Just download Magick 0.2-4 and follow the instructions in post #279 here:  [http://ubuntuforums.org/showthread.php?t=996830&page=28](http://ubuntuforums.org/showthread.php?t=996830&page=28)

By the way 0.2-5 should be out shortly.

---

### Post by R3fr4cti0n on 2009-09-25
ok i installed it and rebooted was that the last step?

---

### Post by Favux on 2009-09-26
Hi R3fr4cti0n,

Once you installed it, it should be working.  Do you have CellWriter installed (through Synaptic)?  Did you right click on the icon in upper right and remove eraser in Advanced Settings?

---

### Post by R3fr4cti0n on 2009-09-26
i dont have cellwriter, darn how do i uninstall gona restart from beginning?

---

### Post by Favux on 2009-09-26
Hi R3fr4cti0n,

You don't need to do that.  Just go ahead and install CellWriter.  If Magick is installed correctly you should see a clockwise green arrow top right in upper panel.

---

### Post by R3fr4cti0n on 2009-09-26
ya, no dice maby i needed cell writer first?

---

### Post by Favux on 2009-09-26
Hi R3fr4cti0n,

Are you able to see the Magick icon, the green arrow?  If you right click on it can you see Advanced Settings?

---

### Post by R3fr4cti0n on 2009-09-26
no the only green arrow i see on the cellwriter is the "enter" arrow  next to the "keys" buttom and if i right click it nothing happens.

---

### Post by Favux on 2009-09-26
Hi R3fr4cti0n,

The Magick Rotation icon (curved green arrow) should be in the same area as the CW icon for CellWriter.  Not in CellWriter.  It should also be next to the Network Manager icon and speaker icon.  In the notification area to the right on the top panel in gnome.  It is the same green arrow icon that was in the Magick Rotation folder you downloaded.

I just posted Magick Rotation 0.2-5.  You could give that a try.  The instructions are slightly different.  Maybe that will help.  It's in post #291 here:  [http://ubuntuforums.org/showthread.php?t=996830&page=30](http://ubuntuforums.org/showthread.php?t=996830&page=30)

---

### Post by R3fr4cti0n on 2009-09-27
Got it! Thanks favux!!

---

### Post by Favux on 2009-09-27
Hi R3fr4cti0n,

I hope you mean Magick Rotation 0.2-5 is working for you.  Is it?

---

### Post by R3fr4cti0n on 2009-09-27
yes, it hung up on me once but i tried it a few more times and no problems, i am in the process of writing a cookie cutter step by step for the all Tx2 features, i have meet like 8 ppl in college that love this thing for art and love the friendlyness of ubuntu for art work (not to mention how fast, reliable ubuntu is and how Beautiful, and engaging compiz is) and so ppl dont have to hunt around and screw up like i did 30 or 40 times before they get it right, i thought this could be how i give back to the commuity. The last thing on my list is the bezel buttons. So if you dont mind could you point me in the direction of the forum post for tx2 buttons?
thanks!

---

### Post by Favux on 2009-09-27
Hi R3fr4cti0n,

Outstanding!  I am happy Magick's working for you.

The bezel buttons are a tough nut.  If you go through the Rotation HOW TO, first page of the thread that Magick's posted on, there's a lot about them and links to more stuff.  Like we've talked about only 1 of the 3 on the TX2z work and we don't know how to get the other two working.  The Rotation HOW TO talks about key binding which you could use to change the assignment of the one button working.

Glad you're helping out other TX2z users on your campus.  That's good of you.

---

### Post by Favux on 2009-09-27
Hi R3fr4cti0n,

I just found a long standing bug in Magick.  I corrected it and replaced Magick Rotation 0.2-5 with the corrected version (same label).  You probably want to download and install the fixed version of 0.2-5.

---

