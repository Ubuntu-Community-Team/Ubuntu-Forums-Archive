---
title: "Display crashing down"
date: 2010-07-01
forum: New to Ubuntu
---

### Post by aprilland on 2010-07-01
Hi! I'm afraid I have got a disaster with my display. 

I didn't install any third-party drivers for the Nvidia videocard. When I launched Ubuntu in the LiveCD mode, everything was OK. But after the yesterday's installation, I'm having a mortal bug like this:

Click! - Black screen - Click! - Black screen - Click! - Black screen...

Very rapidly and endlessly, almost each fifteen minutes, and only Ctrl+Alt+Delete can stop it. XP SP 2 and Linux Slax go well on my computer, no bugs.

I have completely uninstalled the screensaver in the System menu, reduced the screen resolution, but of no avail.

Click! - Black screen - Click! - Black screen - Click! - Black screen...

Should I uninstall Ubuntu or buy a new display instead of "LG"? Which kind of a display should I use with Ubuntu? Can any kind soul help me?

---

### Post by warfacegod on 2010-07-01
Sounds like a driver issue to me. It sounds like it will stay on long enough to this.

Go to: System> Admin.> Hardware Drivers> activate the "Recommended" driver. You'll need to Reboot after it installs.

---

### Post by aprilland on 2010-07-02
> **warfacegod said:**
> Sounds like a driver issue to me. It sounds like it will stay on long enough to this.

Go to: System> Admin.> Hardware Drivers> activate the "Recommended" driver. You'll need to Reboot after it installs.

I did.  "Searching for available drivers... No proprietary or third-party drivers are in use in this system." And that's all.

What's next? Should I wait for  Ubuntu to provide people with correct Nvidia drivers? Or, can I find deb-packages somewhere?

---

### Post by warfacegod on 2010-07-02
```
sudo apt-get install ubuntu-restricted-extras
```

Then try Hardware Drivers again.

---

### Post by aprilland on 2010-07-02
> **warfacegod said:**
> ```
sudo apt-get install ubuntu-restricted-extras
```

Then try Hardware Drivers again.

Thanks, but this command downloads a lot of unnecessary packages such as Adobe Flash and Java, still I see no hardware drivers among them.

Luckily, it installs additional fonts, but that's not the solution of my problem. The last action is "ldconfig deferred processing now taking place", and that's all...

I reduced the resolution and the frequency of the LG display, and now it crashes down not so often. Alas, I seem to need a new one to use Ubuntu.

---

### Post by warfacegod on 2010-07-02
You'll need Adobe Flash if you'll going to watch online videos. I also pulls in mp3 support and allot of codecs for videos. Among other things.

---

### Post by sydbat on 2010-07-02
If you are able to use your computer with no problems under XP, then it is not your monitor.

Also, if there is no "Restricted Driver" for your nVidia card, then it is likely no longer supported. Can you tell us about your video card? What version is it?

---

### Post by aprilland on 2010-07-02
> **warfacegod said:**
> You'll need Adobe Flash if you'll going to watch online videos. I also pulls in mp3 support and allot of codecs for videos. Among other things.

I know the purpose of  Adobe Flash. But if will hardly help me in such a situation.

The point is that if I don't solve the problem with my LG display, no video will be watched at all.

If I solve it, I'll think about Adobe Flash, not earlier.

---

### Post by aprilland on 2010-07-02
> **sydbat said:**
> If you are able to use your computer with no problems under XP, then it is not your monitor.

Also, if there is no "Restricted Driver" for your nVidia card, then it is likely no longer supported. Can you tell us about your video card? What version is it?

What's the use of telling the type of the nvidia card if it is not supported and there's no software for it? 

Besides, Ubuntu was running well in the LiveCD mode. My problems began after the installation only.

I cannot buy a new computer with a modern card.

Is it worth buying a monitor with a built-in video card? With a modern and therefore supported one?

---

### Post by JKyleOKC on 2010-07-02
> **aprilland said:**
> What's the use of telling the type of the nvidia card if it is not supported and there's no software for it? 

Besides, Ubuntu was running well in the LiveCD mode. My problems began after the installation only.The purpose of telling the type of card is so that we can tell you for certain whether it's supported and whether there's drivers for it.

However if it was running well from the LiveCD, the card and monitor are probably both supported just fine and the problem is most likely one of configuration. The newest versions of Ubuntu have gone to doing automatic detection and configuration of the video system, in contrast to the older way that required quite a bit of tweaking. Unfortunately, this new approach depends almost entirely on a pack of information sent by the monitor (called EDID) during the boot process, to tell it what resolutions the monitor can handle. I'd almost bet that if you look at the file **/var//log/Xorg.0.log** you'll find a line in it that says ```
(WW) NVIDIA(GPU-0): The EDID read for display device CRT-0 is invalid: the
(WW) NVIDIA(GPU-0):     checksum for EDID version 1 is invalid.
```
Many monitors, including my Acer X173w, have this situation, and when it happens, Ubuntu defaults to very low resolutions of 800x600 and 640x480.

It can be cured, but may take quite a bit of trial and error. If you want to try this approach, check that log file looking for lines that start with WW or EE (warning or error) and post them here. We can then give you step by step instructions for working around the situation. I have the normal 1400x900 resolution on my monitor despite those warning lines, which I copied from the current log. You, too, can get there with patience!

---

### Post by warfacegod on 2010-07-02
> **aprilland said:**
> I know the purpose of  Adobe Flash. But if will hardly help me in such a situation.

The point is that if I don't solve the problem with my LG display, no video will be watched at all.

If I solve it, I'll think about Adobe Flash, not earlier.

In many situations, pulling in the ubuntu-restricted-extras package will help pull in the *restricted* drivers found in Hardware Drivers. Keeping that in mind, if you think that it's your monitor acting up, fine. Try a different monitor and find out. If it is the monitor then you're wasting your time here.

On the other hand, if it isn't the monitor, then stop wasting *our* time by being a <beep-beep>. There is no reason to be rude to people that you are asking for help and clearly have allot more experience than you do.

---

### Post by aprilland on 2010-07-02
> **warfacegod said:**
>  There is no reason to be rude to people that you are asking for help and clearly have allot more experience than you do.

Ooops! I should never have thought that asking for help could be considered as rudeness!

If you consider me to be rude (and if you just a forum troll) you may not talk to me. Who compells you to waist your time? No problem, I will talk to those who wants to help me.

---

### Post by theozzlives on 2010-07-02
> **warfacegod said:**
> 
On the other hand, if it isn't the monitor, then stop wasting *our* time by being a jerkoff. There is no reason to be rude to people that you are asking for help and clearly have allot more experience than you do.

That was totally uncalled for and VERY rude!

To the OP, have you tried downloading drivers from nVidea?

---

### Post by warfacegod on 2010-07-02
> **aprilland said:**
> I know the purpose of  Adobe Flash. But if will hardly help me in such a situation.

The point is that if I don't solve the problem with my LG display, no video will be watched at all.

If I solve it, I'll think about Adobe Flash, not earlier.

If you guys think what I said was rude then I apologize. However, the above quote is clearly rude with the tone that it carries.

---

### Post by aprilland on 2010-07-02
> **JKyleOKC said:**
> ```
(WW) NVIDIA(GPU-0): The EDID read for display device CRT-0 is invalid: the
(WW) NVIDIA(GPU-0):     checksum for EDID version 1 is invalid.
```


 Everything about the monitor and nvidia in that file:

(==) No Layout section.  Using the first Screen section.
(==) No screen section available. Using defaults.
(**) |-->Screen "Default Screen Section" (0)
(**) |   |-->Monitor "<default monitor>"
(==) No monitor specified for screen "Default Screen Section".
	Using a default monitor configuration.

...

(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.0
	Module class: X.Org Server Extension
(II) NVIDIA GLX Module  195.36.15  Thu Mar 11 23:39:48 PST 2010

...

(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

...

I hope, posting that information will not be considered as rudeness. As well as my desire to use Ubuntu.

---

### Post by theozzlives on 2010-07-02
> **warfacegod said:**
> If you guys think what I said was rude then I apologize. However, the above quote is clearly rude with the tone that it carries.

Go away! There's nothing wrong with the OP's post. Tone? I didn't know typed words can carry a "tone".

OP, go to [www.nvidia.com](www.nvidia.com) and download the Linux drivers. It's prolly a *.bin file and will require some command line work, but we're here for ya.

---

### Post by lkjoel on 2010-07-02
Guys, cool down.
We are trying to help him, we not trying to say that someone else is rude.
[http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)
Scroll down to the **bold** part.
I know that I am not a moderator, but if there is no moderators that come, he will never have his problem fixed.

Kind regards,
Joel.

---

### Post by aprilland on 2010-07-02
> **theozzlives said:**
> Go away! There's nothing wrong with the OP's post. Tone? I didn't know typed words can carry a "tone".

OP, go to [www.nvidia.com](www.nvidia.com) and download the Linux drivers. It's prolly a *.bin file and will require some command line work, but we're here for ya.

Thank you, but I have a doubt whether I can cope with it myself. But I'm not sure if I can ask anything without being considered rude.

---

### Post by lkjoel on 2010-07-02
I certainly agree with you. Check my above post.
This is the first time I have seen this, and I think the moderators should see this too.
I did not find you rude at all.

---

### Post by theozzlives on 2010-07-02
> **aprilland said:**
> Thank you, but I have a doubt whether I can cope with it myself. But I'm not sure if I can ask anything without being considered rude.

You weren't rude. The restricted extras would not have helped you, but I do recommend you install them.

---

### Post by overdrank on 2010-07-02
Please remember the [Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy") when posting. 
> Be respectful of all users at all times. This means please use etiquette and politeness. Treat people with kindness and gentleness. If you do this the rest of the code of conduct won't need more than a cursory mention.

---

### Post by aprilland on 2010-07-04
I have bought a new monitor. The crashing didn't stop, though it occurs not so often.

Despite the weekend, I found a specialist who took a look at my computer and told me that I need the driver for "intel(R) 82845G/GL/GT/PE/GV Graphic Controller".

I could find such a driver neither at the Intel website nor at packages.ubuntu.com.

So, I need a *.deb package with that driver. Please, if anybody can help, give me a link for downloading!

P.S. I hope I was polite enough. I'm awfully sorry if I seemed to be rude again, for some reason or other. When starting this topic, I didn't want any forum troll to provoke hate. All I need is help.

---

### Post by philinux on 2010-07-04
> **aprilland said:**
> I have bought a new monitor. The crashing didn't stop, though it occurs not so often.

Despite the weekend, I found a specialist who took a look at my computer and told me that I need the driver for "intel(R) 82845G/GL/GT/PE/GV Graphic Controller".

I could find such a driver neither at the Intel website nor at packages.ubuntu.com.

So, I need a *.deb package with that driver. Please, if anybody can help, give me a link for downloading!

P.S. I hope I was polite enough. I'm awfully sorry if I seemed to be rude again, for some reason or other. When starting this topic, I didn't want any forum troll to provoke hate. All I need is help.

I think the default install already has the driver. What does system>admin>hardware drivers offer to be activated. If nothing then you have the drivers installed via the kernel.
[http://ubuntuforums.org/showthread.php?t=1448684](http://ubuntuforums.org/showthread.php?t=1448684)

---

### Post by aprilland on 2010-07-04
> **philinux said:**
> I think the default install already has the driver. What does system>admin>hardware drivers offer to be activated. If nothing then you have the drivers installed via the kernel.
[http://ubuntuforums.org/showthread.php?t=1448684](http://ubuntuforums.org/showthread.php?t=1448684)

Thank you for the link! It sends to the manual how to install xserver-xorg-video-intel. But it appeared to be already installed.

As far as I understand, everything is installed on my computer, all necessary packages, but something is still wrong. Today three crashes occurred within a short period of time, and, over again, only "Reset" could help. The same symptoms as described in the beginning of this topic. Still, Windows XP and Linux Slax run well, therefore the hardware is OK.

---

### Post by lkjoel on 2010-07-04
> **aprilland said:**
> Hi! I'm afraid I have got a disaster with my display. 

I didn't install any third-party drivers for the Nvidia videocard. When I launched Ubuntu in the LiveCD mode, everything was OK. But after the yesterday's installation, I'm having a mortal bug like this:

Click! - Black screen - Click! - Black screen - Click! - Black screen...

Very rapidly and endlessly, almost each fifteen minutes, and only Ctrl+Alt+Delete can stop it. XP SP 2 and Linux Slax go well on my computer, no bugs.

I have completely uninstalled the screensaver in the System menu, reduced the screen resolution, but of no avail.

Click! - Black screen - Click! - Black screen - Click! - Black screen...

Should I uninstall Ubuntu or buy a new display instead of "LG"? Which kind of a display should I use with Ubuntu? Can any kind soul help me?
What does Click! - Black screen mean?

---

### Post by aprilland on 2010-07-05
> **lkjoel said:**
> What does Click! - Black screen mean?

It means that the monitor suddenly switches off, then switches on but instantly switches off again, switches on but instantly switches off again, switches on but instantly switches off again... and this cycle seems to be endless. Only Crtl+Alt+Delete or Reset can stop this crash. 

On Saturday I bought a new monitor, it doesn't produce a quiet click when switches on, so it's just a black screen now. 

And it's something with Ubuntu, as Linux Slax and Windows XP go well.

---

### Post by lkjoel on 2010-07-05
> **aprilland said:**
> It means that the monitor suddenly switches off, then switches on but instantly switches off again, switches on but instantly switches off again, switches on but instantly switches off again... and this cycle seems to be endless. Only Crtl+Alt+Delete or Reset can stop this crash. 

On Saturday I bought a new monitor, it doesn't produce a quiet click when switches on, so it's just a black screen now. 

And it's something with Ubuntu, as Linux Slax and Windows XP go well.
Do you have everything up to date?
Do you have 10.04.1? (There IS such a version)

---

### Post by aprilland on 2010-07-05
> **lkjoel said:**
> Do you have everything up to date?
Do you have 10.04.1? (There IS such a version)

I have downloaded and installed all the updates suggested via the Update Manager. Now the list of updates is empty.

Alas, I use 10.04. I cannot download a new *.iso, my internet connection is quite slow. Either I cannot buy a new computer. At least, not now. Maybe, in a half of a year or so.

Besides, what if the new version performs the same issue? Many people use 10.04 and don't encounter such a problem as I do.

Should I try to reinstall Ubuntu?..

---

### Post by lkjoel on 2010-07-05
> **aprilland said:**
>  
Should I try to reinstall Ubuntu?..
If you have backed up all your important data, yes.
We can guide you through the install process if you would like.

---

### Post by aprilland on 2010-07-05
> **lkjoel said:**
> If you have backed up all your important data, yes.
We can guide you through the install process if you would like.

Thank you! I have already burnt my data onto DVD disks.

I seem to have a lot of questions. Should I format the hard drive partitions used by Ubuntu before the re-installation? I mean, do I have to delete all Ubuntu data manually to make free space required for the installation?

---

### Post by lkjoel on 2010-07-05
> **aprilland said:**
> Thank you! I have already burnt my data on DVD disks.

I seem to have a lot of questions. Should I format the hard drive partitions used by Ubuntu before the re-installation? I mean, do I have to delete all Ubuntu data manually to make free space required for the installation?
Nope, that is, if you tell it to take the whole hard disk.

---

### Post by aprilland on 2010-07-08
I have reinstalled Ubuntu. But my problem is not gone. The same crashing repeats appriximately each three hours. But I learnt that the hard drive has bad sectors. Can they possibly be the reason of the crashing?

The Disk Utility says:
[I]"Reallocated sector count.
Count of remapped sectors. When the hard drive finds the read/write/ verification error, it marks the sector as 'relocated'  and transfers data to a special reserved area (spare area)
Warning
Normalized 100
Worst 100
Threshold 36
Value 11 sector[/I]s"

---

### Post by aprilland on 2010-07-26
Well, two weeks passed, but no one helped. No one knows the reason of the videocard crashing down. 
But it's a real bug of Ubuntu.
I'm sorry to say that, but I think I'd better try some other distribution. Maybe, Linux Mint.

---

