---
title: "*ERROR* EDID checksum is invalid, remainder is 87"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by Togop on 2010-05-17
Hello,
I have Asus EEEPC 1000H with Lucid installed (not UNE, but I had UNE earlied and the same problem was there, too)
Upon boot without nomodeset option I see some messages I couldn't find and the message
*ERROR* EDID checksum is invalid, remainder is 87 a few times. With nomodeset option I don't see messages when booting, but they still appear in the /var/log/kern.log file when I look through it later.
Actually, every second LOTS of entries are written to this file (I don't know whether this is normal).

I attack parts of the kern log. Those error messages are in the end, but I don't know it you'll need something else.
I've been googling this for days... It warries me because when something writes to files (i think) is uses battery. And to that file something writes things nonstop...

---

### Post by Togop on 2010-05-23
No ideas?

---

### Post by fatsdt on 2010-06-06
I have a similar message on my eeepc 1000h, but my remainder is 139.  

Unfortunately I haven't figured out what this means either.

---

### Post by John Peschken on 2010-09-28
I have the same problem with my ASUS 904. Apaprently it is a common problem with Intel and many other common video chipsets. I do not truly understand this. but it has something to do with the detection of the screen capabilities. On my system it is harmless enough. It displays the error on boot-up and that seems to be the end of it. I just hate error messages I can't solve as a matter of principle. 
 
I found something today in the FedoraForum.org discussions that might help. The answer might lie in the XORG.CONF file, at least in Fedora. Not sure if Ubuntu has that, but it probably does. I'm away from my Ubuntu machine right now, and plan to mess with it when I get home. I have attached a PDF to this message explaining it all. The solution has to do with these two lines in XORG.CONF that need to be added or modified.
 
Option "IgnoreEDID" "1"
Modes "1152X864" "1024X768" "800x600"
 
This tells whatever it is that reads XORG.CONF to not try to detect the display. This is what fails. Since it will not detect it, you then need to tell it in the "Modes" line what resolutions the display will support. Of course this line needs to be changed to match whatever modes your display will actually support. 
 
Fair warning here: I am not an expert, just a guy who stumbled into something that might offer the solution for both of us. I don't even know where to find XORG.CONF, exactly. It is untested and possibly dangerous. I fear this sort of tinkering can be filled with unintended consequences. We are overiding the automatic detection of something and substituting hard information. It's a duct tape patch on the problem. It's not a solution, it's a work-around. I sometiimes use an external display with different parameters, so I'm not sure how that will play out. See the PDF for more information. For what it's worth, I get the idea the developers are working on this, and the real solution will be in 10.10, which is due out in a couple of weeks, so unless this is a cripling problem it might be best to ignore it for a little while.
 
Good luck to both of us!
 
10/4/10 Update: I could not find the XORGCONF file, and then there's the fact that I'm playing with something I do not fully understand. I decided to wait and see what V10.10 brings.
 
 
10/12/10 Update: V10.10 may have taken care of it.  I see some messages flash by on boot-up. but if the EDID messages are still there I can't make them out.  It might still be in the logs, but I'm away from my Ubuntu machine for a few days.  In any case, whatever the problem was, it was harmless, so I have pretty much lost interest.

---

### Post by fleder on 2010-10-24
Hello,

I am currently experiencing a problem that may be related to this. Every now and then the X server on my machine will die and go back to the login screen, and when I log in again and have a look at dmesg, that's what I see at its end:

```
[  208.522553] Ending clean XFS mount for filesystem: xyz
[ 4181.311828] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 116
[ 4181.311831] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[ 4181.311833] <3>00 ff ff ff ff ff ff 00 4e 8e 0c 00 39 31 4e 50  ........N...91NP
[ 4181.311834] <3>29 0b 01 03 68 24 1b 7e eb 5e 89 a3 53 46 98 98  )...h$.~.^..SF..
[ 4181.311836] <3>11 48 4c ff ff 80 31 59 45 59 61 59 81 99 a9 4f  .HL...1YEYaY...O
[ 4181.311837] <3>e1 40 01 01 01 01 86 3d 00 c0 51 00 30 40 40 a0  .@.....=..Q.0@@.
[ 4181.311838] <3>13 00 60 08 11 00 00 1e 00 00 00 fd 00 32 a0 1e  ..`..........2..
[ 4181.311840] <3>60 1a 00 0a 20 20 20 20 20 20 00 00 00 fc 00 53  `...      .....S
[ 4181.311841] <3>2f 54 20 39 37 50 2f 39 36 50 0a 20 00 00 00 ff  /T 97P/96P. ....
[ 4181.311842] <3>00 48 56 45 52 41 30 33 31 33 31 0a 20 20 00 33  .HVERA03131.  .3
[ 4181.311843]

```I am running Ubuntu 10.10-server 64bit on an Intel i5 650 using the internal Clarkdale graphics on an Gigabyte GA-H55M-USB3 I-H55 S1156 µATX mainboard.

The /var/log/Xorg.0.log does not seem to contain anything useful, what I can see there only are a lot of modelines:

```
[  4529.664] (II) intel(0): Modeline "2048x1536"x60.0  266.95  2048 2200 2424 2800  1536 1537 1540 1589 -hsync +vsync (95.3 kHz)
[  5572.718] (II) intel(0): EDID vendor "STN", prod id 12
[  5572.718] (II) intel(0): Using hsync ranges from config file
[  5572.718] (II) intel(0): Using vrefresh ranges from config file
[  5572.718] (II) intel(0): Printing DDC gathered Modelines:
[  5572.718] (II) intel(0): Modeline "1280x1024"x0.0  157.50  1280 1344 1504 1728  1024 1025 1028 1072 +hsync +vsync (91.1 kHz)
[  5572.718] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz)
[  5572.718] (II) intel(0): Modeline "800x600"x0.0   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz)
[  5572.718] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz)
[  5572.718] (II) intel(0): Modeline "640x480"x0.0   31.50  640 664 704 832  480 489 492 520 -hsync -vsync (37.9 kHz)
[  5572.718] (II) intel(0): Modeline "640x480"x0.0   30.24  640 704 768 864  480 483 486 525 -hsync -vsync (35.0 kHz)
[  5572.718] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz)
[  5572.718] (II) intel(0): Modeline "720x400"x0.0   35.50  720 738 846 900  400 421 423 449 -hsync -vsync (39.4 kHz)
[  5572.718] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz)
[  5572.718] (II) intel(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz)
[  5572.718] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz)
[  5572.718] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz)
[  5572.718] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz)
[  5572.718] (II) intel(0): Modeline "1024x768i"x0.0   44.90  1024 1032 1208 1264  768 768 772 817 interlace +hsync +vsync (35.5 kHz)
[  5572.718] (II) intel(0): Modeline "832x624"x0.0   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz)
[  5572.718] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz)
[  5572.718] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz)
[  5572.718] (II) intel(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz)
[  5572.718] (II) intel(0): Modeline "640x480"x0.0   36.00  640 696 752 832  480 481 484 509 -hsync -vsync (43.3 kHz)
[  5572.718] (II) intel(0): Modeline "800x600"x0.0   56.25  800 832 896 1048  600 601 604 631 +hsync +vsync (53.7 kHz)
[  5572.718] (II) intel(0): Modeline "1024x768"x0.0   94.50  1024 1072 1168 1376  768 769 772 808 +hsync +vsync (68.7 kHz)
[  5572.718] (II) intel(0): Modeline "1600x1200"x0.0  202.50  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (93.8 kHz)
[  5572.718] (II) intel(0): Modeline "2048x1536"x60.0  266.95  2048 2200 2424 2800  1536 1537 1540 1589 -hsync +vsync (95.3 kHz)
```Because of that "invalid EDID checksum" thing I switched off the CRT monitor I have, but that didn't prevent another X server crash from happening while using X11VNC.

I use X11VNC frequently and have a custom autorun entry in my session configuration:
```
x11vnc -usepw -shared -forever -display :0
```I'm going to log its outputs and see whether there is something interesting to get there.

EDIT: It just crashed again. Here's the last lines from x11vnc's STDERR:

```
24/10/2010 18:07:38 created selwin: 0x2200029
24/10/2010 18:07:38 called initialize_xfixes()
24/10/2010 18:07:42 increased wireframe timeouts for slow network connection.
24/10/2010 18:07:42 netrate: 138 KB/sec, latency: 1 ms
24/10/2010 18:22:15 idle keyboard:   turning X autorepeat back on.
24/10/2010 18:24:31 active keyboard: turning X autorepeat off.
24/10/2010 18:29:28 idle keyboard:   turning X autorepeat back on.
24/10/2010 18:34:49 active keyboard: turning X autorepeat off.
24/10/2010 18:44:16 idle keyboard:   turning X autorepeat back on.
24/10/2010 18:44:30 active keyboard: turning X autorepeat off.
caught XIO error:
24/10/2010 18:44:47 deleted 36 tile_row polling images.
```And in dmesg of course another EDID error came up, with the EDID data being slightly different:

```
[ 6914.350018] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 228
[ 6914.350023] [drm:drm_edid_block_valid] *ERROR* Raw EDID:
[ 6914.350027] <3>00 ff ff ff ff ff ff 00 4e 8e 0c 00 39 31 32 50  ........N...912P
[ 6914.350030] <3>29 0b 01 03 68 24 1b 7e eb 5e 89 a3 53 46 98 24  )...h$.~.^..SF.$
[ 6914.350034] <3>11 48 4c ff ff 80 31 59 45 59 61 59 81 99 a9 4f  .HL...1YEYaY...O
[ 6914.350037] <3>e1 40 01 01 01 01 86 3d 00 c0 51 00 30 40 40 a0  .@.....=..Q.0@@.
[ 6914.350040] <3>13 00 60 08 11 00 00 1e 00 00 00 fd 00 32 a0 1e  ..`..........2..
[ 6914.350043] <3>60 1a 00 0a 20 20 20 20 20 20 00 00 00 fc 00 53  `...      .....S
[ 6914.350046] <3>2f 54 20 39 37 50 2f 39 36 50 0a 20 00 00 00 ff  /T 97P/96P. ....
[ 6914.350049] <3>00 48 56 45 52 41 30 33 31 33 31 0a 20 20 00 33  .HVERA03131.  .3
[ 6914.350051]
```For the time being, does anybody know some more logs that might be useful to have a look at?

I may just try to edit the xorg.conf and set
```
Option "UseEDID" "FALSE"
```and copy in the modelines . That is, if I can find that file. It does not seem to exist.

Thanks in advance,
fleder

---

### Post by fleder on 2010-10-24
Yes, /etc/X11/xorg.conf really does not exist. I attempted to create one with
```
sudo Xorg -configure
```but all I got was:
```
Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.


Please consult the The X.Org Foundation support
         at http://wiki.x.org
 for help.

 ddxSigGiveUp: Closing log
```I guess that means that the X server must not be running while doing this and I've got to get into that "fail-safe" boot mode for that ... ?

---

### Post by krunge on 2010-10-24
> **fleder said:**
> 

```
24/10/2010 18:07:38 created selwin: 0x2200029
24/10/2010 18:07:38 called initialize_xfixes()
24/10/2010 18:07:42 increased wireframe timeouts for slow network connection.
24/10/2010 18:07:42 netrate: 138 KB/sec, latency: 1 ms
...
24/10/2010 18:44:30 active keyboard: turning X autorepeat off.
caught XIO error:
24/10/2010 18:44:47 deleted 36 tile_row polling images.
```

If the X server that x11vnc is connected to dies or exits, x11vnc will exit with 'caught XIO error' (i.e. x11vnc can no longer perform I/O with the X server.)  So I suspect this is a symptom, not a cause.

---

### Post by fleder on 2010-10-24
> If the X server that x11vnc is connected to dies or exits, x11vnc will  exit with 'caught XIO error' (i.e. x11vnc can no longer perform I/O with  the X server.)  So I suspect this is a symptom, not a cause.That's what is my impression too.

I did some further research and found out that reading the EDID from that CRT I use has only an about 60% success rate for getting a valid EDID data block.
By the way I also noticed that the EDID can be retrieved from my CRTs even when they are disconnected from the mains.

The thing is, I have been using this monitor for about 3 years now with other Mainboards (Intel D945GCLF and D945GCLF2) using Debian Lenny and various Ubuntu releases up to 10.04-server without those kind of problems. This started when I got the new mainboard and did a fresh 10.10-server installation.

I have another identical CRT to the one that's reporting EDID garbage and tried that one, the success percentage is about the same. A third, different CRT from another manufacturer got me 98 out of 100 tries. So it appears to be an issue of that one CRT model.

I re-checked that problem-prone CRT with another Ubuntu-server 10.10 box that is currently there that has a different mainboard, albeit one with an almost identical chipset and processor (Intel H55 with i5) but is from Asus, not Gigabyte. It showed the same success rate as my box did with this CRT.

So I figure the fault lies with the CRTs I have, *or* the H55 chipset is especially error-prone for this type of CRT (I could not check further because I lacked hardware).

To make sure it really is the cause I'll hook up the problematic CRT to the Asus box, let's see if that thing gets crashes too.

If it does, I will probably file a bug. It is my opinion that in case Xorg gets garbled EDID it should not crash but rather try again, or default to the last successfully read values.

fleder

This is the script I used to test the EDID success rate. It needs to be run as root or with sudo and you need the package "read-edid" installed.
```
#!/bin/bash
var_edid_parsed=""
var_nrofvalid=0
var_nrofalltries=0
var_goodpercent=0
while [ : ]
do
    var_edid_parsed="$(get-edid 2> /dev/null | parse-edid 2>&1)"
    echo "$var_edid_parsed" | grep "EDID checksum passed" &> /dev/null
    if [ $? == 0 ]
    then
        var_nrofvalid=$(($var_nrofvalid+1))
    fi
    var_nrofalltries=$(($var_nrofalltries+1))
    var_goodpercent=$(($(($var_nrofvalid*100))/$var_nrofalltries))
    echo "$var_nrofalltries tries, $var_nrofvalid times successful, ${var_goodpercent}% success rate so far."
    sleep 1
done

```

---

### Post by fleder on 2010-10-25
So ... there ... the EDID thing does not seem to cause trouble after all. The Asus box is just fine. Furthermore, I am still getting Xorg crashes on my computer with the good CRT hooked up.

I did some memtesting which didn't find any errors, I even switched the two RAM units with each other as to make the GPU allocate RAM from the other unit and memtested again. All clean.

I then switched the i5 processors, maybe on mine the GPU is bad? Nope, it was still my box whose X server went down repeatedly.

So it seems to be the Gigabyte GA-H55M-USB3 I-H55 S1156 µATX mainboard after all, as far as I can tell. Either the model is no goodie with Ubuntu-server 10.10 or it simply is a damaged unit.

I think I'll do some more memtesting and if that doesn't hit an error send I will send the Gigabyte back and go get the Asus one as well. :???: 

Of course I do not intend to keep any knowledge about a mainboard that most likely works well with Ubuntu-server 10.10 from you: It is an Asus P7H55D-M PRO.

Meh, that kinda sucked... #-o

fleder

---

### Post by fleder on 2010-10-28
It is very weird. 

Having placed the old Intel D945GCLF2 mainboard back into my Xorg-crashing computer, I was already stowing away the Gigabyte mainboard to send it back when I noticed that Xorg was *still* crashing.

Bad Ubuntu install? Maybe. Therefore I put the Gigabyte board in again, zeroed out my hard drive and, ever so carefully, installed Ubuntu 10.10-server anew.

Nope. Still crashes.

Just for the heck of it I restored a backup of the previous Ubuntu 10.04-server installation.

That was yesterday. Up until now I have had no Xorg crashes at all.

Said backup even runs on the same kernel, as 10.10 does, 2.6.35-22.

Really, I am at loss to explain all that. Regression in Xorg that only surfaces when 10.10 is being installed using said Gigabyte mainboard, and that keeps persisting on other boards too then? That does sound somewhat far-fetched for me. Anybody got better ideas?

Right now I am contemplating whether I should still get the Asus board.

---

### Post by fleder on 2010-10-30
Just  to have you know it, the Gigabyte mainboard seems to be innocent.

I hooked up my drives to the Asus board and installed 10.10-server on that just to make sure it would run if I bought this Asus board. However, I was unsuccessful and the 10.10 installation had the same issues as I had on the Gigabyte, that is, I repeatedly ended up on the gdm login screen with all my graphical programs aborted.

It seems that something I do to the clean install is causing this, not any hardware issue.

I do some "unusual" things, I have to admit that. For instance, I do not want Nautilus to keep track of the files and folders I access, so, in absence of an appropriate setting to make it stop remembering, I delete the file ".recently-used.xbel" in my home dir and replace it with a folder of the same name.
Also, I symlink away (ln -s) some applications' user settings folders to another file system because I either do not want them to store their settings in my home directory or I simply lack disk space there.

10.04-server seems to be fine with that, but it seems that 10.10-server isn't.

Currently I do not intend to inquire further because of all the time and effort that already went into this issue; 10.04 is running stable and I intend to keep it that way. If I can find the leisure to ferret out the real issue, I'll file some bugs. For now, I'm fine with 10.04 and some extra ppa resources for the kernel and other things.

Have fun,
fleder

---

### Post by anewguy on 2010-10-30
I'm going to give you an odd suggestion, because normally problems that this "solution" fixes are noticable right at boot.  I've done a lot of searching on the net, and it appears that the EDID checksum is invalid, with various remainders, is a very common thing lately.  Some have filed bug reports on it.

I did notice that a lot of these posts mention Intel graphics adapters.  I don't know if it is still valid, but there used to be a boot line parameter which worked even on non-915 graphics adapters:  i915modeset=1 or some such thing - I'd have to go searching to find it again and find the exact syntax.  I know there is the option of "nomodeset" you can place on the boot line, and I don't know if it takes the place of the old parameter of not.

What I would suggest is changing the the boot line to include nomodeset and try booting and see what happens - if the problem reoccurs then obviously it's not the fix and should be taken back out of the boot line.

Just a suggestion......

Dave ;)

---

### Post by wadesmart on 2010-11-02
In the last day or so I have been on various lists trying to figure out a problem with why I click on anything in my desktop. I was going through and found a LOT of errors like the ones youre talking about here. 

Im running ati but, how can I use this "nomodeset"? I dont know how to set that.

Wade

---

### Post by davide.cavestro on 2010-11-03
> **fleder said:**
> Yes, /etc/X11/xorg.conf really does not exist. I attempted to create one with
```
sudo Xorg -configure
```but all I got was:
```
Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.


Please consult the The X.Org Foundation support
         at http://wiki.x.org
 for help.

 ddxSigGiveUp: Closing log
```I guess that means that the X server must not be running while doing this and I've got to get into that "fail-safe" boot mode for that ... ?

I stopped the X server from a non-graphical console (CTRL-ALT-F2) using 
```
sudo /etc/init.d/gdm stop
```copied the generated config file using
```
sudo cp $HOME/xorg.conf.new /etc/X11/xorg.conf
```then restarted X using 
```
sudo /etc/init.d/gdm start
``` and everything now works on my eeepc 904HA with ubuntu 10.10.
Cheers
Davide

---

### Post by Tithos on 2012-07-08
I have tried to both the latest 64bit versions and i386 versions i to am geting check sum errors

Any hep is great!

Thanks

---

### Post by wildmanne39 on 2012-07-08
Hi, this is an old thread so it has been closed please start a new thread of your own with a descriptive title.
Thanks

---

