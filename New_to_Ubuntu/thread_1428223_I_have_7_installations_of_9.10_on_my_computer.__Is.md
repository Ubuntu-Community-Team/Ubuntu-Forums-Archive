---
title: "I have 7 installations of 9.10 on my computer.  Is this normal?"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by Tony.B on 2010-03-12
I've had problems with Ubuntu ever since I installed 9.10 and I wonder if I have installed it correctly.

When I switch on my computer I get a page saying
[INDENT]GRUB loading[/INDENT]
followed by a page headed
[INDENT]GNU GRUB version 1.97~beta4[/INDENT]
This page then seems to tell me that I have 7 installations of Ubuntu, which all seem to me to be the same:
[INDENT]Ubuntu.Linux 2.6.31-20-generic
Ubuntu, Linux 2.6.31-20-generic (recovery mode)
Ubuntu, Linux 2.6.31-19-generic
Ubuntu, Linux 2.6.31-19-generic (recovery mode)
Ubuntu, Linux 2.6.31-18-generic
Ubuntu, Linux 2.6.31-18-generic (recovery mode)
Ubuntu, Linux 2.6.31-17-generic
Ubuntu, Linux 2.6.31-17-generic (recovery mode)
Ubuntu, Linux 2.6.31-16-generic
Ubuntu, Linux 2.6.31-16-generic (recovery mode)
Ubuntu, Linux 2.6.31-15-generic
Ubuntu, Linux 2.6.31-15-generic (recovery mode)
Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic (recovery mode)
Memory test etc[/INDENT]

Is this correct?  If it's not correct, how do I get rid of the 6 unwanted versions?

The problems I'm having are:
[INDENT](a) my laptop (Acer Aspire 5315) switches off after about 25 minutes.  It seems to get quite hot.  I didn't notice this with the previous version of Ubuntu, and it certainly didn't happen when I used Vista (sorry if that's a swearword).  When I restart the computer, the problem disappears.  This seems to be a problem with this model of computer and I see there's something called a "patch" but I've no idea how to access it or use it.

(b) I get error messages every time I use Update Manager, or if I try to download anything from Ubuntu Software Centre.  The usual message is
[INDENT]Package Operation failed
The installation or removal of a software package failed[/INDENT]
- followed by a complete stream of computer jargon like this
[INDENT]installArchives() failed: Selecting previously deselected package glabels-data.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 207374 files and directories currently installed.)
Unpacking glabels-data (from .../glabels-data_2.2.5-0ubuntu1_all.deb) ...
Selecting previously deselected package glabels.
Unpacking glabels (from .../glabels_2.2.5-0ubuntu1_i386.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for shared-mime-info ...
Processing triggers for man-db ...
Setting up liba52-0.7.4 (0.7.4-11ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing liba52-0.7.4 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libdvdread4 (4.1.3-5ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libdvdread4 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libid3tag0 (0.15.1b-10build1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libid3tag0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libmad0 (0.15.1b-4) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libmad0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libmpeg2-4 (0.4.1-3) ...
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libmpeg2-4 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libsidplay1 (1.36.59-5) ...
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libsidplay1 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of gstreamer0.10-plugins-ugly:
 gstreamer0.10-plugins-ugly depends on liba52-0.7.4; however:
  Package liba52-0.7.4 is not configured yet.
 gstreamer0.10-plugins-ugly depends on libdvdread4 (>= 4.1.3); however:
  Package libdvdread4 is not configured yet.
 gstreamer0.10-plugins-ugly depends on libid3tag0 (>= 0.15.1b); however:
  Package libid3tag0 is not configured yet.
 gstreamer0.10-plugins-ugly depends on libmad0 (>= 0.15.1b-3); however:
  Package libmad0 is not configured yet.
 gstreamer0.10-plugins-ugly depends on libmpeg2-4; however:
  Package libmpeg2-4 is not configured yet.
 gstreamer0.10-plugins-ugly depends on libsidplay1; however:
  Package libsidplay1 is not configured yet.
dpkg: error processing gstreamer0.10-plugins-ugly (--configure):
 dependency problems - leaving unconfigured
Setting up glabels-data (2.2No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
.5-0ubuntu1) ...

Setting up glabels (2.2.5-0ubuntu1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
/sbin/ldconfig.real: File /usr/lib/liba52-0.7.4.so is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libsidplay.so.1 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libid3tag.so.0.3.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmpeg2convert.so.0.0.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libsidplay.so.1.0.3 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmad.so.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libid3tag.so.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmad.so.0.2.1 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libdvdread.so.4.1.3 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmpeg2convert.so.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmpeg2.so.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmpeg2.so.0.0.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libdvdread.so.4 is empty, not checked.
Errors were encountered while processing:
 liba52-0.7.4
 libdvdread4
 libid3tag0
 libmad0
 libmpeg2-4
 libsidplay1
 gstreamer0.10-plugins-ugly[/INDENT]
I've completed bug reports and had some replies, but these are so technical I'm not even sure they were meant to be sent to me.[/INDENT]

Perhaps someone can tell me whether or not any of these items are related.  And how do I cure them?  I am not a computer geek, so I'd appreciate advice in VERY simple terminology, please.

As always, my apologies for being a nuisance - I really do appreciate your help.  Thanks in advance,

Tony

---

### Post by Method X on 2010-03-12
Its ok.

> Ubuntu.Linux 2.6.31-20-generic
Ubuntu, Linux 2.6.31-20-generic (recovery mode)
Ubuntu, Linux 2.6.31-19-generic
Ubuntu, Linux 2.6.31-19-generic (recovery mode)
Ubuntu, Linux 2.6.31-18-generic
Ubuntu, Linux 2.6.31-18-generic (recovery mode)
Ubuntu, Linux 2.6.31-17-generic
Ubuntu, Linux 2.6.31-17-generic (recovery mode)
Ubuntu, Linux 2.6.31-16-generic
Ubuntu, Linux 2.6.31-16-generic (recovery mode)
Ubuntu, Linux 2.6.31-15-generic
Ubuntu, Linux 2.6.31-15-generic (recovery mode)
Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic (recovery mode)

Its only kernels, you can comment them in /boot/grub/grub.cfg or just delete with synaptic.

You have only ONE ubuntu installed, and kernels are just configuration.
;)

About your laptop temperature:
Maybe you installed x64 version?

And about errors with soft: depences are brocken. Its better to use:

sudo aptitude safe-upgrade

---

### Post by Tikkyca on 2010-03-12
It's ok,kernels...

---

### Post by spiky001 on 2010-03-12
If deleteing them with synaptic it best to leave at least 1 other proberbly 2:6:31:19
just incase the new 1 breaks you can still get in to system to fix it

---

### Post by audiomick on 2010-03-12
> **Tony.B said:**
> I've had problems with Ubuntu ever since I installed 9.10 and I wonder if I have installed it correctly.

When I switch on my computer I get a page saying[INDENT]GRUB loading[/INDENT]followed by a page headed[INDENT]GNU GRUB version 1.97~beta4[/INDENT]This page then seems to tell me that I have 7 installations of Ubuntu, which all seem to me to be the same:[INDENT]Ubuntu.Linux 2.6.31-20-generic
Ubuntu, Linux 2.6.31-20-generic (recovery mode)
Ubuntu, Linux 2.6.31-19-generic
Ubuntu, Linux 2.6.31-19-generic (recovery mode)
Ubuntu, Linux 2.6.31-18-generic
Ubuntu, Linux 2.6.31-18-generic (recovery mode)
Ubuntu, Linux 2.6.31-17-generic
Ubuntu, Linux 2.6.31-17-generic (recovery mode)
Ubuntu, Linux 2.6.31-16-generic
Ubuntu, Linux 2.6.31-16-generic (recovery mode)
Ubuntu, Linux 2.6.31-15-generic
Ubuntu, Linux 2.6.31-15-generic (recovery mode)
Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic (recovery mode)
Memory test etc[/INDENT]Is this correct?  If it's not correct, how do I get rid of the 6 unwanted versions?
This is normal and nothing to worry about. It just means that you have installed a few updates. When you get a kernel update, the old one is not removed. As you can see from the last number of the kernel names, the are not exactly the same but rather successive updates.

There are instructions on removing old kernels towards the end of the first post on this thread
[http://ubuntuforums.org/showthread.php?t=818177](http://ubuntuforums.org/showthread.php?t=818177)[INDENT] > The problems I'm having are:(a) my laptop (Acer Aspire 5315) switches off after about 25 minutes. It seems to get quite hot. I didn't notice this with the previous version of Ubuntu, and it certainly didn't happen when I used Vista (sorry if that's a swearword). When I restart the computer, the problem disappears. This seems to be a problem with this model of computer and I see there's something called a "patch" but I've no idea how to access it or use it.a patch is an alteration to the OS to fix the problem. Sorry, but I don't know how to install them either. I think you have to re-compile whatever part of the OS the patch is applied to.

> (b) I get error messages every time I use Update Manager, or if I try to download anything from Ubuntu Software Centre.  The usual message is[INDENT]Package Operation failed
The installation or removal of a software package failed[/INDENT]- followed by a complete stream of computer jargon like this[INDENT]```
installArchives() failed: Selecting previously deselected package glabels-data.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 207374 files and directories currently installed.)
Unpacking glabels-data (from .../glabels-data_2.2.5-0ubuntu1_all.deb) ...
Selecting previously deselected package glabels.
Unpacking glabels (from .../glabels_2.2.5-0ubuntu1_i386.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for shared-mime-info ...
Processing triggers for man-db ...
Setting up liba52-0.7.4 (0.7.4-11ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing liba52-0.7.4 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libdvdread4 (4.1.3-5ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libdvdread4 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libid3tag0 (0.15.1b-10build1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libid3tag0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libmad0 (0.15.1b-4) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libmad0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libmpeg2-4 (0.4.1-3) ...
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libmpeg2-4 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libsidplay1 (1.36.59-5) ...
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libsidplay1 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of gstreamer0.10-plugins-ugly:
 gstreamer0.10-plugins-ugly depends on liba52-0.7.4; however:
  Package liba52-0.7.4 is not configured yet.
 gstreamer0.10-plugins-ugly depends on libdvdread4 (>= 4.1.3); however:
  Package libdvdread4 is not configured yet.
 gstreamer0.10-plugins-ugly depends on libid3tag0 (>= 0.15.1b); however:
  Package libid3tag0 is not configured yet.
 gstreamer0.10-plugins-ugly depends on libmad0 (>= 0.15.1b-3); however:
  Package libmad0 is not configured yet.
 gstreamer0.10-plugins-ugly depends on libmpeg2-4; however:
  Package libmpeg2-4 is not configured yet.
 gstreamer0.10-plugins-ugly depends on libsidplay1; however:
  Package libsidplay1 is not configured yet.
dpkg: error processing gstreamer0.10-plugins-ugly (--configure):
 dependency problems - leaving unconfigured
Setting up glabels-data (2.2No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
.5-0ubuntu1) ...

Setting up glabels (2.2.5-0ubuntu1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
/sbin/ldconfig.real: File /usr/lib/liba52-0.7.4.so is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libsidplay.so.1 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libid3tag.so.0.3.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmpeg2convert.so.0.0.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libsidplay.so.1.0.3 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmad.so.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libid3tag.so.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmad.so.0.2.1 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libdvdread.so.4.1.3 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmpeg2convert.so.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmpeg2.so.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmpeg2.so.0.0.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libdvdread.so.4 is empty, not checked.
Errors were encountered while processing:
 liba52-0.7.4
 libdvdread4
 libid3tag0
 libmad0
 libmpeg2-4
 libsidplay1
 gstreamer0.10-plugins-ugly
```[/INDENT]I've completed bug reports and had some replies, but these are so technical I'm not even sure they were meant to be sent to me.Don't really know what is going on there. You could try the "fix broken packages" function in the synaptic package manager in the "edit" menu. I don't if that will help, but it shouldn't hurt.
[/INDENT] by the way, you can put long text blocks in a nice box like in the quote above by using the # button in the post window to put code tags around it.

---

### Post by sublimation on 2010-03-12
Just in case you're not that familiar with what they're talking about...

Go to System -> Administration -> Synaptic Package Manager
type in your password.

For me the easiest way to find all the kernels I have installed is by clicking on **Status** on the lower left, then the "Installed" section on the left side.

Now in the Search box above the main section, type "linux-headers". You should see all those same packages as on your boot list. I'd recommend highlighting all the "linux-headers-2.6.blah" except for 
"linux-headers-2.6.31-19", "linux-headers-2.6.31-19-generic", 
"linux-headers-2.6.31-20", and "linux-headers-2.6.31-20-generic"
right click and choose **Mark for Removal**

it's safe to keep two options just in case.

change the search box to "linux-image" and again pick all but the two most recent versions for removal. 

almost forgot, you should leave the "linux-image-generic" and "linux-headers-generic" packages alone, they help with updates.

then go ahead and apply changes.

Next time you boot, you should see far fewer options.

hope that helps!

EDIT: Looks like you beat me to the punch Michael!

---

### Post by Tony.B on 2010-03-12
Thanks, everyone for the fast responses. So it would appear I had too many KERNELS, whatever they are.

Following **Sublimation**'s nice detailed instructions, I've been able to get rid of most of them. It seemed to work fine, thank you, but of course I received the inevitable failure report. I took a screenshot of the report, but I'm not sure I know how to show it here:
/home/tony/Desktop/Screenshot.png

I think I've read somewhere on a forum or bug report that the sudden switching-off of my computer is somehow linked to the crashes whenever Update Manager is used, but I'm not sure about this. My previous post on this subject didn't elicit any replies, let's hope for better luck in this thread.

Tony

---

### Post by Tony.B on 2010-03-12
OK. I've just learnt how to do something else.  Here's the screen shot (I hope)

---

### Post by Tony.B on 2010-03-12
> **audiomick said:**
> Don't really know what is going on there. You could try the "fix broken packages" function in the synaptic package manager in the "edit" menu. I don't if that will help, but it shouldn't hurt.
Thanks for the idea, Michael. Unfortunately it didn't make any difference.

Cheers,
Tony

---

### Post by Djalmahal on 2010-03-12
About your temperature:

I had problems with my Toshiba:

Some kernels didn't let the fan kick in,therefore the CPU was overheating and the computer shut down.

You might want to go to GRUB and try out differnet kernels (if it worked fine with an older Ubuntu Version try out those kernels) and see if the fan kicks in.

Upgrading to Karmic (9.10) solved my overheating.
You can watch your CPU temperature with "sensor-applet", install it through synaptic and the add to panel

Hope that helps
Andreas

---

### Post by cusinmex on 2010-03-12
Everyone has said it right.

Its the same Ubuntu, only thing that changes are the kernels.;)

---

### Post by Tony.B on 2010-03-13
Thanks, Andreas, for your reply.

> **Djalmahal said:**
> You might want to go to GRUB and try out differnet kernels (if it worked fine with an older Ubuntu Version try out those kernels) and see if the fan kicks in.
I'm sorry, I don't know what you're talking about. It sounds a bit dangerous to me.

> **Djalmahal said:**
> You can watch your CPU temperature with "sensor-applet", install it through synaptic and the add to panel
Thanks for the advice.  I went to Synaptic and found something called **Sensord** which seemed to be the thing you mentioned. So I marked it for installation and pressed **Apply**. I know this sounds incredibly stupid but, now that it's installed, where do I find it?


Thanks,
Tony

---

### Post by Tony.B on 2010-03-13
> **cusinmex said:**
> Everyone has said it right.

Its the same Ubuntu, only thing that changes are the kernels.;)

Thank you for the reassurance about all the other offers of help.

I looked up **Kernel** on Wikipedia and found out that it is "the central component of most operating systems", which presumably means it's not the sort of thing an old wrinkly like me should be messing around with.

Tony

---

### Post by seenthelite on 2010-03-13
You could install Ubuntu Tweak and use it to remove anything that is no longer required such as redundant packages and kernels.

---

### Post by carandraug on 2010-03-13
> **Tony.B said:**
> Thanks for the advice.  I went to Synaptic and found something called **Sensord** which seemed to be the thing you mentioned. So I marked it for installation and pressed **Apply**. I know this sounds incredibly stupid but, now that it's installed, where do I find it?

By default, there should be two horizontal bars, one on the top and another on the bottom of the monitor where icons and windows are placed. These are the **panels**. Right click on where you want to see the temperature and choose "Add to panel...". A new window should appear with a list of stuff that can be added. Just find the one that you want.

I don't know **sensord** specifically but panel applications are added this way.

About the extra "ubuntus" I'll just further reassure you that it's perfectly natural, don't worry. You read right, it's the core of the operating system, the thing between the programs and the machine. It tells the machine what the program wants to be done, and then tells to the programs the results of what the machine did. Modules (called drivers in windows terminology), are also part of the kernel. If you want to be very picky, Linux is only the name of the kernel.

The reason you had several kernels, and why that's normal is the following. As you update your system, you install new versions of the kernel. These should work better and have less bugs. However, new bugs can also appear in this new versions. Bugs that in the most extreme cases could make your system unusable. That's why you keep the old kernels after installing a new version, until you're sure that the new version didn't make something stop working. They're usually automatically removed after sometime. Maybe the reason they hadn't been removed is related with your problems with updates.

Now that I explained the reason to keep old kernels, you can understand one of the possibilities of why you didn't had problems with old versions of Ubuntu. A kernel update may have messed up the way it controls your fan which leads to the overheating. This is the reason why it was suggested by **Djalmahal** that you try old versions of the kernel. The shutting the computer down automatically after 25min can be a safety thing that turns off the computer before it gets too hot which is happening because the fan is not being turned on (pun not intended).

Hope it's clear for you now.

---

### Post by 3rdalbum on 2010-03-13
What you need is the "lm-sensors" package from Synaptic. This installs a program called "sensors" that displays the readings from your sensors ONCE.

When you first run 'sensors' it will tell you a command you need to run first, to set up the sensor information.

As for your repositories problem, run:

```
sudo apt-get clean
```

I don't know if this is going to actually fix the problem, but I think you need to do it as part of the solution. (it doesn't do anything harmful).

---

### Post by Tony.B on 2010-03-13
Thank you, carandraug.  I had a look at the **Add to Panel** instruction and it all makes sense, but it seems that the Sensor application didn't load. 

I'm not sure whether it's me, my laptop or this particular installation of Ubuntu causing the problem, but there seems to be a very casual approach to commands, and often nothing happens. Except for the error messages every time I try to do something.

> **carandraug said:**
> ....As you update your system, you install new versions of the kernel. These should work better and have less bugs. However, new bugs can also appear in this new versions. Bugs that in the most extreme cases could make your system unusable. That's why you keep the old kernels after installing a new version, until you're sure that the new version didn't make something stop working. They're usually automatically removed after sometime. Maybe the reason they hadn't been removed is related with your problems with updates.

Now that I explained the reason to keep old kernels, you can understand one of the possibilities of why you didn't had problems with old versions of Ubuntu. A kernel update may have messed up the way it controls your fan which leads to the overheating. This is the reason why it was suggested by **Djalmahal** that you try old versions of the kernel. The shutting the computer down automatically after 25min can be a safety thing that turns off the computer before it gets too hot which is happening because the fan is not being turned on (pun not intended).

Hope it's clear for you now.

Yes, I think that's clear.  It seems that I should not have deleted these old kernels after all, because I can no longer go back and see if they work.

So, I think I'll have to live with the switching-off problem until the upgrade to 10.4 in a few weeks, when everything will, hopefully, be perfect.


My main concern now is that every time I use Update Manager, my system crashes, but I guess I should probably open  up a new thread next time it happens.

Thanks again for your input.

Tony

---

### Post by Tony.B on 2010-03-13
Thank you, 3rdAlbum, for your reply.

> **3rdalbum said:**
> What you need is the "lm-sensors" package from Synaptic. This installs a program called "sensors" that displays the readings from your sensors ONCE.

When you first run 'sensors' it will tell you a command you need to run first, to set up the sensor information.

Unfortunately **Sensors** refused to install.

> **3rdalbum said:**
> As for your repositories problem, run:

```
sudo apt-get clean
```

I don't know if this is going to actually fix the problem, but I think you need to do it as part of the solution. (it doesn't do anything harmful).

This is the only instruction I've run that fails to produce an error report.  But it doesn't seem to do anything at all.  I was expecting a long string of unintelligible rambling, but all I got was:
[INDENT]tony@tony-laptop:~$ sudo apt-get clean
[sudo] password for tony:
tony@tony-laptop:~$[/INDENT]
Is this ok?

Please accept my apologies for not being as computer-literate as everybody else.

Tony

---

### Post by audiomick on 2010-03-13
> **Tony.B said:**
> .... it doesn't seem to do anything at all.  I was expecting a long string of unintelligible rambling, but all I got was:[INDENT]tony@tony-laptop:~$ sudo apt-get clean
[sudo] password for tony:
tony@tony-laptop:~$[/INDENT]Is this ok?

Please accept my apologies for not being as computer-literate as everybody else.

Tony
I think it is ok. I ran it on mine and got the same. Sometimes you don't see much of anything.

No need to apologise. No-one is born knowing about computers...;)

edit: This is from the man page of apt-get
 ```
clean
           clean clears out the local repository of retrieved package files.
           It removes everything but the lock file from
           /var/cache/apt/archives/ and /var/cache/apt/archives/partial/. When
           APT is used as a dselect(8) method, clean is run automatically.
           Those who do not use dselect will likely want to run apt-get clean
           from time to time to free up disk space.
``` I went and looked in the directories that this refers to, and they are empty, so I assume the command did it's work.

Do you know about man pages? You made mention of a "casual approach to commands". If you want to know what a command is supposed to do, type
```
man <command name>
``` in a terminal to read about the command and it's options.
A common one, for instance is
```
sudo fdisk -l
```
whereby that is actually two commands.
```
man sudo
```will tell you about the first bit
```
man fdisk
```will tell you about fdisk and what the -l is for.
Hope that helps.

---

### Post by albert s on 2010-03-13
> **Djalmahal said:**
> About your temperature:

I had problems with my Toshiba:

Some kernels didn't let the fan kick in,therefore the CPU was overheating and the computer shut down.

You might want to go to GRUB and try out differnet kernels (if it worked fine with an older Ubuntu Version try out those kernels) and see if the fan kicks in.

Upgrading to Karmic (9.10) solved my overheating.
You can watch your CPU temperature with "sensor-applet", install it through synaptic and the add to panel

Hope that helps
Andreas


Ive just installed this      "  Sensors-Applet  "   via synaptic, what sort of temps should I be looking for, I have  54c 40c 40c , and do I even have temp sensors in my PC,.?
sorry if this is a dumb question. I know everything has an optimal working temp, just no idea about computers or even if I have a sensor.  :rolleyes:

---

### Post by audiomick on 2010-03-13
You do have sensors. I just installed the applet myself. I am seeing 47°C for the grahpics card and 27°C and 33°C for the two drives on my well ventilated desktop. Is your machine a laptop? If so, I think it is likely to run a bit warmer. I don't think those temperatures are too high, but it does strike me as being rather on the warmer side than on the cooler side. I think upwards of 60°C is when you need to start being concerned, but I don't know for sure. For exact values about optimal / maximum temps, you should consult the documentation for your hardware.

---

### Post by albert s on 2010-03-13
> **audiomick said:**
> You do have sensors. I just installed the applet myself. I am seeing 47°C for the grahpics card and 27°C and 33°C for the two drives on my well ventilated desktop. Is your machine a laptop? If so, I think it is likely to run a bit warmer. I don't think those temperatures are too high, but it does strike me as being rather on the warmer side than on the cooler side. I think upwards of 60°C is when you need to start being concerned, but I don't know for sure. For exact values about optimal / maximum temps, you should consult the documentation for your hardware.

thanks audiomick,
no, its a desktop, but having had the cover off it last night to look at putting another HD in I noticed it only had a small (2 1/2" ?) fan fitted, Im assuming I need something more substantial. I have a spare fan, could I fit that to suck cool air in?

sorry for hijacking the thread.

---

### Post by audiomick on 2010-03-13
> **albert s said:**
>  I have a spare fan, could I fit that to suck cool air in?

sorry for hijacking the thread.I don't know of any reason why not, but don't ask me  where to plug it in....

---

### Post by albert s on 2010-03-13
> **audiomick said:**
> I don't know of any reason why not, but don't ask me  where to plug it in....

LOL,
I suppose I can have a look for a suitable plug,
failing that, my missus has an old laptop cooler with fans fitted that simply plug into USB, so might be an internal USB port, I'll take it apart first,!   :D
my card temp is now at 56c, so rising slowly.
thanks.

---

### Post by Tony.B on 2010-03-13
[SIZE="2"]Thank you again for your help, Michael...
[/SIZE]
> **audiomick said:**
> No need to apologise. No-one is born knowing about computers...;)
[SIZE="2"].... and for being so understanding. My problem was the misfortune of being born a few decades too early.

Cheers,
Tony[/SIZE]

---

### Post by Tony.B on 2010-03-13
> **albert s said:**
> sorry for hijacking the thread.
No problem.  It sounds as if you're trying to start a fan club  :D

Tony

---

### Post by albert s on 2010-03-13
> **Tony.B said:**
> No problem.  It sounds as if you're trying to start a fan club  :D

Tony


:p

thanks Tony,
this is all a learning curve for me too.

---

### Post by audiomick on 2010-03-13
> **Tony.B said:**
> No problem.  It sounds as if you're trying [COLOR=Red]to start a fan club[/COLOR]  :D

Tony
That was almost painful....;)

@albert s : if you have a power supply from something that supplies the right voltage and current, you could run your fan with that.
A friend of mine gave me one that he had connected to a universal power supply of the type that you can get from electronics shops. It is the "luxury" version: the power supply has several voltage levels, and switching them makes the fan run faster or slower. The important thing is that the power supply can supply enough current, and it should only supply a max. voltage as high as the fan can stand.

---

### Post by Tony.B on 2010-03-13
> **Tony.B said:**
> No problem.  It sounds as if you're trying to start a fan club  :D
> **audiomick said:**
> That was almost painful....;)
Agreed, but it was too good to resist!

---

### Post by carandraug on 2010-03-13
> **Tony.B said:**
> 
I've completed bug reports and had some replies, but these are so technical I'm not even sure they were meant to be sent to me.

Perhaps someone can tell me whether or not any of these items are related.  And how do I cure them?  I am not a computer geek, so I'd appreciate advice in VERY simple terminology, please.

Could you give us the link for the bug reports? Maybe we can explain what they mean and if they are directed at you or not.

---

### Post by Tony.B on 2010-03-13
Hi Carandraug.
> **carandraug said:**
> Could you give us the link for the bug reports? Maybe we can explain what they mean and if they are directed at you or not.
I'm not sure what you mean by the word "link", but I've got emails about
[INDENT]Bug 512096
Bug 515032
Bug 529103
Bug 535007[/INDENT]
Is this what you want?

Regards,
Tony

---

### Post by Tony.B on 2010-03-13
Out of curiosity to see what I can look forward to using, I googled Lucid Lynx, and came across the following, which is a direct quote from  [http://www.ghacks.net/2010/02/27/ubuntu-10-4-my-first-impressions/](http://www.ghacks.net/2010/02/27/ubuntu-10-4-my-first-impressions/)  dated 27 February 2010.

[INDENT]**Stability**

The alpha version of 10.4 is certainly NOT to be used in a production environment. If you want to see what is up and coming make sure you do so in either a virtual machine or on a test machine only. Why? You will experience crashing. Right now you can not install software with the UBC without a crash. The software installs, but a crash is reported as well.[/INDENT]

That seems to be exactly my experience with 9.10 Karmic Koala.

---

### Post by audiomick on 2010-03-13
Hi Tony.
Still don't have any really good ideas, but:
> **Tony.B said:**
> I think I've read somewhere on a forum or bug report that the sudden switching-off of my computer is somehow linked to the crashes whenever Update Manager is used, but I'm not sure about this.
This might be true, particularly if it has switched off during an operation that the package manager /software centre / update manager was carrying out.

Here are two more commands to try. I don't know if they will really help, but they wont hurt. I just tried them both on my machine, and no smoke came out, at least.

The first one tells dpkg, which is the package manager at the heart of synaptic, aptitude, the software centre and what have you, to configure any packages that are on the machine but not configured.
```
sudo dpkg --configure -a
```

The next one tells apt-get, which is also part of the whole package management mechanism, to update it's list of packages, so that it is definitely looking for the latest version of everything.
```
sudo apt-get update
```

The "sudo" means "do this with root privileges", and will cause a password request. The required password is the one you log on with. You wont see what you are typing when you type your password in the terminal in response to a password request. Just type it in and hit enter.

As I said, this may not help at all, but I hope it does.

---

### Post by Djalmahal on 2010-03-13
Sorry Tony, I was offline for a while:

- Loading a different kernel is easy. When your computer boots up in the beginning you will see "GRUB loading", you then press ESC, and i shows up the different "UBuntus" you mentioned in your first post, instead of loading the newest by default, scroll down a bit and load an older one instead, then see how the computer behaves, i.e. if it overheats. 

I thought my fan was broken till I updated to Karmic, and with the new kernel the fan worked perfectly.

Tio install the senser load "sensor-applet" in synaptic, then add to the panel as described in one of the previous posts.

Hope that helps
Andreas

---

### Post by carandraug on 2010-03-13
> **Tony.B said:**
> I'm not sure what you mean by the word "link",
I mean something like this [https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/512096](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/512096) pointing to the page where the bugs is.

> **Tony.B said:**
> Bug 512096

According to the description, this bug comes from when the computer shuts down when something was being installed. This is the reason when you are upgrading something while on battery power only, it warns you of that and asks if you're sure you want to continue. Considering your overheating problem, this can be the origin of the update manager problem (which is actually a problem on dpkg. I'll explain better what this is further ahead). What they say to solve this is to run the following commands in a terminal
```

sudo apt-get clean
sudo aptitude download PACKAGE
sudo dpkg --unpack ./PACKAGE_VERSION.deb
sudo dpkg --configure PACKAGE

```

and replacing PACKAGE by the name of the package that fails to install.
The first command erases previous downloaded (not installed) packages from the database which may be corrupted (for example, because it shut down in the middle of the download). The second downloads the package but does not installs it. The third unpacks the package, i.e. it opens the package and takes all the files out but does not configure it so it doesn't count as installed. The last one runs the configuration, placing all the files where they should be, thus making it installed. You're basically doing the installation process step-by-step instead of all in just one command as it's usual.

> **Tony.B said:**
> 
Bug 515032
Bug 529103
Bug 535007


All these are duplicates of the other bug report. That is, they are all related to the same bug. This can be because the other persons didn't search if the bug had already been reported before submitting a new one or maybe they were not aware that the bug was the same. For example, you could fill a bug report about installing firefox thinking that the bug was on firefox. Then someone else would fill a bug report about installing openoffice thinking the bug was in openoffice. However, the bug could actually be on the program that takes care of installing stuff in Ubuntu (dpkg in this case). They are duplicates of one another, it's the same bug, they just look different.

All that said run the following commands to download and install manually the package dpkg. In the bug report it says that a new version was released 2 days ago that should fix this bug. Fingers crossed that will solve your problem (to be honest, I'm not very confident that it will).

```

sudo apt-get clean
sudo apt-get update
sudo aptitude download dpkg
sudo dpkg --unpack ./dpkg_1.15.4ubuntu2.1_i386.deb
sudo dpkg --configure dpkg

```

My instructions have one flaw. If by the time you read this a new update of the dpkg has come out, the 4th command will not work because the package file will have a new name. The better way to do this step is to write (and not run) the command

```
sudo dpkg --unpack ./dpkg_
```
and then press tab once (tab is the key usually above Caps lock). This key tries to auto-complete a command. Since it's unlikely that you have more than one file that starts by dpkg_ , it should autocomplete for the full name of the file. Once the name has been filled press enter and continue for the 5th command.

After all this try to run the Update manager to see if you get any other error.

Good luck and let us know how it went.

---

### Post by qwerty2009 on 2010-03-13
your laptop turning off after 25mins is a hardware issue if you check back on my posts you'll notice that my Acer aspire 5315 just went dead on me one day(still wont start) it was overheating for a few months then the battery life went down suddenly to bout 30 mins, then it started just turning off until about 2 months after it wouldn't even start. 

i took it to get repaired and they told me it was gone for good lol 

id suggest you start saving up for a new laptop soon as plenty of people 5315's stop working.

---

### Post by Tony.B on 2010-03-14
Thanks, qwerty2009, for your input
> **qwerty2009 said:**
> id suggest you start saving up for a new laptop soon as plenty of people 5315's stop working.
I'm hoping for better news than this!

---

### Post by Tony.B on 2010-03-14
Hello Michael
> **audiomick said:**
> Here are two more commands to try. I don't know if they will really help, but they wont hurt. I just tried them both on my machine, and no smoke came out, at least.
No smoke came out of my laptop either.
I got the following printout:
[INDENT]tony@tony-laptop:~$ sudo dpkg --configure -a
[sudo] password for tony: 
Setting up libdvdread4 (4.1.3-5ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libdvdread4 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up liba52-0.7.4 (0.7.4-11ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing liba52-0.7.4 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of gstreamer0.10-plugins-ugly:
 gstreamer0.10-plugins-ugly depends on liba52-0.7.4; however:
  Package liba52-0.7.4 is not configured yet.
 gstreamer0.10-plugins-ugly depends on libdvdread4 (>= 4.1.3); however:
  Package libdvdread4 is not configured yet.
dpkg: error processing gstreamer0.10-plugins-ugly (--configure):
 dependency problems - leaving unconfigured
Setting up libsidplay1 (1.36.59-5) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libsidplay1 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libmpeg2-4 (0.4.1-3) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libmpeg2-4 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libmad0 (0.15.1b-4) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libmad0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libid3tag0 (0.15.1b-10build1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libid3tag0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 libdvdread4
 liba52-0.7.4
 gstreamer0.10-plugins-ugly
 libsidplay1
 libmpeg2-4
 libmad0
 libid3tag0
tony@tony-laptop:~$ sudo apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg                            
Get: 1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                          
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_GB          
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_GB              
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                      
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB                         
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic Release.gpg                  
Get: 2 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Translation-en_GB [63.7kB]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_GB      
Get: 3 [http://dl.google.com](http://dl.google.com) stable Release [2,540B]                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_GB    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release                         
Get: 4 [http://dl.google.com](http://dl.google.com) stable/main Packages [922B]                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages                   
Get: 5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Translation-en_GB [3,402B]
Get: 6 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Translation-en_GB [33.2kB] 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Get: 7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Translation-en_GB [43.8kB]
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates Release.gpg             
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Translation-en_GB     
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Translation-en_GB   
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic Release                                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates Release                        
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Packages                          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Packages                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Sources                           
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Sources                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Packages                      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Sources                       
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Packages                    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Sources[/INDENT]
I, of course, have absolutely no idea what any of this means.
Thanks,
Tony
PS I've just noticed a big NO ENTRY sign on my top Panel. If I hover the mouse over it, it says *An error occurred when checking for updates.*  Is this any help?

---

### Post by Tony.B on 2010-03-14
Thank you for the input, Andreas.
> **Djalmahal said:**
> Loading a different kernel is easy. When your computer boots up in the beginning you will see "GRUB loading", you then press ESC, and i shows up the different "UBuntus" you mentioned in your first post, instead of loading the newest by default, scroll down a bit and load an older one instead, then see how the computer behaves, i.e. if it overheats.
I'll see what happens later. Gosh, I'm learning so much from all you kind people.  I'm just scared I'll forget it all when senile dementia kicks in.
Cheers,
Tony

---

### Post by Tony.B on 2010-03-14
Hello carandraug.

Sorry I was so dense about "link". Here is the answer:
[INDENT][https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/512096](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/512096)
[https://bugs.launchpad.net/ubuntu/+source/celestia/+bug/515032](https://bugs.launchpad.net/ubuntu/+source/celestia/+bug/515032)
[https://bugs.launchpad.net/ubuntu/+source/a52dec/+bug/535007](https://bugs.launchpad.net/ubuntu/+source/a52dec/+bug/535007)
[https://bugs.launchpad.net/ubuntu/+bug/529103](https://bugs.launchpad.net/ubuntu/+bug/529103)[/INDENT]

Thank you for explaining so much to me in your post.  I am always amazed at how many kind people there are on these forums.

You helped tremendously; I think I understand quite a lot more now.

OK, so I ran the next set of instructions, taking your first alternative because I assumed that, being Sunday, there would be a lower possibility of a new package being produced.  I got:
[INDENT]tony@tony-laptop:~$ sudo apt-get clean
[sudo] password for tony: 
tony@tony-laptop:~$ sudo apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg
Get: 1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Translation-en_GB
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_GB
Get: 2 [http://dl.google.com](http://dl.google.com) stable Release [2,540B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Translation-en_GB
Get: 3 [http://dl.google.com](http://dl.google.com) stable/main Packages [922B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Sources
Fetched 3,651B in 8s (416B/s)              
Reading package lists... Done
tony@tony-laptop:~$ sudo aptitude download dpkg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done
Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main dpkg 1.15.4ubuntu2.1 [2,126kB]
Fetched 2,126kB in 53s (39.7kB/s)           
tony@tony-laptop:~$ sudo dpkg --unpack ./dpkg_1.15.4ubuntu2.1_i386.deb
(Reading database ... 140789 files and directories currently installed.)
Preparing to replace dpkg 1.15.4ubuntu2.1 (using .../dpkg_1.15.4ubuntu2.1_i386.deb) ...
Unpacking replacement dpkg ...
Processing triggers for man-db ...
tony@tony-laptop:~$ sudo dpkg --configure dpkg
Setting up dpkg (1.15.4ubuntu2.1) ...

tony@tony-laptop:~$[/INDENT]

I then ran Update Manager. There was only an Update to Adobe Flash Player, which I tried to install but I got the following error message:
[INDENT]E: liba52-0.7.4: subprocess installed post-installation script returned error exit status 2
E: libdvdread4: subprocess installed post-installation script returned error exit status 2
E: libid3tag0: subprocess installed post-installation script returned error exit status 2
E: libmad0: subprocess installed post-installation script returned error exit status 2
E: libmpeg2-4: subprocess installed post-installation script returned error exit status 2
E: libsidplay1: subprocess installed post-installation script returned error exit status 2
E: gstreamer0.10-plugins-ugly: dependency problems - leaving unconfigured[/INDENT]

So I went back to try your next instruction on the assumption that I was wrong about the Sunday working thing.  I got:
[INDENT]tony@tony-laptop:~$ sudo apt-get clean
[sudo] password for tony: 
tony@tony-laptop:~$ sudo apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                     
Get: 1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                          
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_GB              
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_GB          
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic Release.gpg                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Translation-en_GB          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Translation-en_GB    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Translation-en_GB      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Translation-en_GB    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates Release.gpg             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Translation-en_GB
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Translation-en_GB
Get: 2 [http://dl.google.com](http://dl.google.com) stable Release [2,540B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources    
Get: 3 [http://dl.google.com](http://dl.google.com) stable/main Packages [922B]              
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Sources
Fetched 3,651B in 5s (641B/s)
Reading package lists... Done
tony@tony-laptop:~$ sudo aptitude download dpkg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main dpkg 1.15.4ubuntu2.1 [2,126kB]
Fetched 1B in 0s (5B/s)
tony@tony-laptop:~$ sudo dpkg --unpack ./dpkg_1.15.4ubuntu2.1_i386.deb 
(Reading database ... 140789 files and directories currently installed.)
Preparing to replace dpkg 1.15.4ubuntu2.1 (using .../dpkg_1.15.4ubuntu2.1_i386.deb) ...
Unpacking replacement dpkg ...
Processing triggers for man-db ...
tony@tony-laptop:~$ sudo dpkg --configure dpkg
Setting up dpkg (1.15.4ubuntu2.1) ...

tony@tony-laptop:~$[/INDENT]

This time, when I ran Update Manager, all I got was
[INDENT]**Your system is up-to-date**
The package information was updated less than one hour ago.[/INDENT]

Is any of this at all meaningful?

Thank you,
Tony

---

### Post by audiomick on 2010-03-14
Hi Tony. Here's what I can see

> **Tony.B said:**
> 

OK, so I ran the next set of instructions, taking your first alternative because I assumed that, being Sunday, there would be a lower possibility of a new package being produced.  I got:[INDENT]```
tony@tony-laptop:~$ sudo apt-get clean
[sudo] password for tony: 
```[/INDENT][INDENT]
That worked. (I think we had already done that, but never mind that)
> ```
tony@tony-laptop:~$ sudo apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg
Get: 1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic Release.gpg
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Translation-en_GB
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_GB
Get: 2 [http://dl.google.com](http://dl.google.com) stable Release [2,540B]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Translation-en_GB
Get: 3 [http://dl.google.com](http://dl.google.com) stable/main Packages [922B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Sources
Fetched 3,651B in 8s (416B/s)              
Reading package lists... Done
```That worked. (updated your package lists)
> ```
tony@tony-laptop:~$ sudo aptitude download dpkg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Writing extended state information... Done
Get:1 [http://gb.archive.ubuntu.com]("http://gb.archive.ubuntu.com/") karmic-updates/main dpkg 1.15.4ubuntu2.1 [2,126kB]
Fetched 2,126kB in 53s (39.7kB/s)           
```Worked. (got the newest version of dpkg)
> ```
tony@tony-laptop:~$ sudo dpkg --unpack ./dpkg_1.15.4ubuntu2.1_i386.deb
(Reading database ... 140789 files and directories currently installed.)
Preparing to replace dpkg 1.15.4ubuntu2.1 (using .../dpkg_1.15.4ubuntu2.1_i386.deb) ...
Unpacking replacement dpkg ...
Processing triggers for man-db ...
```Worked. (unpacked dpkg)

> ```
tony@tony-laptop:~$ sudo dpkg --configure dpkg
Setting up dpkg (1.15.4ubuntu2.1) ...

tony@tony-laptop:~$
```Worked. (configured the new dpkg)
> I then ran Update Manager. There was only an Update to Adobe Flash Player, which I tried to install but I got the following error message:```
E: liba52-0.7.4: subprocess installed post-installation script returned error exit status 2
E: libdvdread4: subprocess installed post-installation script returned error exit status 2
E: libid3tag0: subprocess installed post-installation script returned error exit status 2
E: libmad0: subprocess installed post-installation script returned error exit status 2
E: libmpeg2-4: subprocess installed post-installation script returned error exit status 2
E: libsidplay1: subprocess installed post-installation script returned error exit status 2
E: [COLOR=Red]gstreamer0.10-plugins-ugly[/COLOR]: dependency problems - leaving unconfigured
```This failed, and this has been consistently failing for you all through the thread. You are somehow not able to install the package in red because the computer can't install it's dependencies.

> So I went back to try your next instruction on the assumption that I was wrong about the Sunday working thing.  I got:```
tony@tony-laptop:~$ sudo apt-get clean
[sudo] password for tony: 
```Worked (again...)


> ```
tony@tony-laptop:~$ sudo apt-get update
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                     
Get: 1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]                          
Ign [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Translation-en_GB              
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic Release                                
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_GB          
Hit [http://archive.canonical.com](http://archive.canonical.com) karmic/partner Packages                
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic Release.gpg                     
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Translation-en_GB          
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Translation-en_GB    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Translation-en_GB      
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Translation-en_GB    
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates Release.gpg             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Translation-en_GB
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_GB
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Translation-en_GB
Get: 2 [http://dl.google.com](http://dl.google.com) stable Release [2,540B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Translation-en_GB
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages   
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources    
Get: 3 [http://dl.google.com](http://dl.google.com) stable/main Packages [922B]              
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Translation-en_GB
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates Release
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/multiverse Sources
Fetched 3,651B in 5s (641B/s)
Reading package lists... Done
```worked (again...)
> ```
tony@tony-laptop:~$ sudo aptitude download dpkg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Get:1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) karmic-updates/main dpkg 1.15.4ubuntu2.1 [2,126kB]
Fetched 1B in 0s (5B/s)
tony@tony-laptop:~$ sudo dpkg --unpack ./dpkg_1.15.4ubuntu2.1_i386.deb 
(Reading database ... 140789 files and directories currently installed.)
Preparing to replace dpkg 1.15.4ubuntu2.1 (using .../dpkg_1.15.4ubuntu2.1_i386.deb) ...
Unpacking replacement dpkg ...
Processing triggers for man-db ...
tony@tony-laptop:~$ sudo dpkg --configure dpkg
Setting up dpkg (1.15.4ubuntu2.1) ...

tony@tony-laptop:~$
```[/INDENT]Successfully re-installed the latest version of dpkg
I know you love reading...;) Here is an explanation of what dpkg is
[http://en.wikipedia.org/wiki/Dpkg](http://en.wikipedia.org/wiki/Dpkg)

> This time, when I ran Update Manager, all I got was[INDENT]```
**Your system is up-to-date**
The package information was updated less than one hour ago.
```[/INDENT]Is any of this at all meaningful?The last message from the update manager looks quite hopeful, and could mean that your installing problems are solved...

What seems odd to me is that you have effectively just re-installed this: dpkg_1.15.4ubuntu2.1_i386.deb
twice, but the Update manager wasn't happy until after the second time. Maybe it just had something stuck in it's throat...:confused:

I hope that helps you make some sense of it all.


At this point, if you are still getting install errors, I would go into the synaptic package manager and de-install the gstreamer0.10-plugins-ugly package,

_** or**_ do
```
sudo apt-get purge gstreamer0.10-plugins-ugly
``` which amounts to the same thing. The command does exactly what "purge" implies. You can look it up in the man pages
```
man apt-get
```This is what the package manager has to say about the package
> GStreamer is a streaming media framework, based on graphs of filters
which operate on media data.  Applications using this library can do
anything from real-time sound processing to playing videos, and just
about anything else media-related.  Its plugin-based architecture means
that new data types or processing capabilities can be added simply by
installing new plug-ins.
[COLOR=Red]
This packages contains plugins from the "ugly" set, a set of
good-quality plug-ins that might pose distribution problems.[/COLOR]so if you remove it, the most that you are likely to lose is functionality in internet streaming or playing videos/music or something like that. I am guessing a bit, I don't know exactly what the package does, but if it were giving me grief I would just chuck it out and hope I don't notice it missing.

This again:
> ```

E: [COLOR=Blue]liba52-0.7.4[/COLOR]: subprocess installed post-installation script returned error exit status 2
E: [COLOR=Blue]libdvdread4[/COLOR]: subprocess installed post-installation script returned error exit status 2
E: [COLOR=Blue]libid3tag0[/COLOR]: subprocess installed post-installation script returned error exit status 2
E: [COLOR=Blue]libmad0[/COLOR]: subprocess installed post-installation script returned error exit status 2
E: [COLOR=Blue]libmpeg2-4[/COLOR]: subprocess installed post-installation script returned error exit status 2
E: [COLOR=Blue]libsidplay1[/COLOR]: subprocess installed post-installation script returned error exit status 2
E: [COLOR=Red]gstreamer0.10-plugins-ugly[/COLOR]: dependency problems - leaving unconfigured
```If you look in the synaptic package manager, search "gstreamer0.10-plugins-ugly", right click on it and chose properties, the second tab in the window that opens contains a list of the dependencies of the package. All the packages in blue above are in the list, so this error message seems to really revolve around the gstreamer0.10-plugins-ugly package.

Hope that is all clear as mud.

---

### Post by Tony.B on 2010-03-14
Good grief, Michael.  What a lot of trouble you've taken.  > **audiomick said:**
> I know you love reading...;) Here is an explanation of what dpkg is
[http://en.wikipedia.org/wiki/Dpkg](http://en.wikipedia.org/wiki/Dpkg) Actually, I'd already read the Wikipedia entry (honestly!) 

> **audiomick said:**
> I hope that helps you make some sense of it all.Now that I've read your post three times, I'm beginning to see a faint light of understanding.

At the moment, of course, I don't know if it's worked or not.  But in the meantime thank you so much for all the advice, help and patience you've shown.

If I still have a problem , I'll try removing that gstreamer thing.  Or I'll commit suicide.

Cheers,
Tony

---

### Post by audiomick on 2010-03-14
Well, I hope it is sorted out, anyway. I'd hate to see you messing up the carpet with drastic actions...

---

### Post by carandraug on 2010-03-14
> **Tony.B said:**
> Good grief, Michael.  What a lot of trouble you've taken.   Actually, I'd already read the Wikipedia entry (honestly!) 

Now that I've read your post three times, I'm beginning to see a faint light of understanding.

At the moment, of course, I don't know if it's worked or not.  But in the meantime thank you so much for all the advice, help and patience you've shown.

If I still have a problem , I'll try removing that gstreamer thing.  Or I'll commit suicide.

Cheers,
Tony

It's not that hard to understand really. The dpkg software is what takes care of installing and removing packages from your system. In the wikipedia page it says that is low-level compared to aptitude. To understand what this low-level means, imagine the following. Dpkg and aptitude were actually software that could be used to instruct a robot to walk. Now imagine that you want to instruct the robot to walk. With dpkg you'd have to say
```

dpkg heigh distribution to left leg
dpkg move up right leg
dpkg move front right leg
dpkg move down right leg
dpkg join left leg to right leg

```
with aptitude instead, you'd say
```

aptitude move front

```

It also says that aptitude is more complex than dpkg taking care of dependencies. To understand this, imagine that the instructions that you wanted to give to the robot were to walk North instead of just walk. Then, your dpkg instructions would look like

```

check current orientation (with some other program other than dpkg)
if not facing north, calculate difference from North
dpkg rotate XX degrees
dpkg heigh distribution to left leg
dpkg move up right leg
dpkg move front right leg
dpkg move down right leg
dpkg join left leg to right leg

```

with apt-get all you'd need would be
```

aptitude move north

```

Aptitude (or apt-get or whatever) actually does the same as dpkg but it's much easier for the normal user to use aptitude, than to specify every single detail. Specially the automatically taking care of dependencies (which are the packages that one package depends on to do its work. For example, a program for instant messaging can have a program to give sounds as dependency so it can give you sound warnings when you receive new messages).

But you never know when something strange happens (for example, there's a wall North of the robot and aptitude was not made to check for that so when he tries to walk North, the robot bumps on to it and falls) and you need to use dpkg instead of aptitude.

On to your problem now. The output of your commands seems good to me as **audiomick** also said. There's a reason that package has the word ugly on its name.
I'd run the following commands (they kind of overlap with **audiomick** commands as they are more of an "extended version" of his suggestion)

```
sudo apt-get purge gstreamer0.10-plugins-ugly
sudo apt-get purge liba52-0.7.4
sudo apt-get purge libdvdread4
sudo apt-get purge libid3tag0
sudo apt-get purge libmad0
sudo apt-get purge libmpeg2-4
sudo apt-get purge libsidplay1
```

Note that this could be made into one big command but I think it'll be easier to follow up this way.
Then, run the following

```

sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install gstreamer0.10-plugins-ugly

```

All this should remove the offending package (and the dependencies that are giving trouble, then remove all packages that have been kept after downloading, re-downloads the list of packages and then installs all available updates. Finally, the last command will try to install the ugly package again. If it works, we can move on to try and solve your overheating problem. If you leave that unchecked it can later damage your computer by wearing it out.

One thing that you should consider doing when replying with the output from the console is to use the CODE tags. On the box to write your reply, there's a button with the # character. Click on it and the word CODE should appear twice between parenthesis (that's the tag). Paste the output between those. This will make it easier for us to read it.

---

### Post by Tony.B on 2010-03-14
First of all, thank you, carandraug, for your really helpful and understandable explanations.

But now I have a problem after executing your first command:
```
tony@tony-laptop:~$ sudo apt-get purge gstreamer0.10-plugins-ugly
[sudo] password for tony: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  gstreamer0.10-plugins-ugly*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
7 not fully installed or removed.
After this operation, 1,188kB disk space will be freed.
Do you want to continue [Y/n]?
```

Do I want to continue?

---

### Post by carandraug on 2010-03-14
> **Tony.B said:**
> Do I want to continue?

Yes you do. It's normal for those commands to ask you to confirm. Press Y and then Enter. And good use of the code tags ;)

---

### Post by durand on 2010-03-14
The easiest way to remove the kernel and keep ubuntu tidier is to just use Computer Janitor, which is here: System > Administration > Computer Janitor

---

### Post by Tony.B on 2010-03-14
Thank you, carandraug, yet again.

I had wondered how all you clever people had managed to get the format of your posts looking so good; I had no idea about the # in the toolbar.

Anyway, here's the print-out:

```
tony@tony-laptop:~$ sudo apt-get purge gstreamer0.10-plugins-ugly
[sudo] password for tony: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  gstreamer0.10-plugins-ugly*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
7 not fully installed or removed.
After this operation, 1,188kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 140787 files and directories currently installed.)
Removing gstreamer0.10-plugins-ugly ...
Setting up liba52-0.7.4 (0.7.4-11ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing liba52-0.7.4 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libdvdread4 (4.1.3-5ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libdvdread4 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libid3tag0 (0.15.1b-10build1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libid3tag0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libmad0 (0.15.1b-4) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libmad0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libmpeg2-4 (0.4.1-3) ...
No apport report written because MaxReports is reached already
                                                              dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libmpeg2-4 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libsidplay1 (1.36.59-5) ...
No apport report written because MaxReports is reached already
                                                              dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libsidplay1 (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 liba52-0.7.4
 libdvdread4
 libid3tag0
 libmad0
 libmpeg2-4
 libsidplay1
E: Sub-process /usr/bin/dpkg returned an error code (1)
tony@tony-laptop:~$ sudo apt-get purge liba52-0.7.4
[sudo] password for tony: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  liba52-0.7.4*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 111kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 140734 files and directories currently installed.)
Removing liba52-0.7.4 ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing liba52-0.7.4 (--purge):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 liba52-0.7.4
E: Sub-process /usr/bin/dpkg returned an error code (1)
tony@tony-laptop:~$ sudo apt-get purge libdvdread4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  liba52-0.7.4 libdvdread4*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 328kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 140724 files and directories currently installed.)
Removing liba52-0.7.4 ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing liba52-0.7.4 (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 liba52-0.7.4
E: Sub-process /usr/bin/dpkg returned an error code (1)
tony@tony-laptop:~$ sudo apt-get purge libid3tag0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  liba52-0.7.4 libid3tag0*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 242kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 140724 files and directories currently installed.)
Removing liba52-0.7.4 ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing liba52-0.7.4 (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 liba52-0.7.4
E: Sub-process /usr/bin/dpkg returned an error code (1)
tony@tony-laptop:~$ sudo apt-get purge libmad0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  liba52-0.7.4 libmad0*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 270kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 140724 files and directories currently installed.)
Removing liba52-0.7.4 ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing liba52-0.7.4 (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 liba52-0.7.4
E: Sub-process /usr/bin/dpkg returned an error code (1)
tony@tony-laptop:~$ sudo apt-get purge libmpeg2-4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  liba52-0.7.4 libmpeg2-4*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 299kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 140724 files and directories currently installed.)
Removing liba52-0.7.4 ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing liba52-0.7.4 (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 liba52-0.7.4
E: Sub-process /usr/bin/dpkg returned an error code (1)
tony@tony-laptop:~$ sudo apt-get purge libsidplay1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  liba52-0.7.4 libsidplay1*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 393kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 140724 files and directories currently installed.)
Removing liba52-0.7.4 ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing liba52-0.7.4 (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 liba52-0.7.4
E: Sub-process /usr/bin/dpkg returned an error code (1)
tony@tony-laptop:~$ sudo apt-get clean
tony@tony-laptop:~$ sudo apt-get update
Get: 1 http://dl.google.com stable Release.gpg [189B]
Hit http://archive.canonical.com karmic Release.gpg                            
Ign http://dl.google.com stable/main Translation-en_GB                         
Hit http://security.ubuntu.com karmic-security Release.gpg                     
Hit http://gb.archive.ubuntu.com karmic Release.gpg                            
Hit http://gb.archive.ubuntu.com karmic/main Translation-en_GB                 
Hit http://gb.archive.ubuntu.com karmic/restricted Translation-en_GB           
Hit http://gb.archive.ubuntu.com karmic/universe Translation-en_GB             
Hit http://gb.archive.ubuntu.com karmic/multiverse Translation-en_GB           
Ign http://archive.canonical.com karmic/partner Translation-en_GB              
Hit http://archive.canonical.com karmic Release                                
Hit http://archive.canonical.com karmic/partner Packages                       
Get: 2 http://dl.google.com stable Release [2,540B]                  
Ign http://security.ubuntu.com karmic-security/main Translation-en_GB 
Hit http://gb.archive.ubuntu.com karmic-updates Release.gpg           
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_GB
Ign http://gb.archive.ubuntu.com karmic-updates/main Translation-en_GB
Get: 3 http://dl.google.com stable/main Packages [922B]
Ign http://security.ubuntu.com karmic-security/universe Translation-en_GB
Ign http://gb.archive.ubuntu.com karmic-updates/restricted Translation-en_GB
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_GB
Ign http://gb.archive.ubuntu.com karmic-updates/universe Translation-en_GB
Hit http://security.ubuntu.com karmic-security Release
Ign http://gb.archive.ubuntu.com karmic-updates/multiverse Translation-en_GB
Hit http://security.ubuntu.com karmic-security/main Packages
Hit http://gb.archive.ubuntu.com karmic Release
Hit http://gb.archive.ubuntu.com karmic-updates Release             
Hit http://security.ubuntu.com karmic-security/restricted Packages  
Hit http://security.ubuntu.com karmic-security/main Sources
Hit http://gb.archive.ubuntu.com karmic/main Packages
Hit http://security.ubuntu.com karmic-security/restricted Sources
Hit http://gb.archive.ubuntu.com karmic/restricted Packages
Hit http://security.ubuntu.com karmic-security/universe Packages
Hit http://gb.archive.ubuntu.com karmic/main Sources
Hit http://gb.archive.ubuntu.com karmic/restricted Sources
Hit http://security.ubuntu.com karmic-security/universe Sources
Hit http://gb.archive.ubuntu.com karmic/universe Packages
Hit http://security.ubuntu.com karmic-security/multiverse Packages
Hit http://gb.archive.ubuntu.com karmic/universe Sources
Hit http://security.ubuntu.com karmic-security/multiverse Sources
Hit http://gb.archive.ubuntu.com karmic/multiverse Packages
Hit http://gb.archive.ubuntu.com karmic/multiverse Sources
Hit http://gb.archive.ubuntu.com karmic-updates/main Packages                  
Hit http://gb.archive.ubuntu.com karmic-updates/restricted Packages            
Hit http://gb.archive.ubuntu.com karmic-updates/main Sources                   
Hit http://gb.archive.ubuntu.com karmic-updates/restricted Sources             
Hit http://gb.archive.ubuntu.com karmic-updates/universe Packages              
Hit http://gb.archive.ubuntu.com karmic-updates/universe Sources               
Hit http://gb.archive.ubuntu.com karmic-updates/multiverse Packages            
Hit http://gb.archive.ubuntu.com karmic-updates/multiverse Sources             
Fetched 3,651B in 8s (414B/s)                                                  
Reading package lists... Done
tony@tony-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  liba52-0.7.4
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 111kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 140724 files and directories currently installed.)
Removing liba52-0.7.4 ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing liba52-0.7.4 (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 liba52-0.7.4
E: Sub-process /usr/bin/dpkg returned an error code (1)
tony@tony-laptop:~$ sudo apt-get install gstreamer0.10-plugins-ugly
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  gstreamer0.10-plugins-ugly
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 362kB of archives.
After this operation, 1,188kB of additional disk space will be used.
Get: 1 http://gb.archive.ubuntu.com karmic/universe liba52-0.7.4 0.7.4-11ubuntu1 [27.2kB]
Get: 2 http://gb.archive.ubuntu.com karmic/universe gstreamer0.10-plugins-ugly 0.10.12-1 [335kB]
Fetched 362kB in 10s (34.4kB/s)                                                
Selecting previously deselected package liba52-0.7.4.
(Reading database ... 140726 files and directories currently installed.)
Preparing to replace liba52-0.7.4 0.7.4-11ubuntu1 (using .../liba52-0.7.4_0.7.4-11ubuntu1_i386.deb) ...
Unpacking replacement liba52-0.7.4 ...
dpkg (subprocess): unable to execute old post-removal script: Exec format error
dpkg: warning: old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg: ... it looks like that went OK.
Selecting previously deselected package gstreamer0.10-plugins-ugly.
Unpacking gstreamer0.10-plugins-ugly (from .../gstreamer0.10-plugins-ugly_0.10.12-1_i386.deb) ...
Setting up liba52-0.7.4 (0.7.4-11ubuntu1) ...

Setting up libdvdread4 (4.1.3-5ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libdvdread4 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libid3tag0 (0.15.1b-10build1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libid3tag0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libmad0 (0.15.1b-4) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libmad0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libmpeg2-4 (0.4.1-3) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libmpeg2-4 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libsidplay1 (1.36.59-5) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libsidplay1 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of gstreamer0.10-plugins-ugly:
 gstreamer0.10-plugins-ugly depends on libdvdread4 (>= 4.1.3); however:
  Package libdvdread4 is not configured yet.
 gstreamer0.10-plugins-ugly depends on libid3tag0 (>= 0.15.1b); however:
  Package libid3tag0 is not configured yet.
 gstreamer0.10-plugins-ugly depends on libmad0 (>= 0.15.1b-3); however:
  Package libmad0 is not configured yet.
 gstreamer0.10-plugins-ugly depends on libmpeg2-4; however:
  Package libmpeg2-4 is not configured yet.
 gstreNo apport report written because MaxReports is reached already
                                                                    No apport report written because MaxReports is reached already
                                                  No apport report written because MaxReports is reached already
                                amer0.10-plugins-ugly depends on libsidplay1; however:
  Package libsidplay1 is not configured yet.
dpkg: error processing gstreamer0.10-plugins-ugly (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
/sbin/ldconfig.real: File /usr/lib/libsidplay.so.1 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libid3tag.so.0.3.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmpeg2convert.so.0.0.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libsidplay.so.1.0.3 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmad.so.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libid3tag.so.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmad.so.0.2.1 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libdvdread.so.4.1.3 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmpeg2convert.so.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmpeg2.so.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmpeg2.so.0.0.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libdvdread.so.4 is empty, not checked.
Errors were encountered while processing:
 libdvdread4
 libid3tag0
 libmad0
 libmpeg2-4
 libsidplay1
 gstreamer0.10-plugins-ugly
E: Sub-process /usr/bin/dpkg returned an error code (1)
tony@tony-laptop:~$ 

```

I've now got a Crash Report symbol on my top panel (next to the battery) - did I do something wrong?

Thanks in advance for your help (again),
Tony

---

### Post by Tony.B on 2010-03-14
Hi Durand
> **durand said:**
> The easiest way to remove the kernel and keep ubuntu tidier is to just use Computer Janitor, which is here: System > Administration > Computer Janitor
Thanks for that idea, but it was one of the first things I tried before I started this thread.  I thought (wrongly) that I could tidy things up without asking for help.
It may be that my meddling has only made matters worse.
Regards,
Tony

---

### Post by audiomick on 2010-03-14
Hi.
I haven't read through your last long post, my girlfriend is waiting for me to organise dinner....

A word to the wise about the Janitor: I don't know what the situation with it is now, but about a month to 6 weeks ago I was regularly seeing reports of it wanting to do things that shouldn't be done, like removing packages that are needed for the system to run. The advice was to always look very carefully at what it wanted to do, and if in any doubt, cancel out of it.

---

### Post by Tony.B on 2010-03-14
[Hi Michael
> **audiomick said:**
> Hi.
I haven't read through your last long post, my girlfriend is waiting for me to organise dinner....

A word to the wise about the Janitor: I don't know what the situation with it is now, but about a month to 6 weeks ago I was regularly seeing reports of it wanting to do things that shouldn't be done, like removing packages that are needed for the system to run. The advice was to always look very carefully at what it wanted to do, and if in any doubt, cancel out of it.


That sounds like excellent advice. Thanks for raising it.

Good luck with the cooking.

Cheers,
Tony

---

### Post by carandraug on 2010-03-14
Hmmm... those packages seem to be a problem. Could you paste here the output of the following commands? They won't do anything, Just check the system and report back the state of things and packages so we can see what to do next

```
dpkg --audit
dpkg --yet-to-unpack
dpkg --status gstreamer0.10-plugins-ugly
dpkg --status liba52-0.7.4
dpkg --status libdvdread4
dpkg --status libid3tag0
dpkg --status libmad0
dpkg --status libmpeg2-4
dpkg --status libsidplay1
```

---

### Post by audiomick on 2010-03-14
This one
```
Preparing to replace liba52-0.7.4 0.7.4-11ubuntu1 (using .../[COLOR="Red"]liba52-0.7.4_0.7.4-11ubuntu1_i386.deb)[/COLOR] ...
Unpacking replacement liba52-0.7.4 ...
dpkg (subprocess): unable to execute old post-removal script: Exec format error
dpkg: warning: old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
dpkg: ... [COLOR="Red"]it looks like that went OK.[/COLOR]
Selecting previously deselected package gstreamer0.10-plugins-ugly.
Unpacking gstreamer0.10-plugins-ugly (from .../gstreamer0.10-plugins-ugly_0.10.12-1_i386.deb) ...
Setting up liba52-0.7.4 (0.7.4-11ubuntu1) ...
```
is the only one that looks like it even came close...
Blowed if I know what's going on.
I'll be interested to see that output too.

---

### Post by Tony.B on 2010-03-15
Thanks again for your help.
Here's the info you requested:
```
tony@tony-laptop:~$ dpkg --audit
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 gstreamer0.10-plugins-ugly GStreamer plugins from the "ugly" set

The following packages are only half configured, probably due to problems
configuring them the first time. The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 libdvdread4          library for reading DVDs
 libsidplay1          SID (MOS 6581) emulation library
 libmpeg2-4           MPEG1 and MPEG2 video decoder library
 libmad0              MPEG audio decoder library
 libid3tag0           ID3 tag reading library from the MAD project

tony@tony-laptop:~$ dpkg --yet-to-unpack
tony@tony-laptop:~$ dpkg --status gstreamer0.10-plugins-ugly
Package: gstreamer0.10-plugins-ugly
Status: install ok unpacked
Priority: optional
Section: libs
Installed-Size: 1160
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: gst-plugins-ugly0.10
Version: 0.10.12-1
Replaces: gstreamer0.10-plugins-bad (<< 0.10.10.2), gstreamer0.10-plugins-good (<< 0.10.9.2)
Depends: liba52-0.7.4, libc6 (>= 2.4), libcdio7, libdvdread4 (>= 4.1.3), libgcc1 (>= 1:4.1.1), libglib2.0-0 (>= 2.16.0), libgstreamer-plugins-base0.10-0 (>= 0.10.23), libgstreamer0.10-0 (>= 0.10.23), libid3tag0 (>= 0.15.1b), libmad0 (>= 0.15.1b-3), libmpeg2-4, liboil0.3 (>= 0.3.8), libsidplay1, libstdc++6 (>= 4.1.1), libtwolame0
Conflicts: gstreamer0.10-plugins-bad (<< 0.10.5.2)
Description: GStreamer plugins from the "ugly" set
 GStreamer is a streaming media framework, based on graphs of filters
 which operate on media data.  Applications using this library can do
 anything from real-time sound processing to playing videos, and just
 about anything else media-related.  Its plugin-based architecture means
 that new data types or processing capabilities can be added simply by
 installing new plug-ins.
 .
 This packages contains plugins from the "ugly" set, a set of
 good-quality plug-ins that might pose distribution problems.
Original-Maintainer: Maintainers of GStreamer packages <pkg-gstreamer-maintainers@lists.alioth.debian.org>
Gstreamer-Decoders: application/vnd.rn-realmedia; application/x-pn-realaudio; application/x-rdt, media=(string)application, encoding-name=(string)X-REAL-RDT; application/x-rtp, media=(string){ application, video, audio }, encoding-name=(string)X-ASF-PF; audio/ac3; audio/mpeg, mpegversion=(int)1, layer=(int)[ 1, 3 ]; audio/mpeg, mpegversion=(int)1, parsed=(boolean)false; audio/x-ac3; audio/x-lpcm; audio/x-private1-ac3; audio/x-private1-lpcm; audio/x-sid; video/mpeg, mpegversion=(int)[ 1, 2 ], systemstream=(boolean)false; video/mpeg, mpegversion=(int){ 1, 2 }, systemstream=(boolean)true; video/x-ms-asf
Gstreamer-Elements: a52dec, ac3iec958, asfdemux, cdiocddasrc, dvddemux, dvdlpcmdec, dvdreadsrc, dvdsubdec, dvdsubparse, mad, mp3parse, mpeg2dec, mpegdemux, mpegparse, pnmsrc, rademux, rdtdepay, rdtmanager, rmdemux, rtpasfdepay, rtspreal, rtspwms, siddec, twolame, xingmux
Gstreamer-Encoders: audio/mpeg, mpegversion=(int)1, layer=(int)2; audio/x-iec958; audio/x-raw-int, endianness=(int)4321, signed=(boolean)true
Gstreamer-Uri-Sources: cdda, dvd, pnm
Gstreamer-Version: 0.10
tony@tony-laptop:~$ dpkg --status liba52-0.7.4
Package: liba52-0.7.4
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 108
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Source: a52dec
Version: 0.7.4-11ubuntu1
Depends: libc6 (>= 2.7-1)
Description: library for decoding ATSC A/52 streams
 liba52 is a free library for decoding ATSC A/52 streams. The A/52 standard is
 used in a variety of applications, including digital television and DVD. It is
 also known as AC-3.
 .
  Homepage: <http://liba52.sourceforge.net/>
Original-Maintainer: Debian multimedia packages maintainers <pkg-multimedia-maintainers@lists.alioth.debian.org>
tony@tony-laptop:~$ dpkg --status libdvdread4
Package: libdvdread4
Status: install ok half-configured
Priority: optional
Section: libs
Installed-Size: 212
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Source: libdvdread
Version: 4.1.3-5ubuntu2
Depends: libc6 (>= 2.4)
Recommends: libdvdnav4
Suggests: libdvdcss2, wget, debhelper, fakeroot, build-essential
Description: library for reading DVDs
 libdvdread provides the functionality that is required to access many DVDs. It
 parses IFO files, reads NAV-blocks, and performs CSS authentication and
 descrambling.
 .
 libdvdread currently uses libdl to dynamically probe for libdvdcss at runtime.
 If found, libdvdcss will be used to decrypt sections of the DVD as necessary.
Original-Maintainer: Daniel Baumann <daniel@debian.org>
tony@tony-laptop:~$ dpkg --status libid3tag0
Package: libid3tag0
Status: install ok half-configured
Priority: optional
Section: libs
Installed-Size: 128
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: libid3tag
Version: 0.15.1b-10build1
Depends: libc6 (>= 2.4), zlib1g (>= 1:1.1.4)
Description: ID3 tag reading library from the MAD project
 ID3 tag manipulation library with full support for reading ID3v1, ID3v1.1,
 ID3v2.2, ID3v2.3, and ID3v2.4 tags, as well as support for writing ID3v1,
 ID3v1.1, and ID3v2.4 tags.
Original-Maintainer: Mad Maintainers <pkg-mad-maintainers@lists.alioth.debian.org>
tony@tony-laptop:~$ dpkg --status libmad0
Package: libmad0
Status: install ok half-configured
Priority: optional
Section: libs
Installed-Size: 156
Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Source: libmad
Version: 0.15.1b-4
Depends: libc6 (>= 2.4)
Description: MPEG audio decoder library
 MAD is an MPEG audio decoder. It currently only supports the MPEG 1
 standard, but fully implements all three audio layers (Layer I, Layer II,
 and Layer III, the latter often colloquially known as MP3.)
 .
 MAD has the following special features:
   - 100% fixed-point (integer) computation
   - completely new implementation based on the ISO/IEC 11172-3 standard
   - distributed under the terms of the GNU General Public License (GPL)
Original-Maintainer: Mad Maintainers <pkg-mad-maintainers@lists.alioth.debian.org>
tony@tony-laptop:~$ dpkg --status libmpeg2-4
Package: libmpeg2-4
Status: install ok half-configured
Priority: optional
Section: libs
Installed-Size: 184
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Source: mpeg2dec
Version: 0.4.1-3
Depends: libc6 (>= 2.4)
Description: MPEG1 and MPEG2 video decoder library
 libmpeg2 is a library which can decode MPEG1 and MPEG2 video streams.
 .
 The main features in libmpeg2 are:
 .
  * Conformance - libmpeg2 is able to decode all mpeg streams that conform to
    certain restrictions. For streams that follow these restrictions, libmpeg2
    is probably 100% conformant to the mpeg standards - and there's a pretty
    extensive test suite to check this.
 .
  * Speed - there has been huge efforts there, and libmpeg2 is probably the
    fastest library around for what it does.
 .
  * Portability - most of the code is written in C, and when platform-specific
    optimizations are used, there always is a generic C routine to fall back
    on.  This should be portable to all architectures - at least we have heard
    reports from people running this code on x86, ppc, sparc, arm and sh4.
 .
  * Reuseability - libmpeg2 is not intended to include any project-specific
    code, but it should still include enough features to be used by very
    diverse projects.
 .
 This package contains the libmpeg2 shared libraries.
 .
 http://libmpeg2.sourceforge.net/
Original-Maintainer: Loic Minier <lool@dooz.org>
Homepage: http://libmpeg2.sourceforge.net/
tony@tony-laptop:~$ dpkg --status libsidplay1
Package: libsidplay1
Status: install ok half-configured
Priority: extra
Section: libs
Installed-Size: 276
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Source: libsidplay
Version: 1.36.59-5
Replaces: libsidplay1-c102 (<= 1.36.59-2), libsidplay1.36
Depends: libc6 (>= 2.4), libgcc1 (>= 1:4.1.1-21), libstdc++6 (>= 4.2.1-4)
Suggests: sidplay-base, xsidplay
Conflicts: libsidplay1-c102 (<= 1.36.59-2), libsidplay1.36, sidplay (<= 1.36.36)
Description: SID (MOS 6581) emulation library
 This is a (shared) library that implements the emulation of the C64's
 SID chip (MOS 6581) and CPU (6510). It is used by several "player"
 applications, e.g. sidplay, which make it possible to listen to *really*
 a lot (13.600+) of tunes, known from old and new C64 programs (as well
 as Amiga compositions).
 Find most of the available musics from your favourite games or demos
 and more in the High Voltage SID Collection (HVSC). For downloads and
 information about the volunteers, who maintain the collection, look at
 the HVSC homepage http://www.hvsc.c64.org.
Original-Maintainer: Laszlo Boszormenyi (GCS) <gcs@debian.hu>
tony@tony-laptop:~$ 


```
I hope this makes more sense to you than it does to me.

Regards,
Tony

---

### Post by carandraug on 2010-03-15
> **Tony.B said:**
> I hope this makes more sense to you than it does to me.

Yes, it does make sense and soon it will also make sense to you. Consider the following. When you install something, it's not a one step thing (as I explained before).
[LIST=1]
[*]the package is donwloaded
[*]the package is unpacked. Here you need to understand that a package is exactly that. One file (package) that has several files inside them. These files will have to be placed on the right places for the program to work
[*]the package is configured. Inside the package also comes a script (think of this as a small program), that places the files on the correct place and configures stuff for you such as setting the best options considering your system
[*]after all this, the system considers the package as installed
[/LIST]

The commands I asked you to run checked where in these steps the packages got stuck. The first one (dpkg --audit)
[QUOTE=man dpkg]Searches  for packages that have been installed only partially on your system. dpkg will suggest what to do with them to get them working.[/QUOTE]
The second one (dpkg --yet-to-unpack)
[QUOTE=man dpkg]Searches for packages selected for installation, but which for some reason still haven't been installed.[/QUOTE]
The other ones (dpkg --status PACKAGE_NAME) reports the specific status of each package (the ones that were giving problems before) plus a bunch of other information such as it's dependencies and descriptions.

The information from each command sort of overlaps but I'd rather get all the information at once that have to ask you again to run some other command and have to wait for the answer. All that said,try to read this output and make some sense of it.

```

[COLOR="Blue"]tony@tony-laptop:~$ dpkg --audit[/COLOR]
[COLOR="Red"]The following packages have been unpacked but not yet configured.
[/COLOR]They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 gstreamer0.10-plugins-ugly GStreamer plugins from the "ugly" set
[COLOR="Red"]
The following packages are only half configured, probably due to problems
configuring them the first time.[/COLOR] The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 libdvdread4          library for reading DVDs
 libsidplay1          SID (MOS 6581) emulation library
 libmpeg2-4           MPEG1 and MPEG2 video decoder library
 libmad0              MPEG audio decoder library
 libid3tag0           ID3 tag reading library from the MAD project

[COLOR="Blue"]tony@tony-laptop:~$ dpkg --yet-to-unpack[/COLOR]

[COLOR="Blue"]tony@tony-laptop:~$ dpkg --status gstreamer0.10-plugins-ugly[/COLOR]
Package: gstreamer0.10-plugins-ugly
Status: install ok unpacked

[COLOR="Blue"]tony@tony-laptop:~$ dpkg --status liba52-0.7.4[/COLOR]
Package: liba52-0.7.4
Status: install ok installed

[COLOR="Blue"]tony@tony-laptop:~$ dpkg --status libdvdread4[/COLOR]
Package: libdvdread4
Status: install ok half-configured

[COLOR="Blue"]tony@tony-laptop:~$ dpkg --status libid3tag0[/COLOR]
Package: libid3tag0
Status: install ok half-configured

[COLOR="Blue"]tony@tony-laptop:~$ dpkg --status libmad0[/COLOR]
Package: libmad0
Status: install ok half-configured

[COLOR="Blue"]tony@tony-laptop:~$ dpkg --status libmpeg2-4[/COLOR]
Package: libmpeg2-4
Status: install ok half-configured

[COLOR="Blue"]tony@tony-laptop:~$ dpkg --status libsidplay1[/COLOR]
Package: libsidplay1
Status: install ok half-configured

```

I hope it was clear to you. If not, here's what it seems to me that is going on. You have a bunch of offending packages. Their names are
[LIST]
[*]gstreamer0.10-plugins-ugly
[*]libdvdread4
[*]libsidplay1
[*]libmpeg2-4
[*]libmad0
[*]libid3tag0
[/LIST]
The first one was unpacked but never got to the step of being configured. All the other ones were unpacked, their configuration process started but it never finished. The reason that the first one (gstreamer) never got to start its configuration is that it has the other 5 as dependencies. Since their dependencies were not configured (and therefore not installed) gstreamer configuration can't start.

Among the configuration step, it's the creation of instructions on how to remove the package. Because the configuration was never done, these instructions were not created and it failed when we tried to solve it be removing the packages. At least that's my understanding of the situation but I may be wrong.

The --yet-to-unpack command returned nothing which means that there's no downloaded package that got stuck on that step. And one of the packages that you checked the status had everything ok with it (**Package:** liba52-0.7.4 **Status:** install ok installed).

What dpkg --audit recommended to do was to run the configuration of those packages again. You already done it before when upgrading the package dpkg. Here's the commands to do it again (there's a reason configuration of gstreamer is the last command and you should be able to know why by now;))
```

sudo dpkg --configure libdvdread4
sudo dpkg --configure libid3tag0
sudo dpkg --configure libmad0
sudo dpkg --configure libmpeg2-4
sudo dpkg --configure libsidplay1
sudo dpkg --configure gstreamer0.10-plugins-ugly
```

Hopefully this will solve it and the following commands should return no errors.

```
sudo apt-get update
sudo apt-get upgrade

```
By the way, how's the overheating problem? Is Ubuntu still shutting down unexpectedly every 25min or so?

---

### Post by audiomick on 2010-03-15
Hi Tony.
the Package issue has got to the point where I would be following a scientifically based "suck it and see" method. ;)
Having said that, what carandraug suggests is exactly what I would try in the light of the last lot of output you posted.

---

### Post by Tony.B on 2010-03-15
Hello carandraug.  Thank you for your comments

> **carandraug said:**
> ...there's a reason configuration of gstreamer is the last command and you should be able to know why by now;)
I'm not sure I do know, but if gstreamer is dependent on the others, it would make sense to sort out the others first.

Here is the output from the commands you suggested:
```
tony@tony-laptop:~$ sudo dpkg --configure libdvdread4
[sudo] password for tony: 
Setting up libdvdread4 (4.1.3-5ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libdvdread4 (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 libdvdread4
tony@tony-laptop:~$ sudo dpkg --configure libid3tag0
Setting up libid3tag0 (0.15.1b-10build1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libid3tag0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 libid3tag0
tony@tony-laptop:~$ sudo dpkg --configure libmad0
Setting up libmad0 (0.15.1b-4) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libmad0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 libmad0
tony@tony-laptop:~$ sudo dpkg --configure libmpeg2-4
Setting up libmpeg2-4 (0.4.1-3) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libmpeg2-4 (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 libmpeg2-4
tony@tony-laptop:~$ sudo dpkg --configure libsidplay1
Setting up libsidplay1 (1.36.59-5) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libsidplay1 (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 libsidplay1
tony@tony-laptop:~$ sudo dpkg --configure gstreamer0.10-plugins-ugly
dpkg: dependency problems prevent configuration of gstreamer0.10-plugins-ugly:
 gstreamer0.10-plugins-ugly depends on libdvdread4 (>= 4.1.3); however:
  Package libdvdread4 is not configured yet.
 gstreamer0.10-plugins-ugly depends on libid3tag0 (>= 0.15.1b); however:
  Package libid3tag0 is not configured yet.
 gstreamer0.10-plugins-ugly depends on libmad0 (>= 0.15.1b-3); however:
  Package libmad0 is not configured yet.
 gstreamer0.10-plugins-ugly depends on libmpeg2-4; however:
  Package libmpeg2-4 is not configured yet.
 gstreamer0.10-plugins-ugly depends on libsidplay1; however:
  Package libsidplay1 is not configured yet.
dpkg: error processing gstreamer0.10-plugins-ugly (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gstreamer0.10-plugins-ugly
tony@tony-laptop:~$ sudo apt-get update
Hit http://security.ubuntu.com karmic-security Release.gpg
Hit http://archive.canonical.com karmic Release.gpg                            
Get: 1 http://dl.google.com stable Release.gpg [189B]                          
Ign http://dl.google.com stable/main Translation-en_GB                         
Ign http://security.ubuntu.com karmic-security/main Translation-en_GB          
Ign http://archive.canonical.com karmic/partner Translation-en_GB    
Hit http://archive.canonical.com karmic Release                      
Hit http://archive.canonical.com karmic/partner Packages                       
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_GB
Get: 2 http://dl.google.com stable Release [2,540B]                  
Hit http://gb.archive.ubuntu.com karmic Release.gpg                   
Get: 3 http://gb.archive.ubuntu.com karmic/main Translation-en_GB [63.7kB]
Ign http://security.ubuntu.com karmic-security/universe Translation-en_GB      
Get: 4 http://dl.google.com stable/main Packages [922B]                        
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_GB    
Hit http://security.ubuntu.com karmic-security Release          
Hit http://security.ubuntu.com karmic-security/main Packages    
Get: 5 http://gb.archive.ubuntu.com karmic/restricted Translation-en_GB [3,402B]
Get: 6 http://gb.archive.ubuntu.com karmic/universe Translation-en_GB [33.2kB] 
Hit http://security.ubuntu.com karmic-security/restricted Packages
Hit http://security.ubuntu.com karmic-security/main Sources     
Hit http://security.ubuntu.com karmic-security/restricted Sources
Hit http://security.ubuntu.com karmic-security/universe Packages
Hit http://security.ubuntu.com karmic-security/universe Sources 
Hit http://security.ubuntu.com karmic-security/multiverse Packages
Hit http://security.ubuntu.com karmic-security/multiverse Sources
Get: 7 http://gb.archive.ubuntu.com karmic/multiverse Translation-en_GB [43.8kB]
Hit http://gb.archive.ubuntu.com karmic-updates Release.gpg                    
Ign http://gb.archive.ubuntu.com karmic-updates/main Translation-en_GB         
Ign http://gb.archive.ubuntu.com karmic-updates/restricted Translation-en_GB   
Ign http://gb.archive.ubuntu.com karmic-updates/universe Translation-en_GB     
Ign http://gb.archive.ubuntu.com karmic-updates/multiverse Translation-en_GB   
Hit http://gb.archive.ubuntu.com karmic Release                                
Hit http://gb.archive.ubuntu.com karmic-updates Release                        
Hit http://gb.archive.ubuntu.com karmic/main Packages                          
Hit http://gb.archive.ubuntu.com karmic/restricted Packages                    
Hit http://gb.archive.ubuntu.com karmic/main Sources                           
Hit http://gb.archive.ubuntu.com karmic/restricted Sources                     
Hit http://gb.archive.ubuntu.com karmic/universe Packages                      
Hit http://gb.archive.ubuntu.com karmic/universe Sources                       
Hit http://gb.archive.ubuntu.com karmic/multiverse Packages                    
Hit http://gb.archive.ubuntu.com karmic/multiverse Sources                     
Hit http://gb.archive.ubuntu.com karmic-updates/main Packages                  
Hit http://gb.archive.ubuntu.com karmic-updates/restricted Packages            
Hit http://gb.archive.ubuntu.com karmic-updates/main Sources                   
Hit http://gb.archive.ubuntu.com karmic-updates/restricted Sources             
Hit http://gb.archive.ubuntu.com karmic-updates/universe Packages              
Hit http://gb.archive.ubuntu.com karmic-updates/universe Sources               
Hit http://gb.archive.ubuntu.com karmic-updates/multiverse Packages            
Hit http://gb.archive.ubuntu.com karmic-updates/multiverse Sources             
Fetched 148kB in 13s (10.8kB/s)                                                
Reading package lists... Done
tony@tony-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up libdvdread4 (4.1.3-5ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libdvdread4 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libid3tag0 (0.15.1b-10build1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libid3tag0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libmad0 (0.15.1b-4) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libmad0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libmpeg2-4 (0.4.1-3) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libmpeg2-4 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libsidplay1 (1.36.59-5) ...
No apport report written because MaxReports is reached already
                                                              dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libsidplay1 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of gstreamer0.10-plugins-ugly:
 gstreamer0.10-plugins-ugly depends on libdvdread4 (>= 4.1.3); however:
  Package libdvdread4 is not configured yet.
 gstreamer0.10-plugins-ugly depends on libid3tag0 (>= 0.15.1b); however:
  Package libid3tag0 is not configured yet.
 gstreamer0.10-plugins-ugly depends on libmad0 (>= 0.15.1b-3); however:
  Package libmad0 is not configured yet.
 gstreamer0.10-plugins-ugly depends on libmpeg2-4; however:
  Package libmpeg2-4 is not configured yet.
 gstreamer0.10-plugins-ugly depends on libsidplay1; however:
  Package libsidplay1 is not configured yet.
dpkg: error processing gstreamer0.10-plugins-ugly (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            Errors were encountered while processing:
 libdvdread4
 libid3tag0
 libmad0
 libmpeg2-4
 libsidplay1
 gstreamer0.10-plugins-ugly
E: Sub-process /usr/bin/dpkg returned an error code (1)
tony@tony-laptop:~$
```

Does this help?

> **carandraug said:**
> By the way, how's the overheating problem? Is Ubuntu still shutting down unexpectedly every 25min or so?
I'm not positively sure it is overheating, but other people on other threads have suggested that it may be, and my laptop certainly feels a bit warmer when it happens.  But, whatever the reason, it shuts down soon after I switch on. When I restart, everything is ok and it will run all day without problems.

Thank you so much for taking the time and trouble to investigate this for me.

Tony

---

### Post by audiomick on 2010-03-15
Hi Tony.
So you are still getting stuck on the same packages. I am beginning to wonder if something is missing that the "post installation script" needs to run, but that is really a wild guess. See what carandaug says about it...

> But, whatever the reason, it shuts down soon after I switch on. When I  restart, everything is ok and it will run all day without problems.
So if I understand this right, sometimes it runs ok and sometimes it shuts down without warning?

---

### Post by Tony.B on 2010-03-15
Hi Michael

> **audiomick said:**
> So if I understand this right, sometimes it runs ok and sometimes it shuts down without warning?
Not quite right.  The shutting-down-without-warning only occurs soon after I've switched my laptop on, usually about 20-30 mins after starting up.

After it's switched itself off, I can restart it and it will run all day with no problems.

Having said that, whatever I did this morning (with those instructions I got from carandraug) may have accidentally sorted it.  This afternoon I've been running from a "cold" start for well over an hour and I haven't even had a hiccup.

Admittedly, weatherwise it's a little cooler today and there's much less humidity, but I wouldn't have thought that would affect things too much.

Let's hope it's fixed.

Cheers,
Tony

---

### Post by Tony.B on 2010-03-15
I spoke too soon (or typed too loudly).

My laptop cut out immediately after making that last post.

It is NOT fixed.

---

### Post by theozzlives on 2010-03-15
> **Tony.B said:**
> Thanks, everyone for the fast responses. So it would appear I had too many KERNELS, whatever they are.

The Kernel simply put is what makes Linux Linux. It makes it go. Windows and MAC OS also have kernels.

---

### Post by carandraug on 2010-03-15
> **Tony.B said:**
> I'm not sure I do know, but if gstreamer is dependent on the others, it would make sense to sort out the others first.

Yes, that's the reason.

Well, your problem seems to start rubbing the limits of my knowledge. The last thing I can think of, is to redownload, unpack and configure it manually from the start. Seems like something was missing from the package or maybe we deleted it when trying to fix it in some other way. Try the following commands. This will hopefully fix the problem for one of the packages. If it does work, we can do it for all the others (I will give you the code then).

```
sudo rm /var/lib/dpkg/info/libdvdread4.p*
sudo apt-get remove --purge libdvdread4
sudo apt-get clean
sudo aptitude download libdvdread4
sudo dpkg --unpack ./libdvdread4_4.1.3-5ubuntu2_i386.deb
sudo dpkg --configure libdvdread4
```

---

### Post by Tony.B on 2010-03-15
> **theozzlives said:**
> The Kernel simply put is what makes Linux Linux. It makes it go. Windows and MAC OS also have kernels.
Thanks, I think I'm getting the idea.

---

### Post by Tony.B on 2010-03-15
Hi carandraug.

Does this look better?

```
tony@tony-laptop:~$ sudo rm  var/lib/dpkg/info/libdvdread4.p*
tony@tony-laptop:~$ sudo apt-get remove --purge libdvdread4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  gstreamer0.10-plugins-ugly* libdvdread4*
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 1,405kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 140787 files and directories currently installed.)
Removing gstreamer0.10-plugins-ugly ...
Removing libdvdread4 ...
Setting up libid3tag0 (0.15.1b-10build1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libid3tag0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libmad0 (0.15.1b-4) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libmad0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libmpeg2-4 (0.4.1-3) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libmpeg2-4 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libsidplay1 (1.36.59-5) ...
E: Sub-process /usr/bin/dpkg returned an error code (1)
tony@tony-laptop:~$ sudo apt-get clean
tony@tony-laptop:~$ sudo aptitude download libdvdread4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Writing extended state information... Done
Get:1 http://gb.archive.ubuntu.com karmic/universe libdvdread4 4.1.3-5ubuntu2 [64.2kB]
Fetched 64.2kB in 2s (22.0kB/s)     
tony@tony-laptop:~$ sudo dpkg --unpack ./libdvdread4_4.1.3-5ubuntu2_i386.deb
Selecting previously deselected package libdvdread4.
(Reading database ... 140724 files and directories currently installed.)
Unpacking libdvdread4 (from .../libdvdread4_4.1.3-5ubuntu2_i386.deb) ...
tony@tony-laptop:~$ sudo dpkg --configure libdvdread4
Setting up libdvdread4 (4.1.3-5ubuntu2) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
/sbin/ldconfig.real: File /usr/lib/libsidplay.so.1 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libid3tag.so.0.3.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmpeg2convert.so.0.0.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libsidplay.so.1.0.3 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmad.so.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libid3tag.so.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmad.so.0.2.1 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmpeg2convert.so.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmpeg2.so.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmpeg2.so.0.0.0 is empty, not checked.
tony@tony-laptop:~$ 
```

Regards,
Tony

---

### Post by carandraug on 2010-03-15
Good morning,
> **Tony.B said:**
> Does this look better?
I'm not sure but I think it might be good despite all the errors. Could you please paste the output of

```
sudo dpkg --status libdvdread4
```

---

### Post by Tony.B on 2010-03-15
> **carandraug said:**
> Good morning,

I'm not sure but I think it might be good despite all the errors. Could you please paste the output of

```
sudo dpkg --status libdvdread4
```

It's evening here in sunny South Africa, but here's the output:
```
tony@tony-laptop:~$ sudo dpkg --status libdvdread4
Package: libdvdread4
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 212
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Architecture: i386
Source: libdvdread
Version: 4.1.3-5ubuntu2
Depends: libc6 (>= 2.4)
Recommends: libdvdnav4
Suggests: libdvdcss2, wget, debhelper, fakeroot, build-essential
Description: library for reading DVDs
 libdvdread provides the functionality that is required to access many DVDs. It
 parses IFO files, reads NAV-blocks, and performs CSS authentication and
 descrambling.
 .
 libdvdread currently uses libdl to dynamically probe for libdvdcss at runtime.
 If found, libdvdcss will be used to decrypt sections of the DVD as necessary.
Original-Maintainer: Daniel Baumann <daniel@debian.org>
tony@tony-laptop:~$
```

To my untrained eye, it looks lovely!

---

### Post by audiomick on 2010-03-15
I think the errors were because dpkg tried again to configure the other packages while it was at it, weren't they?

The thing that strikes me is this
```
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
/sbin/ldconfig.real: File /usr/lib/libsidplay.so.1 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libid3tag.so.0.3.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmpeg2convert.so.0.0.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libsidplay.so.1.0.3 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmad.so.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libid3tag.so.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmad.so.0.2.1 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmpeg2convert.so.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmpeg2.so.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmpeg2.so.0.0.0 is empty, not checked.
```makes me think that maybe 
libdvdread4
should have come last if it goes looking for the other ones to configure itself?

---

### Post by carandraug on 2010-03-15
> **Tony.B said:**
> To my untrained eye, it looks lovely!

Yes, those are great news. Here's the commands to hopefully fix the package mess.

```
sudo rm /var/lib/dpkg/info/libsidplay1.p*
sudo apt-get remove --purge libsidplay1
sudo apt-get clean
sudo aptitude download libsidplay1
sudo dpkg --unpack ./libsidplay1_1.36.59-5_i386.deb
sudo dpkg --configure libsidplay1

sudo rm /var/lib/dpkg/info/libmpeg2-4.p*
sudo apt-get remove --purge libmpeg2-4
sudo apt-get clean
sudo aptitude download libmpeg2-4
sudo dpkg --unpack ./libmpeg2-4_0.4.1-3_i386.deb
sudo dpkg --configure libmpeg2-4

sudo rm /var/lib/dpkg/info/libmad0.p*
sudo apt-get remove --purge libmad0
sudo apt-get clean
sudo aptitude download libmad0
sudo dpkg --unpack ./libmad0_0.15.1b-4_i386.deb
sudo dpkg --configure libmad0

sudo rm /var/lib/dpkg/info/libid3tag0.p*
sudo apt-get remove --purge libid3tag0
sudo apt-get clean
sudo aptitude download libid3tag0
sudo dpkg --unpack ./libid3tag0_0.15.1b-10build1_i386.deb
sudo dpkg --configure libid3tag0

sudo dpkg --configure gstreamer0.10-plugins-ugly
```

---

### Post by Tony.B on 2010-03-15
Sorry to take so long - had to fix & eat dinner.

Herewith output:
```
tony@tony-laptop:~$ sudo rm /var/lib/dpkg/info/libsidplay1.p*
[sudo] password for tony: 
tony@tony-laptop:~$ sudo apt-get remove --purge libsidplay1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  libsidplay1*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 283kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 140734 files and directories currently installed.)
Removing libsidplay1 ...
Setting up libid3tag0 (0.15.1b-10build1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libid3tag0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libmad0 (0.15.1b-4) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libmad0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libmpeg2-4 (0.4.1-3) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libmpeg2-4 (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 libid3tag0
 libmad0
 libmpeg2-4
E: Sub-process /usr/bin/dpkg returned an error code (1)
tony@tony-laptop:~$ sudo apt-get clean
tony@tony-laptop:~$ sudo aptitude download libsidplay1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Writing extended state information... Done
Get:1 http://gb.archive.ubuntu.com karmic/universe libsidplay1 1.36.59-5 [73.5kB]
Fetched 73.5kB in 3s (20.4kB/s)     
tony@tony-laptop:~$ sudo dpkg --unpack ./libsidplay1_1.36.59-5_i386.deb
Selecting previously deselected package libsidplay1.
(Reading database ... 140730 files and directories currently installed.)
Unpacking libsidplay1 (from .../libsidplay1_1.36.59-5_i386.deb) ...
tony@tony-laptop:~$ sudo dpkg --configure libsidplay1
Setting up libsidplay1 (1.36.59-5) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
/sbin/ldconfig.real: File /usr/lib/libid3tag.so.0.3.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmpeg2convert.so.0.0.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmad.so.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libid3tag.so.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmad.so.0.2.1 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmpeg2convert.so.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmpeg2.so.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmpeg2.so.0.0.0 is empty, not checked.
tony@tony-laptop:~$ sudo rm /var/lib/dpkg/info/libmpeg2-4.p*
tony@tony-laptop:~$ sudo apt-get remove --purge libmpeg2-4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  libmpeg2-4*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 188kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 140734 files and directories currently installed.)
Removing libmpeg2-4 ...
Setting up libid3tag0 (0.15.1b-10build1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libid3tag0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libmad0 (0.15.1b-4) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libmad0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 libid3tag0
 libmad0
E: Sub-process /usr/bin/dpkg returned an error code (1)
tony@tony-laptop:~$ sud apt-get clean
No command 'sud' found, did you mean:
 Command 'sed' from package 'sed' (main)
 Command 'sum' from package 'coreutils' (main)
 Command 'sup' from package 'sup' (universe)
 Command 'sux' from package 'sux' (universe)
 Command 'sbd' from package 'heartbeat' (universe)
 Command 'sdd' from package 'sdd' (universe)
 Command 'sudo' from package 'sudo' (main)
 Command 'sudo' from package 'sudo-ldap' (universe)
 Command 'sid' from package 'tendra' (universe)
 Command 'snd' from package 'snd-gtk' (universe)
 Command 'su' from package 'login' (main)
sud: command not found
tony@tony-laptop:~$ sudo apt-get clean
tony@tony-laptop:~$ sudo aptitude download libmpeg2-4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Writing extended state information... Done
Get:1 http://gb.archive.ubuntu.com karmic/universe libmpeg2-4 0.4.1-3 [55.9kB]
Fetched 55.9kB in 2s (22.3kB/s)    
tony@tony-laptop:~$ sudo dpkg --unpack ./libmpeg2-4_0.4.1-3_i386.deb
Selecting previously deselected package libmpeg2-4.
(Reading database ... 140725 files and directories currently installed.)
Unpacking libmpeg2-4 (from ./libmpeg2-4_0.4.1-3_i386.deb) ...
tony@tony-laptop:~$ sudo dpkg --configure libmpeg2-4
Setting up libmpeg2-4 (0.4.1-3) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
/sbin/ldconfig.real: File /usr/lib/libid3tag.so.0.3.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmad.so.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libid3tag.so.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libmad.so.0.2.1 is empty, not checked.
tony@tony-laptop:~$ sudo rm /var/lib/dpkg/info/libmad0.p*
tony@tony-laptop:~$ sudo apt-get remove --purge libmad0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  libmad0*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 160kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 140734 files and directories currently installed.)
Removing libmad0 ...
Setting up libid3tag0 (0.15.1b-10build1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libid3tag0 (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 libid3tag0
E: Sub-process /usr/bin/dpkg returned an error code (1)
tony@tony-laptop:~$ sudo apt-get clean
tony@tony-laptop:~$ sudo aptitude download libmad0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Writing extended state information... Done
Get:1 http://gb.archive.ubuntu.com karmic/main libmad0 0.15.1b-4 [74.5kB]
Fetched 74.5kB in 3s (23.1kB/s) 
tony@tony-laptop:~$ sudo dpkg --unpack ./libmad0_0.15.1b-4_i386.deb
Selecting previously deselected package libmad0.
(Reading database ... 140728 files and directories currently installed.)
Unpacking libmad0 (from ./libmad0_0.15.1b-4_i386.deb) ...
tony@tony-laptop:~$ sudo dpkg --configure libmad0
Setting up libmad0 (0.15.1b-4) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
/sbin/ldconfig.real: File /usr/lib/libid3tag.so.0.3.0 is empty, not checked.
/sbin/ldconfig.real: File /usr/lib/libid3tag.so.0 is empty, not checked.
tony@tony-laptop:~$ sudo rm /var/lib/dpkg/info/libid3tag0.p*
tony@tony-laptop:~$ sudo apt-get remove --purge libid3tag0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  libid3tag0*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 131kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 140734 files and directories currently installed.)
Removing libid3tag0 ...
tony@tony-laptop:~$ sudo apt-get clean
tony@tony-laptop:~$ sudo aptitude download libid3tag0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initialising package states... Done
Writing extended state information... Done
Get:1 http://gb.archive.ubuntu.com karmic/main libid3tag0 0.15.1b-10build1 [35.4kB]
Fetched 35.4kB in 2s (14.7kB/s)    
tony@tony-laptop:~$ sudo dpkg --unpack ./libid3tag0_0.15.1b-10build1_i386.deb
Selecting previously deselected package libid3tag0.
(Reading database ... 140728 files and directories currently installed.)
Unpacking libid3tag0 (from .../libid3tag0_0.15.1b-10build1_i386.deb) ...
tony@tony-laptop:~$ sudo dpkg --configure libid3tag0
Setting up libid3tag0 (0.15.1b-10build1) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
tony@tony-laptop:~$ sudo dpkg --configure gstreamer0.10-plugins-ugly
dpkg: error processing gstreamer0.10-plugins-ugly (--configure):
 no package named `gstreamer0.10-plugins-ugly' is installed, cannot configure
Errors were encountered while processing:
 gstreamer0.10-plugins-ugly
tony@tony-laptop:~$ 
```

I think the wheels fell off at the end.

---

### Post by carandraug on 2010-03-15
> **Tony.B said:**
> I think the wheels fell off at the end.

Seems good to me. Run these two and I think you'll be done

```
sudo apt-get install gstreamer0.10-plugins-ugly
sudo dpkg --audit
```

The last commands is just too check if everything is correct.

---

### Post by Tony.B on 2010-03-15
Oh. Is it going ok?

```
tony@tony-laptop:~$ sudo apt-get install gstreamer0.10-plugins-ugly
[sudo] password for tony: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  gstreamer0.10-plugins-ugly
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 335kB of archives.
After this operation, 1,188kB of additional disk space will be used.
Get: 1 http://gb.archive.ubuntu.com karmic/universe gstreamer0.10-plugins-ugly 0.10.12-1 [335kB]
Fetched 335kB in 8s (37.6kB/s)                                                 
Selecting previously deselected package gstreamer0.10-plugins-ugly.
(Reading database ... 140736 files and directories currently installed.)
Unpacking gstreamer0.10-plugins-ugly (from .../gstreamer0.10-plugins-ugly_0.10.12-1_i386.deb) ...
Setting up gstreamer0.10-plugins-ugly (0.10.12-1) ...
tony@tony-laptop:~$ sudo dpkg --audit
tony@tony-laptop:~$ 
```

---

### Post by Tony.B on 2010-03-15
Is that good?
Is it all working as it should do?

---

### Post by carandraug on 2010-03-15
> **Tony.B said:**
> Oh. Is it going ok?

Yes it is. The reason why "the wheels fell off at the end" the previous time was that my last command was not thr most appropriate. Considering the output of the last commands, you problem (at least the one with installing stuff is solved). Hope you understood all you've done and learned a bit more about how the system works. The last command this time (--audit) returned nothing so all problematic packages were solved.

You should be able to install the temperature sensors now. To do that run

```
sudo apt-get install sensors-applet
```
This command should ask you once if you're sure you want to install. Say yes. Then it will ask you if you want it to boot at start-up. Choose no. Once it finishs installing, right click on one of the panels and choose "Add to Panel...". Somewhere on the list should now be a "Hardware Sensors Monitor". Either double click on it or click on it once and then press "Add". That should allow to check the temperature. If you right click on the new icon you can add other info to the icon such as the speed of the fan.

---

### Post by Tony.B on 2010-03-15
Yes. It's all worked.
I've got two little thermometers on my top panel, both fluctuating between 45-50 deg C.  One is labelled CPU, and the other says Temp1.
But if I right-click on either of them, all I get is a menu saying Preferences/Help/About/Remove from Panel/Move (blanked out)/Lock to Panel.
Still, not to worry, the main thing is that everything seems to be much improved.

Thank you so much, carandraug. And also thanks to audiomick for all his input.  You guys are S*T*A*R*S.

Best regards,
Tony

---

### Post by carandraug on 2010-03-15
> **Tony.B said:**
> Yes. It's all worked.
If it all worked you should mark this as solved. On the top of the thread there's a button that says "Thread tools". Click on a it a menu should appear. Then click on Mark this as solved (or something around those lines). This will add the prefix [solved] to the thread title.

> **Tony.B said:**
> I've got two little thermometers on my top panel, both fluctuating between 45-50 deg C.  One is labelled CPU, and the other says Temp1.
But if I right-click on either of them, all I get is a menu saying Preferences/Help/About/Remove from Panel/Move (blanked out)/Lock to Panel.
Click on preferences and you can change a bunch of stuff. You can have the temperature only with no icon for example, add temperatures of things other than the CPU or the speed of the fan. You'll want everything to be shown so you can keep an eye on them.

> **Tony.B said:**
> Thank you so much, carandraug.
You're welcome. Glad to be of any help.

---

### Post by audiomick on 2010-03-15
> **Tony.B said:**
> Yes. It's all worked.
I've got two little thermometers on my top panel, both fluctuating between 45-50 deg C.  One is labelled CPU, and the other says Temp1.

for reference: I  installed those a few days ago on mine. I don't get a CPU value (don't know why; I expected to...) and I see somewhere around 30°C for the two drives and about 56°C for the graphics card. Generally speaking (and drawing on experience from audio stuff like PA amps and digital mixing consoles) up to about 60°C is not a great drama, but above that (broadly speaking) one should start looking at manufacturer's specs to see what is ok and what not.

If your temps don't get much over that, and in the light of what you have posted about your crashes, I would be suspecting something other than overheating as the cause for the crash.

I am glad you got your packages sorted out. I would like to know what went wrong there, but I suspect that this will remain a mystery....;)

---

### Post by carandraug on 2010-03-15
> **audiomick said:**
> I would like to know what went wrong there, but I suspect that this will remain a mystery....;)

Probably system crash during their first installation (or attempt of installation). Consider this comment about the patch for his bug
[QUOTE=Jean-Baptiste Lallement on dpkg bug #512096]Here is a patch proposal which add some fsync on files and directories to prevent delayed allocation and the zero-length file problem after a system crash.[/QUOTE]

---

### Post by audiomick on 2010-03-15
> **carandraug said:**
> Probably system crash during their first installation (or attempt of installation). Consider this comment about the patch for his bug
Yes, that is probably the most likely, I suppose.

---

### Post by Tony.B on 2010-03-17
I have just used the Update Manager and everything installed without the system crashing.  Thank you again for all the help.

---

### Post by sixthwheel on 2010-03-17
You guys totally ROCK!!!!
No, I did not have the same problem as Tony, but it was fascinating to read how all of you got together and fixed the problem, with so much patience, and understanding.

Hopefully one day I'll be able to help others , but for now  I'm a nOOb like Tony, and will just keep reading and learning.

This is one of the reasons I'm going to stick with Linux (Ubuntu) no matter the problems.
I could never find this kind of help on a Windows forum.

---

### Post by Tony.B on 2010-03-17
Well said, sixthwheel.

My sentiments exactly.

---

### Post by sublimation on 2010-03-17
> **Tony.B said:**
> I have just used the Update Manager and everything installed without the system crashing.  Thank you again for all the help.

huzah! Now wait a couple days for the next update to push through, and cross your fingers. Let's hope everything stays clean and clear.

---

### Post by Tony.B on 2010-03-22
> **sublimation said:**
> huzah! Now wait a couple days for the next update to push through, and cross your fingers. Let's hope everything stays clean and clear.
And it all worked OK (of course!).  
My thanks are due to everyone who helped me.

Cheers,
Tony

---

