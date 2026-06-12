---
title: "Server: Realtek Wireless USB receiver not working"
date: 2014-08-25
forum: Networking &amp; Wireless
---

### Post by matthew50 on 2014-08-25
Hello everybody,

I am trying to connect a server computer to the internet but the USB wireless receiver isn't working.  I know it needs a driver, and have the driver installation disk for linux.  However, the install.sh file opens in the windows equivalent of notepad (text editor).  

I was wondering if I'm doing something wrong (I'm new to ubuntu, if you couldn't tell) and if anybody else has had a similar problem.  I can't just simply connect the computer to the router with a LAN cable, it has to be wireless...I know that's not the best thing for a server, but that's the only option I have at the moment.

If anyone could point me in the right direction, or even tell me how to get .sh files to open (I already tried 'open with...Run Software' but even that wouldn't work), I'd be greatly appreciative.

Thanks!

Also, sorry if this thread is in the wrong place.

---

### Post by newb85 on 2014-08-25
Unfortunately, the default setting for executable files in Ubuntu was changed recently to automatically open in a text editor.  Fortunately, you can change that.

Open Nautlus (the file browser) by clicking the icon that looks like a file cabinet drawer near the upper-right corner.  Go to File>Preferences.  In the behavior tab, there's a section for Executable Text Files.  I think you get the drift from there.

*However*, for tasks that make changes to the system (such as installing drivers), you need to be superuser to execute, and by default you are not.  This is for good reason.  You could open a browser window as superuser from a terminal.  You open the terminal with Ctrl+Alt+T.  Then enter this and hit enter.

```
gksudo nautilus
```

The prefix *gksudo* is basically "superuser do" for graphical programs.  It's a good idea to only use a superuser browser for what you have to.

Alternatively, you can simply execute the file from a terminal as well.  

```
sudo path/to/executable.sh
```

Again, the prefix *sudo* is "superuser do".

---

### Post by matthew50 on 2014-08-25
Thanks for all your help.  I can now execute .sh files, however the .sh file seems to be trying to 'cd driver', which then returns the 'no such file or directory' error.

As I am running the latest version of ubuntu (14.04), gksu isn't installed, as the general consensus on the internet says "[COLOR=#333333][FONT=Ubuntu]Recent versions of some flavours might not have gksu installed." [SIZE=2] Unfortunately it seems I need an internet connection to install this feature.

Thanks once again for your help and I hope I will resolve this issue soon. :)
[/SIZE]
[/FONT][/COLOR]

---

### Post by newb85 on 2014-08-26
cd is the command for changing into a directory.  My guess is "driver" is a directory on the driver disc (probably contained in the same directory as the .sh file).  Before executing the .sh file, cd into the directory containing the "driver" directory.

---

### Post by varunendra on 2014-08-27
Welcome to the forums matthew50!

The installation discs supplied with wireless adapters almost always contain outdated driver versions that may not be compatible with the rapidly changing current kernel version. And most of the realtek chips are natively supported by Linux kernel, in which case, you shouldn't need an external driver at all.

Please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by QIII on 2014-08-27
*Moved to **Networking & Wireless***

---

### Post by matthew50 on 2014-08-27
Thanks for all the help everyone!  I managed to solve my issue.

I hope to be a regular contributor to the Ubuntu forums!

---

### Post by varunendra on 2014-08-27
Glad you got it sorted.

You can start contributing right now by -

1) Sharing with us how you solved the problem. Description, steps or the link to the guide/post you followed.
2) Mark this thread as [SOLVED] using "Thread Tools" link above the first post. You can follow the "see how" link in my signature below to see how it helps others. :)

---

