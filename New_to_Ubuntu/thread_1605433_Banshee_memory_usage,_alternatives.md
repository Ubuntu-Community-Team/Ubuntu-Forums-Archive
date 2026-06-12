---
title: "Banshee memory usage, alternatives?"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by Cycledoc on 2010-10-25
I've been trying to use Banshee.  I like the interface, it's ability to download podcasts and how it works with my old Creative music player.  However when I try to play podcasts through the computer it's memory usage exceeds the 512 RAM that my elderly laptop has.

I know rhythmbox is one alternative, are there others with similar functionality but better memory efficiency?  Banshee is useless for me.

Many thanks

---

### Post by NightwishFan on 2010-10-25
Try Exaile. Though I think it should be fine even with swapping. Ubuntu runs fine on my laptop with 386mb.

---

### Post by cascade9 on 2010-10-25
> **NightwishFan said:**
> Try Exaile. Though I think it should be fine even with swapping. Ubuntu runs fine on my laptop with 386mb.

Arent you running a cut-down ubuntu? That makes a big difference. 

I've found deadbeef uses less memory than exaile. Currently I'm using 9.0MB and 14.9MB shared with deadbeef playing (with album art, which will eat more memory, but not a huge playlist loaded). Mind you, thats not ubuntu, things might be different with ubuntu...worth a try though. 

[http://deadbeef.sourceforge.net/](http://deadbeef.sourceforge.net/)

---

### Post by NightwishFan on 2010-10-25
Just no compiz, and vm.swappiness=100.

---

### Post by SlugSlug on 2010-10-25
this is by far the best I have used

mpd & gmpc

[http://www.webupd8.org/2009/11/gnome-music-player-client-gmpc-mpd-just.html](http://www.webupd8.org/2009/11/gnome-music-player-client-gmpc-mpd-just.html)

---

### Post by Cycledoc on 2010-10-25
I appreciate the suggestions and will try the other players.  FYI My computer has 512RAM has MSHome and ubuntu 10.04 and 10.10 partitions.  

Nightwishfan I disabled Compiz and changed the swappiness but there seemed no difference in the swap partition use.  

**Using 'free' at the terminal with Chrome and terminal open:**

          total       used       free     shared    buffers     cached
Mem:        507972     493740      14232          0      20032     256920
-/+ buffers/cache:     216788     291184
Swap:      1486844       6164    1480680

**Using 'free' with Chrome, terminal, and banshee playing a podcast (in the process of slowing system to unusable (terminal showing 100% processor use:**

            total       used       free     shared    buffers     cached
Mem:        507972     497796      10176          0      14972     235740
-/+ buffers/cache:     247084     260888
Swap:      1486844       7616    1479228

**A little later same programs active**
             total       used       free     shared    buffers     cached
Mem:        507972     498176       9796          0      14976     236056
-/+ buffers/cache:     247144     260828
Swap:      1486844       7612    1479232

Is the swap disk working as it should?  

Swap was originally set up to run with 10.04. Swap is marked as being on in gparted in the 10,10 partitions.  

For what it's worth in the 10,04 version everything works without crashing and there appears to be greater use of the swap partition--over 19,000--with Banshee, chrome and terminal.

Unless this is a fixable issue I'll may just  stay with 10,04.  Any ideas?

Again thank you all for responding.

---

### Post by NightwishFan on 2010-10-25
Changing swappiness to 100 gives you more ram for what you currently are running. If you are interested in improving performance on low performing hardware I can help you in another thread.

Though as for Banshee, I just found it odd it used so much RAM. Perhaps find something that use a lighter database such as sqlite. (Not sure if exaile does this, but it was the default Xubuntu player).

If 10.04 works for you by all means use it, as it is supported for a long period of time. 10.10 though has had a lot of success on light hardware for me.

[[IMG]http://img219.imageshack.us/img219/1708/lowmem.th.png[/IMG]](http://img219.imageshack.us/i/lowmem.png/)

Uploaded with [ImageShack.us](http://imageshack.us)

---

### Post by Cycledoc on 2010-10-25
This problem is driving me a little batty. I've downloaded gpodder and used to to test the different players. 

VLC and gxine will play podcasts without difficulty both by linking to the file where they are stored or through gpodder's link. Rhythmbox, Banshee and Exaile won't play and as described previously their memory usage is 100% while the system is slowly grinding to a halt.  

Am I missing some dependency that these programs require, that VLC and gxine don't, to play mp3 podcasts?  Yes I have the Gnome restricted extras installed.  Any ideas?

---

### Post by NightwishFan on 2010-10-25
Rhythmbox, Banshee, and Exaile all happen to be based on gstreamer. Though generally it should not be an issue of RAM but CPU if they play. So perhaps there is a gstreamer bug? What is the process exactly that was hogging, the player, or something like pulseaudio?

---

### Post by Cycledoc on 2010-10-25
When I launch the podcast in Rhythmbox, Pulseaudio grabs around 90% of the CPU and doesn't decrease even after exiting the program.  There is no sound.  I didn't test it in the other programs (Banshee and Exaile) but presume it's the same glitch.  The system essentially stops functioning and I have to restart.

Any ideas?

thanks

---

### Post by NightwishFan on 2010-10-25
Hmm... I would say you could try removing pulseaudio, though there are a few steps to that. Also you should probably report a bug. Try resetting pulse settings for new. Show all files in your home folder, delete the .pulse folder and then reboot.

---

### Post by Cycledoc on 2010-10-25
Deleting the .pulse file helped but the problem is still there.  Now however, I can pause the playback and the memory usage will normalize.  When I restart it plays.  

Are there alternatives to pulse audio I'd like to explore them as there clearly is some glitch between my system and the pulseaudio program.  What's fascinating is that all these programs run fine on 10.04 on this machine.

My system is as follows:  A Dell 2650 with 512 RAM 

00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 05)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 05)
00:1d.0 USB Controller: Intel Corporation 82801CA/CAM USB Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801CA/CAM USB Controller #2 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801CA/CAM SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801CA/CAM AC'97 Modem Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2)
02:01.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
02:04.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
03:00.0 USB Controller: NEC Corporation USB (rev ff)
03:00.1 USB Controller: NEC Corporation USB (rev ff)
03:00.2 USB Controller: NEC Corporation USB 2.0 (rev 02)

thanks again for your help.

---

### Post by bioterror on 2010-10-25
If you dont fear terminal, I suggest you to try MOC (Music On Console). I'm using it, and I'm also loving it.

And you can use [http://github.com/fluxid/mocp-scrobbler]("http://github.com/fluxid/mocp-scrobbler") this one to make it scrobble your playings to last.fm.

Looks something like this as a default
[IMG]http://beshenov.ru/debaday/img/moc.png[/IMG]
But there's theme files and you can easily edit colors to suit more your taste. And you can hide that playlist, if you dont need it. No libraries, just music.

---

### Post by Cycledoc on 2010-10-28
The solution was to remove pulse audio and use something called ALSA.  Everything seems to work to my undemanding satisfaction.  Memory utilization is within my computer's limited resources (512mb) and the system is humming again.  I configured ALSA with gstreamer0.10-alsa and use the Gnome alsa mixer to control volume--I have it's shortcut on the Gnome Panel.

I followed the instructions to remove pulse audio here:  [http://art.ubuntuforums.org/showthread.php?t=1313253&page=14](http://art.ubuntuforums.org/showthread.php?t=1313253&page=14)  post #133

FYI my issue is not unique to my computer.  I found several other people having similar issues with memory and Pulseaudio.  It's nice to have an alternative.

Many thanks to those offering help!

---

### Post by NightwishFan on 2010-10-28
Ah, glad you got it working. Forgive my delay, I was going to suggest trying alsa though there are some issues and steps to make it work right.

---

