---
title: "How to restore lost panels in Gnome"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by Sleepy-zz-John on 2009-02-07
Hi,

   I have a problem similar to pzs in thread 1052064 last week.  I removed Evolution because I'd replaced it with Thunderbird and I took out too many Evolution dependencies in the process so that I lost all my Gnome panels the next time I restarted.  OK, I know, Silly me :oops:

That means I can't do anything from my blank desktop,  not even bring up a terminal:(

However by restarting in recovery mode, I can get a root command line and I've tried to follow RomeReactor's suggestions to pzs on that.

First I tried ```
gconftool-2 --shutdown
```
then ```
rm -rf ~/.gconf/apps/panel
```
and then ```
rm -rf ~/.gconf/apps/panel
```
and ```
pkill gnome-panel
```
but this did not work.

So then I tried RomeReactor's ```
sudo aptitude install ubuntu-desktop
```
but this didn't restore my panels either.

In summary,  my questions are:

1.  From a blank desktop without any panels,  is there easier way to get a terminal up than by restarting in recovery mode?

2.  What else could I try?

---

### Post by billgoldberg on 2009-02-07
> **Sleepy-zz-John said:**
> Hi,

   I have a problem similar to pzs in thread 1052064 last week.  I removed Evolution because I'd replaced it with Thunderbird and I took out too many Evolution dependencies in the process so that I lost all my Gnome panels the next time I restarted.  OK, I know, Silly me :oops:

That means I can't do anything from my blank desktop,  not even bring up a terminal:(

However by restarting in recovery mode, I can get a root command line and I've tried to follow RomeReactor's suggestions to pzs on that.

First I tried ```
gconftool-2 --shutdown
```
then ```
rm -rf ~/.gconf/apps/panel
```
and then ```
rm -rf ~/.gconf/apps/panel
```
and ```
pkill gnome-panel
```
but this did not work.

So then I tried RomeReactor's ```
sudo aptitude install ubuntu-desktop
```
but this didn't restore my panels either.

In summary,  my questions are:

1.  From a blank desktop without any panels,  is there easier way to get a terminal up than by restarting in recovery mode?

2.  What else could I try?

alt+f2 should bring up the run prompt.

You can start programs from that (with tab completion).

--

Is "gnome-panel(s)" installed?

Press alt+f2 and enter "gksu synaptic".

Look for gnome-panel(s) and see if it's installed.

It migth have been removed when removing evolution.

---

### Post by Sleepy-zz-John on 2009-02-07
Thanks for that suggestion,  but alt+f2 doesn't do anything in my present state. I tried all the alt +f* combinations and the only one that does anything at all is alt+f6 which breifly brings up an x-nautilus desktop icon while I hold the alt key down.

Would it be OK to try that gksu synaptic from a root command line in recovery mode?

---

### Post by Sleepy-zz-John on 2009-02-17
I've been struggling with the above problem for a week now, and still haven't managed to restore my Gnome panels.   Been trying to use the Rescue mode on my original CD to fix my broken system but this is failing as I've described in a new General Help thread 1072170 "Rescue fails to install the base system".  
Hopefully the solution to my lost Gnome panels will now be found by rescuing my broken system with the original installation CD, but let this thread serve as a warning to others not to try and delete evolution packages unless you really know what you're doing!
Meanwhile,  I'd welcome any further suggestions about my ongoing problem after you've read my General Help thread 1072170 "Rescue fails to install the base system".    
To avoid running two seperate threads, please post any such suggestions on  General Help thread 1072170 so this thread can be closed.

---

### Post by Metallion on 2009-02-17
You cannot launch Synaptic from the root commandline but you can use apt-get instead. It does the same as Synaptic actually is a frontend to apt-get. On the root console type:
```
apt-get install gnome-panel
```

It should install the panels for you and if it tells you that the panels are already installed, you can try this:

```
startx
```

X11 and Gnome should start now. If the panels are still gone, try this:

```
apt-get remove gnome-panel --purge
```

This will uninstall the panels and delete all configuration files. Then you can install them again with the first command:

```
apt-get install gnome-panel
```

---

### Post by Sleepy-zz-John on 2009-02-18
Thanks for the suggestions Metallion,  but I'm afraid no success so far.
Here's what happens:

> Code:
apt-get install gnome-panel

Many unmet dependencies are recommended,  but they're then listed as not going to be installed.  This is followed by a suggestion to try 

Code:
apt-get -f install

which I attempted on the listed dependencies individually,  but those attempts only bring up more lists of unmet dependencies, and I can't make any progress in reducing my unmet list.  

> ..... if it tells you that the panels are already installed, you can try this:

Code:
startxX11

 and Gnome should start now. If the panels are still gone, try this:

Code:
apt-get remove gnome-panel --purge

This will uninstall the panels and delete all configuration files. 

Although the panels didn't seem to be installed,  I did try that suggestion.  It confirmed my suspicion with:

'Package gnome-panel is not installed so not removed'

Moving on,  I've been able to find the following from old logs:

'Completely removed the following packages  
   evolution-plugins
ekiga
evolution
evolution-common
evolution-data-server
evolution-exchange
evolution-webcal
fast-user-switch-applet
gnome-applets
gnome-panel
libedataserverui1.2-8
ubuntu-desktop'

> Then you can install them again with the first command:

Code:
apt-get install gnome-panel 

Needless to say that doesn't work.  

Since so many packages are missing,  I feel I ought to try and restore them from my original installation CD,  which is what I've described in my new General Help thread 1072170 "Rescue fails to install the base system".  

If I use an installer environment shell in that CD's Rescue mode,  I can find most of the packages I'm missing on the CD.  For example  

/cdrom/pool/main/g/gnome-panel

But my problem now is that the apt-get command doesn't work within that shell.  

apt-get does work OK from a shell in /dev/sda1,  but when I'm in /dev/sda1,  I can't see the files on my CDROM

The installer environment shell allows BusyBox commands so maybe I should try to use these to export the packages I need into my target area,  and then having assembled them there,  pick them up from a shell in /dev/sda1 and install them with apt-get from there,   but this is all unfamiliar territory and I feel there ought to be an easier way of getting my CD's Rescue mode to reinstall the packages for me.  

In summary,  I think the area where I could benefit most from advice is on my CD's Rescue mode and its failure to complete its 'Install the base system' step.

---

### Post by SunnyRabbiera on 2009-02-18
did you try sudo apt-get instal ubuntu-desktop?

---

### Post by Sleepy-zz-John on 2009-02-18
> did you try sudo apt-get instal ubuntu-desktop?

Yes,  thanks, I've tried that,  but it produces an even bigger list of unmet dependencies than apt-get install gnome-panel does.  

Given the above list of evolution packages that have been removed,  I think this is only to be expected.  

My most significant question now,  I believe,  is how can I restore all these missing packages without a complete re-installation that overwrites my remaining good files and data on the partition?

---

### Post by Metallion on 2009-02-18
It sounds to me like you tried apt-get -f install nameOfDependency? Can you try to do it with no other arguments? Just like this:
```
apt-get -f install
```

Actually the thing this command does is automatically resolve unmet dependencies for you.

I suggest you run it first and then do as SunnyRabbiera suggested:
```
apt-get instal ubuntu-desktop
```

---

### Post by Sleepy-zz-John on 2009-02-19
> It sounds to me like you tried apt-get -f install nameOfDependency? Can you try to do it with no other arguments? Just like this:

Code:
apt-get -f install

Actually the thing this command does is automatically resolve unmet dependencies for you.

Yes,  that was a good suggestion and it moved me forward a little.  I ran it in recovery mode, and it reported 49 newly installed archives,  but then this error:

"E: couldn't configure pre-depend libc6 for findutils,  probably a dependency cycle" 

> and then do as SunnyRabbiera suggested:

Code:
apt-get instal ubuntu-desktop

OK, running that produced:

"dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct"

so then I ran dpkg and got this output:

"Setting up initramfs-tools (0.92buntu15)...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools...
update-initramfs: Generating /boot/initrd.img-2.6.27-11-generic
Cannot find /lib/modules/2.6.27-11-generic
update-initramfs: failed for /boot/initrd.img-2.6.27-11-generic
dpkg: subprocess post-installation script returned error exit status 1"

I have tried to boot in recovery mode a couple of times, once with 2.6.27.11 and once with 2.6.27.9.   They failed with

modprobe: FATAL: Could not load /lib/modules/2.6.27-9-generic/modules.dep: No such file or directory

I checked in /boot and found I have three saved generics:

initrd.img-2.6.27-11-generic    Jan 31 
initrd.img-2.6.27-9-generic    Dec 22
initrd.img-2.6.27-7-generic    Nov 26

My installation disc which I've been trying to use in rescue mode was downloaded in Nov so it would only have 2.6.27-7 on it.

Another anomaly I noticed when trying to boot in recovery mode was that my user and password are now giving me log-in fails, so I could not proceed beyond that point.

Would it make sense to download a new installation disc with the latest generic updates and try and run that in rescue mode?    Or maybe try to install from a new installation disc without reformatting my partition and without overwriting my old files?    

Appreciate any further ideas and suggestions.    Many thanks!

---

### Post by Tundro Walker on 2009-03-12
I know it's old, but Thank God for this thread.  

I did a fresh install of Intrepid tonight in order to try to fix Pulse Audio not playing any sound.  My modus-operandi after installs is to go through and get rid of packages I don't use.  I don't use Evolution at all, so I dumped it off, having done so in the past without issue.

This time, it dumped off the gnome-panel package without me realizing it.  I've been screwing around for better part of 2 hours trying to figure this crap out.  Who the hell made gnome-panel dump off if you uninstall Evolution?  That's ridiculous!

Like the OP, I couldn't get Atl+F2 to work, nor could I create app launchers on the desktop.  I basically cheated by making a .sh document with "firefox" in it, so I could get web-browser going.  Then read various places talking about "pkill gnome-panel", but never got feedback saying gnome-panel was not installed.

When I read this post here, I apt-get gnome-panel, and come to find out it's not installed b/c of Evolution.  Apt-get'ing it and installing all dep's worked like a charm.

But still, WTH?  So basically you HAVE to have Evolution installed if you want to use Gnome (at least, use it in a normal person's way, with panels).  That's just stupid.  There should be some kind of pop-up in Synaptic saying "you're removing a critical piece of the desktop" or something when things like gnome-panel are about to get removed.

It's just frustrating that I was able to dump off Evolution all through out Dapper to Hardy, but now it's mandatory for gnome-panel all of a sudden.

EDIT: To add insult to injury, a fresh install still hasn't fixed Pulse Audio.  So now I have to screw around with that, too.  I understand the push to get newer, fresher, better technology integrated into Ubuntu, but it seems every distro is 2 steps forward, 1 step back.  (But, to be honest, I sort of love this trouble-shooting.  When a Linux system is all setup properly, it's boring, because it takes care of itself.  This rare trouble-shooting at least makes me feel like I'm helping out my computer.  How sad is that?)

---

### Post by E.T.Smith on 2009-04-26
Facing this same problem right now, so just posting to "tag" the thread for reference. But my sentiment is the same as the above poster: why is the gnome-panel dependent on evolution? Why does removing this particular application yank a lynchpin out of the desktop structure? Not so much angered as curious.

---

