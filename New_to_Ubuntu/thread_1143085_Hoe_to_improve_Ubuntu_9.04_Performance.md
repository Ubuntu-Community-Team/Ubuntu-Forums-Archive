---
title: "Hoe to improve Ubuntu 9.04 Performance"
date: 2009-04-29
forum: New to Ubuntu
---

### Post by rvgsd on 2009-04-29
Hi, 

I recently installed Ubuntu 9.04. I now have a dual boot system with Windows XP on one partition. 

I found that Ubuntu runs very Slow as compared to Windows XP.
What should I do to improve ubuntu performance?

My system is Pentium 2.4 Ghz(Single core) and 1 GB RAM.

Thanks for any help.!

Regards,
RSD.

---

### Post by Temposs on 2009-04-29
What in particular are you running when you notice that it is slow?

You could start by turning off Desktop Effects. Go to System->Preferences->Appearance->Visual Effects. Then choose "None". That will speed up your system, if you had it on another setting.

---

### Post by MockY on 2009-04-29
Do you happen to have an Intel graphic card?

---

### Post by dannysanchez7924 on 2009-04-29
what bit of linux are you using, 32 or 64?

---

### Post by ibuclaw on 2009-04-29
> **rvgsd said:**
> Hi, 

I recently installed Ubuntu 9.04. I now have a dual boot system with Windows XP on one partition. 

I found that Ubuntu runs very Slow as compared to Windows XP.
What should I do to improve ubuntu performance?

My system is Pentium 2.4 Ghz(Single core) and 1 GB RAM.

Thanks for any help.!

Regards,
RSD.

Do you have any benchmarks to prove this?

IMO, don't try to make something fast unless you can quantify slow.

Regards
Iain

---

### Post by Temposs on 2009-04-29
tinivole is correct. You should identify exactly at what point you notice something in Ubuntu being slower than in Windows.

---

### Post by NightwishFan on 2009-04-29
Define slow.

Slow to boot up: Likely bad or poorly supported hardware, or disk.

Slow opening programs: Install preload if it is not too slow, if it is really slow, you might have installed with a bad disk.

Slow youtube: Disable compiz, and make sure you have the non free flash plugin.

Slow Graphics: Disable compiz desktop effects.

Etc...

If you want to define Windows Xp as fast, try multitasking on it...

---

### Post by rvgsd on 2009-04-29
HI,
Appreciate the reply guys. 

Its a 32 bit Linux. It is slow in the sense for example if I double click on a folder, it pauses for a while and then starts opening it. I have trouble while scrolling up and down in firefox. 

I also have WindowsXP on the other partition which runs smooth, with and ANtivirus and Anti Spyware running continuously in the background. Thus to define Slow, i compare WinXp and Ubuntu 9.04.

I have disabled all the graphic effects, and also some unneeded services like Bluetooth and Visual assistance, etc. Still doesnt help much.

Thanks for your help.
What should I try next?

Regards,
RSD.

---

### Post by oldos2er on 2009-04-29
Look in the Tutorials & Tips subforum, I'm sure there's some info there on speeding things up.

---

### Post by viljun on 2009-04-29
Disable desktop search indexing (in services) - I suppose it's in 9.04, too.

Then go to terminal and write "top" and press enter and you'll see what's eating your processor speed. Post its output here.

---

### Post by rvgsd on 2009-04-29
top - 17:45:56 up 48 min,  2 users,  load average: 0.38, 0.71, 0.59
Tasks: 113 total,   4 running, 109 sleeping,   0 stopped,   0 zombie
Cpu(s): 36.5%us,  3.7%sy,  0.0%ni, 59.1%id,  0.0%wa,  0.7%hi,  0.0%si,  0.0%st
Mem:   1026520k total,   577872k used,   448648k free,    29988k buffers
Swap:   787144k total,        0k used,   787144k free,   318036k cached

PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND 

 2605 root    20   0 52828  24m 9100 S 22.6  2.5   4:31.75 Xorg               
 4031 rsd     20   0  294m  96m  29m R 12.0  9.6   6:33.45 firefox            
 6611 rsd     20   0 33528  13m 9328 R  2.7  1.4   0:01.02 gnome-terminal     
 3286 rsd     20   0 23536  10m 8412 S  0.7  1.0   0:07.93 geyes_applet2      
 3352 rsd     20   0 16376 2904 1780 S  0.7  0.3   0:04.53 gnome-screensav    
 2572 root      20   0  5180 1804 1592  S  0.3  0.2   0:00.77 hald-addon-stor    
      1 root      20   0  3084 1884  564   S  0.0  0.2   0:01.42 init               
      2 root      15  -5     0    0      0       S  0.0  0.0   0:00.00 kthreadd           
      3 root      RT  -5     0    0    0        S   0.0  0.0   0:00.00 migration/0        
      4 root      15  -5     0    0    0        S  0.0  0.0   0:00.12 ksoftirqd/0        
      5 root      RT  -5     0    0    0        S  0.0  0.0   0:00.00 watchdog/0         
      6 root      15  -5     0    0    0        S  0.0  0.0   0:00.08 events/0           
      7 root      15  -5     0    0    0        S  0.0  0.0   0:00.00 khelper            
      8 root      RT  -5     0    0    0        S  0.0  0.0   0:00.00 kstop/0            
      9 root      15  -5     0    0    0        S  0.0  0.0   0:00.00 kintegrityd/0      
    10 root      15  -5     0    0    0        S  0.0  0.0   0:00.02 kblockd/0          
    11 root      15  -5     0    0    0        S  0.0  0.0   0:00.00 kacpid

---

### Post by Sir Jasper on 2009-04-29
Hi,

Re: Firefox scrolling:

I had a similar problem and adjusted my Accessibility and Browsing settings found at Edit>Preferences>Advanced>General

There may also be other tweaks I don't know about e.g. number of lines to scroll on clicking.

My regards

---

### Post by kansasnoob on 2009-04-29
Using "top" is fine, but I'm a gui guy!

While you're running Ubuntu open System Monitor (System > Administration > System Monitor) and you can then change desktops and/or windows and scroll thru and see what's eating resources.

I'd suggest also right clicking the desktop & selecting Change Desktop Background > Visual Effects - select NONE!

---

### Post by scottuss on 2009-04-29
I wish my Hoe would improve Ubuntu 9.04 Performance. Sorry. Bad joke.

---

### Post by NightwishFan on 2009-04-30
What graphics card are you using? Ubuntu should not be slower than Windows on any machine with more than 512mb ram, unless there is a hardware issue. You might have a graphics issue. My one machine with an Intel card performs horribly using Ubuntu, because of its status.

Do as the poster above said, and post screenshots of all the tabs of Gnome-System-Monitor.

If xorg or other processes use cpu (more than 10%) constantly, you might have burned with a bad disk. To check:

[LIST=1]
[*]Put the Ubuntu CD you used to install into the drive.
[*]Open a terminal
[*]Type (without quotes) "cd /media/cdrom0" and push enter
[*]Type "md5sum -c md5sum.txt" and push enter. If it says file not found, then I got the filename wrong. If so, type md5 and push tab to autocomplete.
[/LIST]

If it says that you have any errors while checking, then you burned or downloaded the CD wrong. You can also check the CD from the boot up menu when you restart and load the live CD.

---

### Post by rvgsd on 2009-04-30
Hi all, Thanks again for your help. I really appreciate it (Really!).

I am attaching the screenshots of the system monitor along with the ouput of 'lspci -v' since I am not sure of my Graphics Card. 
I have installed Ubuntu using the "[UNetbootin]("http://unetbootin.sourceforge.net/")" ([http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)).
Would it help if I do a fresh install using a CD or DVD rom?

Ubuntu is so laggy that I rarely Logon to it (even if I want to).

Attachments:
[ATTACH]111840[/ATTACH]
[ATTACH]111841[/ATTACH]
[ATTACH]111842[/ATTACH]
[ATTACH]111843[/ATTACH]
[ATTACH]111844[/ATTACH]

Glad for the gelp and hope to make Ubuntu faster so that I can switch permanently :)

Regards,
RVGSD.

---

### Post by y_garti on 2009-04-30
first of all your computer is not so good
and second i had a similar problem with my computer and in the end i had a mother board problem one of the Capacitor got burn (so if you know how to check them its very simply if you press with your finger they need to be press towards the mother board and not the other side)

---

### Post by LowSky on 2009-04-30
that text file was impossible to read, thank the stars I could use the find feature
ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]

thats your card


[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by rvgsd on 2009-04-30
Hi, 
I read through this page
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
I checked and my system doesn't have the 'fglrx' drivers installed. So I guess thats not causing me any problems. However I checked the xorg.conf file, and it doesnt look like the one mentioned on this page. 
Thanks again.
So still do I need to mess with the xorg.conf? (I tried using the settings mentioned in there, and finally had to restore the old one :) )
(Glad that I am getting all this help!)

[ATTACH]111868[/ATTACH]


Regards,
RVGSD.

---

### Post by HavocXphere on 2009-04-30
> **tinivole said:**
> IMO, don't try to make something fast unless you can quantify slow.
Sure thing.

Slow = Vista on laptop w/ 512mb](*,)

or was that the definition of slit-wrists-slow...

---

### Post by Tulsapoke on 2009-04-30
I had the slow scrolling issue with Firefox after I upgraded my (8yr old) machine to Jaunty.  Every time I would scroll the CPU would go 100%.  I read someone else on here had the same problem and said it was due to my xorg.conf file being outdated or something. 

I booted into the recovery/safe mode option and used the fix graphics issue option.  This did a redo on my xorg.conf file.  After rebooting from this all was good, and my speed was back as it was in Intrepid.

My father after his upgrade had an xorg.conf file from Intrepid that would wouldn't show anything so he had to run the same fix. I think they must have made some pretty major xorg changes in Jaunty.

Hope that helps someone.

---

### Post by NightwishFan on 2009-05-01
The posters PC is fine to run Ubuntu. It is almost better than mine. The only thing I can think of is you have very slow disk access. Your CPU seems to be fairly overwhelmed as well.

---

### Post by NESFreak on 2009-05-01
> **rvgsd said:**
> Hi, 
I read through this page
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
I checked and my system doesn't have the 'fglrx' drivers installed. So I guess thats not causing me any problems. However I checked the xorg.conf file, and it doesnt look like the one mentioned on this page. 
Thanks again.
So still do I need to mess with the xorg.conf? (I tried using the settings mentioned in there, and finally had to restore the old one :) )
(Glad that I am getting all this help!)

[ATTACH]111868[/ATTACH]


Regards,
RVGSD.

Not having the driver might be the problem. See the slow scrolling speed is probably caused by the video-output being software rendered. Which is even slow on a modern i7. (As long as you select a high screen resolution). Your system is fine for running ubuntu.

If the opensource ati driver fails, you might consider installing ati's own proprietary driver, which should be available from the restricted driver manager. Just follow the instructions and you should be ready to go.

---

### Post by rvgsd on 2009-05-01
Hi All,

While going across the forum, I learned about the **xorg.conf** file. 
In this file I changed the value of DefaultDepth from 24 to 16. The performance of my system now is definitely satisfactory (I can slightly feel the color difference, but that doesn't matter!) 
Earlier **glxgears** gave FPS of ~100 with the 24 bit color setting and now its ~1100 with the 16 bit(Huge difference!). 
I guess my problem is solved :)
Thankyou all for helping. All replies appreciated !

Regards,
RVGSD.

---

### Post by NightwishFan on 2009-05-02
I am glad you got it working. Although that seems to be a harsh solution.

That is one of the reasons I want to use OpenSUSE so bad is that it actually has a GUI option to configure things such as Color Depth and CPU Schedulers. Then again I pretty much always use 24-bit and CFQ.... I guess I just like having the option there?

---

### Post by sailor420 on 2009-05-04
> **NESFreak said:**
> Not having the driver might be the problem. See the slow scrolling speed is probably caused by the video-output being software rendered. Which is even slow on a modern i7. (As long as you select a high screen resolution). Your system is fine for running ubuntu.

If the opensource ati driver fails, you might consider installing ati's own proprietary driver, which should be available from the restricted driver manager. Just follow the instructions and you should be ready to go.
How would one know if the video output was being software rendered? If it is, how would one change it to hardware rendering?

I am having a very similar problem, and it seems to be the video card--there are lots of people having issues with this card in Linux.

I tried the 16-bit fix too, and it sped it up--but also managed to prevent lots of windows from rendering correctly (such as the Admin login screen, or all window decorations like maximize/minimize/close buttons). Made it pretty much unusable.

Any help is appreciated.

---

