---
title: "TV card not working in 9.10"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by pdlethbridge on 2009-11-05
I used this series of commands to get my tv card working in 9.04 but it won't work in 9.10. Am I missing something? I can't change the video source. can't open capture device /dev/videoO
Thanks in advance
step 1:

sudo nano /etc/modprobe.d/saa7134                                                                             hit enter
next you will be asked for your password enter and press the enter key.

now in the nano editor, type the following lines pressing enter at the end of each one.

alias chr-major-81 videodev                                                                                               enter
alias chr-major-81-0 saa7134                                                                                              enter
options saa7134 card=42 tuner=43 oss=1                                                                          enter

now press the control key (ctrl) and the "x" key at the same time
you will be asked if you want to save file: saa7134 
say yes by pressing "y" key on the keyboard.

---

### Post by pdlethbridge on 2009-11-08
bump

---

### Post by pdlethbridge on 2009-11-12
bump. any help?

---

### Post by pdlethbridge on 2009-11-16
Can anyone give me some help with this problem. The TV card is the only thing not working in 9.10 Thanks in advance

---

### Post by sisco311 on 2009-11-16
rename the config file:
```
sudo mv /etc/modprobe.d/saa7134 /etc/modprobe.d/saa7134.conf
```

only .conf files are read at boot time.

---

### Post by pdlethbridge on 2009-12-09
I tried that without success. I think I'll stick with 9.04. It has been absolutely stable. Personally, I don't think 9.10 is ready for prime time. It's slow to boot and run and the tv card won't work.

---

### Post by sisco311 on 2009-12-09
Try to load the module manually.

Post the output of:
```
sudo modprobe saa7134
```

```
lsmod
```

and

```
dmesg | tail -n 30
```

EDIT:

never mind

> **pdlethbridge said:**
> I think I'll stick with 9.04. It has been absolutely stable.

---

### Post by ukripper on 2009-12-09
you have marked it as solved, can you post the solution here for people who are having problem can refer to it.

---

### Post by pdlethbridge on 2009-12-09
my solution was to go back to 9.04, a much better and easier fix.

---

### Post by ukripper on 2009-12-09
People with saa7134 module who want to follow the bug report on launchpad for Karmic (9.10) - go here [https://bugs.launchpad.net/ubuntu/+source/tvtime/+bug/458832](https://bugs.launchpad.net/ubuntu/+source/tvtime/+bug/458832)> Matías Szeftel  wrote on 2009-11-09:  	  #4

**[COLOR="Blue"]Using kernel 2.6.28 also fixed this for me[/COLOR]**.

I guess the 2.6.31 kernel broke something in the saa7134 module.


---

### Post by Cuco3 on 2009-12-09
> **pdlethbridge said:**
> my solution was to go back to 9.04, a much better and easier fix.You don't know how many times I've tried preaching this solution only to have it fall upon deaf ears. It's the easiest solution to most bizarre problems but people would rather spend months trying to find a fix.

---

### Post by ukripper on 2009-12-09
> **Cuco3 said:**
> You don't know how many times I've tried preaching this solution only to have it fall upon deaf ears. It's the easiest solution to most bizarre problems but people would rather spend months trying to find a fix.

some people want problems to be resolved in the release they are using to make future release better. Therefore, i urge everyone to report bugs on launchpad, we don't want to stay with the same release all life, or do we? Lack of bug reporting may hinder innovation and progress.

---

### Post by Cuco3 on 2009-12-09
> **ukripper said:**
> some people want problems to be resolved in the release they are using to make future release better. Therefore, i urge everyone to report bugs on launchpad, we don't want to stay with the same release all life, or do we? Lack of bug reporting may hinder innovation and progress.I agree wholeheartedly with reporting bugs. I just think it's not worth it to spend more time fixing something that already has taken up enough of someone's time.

So yeah, report the bugs so the developers can improve the product, but don't work yourself over for a resolution that's an upgrade/downgrade away from fixing your problem.

---

### Post by ukripper on 2009-12-10
> **Cuco3 said:**
> I agree wholeheartedly with reporting bugs. I just think it's not worth it to spend more time fixing something that already has taken up enough of someone's time.

So yeah, report the bugs so the developers can improve the product, but don't work yourself over for a resolution that's an upgrade/downgrade away from fixing your problem.

+1 fully agreed. i would say have one working release and another just to report any bugs dual booting.

---

### Post by pdlethbridge on 2009-12-16
I guess I'll give 9.10 another try but I'll need help in getting the right kernel installed.

---

### Post by ukripper on 2009-12-17
> **pdlethbridge said:**
> I guess I'll give 9.10 another try but I'll need help in getting the right kernel installed.

Easiest way to compile & install latest kernel is via kernelcheck - [http://ubuntuforums.org/showthread.php?t=618563](http://ubuntuforums.org/showthread.php?t=618563)

---

### Post by pdlethbridge on 2009-12-17
I'm in the process of down loading 9.10 for the upgrade. I also down loaded kernelcheck. Will I be able to go back to the 9.04 kernel?

---

### Post by ukripper on 2009-12-17
> **pdlethbridge said:**
> I'm in the process of down loading 9.10 for the upgrade. I also down loaded kernelcheck. Will I be able to go back to the 9.04 kernel?

With kernel check you can install any kernel image you want it is not just to upgrade kernel. It is to install your own custom kernel as well.

---

### Post by pdlethbridge on 2009-12-18
I messed up the download so I'll try this another day when I feel better

---

### Post by joes7 on 2009-12-18
Is your TV Card even recognized? You can always look for its drivers (done for Linux).

---

### Post by pdlethbridge on 2009-12-19
I installed kernel check but I get an error code 404 and then it shuts down.
Oh sigh!

---

### Post by pdlethbridge on 2009-12-20
bump

---

### Post by pdlethbridge on 2009-12-31
This has been an interesting process. I finally have 9.10 working and the TV card works as well.I spent time tonight downloading the OS and after a couple of hours it started to install. I kept getting errors during the set up like this, lots of them.
"Building initial module for 2.6.28-17-generic
process 31577: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file dbus-errors.c line 278.
This is normally a bug in some application using the D-Bus library."
 The set up seemed to take forever and in frustration I rebooted and got a dos screen. I did a command for dpkg as recommended and it finally booted up correctly to 9.10. I used start up manager to change the kernel and it worked. I wasn't getting a picture with the new kernel but when I back dated it in start up manager it worked. So I have the problem with OS solved but the errors on set up are a concern.
Now the only thing that doesn't work is the volume, I have none. Well, back to the drawing board and 9.04

---

### Post by pdlethbridge on 2009-12-31
I'm wondering if all the problems I've had with installation are caused by not using a cd? I've run the installation from both upgrade in synaptic and through the command line in terminal with the same bad results.

---

### Post by pdlethbridge on 2010-01-08
bump

---

### Post by Methuselah on 2010-01-08
I saw something about oss=1 in your driver options.
This is a total shot in the dark but is that related to sound?
If so, why oss?

---

### Post by pdlethbridge on 2010-01-09
not sure. I'm new, only switched about 3 -4 years ago. I love to play with the computer from time to time. I'm retired because of a stroke so I have loads of time to mess things up then fix them. I might order a cd and see if that helps. I've been upgrading through synaptic and that may be where I'm getting the errors. 
A side note about the kernel, I could use startup manger to back date a bad kernel

---

### Post by pdlethbridge on 2010-01-27
The install of an operating system can have some serious ups and downs. I downloaded and burned a 9.10 cd and  formated and installed it over the old OS but kept the home folder intact. There were some problems caused directly by the home folder. For instance, I couldn't find the applications, places, systems icon,(found it in the add to panel applet)The sound was still choppy, tvtime didn't work,(tried several things) and the drivers I was using for my canon pixma ip1500 printer were not allowed to finish downloading because of one file ( libsys2, I think.)
So I re-installed the OS, formated and repartitioned the drive to , one, give me more space for the OS, and two, format and enlarge the home folder. I left the home folder blank as I have certain files backed up on a fat32 partition at the end of the drive. It went okay and I got to the desktop so I did my usual putting the panel at the bottom. Again, I was unable to get tvtime to work, the sound was still choppy, and after spending time looking for canon drivers, I gave up. This took several hours, but as I'm handicapped, I have the time on my hands.
With the let out of a big sigh, I have gone back again to 9.04. If I'm up to it, I try it again next week. I WILL make it work.

---

### Post by pdlethbridge on 2010-02-07
Well, I spent 6 hours trying to get it to work last night with no success. I don't like to quit trying to fix the problem, but this was way over my head. I had tried to do an upgrade from 9.04, I had burned a CD of 9.10 and used that and I had ordered a CD from canonical. All were unsuccessful. So I'm back to 9.04 and I'll stay with that until 10.04

---

### Post by pdlethbridge on 2010-05-17
After spending time on the 10.04 LTS upgrade, I have switched back to 9.04. The same problems were happening and a new one was overcome. That was the install issue of changing to ext 4 from ext 2. But that was fixed only by a lot of reading and exploring and just by chance catching the suggestion. It was not part of the install info at the wiki, but on a list of bug reports for the OS.
 I hope that the problems can be fixed, because 9.04 will run out of support late this year and I'll be forced to make a choice. I have used Ubuntu since the 6.04 days and have seen wonderful changes. I'm concerned that the geek aspect of the OS is creeping back in and that new users will be scared away from an otherwise great OS. If it becomes too difficult for a new user to have an easy to run operating system, a lot of people will be scared back to the dark side.( windoze )

---

### Post by pdlethbridge on 2010-06-03
It's wonderful to talk to yourself, no arguments,, Unless, of course, you have a split personality

---

### Post by kumar116 on 2010-06-06
Here are two tips 1 is for tvtime-audio another is for tvtime-recording
please run the follwoing command in terminal for tvtime-audio:

[COLOR=Red]arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay -[/COLOR]


run the following command for tvtime recording:

[COLOR=Red]mencoder tv:// -tv driver=v4l2:input=0:norm=pal:width=720:height=480:outfmt=yuy2:device=/dev/video0:forceaudio:audiorate=32000:adevice=/dev/dsp1 buffersize=128 -ovc lavc -lavcopts vcodec=mpeg4:vbitrate=2000:keyint=30 -oac mp3lame -lameopts br=128:cbr:mode=3 -ffourcc divx -o record.avi
[/COLOR]
NOTE:change norm=pal/ntsc (as per your tvtime configuration)
         device=/dev/video0 or video1 as per your tvtime capturing device

finally to stop tvtime recording use ctrC

         ALL THE BEST   IT WORKS VERY WELL

---

### Post by pdlethbridge on 2010-06-07
Those commands would be useless as I can't get a picture or change a channel.

---

### Post by ukripper on 2010-06-08
Few easy solutions IMHO:
[LIST=1]
[*]Your TV card has been supplied with drivers for specific OS.
[*]Option 2 - Dual boot
[*]Option 3 - Get different TV card supported by Linux
[/LIST]

---

### Post by pdlethbridge on 2010-06-08
what cards are linux supported? I found none from newegg or tiger direct.

---

