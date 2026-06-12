---
title: "Nvidia Drivers: to use, or not to use?"
date: 2010-12-02
forum: New to Ubuntu
---

### Post by maryalesia on 2010-12-02
HOKAY. So I've been using Linux for a couple of months now, and I have some lingering questions about the proprietary drivers nvidia uses. For example:

Why can't I change refresh rates (especially in twin view, when the two screens might require drastically different rates)? Which leads me to my second question ...

Why is screen-tearing such a common problem? 

Also: when I have the drivers enabled, the ubuntu logo at login is really pixelated. When they are disabled, it looks fantastic. Shouldn't it be the other way around?

In another (unrelated) thread, a user suggested that I switch to the default drivers. The last time I disabled nvidia, I had a LOT of screen tearing. I could barely move my cursor without a tear. 

Part of me wants to stay with the nvidia drivers as they are right now, because it took months to get the tearing to stop and I'm not entirely sure how I did it. Something about medibuntu and changing start-up applications, and even now there are still tears when I use sites like Hulu.

Has anybody gotten their computer to work (tear-free) without the proprietary drivers? 

Sorry for the long post! Nvidia drivers make me kind of nuts.

PS my graphics card is nvidia geforce 9800M GTS

---

### Post by Zzl1xndd on 2010-12-02
I use a dual monitor set with a GT8800 and the proprietary drivers. I haven't had any issues. No tearing, etc. Can't say regarding the refresh rates as my monitors are identical and would have been set to same either way.

I also have a friend using an 9800, dual monitors and he hasn't mentioned any issues either. However I believe he is still using 10.04

---

### Post by maryalesia on 2010-12-02
> **tweakedenigma said:**
> I use a dual monitor set with a GT8800 and the proprietary drivers. I haven't had any issues. No tearing, etc. Can't say regarding the refresh rates as my monitors are identical and would have been set to same either way.

I also have a friend using an 9800, dual monitors and he hasn't mentioned any issues either. However I believe he is still using 10.04

AHK! I'm still using 10.04 too. Didn't realize there was an upgrade available.

Downloading right now. Last time I did this the stuff I did to fix screen tearing was somehow disabled so when I come back this might be a more pressing issue than when I initially posted. :o

System upgrades make me nervous. When I first installed it was x.org fail: black screen of DOOM!! I'm always afraid I'll never see my desktop again;)

---

### Post by maryalesia on 2010-12-02
all upgraded! :D

And no screen-tearing, either. Yay! 

Haven't tested with twin-view yet, though. Here is what happened before in twinview:

I hook up my laptop to a 22 inch HD tv via HDMI chord. When I set it as twinview with the TV "to the left of" my laptop display, there is tearing on the TV. If I set the TV as the "primary display for the x server" I am able to watch movies I have downloaded in fullscreen on the TV (if I keep my laptop as the primary display for the x server fullscreen will default back onto the laptop display). However, even with the TV as the primary display, hulu *always* defaults onto the laptop in fullscreen.

When I set it as twinview with the displays clones of eachother, I end up with a small screen overlaying a larger one, so my laptop display is limited to the upper right hand corner of the larger TV display. (I don't know if I'm explaining this well). If I change the resolution of the TV to match that of the laptop, the picture quality on the TV diminishes. Either way, there is still tearing on the TV. 

If I set them up as two separate X screens, the cursor *always* gets stuck in the TV display (unless I'm using a usb mouse). Can't remember if there was screen tearing, but considering my luck with this issue there probably was.

I can sidestep the issue by disabling my laptop display, but one day I would like to be able to connect my laptop without disabling.

Again ... sorry that this is such a long post!

---

### Post by maryalesia on 2010-12-02
PS - 

This problem existed in windows also. However, because I was able to change the refresh rates, I could get it so the TV display didn't tear while the laptop display did tear. I didn't mind it this way because the whole point was I kept the laptop display on to browse the internet, etc and the tv on to watch videos.

Anyway I would be more than happy if I could get this same, imperfect outcome in ubuntu.

---

### Post by Zzl1xndd on 2010-12-02
Just got home and tested from the Nvidia X server Settings tool and it looks like I can set a different refresh for each monitor. Are you using the Nvidia tool?

---

### Post by maryalesia on 2010-12-02
> **tweakedenigma said:**
> Just got home and tested from the Nvidia X server Settings tool and it looks like I can set a different refresh for each monitor. Are you using the Nvidia tool?

Yup. I can change the resolution from "auto" to 1400x900 (which is the same as the auto setting). It unfreezes the drop-down menu of refresh rates. The drop down menu consists of two choices: auto, and 60. (HINT: they are the same.)

---

### Post by Cavsfan on 2010-12-02
I always wanted the latest driver after I found out I could get them, but went through nVidia driver hell this morning 
after getting an update to the latest driver. It took me over half a day just to boot into anything but recovery mode.

I would suggest not using the latest and greatest, unless you are prepared for some head aches!

I had 3 kernels and none of them would work. I accidentally removed them all and rebooted, which left me not able 
to get back in. I had to boot with the Live-cd and install the kernel with drs305's help from one of his GRUB tutorials. 
That is the hard way. I am back to using 260.19.12 and I will stay with it!

---

### Post by maryalesia on 2010-12-02
> **Cavsfan said:**
> I always wanted the latest driver after I found out I could get them, but went through nVidia driver hell this morning 
after getting an update to the latest driver. It took me over half a day just to boot into anything but recovery mode.

That's insane! I'm glad you got it fixed :D

I have heard rumors that intel graphics cards work better than others with linux because they started out as open source. Is there any truth to this? 

Because from what I've read online, nvidia and ATI don't play nicely with linux in a lot of cases.

---

### Post by bodhi.zazen on 2010-12-02
What do you need that the nouveau driver does not provide ?

[http://nouveau.freedesktop.org/wiki/](http://nouveau.freedesktop.org/wiki/)

The advantage of the nouveau driver is that you get support from the open source community. If you use the nvidia driver, and you have problems, you will get support from nvidia (and loose at least kernel support from the open source community).

I personally use the nouveau driver and it "works for me".

---

### Post by maryalesia on 2010-12-02
> **bodhi.zazen said:**
> What do you need that the nouveau driver does not provide ?.

when I had the advanced graphics driver disabled, I had a lot of screen tearing. I don't know if this is still the case. I will try disabling and get back to you.

---

### Post by maryalesia on 2010-12-02
disabled the drivers and now I have screen tearing when I move around windows and play videos. This is a problem because essentially all I do on my computer is watch television and movies. However, if there is a way using the open source driver to stop screen tearing AND to make using two monitors (without tearing) possible, I'm game.

---

### Post by bodhi.zazen on 2010-12-02
What driver are you using ? If it is the nouveau driver you should file a bug report (include your hardware).

---

### Post by maryalesia on 2010-12-02
> **bodhi.zazen said:**
> What driver are you using ? If it is the nouveau driver you should file a bug report (include your hardware).

I have no idea. I don't think it's a bug, just that the refresh rate was preset to 50 (my monitor needs at least 60). There was no way to change the refresh rate in the "monitors" tool, so I changed it from compiz config. I also clicked "sync to v blank" which helped when I was using nvidia drivers (although I have no idea what it means or does or if it is of any use in this area). 

Anyway, tearing has gone WAY down. No longer noticeable when I move windows and hardly any in hulu. (there is still a little in hulu but I think that has less to do with refresh rates and more to do with flash. Any way I use it as my ultimate screen tearing test.) 

Now the question: can it work in twin-view?

---

### Post by maryalesia on 2010-12-02
here's where I've found myself:

I hooked it up to a tv successfully. The screen tears when I move windows around but not when I play video files that I've downloaded. It tears very badly when I play hulu videos in full screen. I still think that could have something to do with flash being messed up, but I'm not sure. This occurs on both my laptop monitor and my tv screen. This is a step in the right direction.

The tearing when I move around windows doesn't bother me, but the hulu playback problems do. Does anyone know why this happens? Is it a hulu-linux-flash compatability problem?

In other words: any ideas?

---

### Post by Cavsfan on 2010-12-20
**maryalesia**, did you ever get your problem solved? I ended up getting the latest nVidia driver - 260.19.29 from the nVidia website. 
And then went by these instructions to create a script that will install that driver in any new kernel that is installed.

[[COLOR=blue]_HOWTO: Automatically update manually installed NVidia drivers after kernel updates_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=835573")

I got a new kernel and it successfully installed the driver into the kernel.
There is a message as the kernel is installed: 
"Building NVIDIA driver for kernel xxxx" and then this message appears next: "SUCCESS: Driver installed for kernel xxxx".

My problem was that in addition to the above script with a hard coded driver name, I had added the x-swat PPA and got a beta nvidia driver.
That was why nothing would boot up and it took me a while to figure that out.

I hope you got your issue resolved. :D

---

### Post by maryalesia on 2010-12-20
> **Cavsfan said:**
> **maryalesia**, did you ever get your problem solved? 

This is what happened: I ran a script to fix the plymouth resolution problem and ended up causing more problems then I could have potentially solved. (Shut down only shut down x-org, not the entire comp, screen kept freezing, etc.)

Since I pretty much useless in the terminal and didn't have many files on my computer that I couldn't re-download, I reinstalled 10.04 to fix the problems I created in plymouth (I'm waiting for a stable release of 10.10, just because). 

I fixed the screen tearing issues the way I always did (sync to v-blank in compiz and nvidia settings, set refresh rate to 60 in compiz, and add nvidia settings to start up apps).

Basically, I'm back where I started. I still have to disable my laptop display when using HDMI out, or else the TV screen tears. While I'm still curious as to why nvidia doesn't fix this problem, I've decided it's an inconvenience I can live with.:D

I'm not computer savvy enough to do anything like what you've done, but I'm glad you got your computer to work (you did get it working, right?).

---

### Post by Cavsfan on 2010-12-20
> **maryalesia said:**
> This is what happened: I ran a script to fix the plymouth resolution problem and ended up causing more problems then I could have potentially solved. (Shut down only shut down x-org, not the entire comp, screen kept freezing, etc.)

Since I pretty much useless in the terminal and didn't have many files on my computer that I couldn't re-download, I reinstalled 10.04 to fix the problems I created in plymouth (I'm waiting for a stable release of 10.10, just because). 

I fixed the screen tearing issues the way I always did (sync to v-blank in compiz and nvidia settings, set refresh rate to 60 in compiz, and add nvidia settings to start up apps).

Basically, I'm back where I started. I still have to disable my laptop display when using HDMI out, or else the TV screen tears. While I'm still curious as to why nvidia doesn't fix this problem, I've decided it's an inconvenience I can live with.:D

I'm not computer savvy enough to do anything like what you've done, but I'm glad you got your computer to work (you did get it working, right?).

Yes, I got mine working pretty well. And I am on Ubuntu 10.10 Maverick Meerkat and it is real stable. 
The final release was on 10-10-10 and is ironically version 10.10.
See here: [[COLOR=blue]_http://releases.ubuntu.com/10.10/_[/COLOR]]("http://releases.ubuntu.com/10.10/")

Glad you got yours working! :D

---

### Post by maryalesia on 2010-12-21
> **Cavsfan said:**
> Yes, I got mine working pretty well. And I am on Ubuntu 10.10 Maverick Meerkat and it is real stable. 
The final release was on 10-10-10 and is ironically version 10.10.]

Glad you got yours working! :D

Are you sure that was the final release? My system is set to alert me when the next LTS release is available; I got maverick before by changing that to accept the latest release, beta or otherwise. 

I'm worried about the screen-freeze problem. I don't think messing with python could have caused that, and it never happened before I updated. It happened frequently when switching users, when the screen was left for an extended period of time on the same image & after "hibernation" when I closed the laptop lid. I had to manually shut down the computer every time. (granted: I didn't wait very long to see if it would fix itself.)

---

### Post by Cavsfan on 2010-12-22
> **maryalesia said:**
> Are you sure that was the final release? My system is set to alert me when the next LTS release is available; I got maverick before by changing that to accept the latest release, beta or otherwise. 

I'm worried about the screen-freeze problem. I don't think messing with python could have caused that, and it never happened before I updated. It happened frequently when switching users, when the screen was left for an extended period of time on the same image & after "hibernation" when I closed the laptop lid. I had to manually shut down the computer every time. (granted: I didn't wait very long to see if it would fix itself.)

Oh, I thought you meant 10.10 RC and not LTS the next LTS won't be for quite a while.

---

### Post by inkrypted on 2010-12-22
Don't know about anyone else but I upgraded to Maverick shortly after installing a 260 GTX and had massive problems with twinview and other things until I went to the latest drivers by following advice found in this forum. Basically it was just open a terminal and type sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings
This got me the latest drivers and has been working great ever since.

---

### Post by Cavsfan on 2010-12-23
> **inkrypted said:**
> Don't know about anyone else but I upgraded to Maverick shortly after installing a 260 GTX and had massive problems with twinview and other things until I went to the latest drivers by following advice found in this forum. Basically it was just open a terminal and type sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings
This got me the latest drivers and has been working great ever since.

That is what I had setup, but I had mistakenly left the script in to install a specific driver at the same time and everything went haywire 
when the next kernel was installed.

The PPA you mention will give you the latest nVidia driver but, it will also give you beta drivers too. If you are good with that, all is good.

---

### Post by inkrypted on 2010-12-24
Yeah that's true and all I can say is so far so good. I have a laptop that is a bit antiquated with an Nvidia Go and I have not had to mess with it at all maybe it's when you start using things like Twinview or getting a more up to date card that you have to start using different drivers? I have noticed that when I get kernel updates I have to boot using low graphics mode and remove the drivers and put them back in and reboot but I kinda expected that thinking that it now has to use what it replaced.

---

