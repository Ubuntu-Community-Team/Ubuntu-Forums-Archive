---
title: "Ubuntu 10.04 and iPod dislike each other"
date: 2010-12-26
forum: New to Ubuntu
---

### Post by fslezak on 2010-12-26
Hi.

I recently accquired a iPod Touch 4th Generation. The information is found below:

- iOS 4.2.1
- 8 GB

My computer thinks that it is a digital camera. Banshee and Rythmbox do not see the iPod at all.

Please help!

---

### Post by davidmohammed on 2010-12-26
I think I remember omgubuntu.co.uk claiming that the latest version of banshee will work for your Ipod shuffle

suggest

sudo add-apt-repository ppa:banshee-team/ppa

sudo apt-get update && sudo apt-get upgrade

sudo apt-get install banshee

---

### Post by fslezak on 2010-12-26
Banshee is the NEWEST version.

---

### Post by davidmohammed on 2010-12-26
... yes correct.  I misread the report.  Apparently Apple has changed the database format yet again making gpod incompatible.

Need to look at the daily builds to see if they have resolved the matter.  If not, I'm sure a few weeks/months this will be resolved.


....

but if you cant wait - [look]("http://cogizio.org/operating-systems/ubuntu/3089") at this post...

---

### Post by fslezak on 2010-12-26
Jailbreaking can RUIN my pod, and I won't be able to use Apple's warrenty and replace it.

---

### Post by DaveBooth on 2010-12-26
I have exactly the same problem, 10.04 and G4 iPOD touch, shows as digicam only. Has anyone discovered a viable workaround for this yet?

Dave

---

### Post by davidmohammed on 2010-12-26
see this [link]("https://help.ubuntu.com/community/PortableDevices/iPhone") for iPod support

note clicking through to [here]("http://www.libimobiledevice.org/") says that your current firmware is supported - look at the comments at the bottom of that webpage - it looks like you'll need to compile some code to update the version of libimobiledevice currently installed in 10.10.

---

### Post by fslezak on 2010-12-26
Geez, I am insane!

I removed my current libimobiledevice for the deveopment (unstable) version. After that didn't work (make fault), I upgraded my machine and attempted to re-install libimobiledevice .
The problem is below:

```


Unpacking libimobiledevice1-dbg (from .../libimobiledevice1-dbg_1.0.4-1ubuntu1~lucid1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libimobiledevice1-dbg_1.0.4-1ubuntu1~lucid1_i386.deb (--unpack):
 trying to overwrite '/usr/lib/debug/usr/bin/idevice_id', which is also in package libimobiledevice0-dbg 0:0.9.7-1ubuntu1
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libimobiledevice1-dbg_1.0.4-1ubuntu1~lucid1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by muteXe on 2010-12-26
Maybe run an xp in virtualbox. I don't really understand why iPod users even bother with Linux.

---

### Post by fslezak on 2010-12-26
Tried that...

I have to constantly reboot (Ubuntu) just so WinXP (in vBox) can see it.
Is there ANY way to get iPod support on Ubuntu?

And also... did anyone figure out what was happening in Post 8?

---

### Post by ivanovnegro on 2010-12-26
> **fslezak said:**
> Tried that...

I have to constantly reboot (Ubuntu) just so WinXP (in vBox) can see it.
Is there ANY way to get iPod support on Ubuntu?

And also... did anyone figure out what was happening in Post 8?

iPods can make some hard problems always.
First to your output, seems to me something is broken with your packages, you could repair them.
Second, I dont own an iPod so I couldnt be the great helper here but did you try your ipod with Clementine Music Player? It has iPod support also, not sure if it will work with yours.

---

### Post by fslezak on 2010-12-26
Repair packages how?

Also, when I removed libimobiledevice for the unstable version, it got rid of LOTS of Rythmbox files, including all my music stores.

---

### Post by tekkidd on 2010-12-26
You probably don't have the latest libimobile device installed ```
sudo add-apt-repository ppa:pmcenery/ppa
```
then ```
sudo apt-get update
``` then ```
sudo apt-get upgrade
``` then it should work

---

### Post by ivanovnegro on 2010-12-26
> **fslezak said:**
> Repair packages how?

Also, when I removed libimobiledevice for the unstable version, it got rid of LOTS of Rythmbox files, including all my music stores.

You could go to Synaptic and there you will find one entry in the menu that says "Repair broken packages" or in the terminal.
Because I dont know what is the specific problem right now, [here]("https://help.ubuntu.com/community/SynapticHowto") is a link with many infos about similar things and how to solve them.

---

### Post by fslezak on 2010-12-26
Package fix didn't work.

The solution from tekkid also didn't work.

---

### Post by ivanovnegro on 2010-12-26
> **fslezak said:**
> Package fix didn't work.

The solution from tekkid also didn't work.

What is the error output right now?
Did you install the new PPA?

---

### Post by fslezak on 2010-12-28
Same output.

I did install the PPA. It seems I need to wait.

---

### Post by iann128 on 2010-12-28
> **muteXe said:**
> Maybe run an xp in virtualbox. I don't really understand why iPod users even bother with Linux.

Because if the iPod is the only thing that does not work I can live with a small duel boot partition to run a copy of Windows. Every computer (unless home built) comes with a license to run Windows so just boot into it every now and then to update the iPods... And the are many that have gotten them to work under Linux. Mine shows up, but I choose not to mess with it under Linux, one of these days I may just to see how it works. I do not use my iPod for music much anyway. It controls my XM radio in the car, and I use the Kindle app to read books with it.

---

### Post by fslezak on 2010-12-28
Thank you all for your help.

I will not mess with Windows so I am marking this thread as solved. 

To all of your iPod users, I hope that the iOS 4.2.1 will work soon!

---

### Post by fslezak on 2010-12-30
Ok, thread back on. I managed to get my Ubuntu to see my iPod, however I can not see it in Rythmbox or on my desktop.

Here are the steps I did:

1. sudo add-apt-repository ppa:pmcenary/ppa
2. sudo apt-get update
3. sudo apt-get upgrade
4. ```
 
sudo apt-get remove libimobiledevice*
sudo apt-get install libimobiledevice-utils
sudo apt-get install gtkpod
sudo apt-get upgrade

```
5. idevicepair unpair
6. idevicepair pair
7. idevicepair validate

Let's get going!

---

### Post by RedRat on 2010-12-30
Not to rain on anybody's parade here, but I would say that Linux users ought to avoid buying into the iPod franchise. I could fully understand a beginners frustrations here.

---

### Post by andy95 on 2010-12-30
Ubuntu 10.10 can see pictures and play music on my iPod Touch 2G. I don't know if the computer operating system makes a difference or my jailbroken iPod.

---

### Post by Chronon on 2010-12-30
andy, apparently it is because your iPod does not use the newest iOS.

---

### Post by fslezak on 2010-12-31
Again...

My "ideviceinfo" can see the iPod, but Nautilus, Rythmbox, GTKPod, and Banshee can't see it.

---

### Post by jdforsythe on 2011-01-02
I'm having the same issue.

What is the mount point for the ipod touch on 11.04? I can view the files on the ipod in nautilus and ideviceinfo can see the ipod. I can't get gtkpod, rhythmbox, or banshee to recognize that it's plugged in.

gtkpod might work if I knew the mount point.

This is my mount list with the ipod automatically mounted:
```

$ sudo mount
/dev/sda5 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda7 on /home type ext4 (rw,nosuid,nodev,commit=0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
```

If I right-click and unmount in nautilus, I get the exact same list. The open folder dialog in gtkpod doesn't show the ipod, but it's shown in nautilus and I can write to it.

---

### Post by fslezak on 2011-01-02
Ah.

I can't see the iPod in Nautilus, but ideviceinfo can see it.

---

### Post by earthpigg on 2011-01-02
Here's the long-term solution folks:

-Stop updating your iPod/iPhone/iPad.
-Continue to use the most recent versions of Ubuntu/Banshee/etc.
-It'll work itself out eventually. The more recently you updated your i___, the longer you will have to wait.
-If you are just buying an i___ device, understand that it may be a few months before it works with Ubuntu.


If you want the most up-to-date of both, then that is your choice. Understand that you are subjecting yourself to the cat/mouse game between Apple Corporation and volunteer Open Source hackers.

---

### Post by DaveBooth on 2011-03-02
Has anyone got their 4th Gen ipods to work yet, either in gtkpod or any other application?

---

### Post by donc786 on 2011-03-13
I have been able to use my ipod touch 4g with ios 4.2.1 in ubuntu 10.04 on one of my computers, but not another one. I still can't figure out why. I can't remember the exact steps for achieving this. I ran across the instructions when searching Google for i pod touch Linux. Some have said jail breaking is required. I found that jail breaking was unnecessary, although I have done so since being able to sync with Ubuntu 10.04 (used greenpios0n). Jail breaking allowed ssh, but didn't really make any difference as far as syncing with Ubuntu was concerned. As I recall I had to do something with usbmuxd, and libimobiledevice1, and iFuse permissions. I'll try to find the terminal commands I used when I can get to the other pc I am able to sync with.

---

### Post by donc786 on 2011-03-13
[Here]("http://www.libimobiledevice.org/") is a site relating to syncing your iphone/pod with Ubuntu. About halfway down the page there is a list of related packages that are useful.

---

