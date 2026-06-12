---
title: "Default monitor frequency"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by rrobey on 2009-01-28
I have struggled with a Ubuntu installation to the point of complete disgust. Installation goes without a hitch, everything is just fine until I re-boot. While it is loading, Ubuntu displays at 60 HZ for login, but once past that I can see nothing. My monitor needs to run at 60 Hz but Ubuntu has decided that 70 Hz is what it is going to do. 

I have read all sorts of posts and suggestions about monitor frequency. Each one describes some esoteric incantation needed to correct the problem. How exactly am I supposed to do this? I CAN'T SEE THE DESKTOP...AT ALL. EVER.

My monitor is a Viewsonic HD 30" widescreen that is about a year old, so I really am not interested in hearing that "your monitor is old and busted".

I have deleted the installation and re-installed WAY too many times with the same results every time. 

While Vista took a little getting used to, at least I could see something on my monitor. 

"It just works"? Don't think so. At least not for me...

Unless there is some sort of fix where I can lock in the monitor frequency during installation, I have wasted WAY too much time on something that has repeatedly disappointed me.

---

### Post by igknighted on 2009-01-28
> **rrobey said:**
> I have struggled with a Ubuntu installation to the point of complete disgust. Installation goes without a hitch, everything is just fine until I re-boot. While it is loading, Ubuntu displays at 60 HZ for login, but once past that I can see nothing. My monitor needs to run at 60 Hz but Ubuntu has decided that 70 Hz is what it is going to do. 

I have read all sorts of posts and suggestions about monitor frequency. Each one describes some esoteric incantation needed to correct the problem. How exactly am I supposed to do this? I CAN'T SEE THE DESKTOP...AT ALL. EVER.

My monitor is a Viewsonic HD 30" widescreen that is about a year old, so I really am not interested in hearing that "your monitor is old and busted".

I have deleted the installation and re-installed WAY too many times with the same results every time. 

While Vista took a little getting used to, at least I could see something on my monitor. 

"It just works"? Don't think so. At least not for me...

Unless there is some sort of fix where I can lock in the monitor frequency during installation, I have wasted WAY too much time on something that has repeatedly disappointed me.

1) Take a deep breath and chill for a bit.  In the end, it's just a computer, it's not worth getting upset about.

2) You will probably have to do some manual editing from the CLI.  If you let it boot up (and the screen turn black when it goes out of range), try hitting ctrl+alt+f1 to switch back to a text-only terminal.  Now you can enter some of the commands you see.

3) You are attempting to install a new and unfamiliar OS from scratch (even a windows install from scratch is a nightmare, thats why OEMs ship customized disks with all needed drivers).  To think it would "just work" would be neive.  It's a process, and a learning experience, and usually plenty of work.  But there's millions worldwide who found it well worth it.

EDIT: I don't know a thing about how to manually set your refresh rate in the latest Ubuntu (8.10) due to some recent changes, Just trying to get you back on the right track here.

---

### Post by robert shearer on 2009-01-28
>  While it is loading, Ubuntu displays at 60 HZ for login, but once past that I can see nothing. 

This info is helpful.Thank you.

Now, assuming you are installing Ubuntu only and have no other o/s on this compy?

As soon as the compy completes its POST, and **before** the log in screen comes, up hit the 'Esc" key on your keyboard repeatedly.

This should bring up the grub menu (at a default 60hz so you should see it)
There will be some options here that you can try such as "fix x" or 'Recovery mode'.

scroll down to these and select one by pressing enter.

From memory fix x will try to reconfigure your video configuration, otherwise recovery mode will give you a text based command line system that we can use to configure the video settings.

Try those and post back. (be patient as we all have to sleep sometime and you may get several replys/helpers)

If you have a dual boot with another o/s then you should be seeing the grub screen anyway.

A couple more questions,
What is the video card make and model in your comp and are you using anything between the comp and the monitor?  like a kvm switch ?

Assuming too that you are installing from the live cd? and are able to load that and get a desktop while it is running and before you install.(Post if otherwise.)

If so then this is good as it shows that the monitor will work and we only need to use the same settings that the live cd uses and write those into the installed systems configuration file:D

---

