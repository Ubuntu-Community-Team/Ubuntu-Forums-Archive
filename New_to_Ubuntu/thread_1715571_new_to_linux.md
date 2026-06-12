---
title: "new to linux"
date: 2011-03-27
forum: New to Ubuntu
---

### Post by dave48838 on 2011-03-27
Hello, I'm a pc expert, but new to linux.  the reason I want to learn is mainly for the purpose of data recovery.  From what I understand linux can do some things windows can't. 

Specifically I've been looking into ddrescue due to the fact it can look at the drive from back to front.

What I've done so far is installed ubuntu on a hd.  It's really good about finding drivers, I'm impressed.  right up there with windows 7.  wireless, video, audio, no problem.  I'm very impressed.

Where I'm stuck at is where to go from here.

any help would be appreciated.

I do have this thread set up with instant email notification so I will respond as quick as I check my email.

Thanks,
Dave:confused:

---

### Post by Rubi1200 on 2011-03-27
Hi and welcome to the forums :-)

For general data recovery information:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

For ddrescue:
[http://www.gnu.org/software/ddrescue/ddrescue.html](http://www.gnu.org/software/ddrescue/ddrescue.html)

---

### Post by Frogs Hair on 2011-03-27
You can subscribe to a thread from the user cp on your profile page.

---

### Post by ikt on 2011-03-27
> **dave48838 said:**
> Hello, I'm a pc expert, but new to linux.

when it comes to using linux for the first time it's best to throw away all that windows expertness, linux is not windows and many windows experts hurt themselves trying to make it so.

---

### Post by steveneddy on 2011-03-27
> **ikt said:**
> when it comes to using linux for the first time it's best to throw away all that **windows expertness** [COLOR="Red"](what's that?)[/COLOR], linux is not windows and many windows experts hurt themselves trying to make it so.

I could not agree more.

You must forget everything you learned for the Windows world - Linux is a different animal - and as soon as you accept that fact the acceptance of what you learn about Linux will go smoother.

Remember:

* The terminal is your friend.

* Cutting and pasting in Linux is so much easier - just highlight with the mouse what you want to copy - the go to the application you want to paste to - then go to the field or area you want to past to  - click the middle mouse button - or two finger tap the mouse pad - easy peasy. You don't have to **CTRL+C** and **CTRL+V** - although you can - this skill will save you a few steps.

You will want to get that down because it keeps you from typing out commands you find on the internet - and you make less mistakes.

* Google has most of the answers - it you ask the question the right way.

* Search the UF - if you don't find the answer - post a thread asking your question.

Good luck.

---

### Post by Diametric on 2011-03-27
I, like you was* a windows expert.  I switched to Linux exclusively about a year and half ago and have never looked back.  

However, there is a high learning curve, and like someone else said, the terminal (or CLI or bash...all different names for the same tool) is the key to being successful.  Grab a book and spend some time getting to know how this OS works.  I recommend the following books:

[This one]("http://www.amazon.com/Ubuntu-Linux-Toolbox-Commands-Debian/dp/0470082933") because of the cool stuff it shows you how to do.  It's a great for learning some practical utilities Linux can perform from the Command Line.

And [This one]("http://www.amazon.com/Learning-bash-Shell-Cameron-Newham/dp/1565923472") for getting into the nitty gritty of what bash can do.  

Good luck and enjoy!

---

### Post by Dutch70 on 2011-03-27
Hi Dave & welcome to a whole new world & community. 
Oh yeah, and OS. ;)

Here are some sites that I think will come in handy sooner or later.
[[COLOR="Blue"]http://linuxcommand.org/[/COLOR]]("http://linuxcommand.org/")
[[COLOR="Blue"]http://k12linux.mesd.k12.or.us/sag/c37.html[/COLOR]]("http://k12linux.mesd.k12.or.us/sag/c37.html")
[[COLOR="Blue"]http://www.osalt.com/[/COLOR]]("http://www.osalt.com/")
[[COLOR="Blue"]http://www.bauer-power.net/2009/04/ubuntu-n00b-here-free-ubuntu-pocket.html[/COLOR]]("http://www.bauer-power.net/2009/04/ubuntu-n00b-here-free-ubuntu-pocket.html")

Best regards

---

### Post by Hedgehog1 on 2011-03-27
> **dave48838 said:**
> Specifically I've been looking into ddrescue due to the fact it can look at the drive from back to front.

dave48838,

If one of your goals is rescuing Windows PCs and the data on them, then you will want to do a real install of Ubuntu onto the fastest USB stick you can scrounge up.

The idea is this:  You can boot a PC using the Ubuntu USB stick, and then copy data from the drive to an external drive (or even burn the data to a CD/DVD).  You can also boot a PC and use ddrescue to copy data from a old or dying drive to a new drive.

Because Ubuntu does not use drivers for specific chip sets, you can boot any PC no matter the motherboard or processor (as long as it honors USB boot).

Here is what I suggest:

Using: the LiveCD, any PC you have and a ***FAST*** USB stick

1) Disconnect the hard drive in the PC

2) Boot off of the Ubuntu LiveCD

3) Using gparted, partiton your USB stick something like this (assumes 16 gig stick, but you can use 8 gig):

[IMG]http://img197.imageshack.us/img197/6631/gparteduaos.png[/IMG]

The idea is the first fat32 partition allows you to use the stick for normal windows-to-windows transfers, and keeps windows PCs from offering to format the USB stick for you.

On this stick, I keep about 12 albums of music, the ddrescue documentation, a few simpsons episodes and so on.

I use it to boot ANY computer, and can surf the web, rock out or save data from a failing hard drive.

4) Use gparted off the liveCD to partition your USB.  You will find it by menuing to System >> administration >> gparted partition editor.  Partition your USB using the picture as a guide.  You can use all primary partitions if you prefer.

5) Install Ubuntu on the USB, select the 'Manual' configuration and assign the ext4 partiton to mount at '/' (said as "root").

6) When install is done, it will ask you to remove the CD and reboot. Do that.

Before you allow the updates after reboot to happen, please do these two things to keep the USB stick from loading specific drivers:
7) In the terminal, do this:
```
sudo rm /etc/grub.d/30_os-prober
```

8.) Menu to: system >> preferences >> startup applications and uncheck "Check for new hardware drivers".  By not loading specific drivers, this USB stick will operate on any PC. The generic video drivers run everywhere, and nearly all sound cards will work with the generic sound card driver.

9) Now allow the updates to run (please do not allow the 'Additional Drivers' to run - keep it generic).

10) The USB will want to reboot one more time, let it.

11) Once the second reboot is complete and things look OK, shut down the system and reconnect the hard drive.

You can know take your USB '**Ubuntu-On-A-Stick!**' and boot it on any computer that allows USB boot.  You can also surf the web while you are running a ddrescue copy.

***The Hedge***

:KS

p.s. I have a laptop with the dead hard drive removed (new drive is in transit).  I can boot the laptop off the USB and post to the forum and listen to my music.  I did this last night 'just because'.  Works fine.

---

### Post by Hedgehog1 on 2011-03-27
> **dave48838 said:**
> What I've done so far is installed ubuntu on a hd.  ***It's really good about finding drivers, I'm impressed. *** right up there with windows 7.  wireless, video, audio, no problem.  I'm very impressed.

dave48838,

I want to thank you for noticing this fact.  I have found with reasonably current hardware, 'drivers' tend to install themselves correctly, too.  I also rate it about equal with Windows 7 on this score.  Most install issues I see are caused by unusual hardware configurations or the complexities of dual-booting Ubuntu and Windows (Particularly when multiple hard drives are in use).

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-03-27
dave48838,

Hey - one more thing: Virtual Box in Ubuntu works great.  Be sure to download and install the version from the Virtual Box web site so USB works on the virtual machines.

I keep a number of OS combinations on my Ubuntu:

[IMG]http://img219.imageshack.us/img219/455/vbox01.png[/IMG]

And I also run Win7 full screen in one workspace so I can hope back and forth between OSs:

[IMG]http://img88.imageshack.us/img88/9595/vbox02.png[/IMG]

I find the ability to test an OS install in a virtual machine is just invaluable. You may also find this to be the case...

***The Hedge***

:KS

---

### Post by Diametric on 2011-03-27
Dude, you just saved me a TON of frustration.  I forgot that the version supplied by Synaptic doesn't support USB, and i couldn't figure out why it wouldn't work.  thank you!



> **Hedgehog1 said:**
> dave48838,

Hey - one more thing: Virtual Box in Ubuntu works great.  Be sure to download and install the version from the Virtual Box web site so USB works on the virtual machines.

I keep a number of OS combinations on my Ubuntu:

[IMG]http://img219.imageshack.us/img219/455/vbox01.png[/IMG]

And I also run Win7 full screen in one workspace so I can hope back and forth between OSs:

[IMG]http://img88.imageshack.us/img88/9595/vbox02.png[/IMG]

I find the ability to test an OS install in a virtual machine is just invaluable. You may also find this to be the case...

***The Hedge***

:KS

---

### Post by Diametric on 2011-03-27
Dude, you just saved me a TON of frustration.  I forgot that the version supplied by Synaptic doesn't support USB, and i couldn't figure out why it wouldn't work.  Thank you!



> **Hedgehog1 said:**
> dave48838,

Hey - one more thing: Virtual Box in Ubuntu works great.  Be sure to download and install the version from the Virtual Box web site so USB works on the virtual machines.

I keep a number of OS combinations on my Ubuntu:

[IMG]http://img219.imageshack.us/img219/455/vbox01.png[/IMG]

And I also run Win7 full screen in one workspace so I can hope back and forth between OSs:

[IMG]http://img88.imageshack.us/img88/9595/vbox02.png[/IMG]

I find the ability to test an OS install in a virtual machine is just invaluable. You may also find this to be the case...

***The Hedge***

:KS

---

