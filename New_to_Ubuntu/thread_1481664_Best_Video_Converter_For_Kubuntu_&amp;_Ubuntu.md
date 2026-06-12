---
title: "Best Video Converter For Kubuntu &amp; Ubuntu"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by SKhan on 2010-05-12
What's the best available video converter for Kubuntu & Ubuntu?
Basically i will use it for converting youtube HD videos for my Nokia mobile.
(on MS windows i have been using Any-Video-Converter, which is very fast and high quality converter. I need something equivalent or better)




Edit: 23 may 2010
Since most of the softwares advised to me in later posts didn't serve the purpose. I wanna clarify the type of converter i want to use. So before you advice a software to me, please make sure it has following options.

1. avi, 3gp, video output. or any format a Nokia s60 device can play.
2. ability to turn-off audio in output video file.
3. ability to set custom dimensions for output file. (most of the times i need a 320x240 output)

---

### Post by skibum3027 on 2010-05-12
Handbrake... It's GTK but it looks fine in KDE and it's very simple for being as good of a converter as it is. Assuming your device does the H.264 codec.

---

### Post by MrWES on 2010-05-12
> **SKhan said:**
> What's the best available video converter for Kubuntu & Ubuntu?
Basically i will use it for converting youtube HD videos for my Nokia mobile.
(on MS windows i have been using Any-Video-Converter, which is very fast and high quality converter. I need something equivalent or better)

ffmpeg with x264 and you can use the frontend GUI WinFF.

[http://ubuntuforums.org/showthread.php?t=786095]("http://ubuntuforums.org/showthread.php?t=786095")

```
sudo apt-get install winff
```

Bill

---

### Post by SKhan on 2010-05-14
> **skibum3027 said:**
> Handbrake... It's GTK but it looks fine in KDE and it's very simple for being as good of a converter as it is. Assuming your device does the H.264 codec.

handbrake not giving any option to set the resolution.

---

### Post by SKhan on 2010-05-14
> **MrWES said:**
> ffmpeg with x264 and you can use the frontend GUI WinFF.

[http://ubuntuforums.org/showthread.php?t=786095]("http://ubuntuforums.org/showthread.php?t=786095")

```
sudo apt-get install winff
```

Bill
it's taking ages to convert a file. i waited for more than hour but it could not complete the conversion of 700mb file. between it's not complete GUI frontend. It still has some CLI looks.

---

### Post by JohnAStebbins on 2010-05-14
> **SKhan said:**
> handbrake not giving any option to set the resolution.

Um, what?  HandBrake as a whole dialog dedicated to tuning cropping, scaling, and aspect ratio.

Let me guess, your trying to run the 0.9.4 release on Lucid.  If so, you need to use the nightly snapshots.  The latest version of gtk introduced an API change that isn't backwards compatible.

[http://forum.handbrake.fr/viewtopic.php?f=6&t=15901](http://forum.handbrake.fr/viewtopic.php?f=6&t=15901)
[https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots](https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots)

---

### Post by oupamster on 2010-05-14
have you tried using transmageddon?

sudo aptitude install transmageddon

Homepage: [http://www.linuxrising.org/transmageddon/](http://www.linuxrising.org/transmageddon/)

that's what I use... :-)

---

### Post by jerome1232 on 2010-05-14
I second Handbrake. Winff is my goto if I need an avi (handbrake dropped support for that container it seem's)

---

### Post by SKhan on 2010-05-16
> **JohnAStebbins said:**
> Um, what?  HandBrake as a whole dialog dedicated to tuning cropping, scaling, and aspect ratio.

Let me guess, your trying to run the 0.9.4 release on Lucid.  If so, you need to use the nightly snapshots.  The latest version of gtk introduced an API change that isn't backwards compatible.

[http://forum.handbrake.fr/viewtopic.php?f=6&t=15901](http://forum.handbrake.fr/viewtopic.php?f=6&t=15901)
[https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots](https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots)
it was HandBrake-0.9.4-Ubuntu_GUI_i686.deb
where can i get nightly snapshots? handbrake website says "see the forum annoucements". so where these forum announcements are?

---

### Post by SKhan on 2010-05-16
> **oupamster said:**
> have you tried using transmageddon?

sudo aptitude install transmageddon

Homepage: [http://www.linuxrising.org/transmageddon/](http://www.linuxrising.org/transmageddon/)

that's what I use... :-)
never used or even seen a computer running Linux until just a month ago, let alone transmageddon? i have just started my transition towards linux. will give transmageddon a try.
I have downloaded transmageddon-0.15.tar.bz2

---

### Post by philinux on 2010-05-16
> **SKhan said:**
> 
I have downloaded transmageddon-0.15.tar.bz2

No need to download it's in the ubuntu repositories.

Either Applications>software centre or

in firefox address bar type apt:transmageddon

or
System>admin>synaptic package manager 

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by SKhan on 2010-05-16
> **philinux said:**
> No need to download it's in the ubuntu repositories.

Either Applications>software centre or

in firefox address bar type apt:transmageddon

or
System>admin>synaptic package manager 

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

aah true.

---

### Post by SKhan on 2010-05-16
transmageddon installed. but it didn't solve my problem.
I want to set the resolution. Any transcoder that doesn't allow to set the resolution of output file, won't serve the purpose.

---

### Post by jerome1232 on 2010-05-16
Handbrake. see my screen shot to see me editing the resolution.

nightly build is here

[http://build.handbrake.fr/](http://build.handbrake.fr/)

download fedora 32 if your are 32 bit, fedora 64 if you are 64 bit.

How to tell? will return i386, i486, i586, or i686 if you are 32 bit, x86_64 if you are 64 bit.

```
uname -m
``` 

Use Alien to convert the rpm to a deb

```
sudo apt-get install alien
sudo alien filename.here
```

---

### Post by JohnAStebbins on 2010-05-16
> **SKhan said:**
> it was HandBrake-0.9.4-Ubuntu_GUI_i686.deb
where can i get nightly snapshots? handbrake website says "see the forum annoucements". so where these forum announcements are?

HandBrake forums: 
[http://forum.handbrake.fr/](http://forum.handbrake.fr/)  
You should go here if you need help with handbrake.

Announcements: 
[http://forum.handbrake.fr/viewforum.php?f=6&sid=2a2169312ee1830faaafd00abae096f7](http://forum.handbrake.fr/viewforum.php?f=6&sid=2a2169312ee1830faaafd00abae096f7)
Every single forum group has theses announcements at the top.

Snapshot announcement: 
[http://forum.handbrake.fr/viewtopic.php?f=6&t=15901](http://forum.handbrake.fr/viewtopic.php?f=6&t=15901) 

Snapshot PPA: 
[https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots](https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots)

---

### Post by JohnAStebbins on 2010-05-16
> **jerome1232 said:**
> Handbrake. see my screen shot to see me editing the resolution.

nightly build is here

[http://build.handbrake.fr/](http://build.handbrake.fr/)

download fedora 32 if your are 32 bit, fedora 64 if you are 64 bit.

How to tell? will return i386, i486, i586, or i686 if you are 32 bit, x86_64 if you are 64 bit.

```
uname -m
``` 

Use Alien to convert the rpm to a deb

```
sudo apt-get install alien
sudo alien filename.here
```

Um, on that nightly build page is a link to a PPA with debs for lucid and karmic.  No need to muck around with Alien and rpm packages.

---

### Post by jerome1232 on 2010-05-16
> **JohnAStebbins said:**
> Um, on that nightly build page is a link to a PPA with debs for lucid and karmic.  No need to muck around with Alien and rpm packages.



Crazy! I totally didn't see that lol. I was all sad when I saw they didn't package it for Debian systems.

Guess I was wrong lol.

---

### Post by SKhan on 2010-05-19
i tried to install alien but there was a warning that said something like "installing alien needs untrusted packages to be installed". So i didn't install it.

just downloaded deb package from ppa link. let me install and check.

---

### Post by SKhan on 2010-05-22
I installed Handbrake but the problem is that i can't launch it. It doesn't appear anywhere with other apps. It can't be launched from Terminal either. what to do now?

---

### Post by jerome1232 on 2010-05-22
from a terminal

```
ghb
```

But it should be under Applications -> Sound and Video

If it's not there try right clicking your menu, click edit menu's and look for it there. You can always create a new item, remember the command to launch handbrake is "ghb".

---

### Post by SKhan on 2010-05-22
> **jerome1232 said:**
> from a terminal

```
ghb
```

But it should be under Applications -> Sound and Video

If it's not there try right clicking your menu, click edit menu's and look for it there. You can always create a new item, remember the command to launch handbrake is "ghb".
No it's not there. I already had tried to edit menu in order to find handbrake somewhere.

ghb code gave this error

```
No command 'ghb' found, did you mean:
 Command 'gdb' from package 'gdb' (main)
 Command 'gvb' from package 'gvb' (universe)
 Command 'gcb' from package 'gcb' (universe)
 Command 'thb' from package 'pvm-examples' (universe)
ghb: command not found
```

---

### Post by JohnAStebbins on 2010-05-22
Maybe you installed the cli instead of the gui?  cli command is
```
HandBrakeCLI
```
You might want to inspect the packages you installed
```
dpkg -l | grep -i handbrake
```

---

### Post by MooPi on 2010-05-22
So does anyone use mencoder? I've used it to convert flash video whit great success. Simple bash script and you're off and running.

---

### Post by SKhan on 2010-05-22
> **JohnAStebbins said:**
> Maybe you installed the cli instead of the gui?  cli command is
```
HandBrakeCLI
```
You might want to inspect the packages you installed
```
dpkg -l | grep -i handbrake
```

That's it! The version i installed was cli instead of gui. #-o
Now i have installed gui version. and I can launch it.
My bad i didn't notice that cli there meant command line interface.  #-o
Thanks.

---

### Post by SKhan on 2010-05-23
> **MooPi said:**
> So does anyone use mencoder? I've used it to convert flash video whit great success. Simple bash script and you're off and running.
it seems i might have to..., because so far i couldn't get desired results from handbrake.

---

### Post by Rasa1111 on 2010-05-23
check out Arista Transcoder, if you havent already. 

I didnt read all 3 pages to see if it was suggested though.
Sorry if so.

---

### Post by SKhan on 2010-05-23
ok guys. handbrake installed successfully. and videos converted successfully. but still i couldn't get desired results even after trying quite a few times.

1, video output can either m4v or mkv, non of which my mobile understands.

2. there no 3gp or avi option.

3. Option to set output dimensions is somewhat cumbersome, though i managed to handle it.

---

### Post by SKhan on 2010-05-23
> **Rasa1111 said:**
> check out Arista Transcoder, if you havent already. 

I didnt read all 3 pages to see if it was suggested though.
Sorry if so.

Just installed. But it's not as simple as it looks.

1, Counldn't add any video to queue. it always gives error when i try.

2. Then i noted, i can choose source file from top-right drop-down menu. So what else is the purpose of queue, if it doesn't contain source files?

3. I couldn't convert the source file that i chose. there was no encode/convert option.

4. No option to set output dimensions for a video. Any software that doesn't have this option wont work for me.

---

### Post by fjpos on 2010-05-30
> **SKhan said:**
> it was HandBrake-0.9.4-Ubuntu_GUI_i686.deb
where can i get nightly snapshots? handbrake website says "see the forum annoucements". so where these forum announcements are?

Hi there,

Use the following

 [https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots](https://edge.launchpad.net/~stebbins/+archive/handbrake-snapshots)

Hanbrake 0.9.0.4 will not work on Lucid Lynx 10.04 so as Mr John Stebbins has magnificently done use his nightly build and it works .


Patrick
Adelaide, South Australia

---

### Post by MrWES on 2010-05-30
> **SKhan said:**
> ok guys. handbrake installed successfully. and videos converted successfully. but still i couldn't get desired results even after trying quite a few times.

1, video output can either m4v or mkv, non of which my mobile understands.

2. there no 3gp or avi option.

3. Option to set output dimensions is somewhat cumbersome, though i managed to handle it.

Learn to use ffmpeg; it's the most powerful video tool in linux. IHMO worth a little time to learn it, and there are tons of guides on the 'Net.

Bill

---

### Post by alphacrucis2 on 2010-05-30
Another thing to try is Avidemux. Fairly straightforward GUI interface.

---

### Post by SKhan on 2010-05-30
> **alphacrucis2 said:**
> Another thing to try is Avidemux. Fairly straightforward GUI interface.

just installed and tested.
even though, it has more straight forwarde gui than all the previous apps i tested so far but still i couldn't fully understand this program.

1. I converted 2 videos, of which 1 is playable on my mobile while the other is not. Both the videos were converted with identical settings.

2. Other than auto-menu there was no option to set video resolution, or i couldn't find one.

3. Since the only option to set resolution was under auto-menu, therefore i selected ipod settings under auto-menu, and pressed ok. Then it gave the codec error "cannot select the MPEG-4 SP codec"
So i reset edits under edit-menu.
Then again i selected PSP (H.264) from auto-menu, and target-type in auto-wizard as Ipod (320 * 240)
then i clicked save button.
the output video was saved but it's resolution was NOT 320 * 240, but it was identical to that of the source video.

4. there was no option to turn off the audio in output file.

what do you say about this?

---

### Post by sandyd on 2012-12-19
**Necromancing - thread closed**
As per the Ubuntu Forums Code of Conduct, please do not post in threads more than one year old. 

Thanks!

---

