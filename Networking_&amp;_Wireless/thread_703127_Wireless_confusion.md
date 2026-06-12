---
title: "Wireless confusion"
date: 2008-02-21
forum: Networking &amp; Wireless
---

### Post by Bucky Ball on 2008-02-21
Laptop: HP DV6305us, AMD Turion 64x2 TL-50 1.60 GHz, 2Gb RAM, Broadcom 802.11b/g WLAN, NVIDIA GeForce Go 6150 (Vista Basic/Ubuntu Studio)

Hi all. Hoping someone can help me out with this.

Bought a D-Link Wireless router awhile ago and my laptop was connecting to network/internet okay, but not a brilliant signal. Maybe I should have stuck to the theory 'If it ain't broke, don't fix it', but in this case, I thought I could probably speed it up by wrapping the windows driver for my wireless card with ndiswrapper.

With the help of the excellent Ubuntu forums, I was quite proud when I managed to wrap the driver with ndiswrapper. iwconfig was showing everything as advised on the forum etc (and also ifconfig? from memory), so I went ahead and put ndiswrapper into /etc/modules. (Just reading about the Broadcom NetExtreme series driver *written for Linux* ... yay!)

When I rebooted machine, it got about halfway through the working bar on the Ubuntu Studio loading/splash screen, then fade to black ... well, not quite, but it appears to be going for eth1, not eth0 which is where the wireless is set up.

I did manage to get to my system through booting into recovery, although what goes on there is unpredictable also. I thought I'd try removing the ndiswrapper file from the /etc/modules directory so logged in as root, but have been busy so don't remember root password! If I type passwd at the prompt that will let me change it, yes?

Some of the error messages I have seen at various stages:

No eth1 loaded at initialization
(This is okay as I am trying to get to eth0)

ADDRCONF(NETDEV_UP): eth1: link is not ready
(also okay, I guess - unless I want to use the hardwire cable)

IRQ 7: nobody cared (try booting with 'irqpoll' option)
?

Turning off IO-APIC fast mode
(I had actually added 'noapic' to kernel line at boot)

So, haven't seen my KDE desktop in quite awhile and I'm pining!!! (Desktop also has minor problem which I'll post elsewhere so Ubuntu-less on that, too). :(

I am pretty new at this and haven't had time to tackle this problem for a couple of weeks so is a bit hazy and slowly remembering what I did back to try and resolve the problem back then, so apologies for that.

If I sound like I know anything at all about this, it is gleaned from these excellent forums which I thank the whole community for. Wonderful Evolution! :KS (I started dual booting both my machines around xmas and haven't needed to post even though I've had a million problems along the way and have been a member for awhile - eventually I found the answers).  :)

Any advice would be greatly appreciated.

---

### Post by Bucky Ball on 2008-02-21
... just adding to that last post.

I hit control/alt/delete when it got to the part in the splash screen where things normally crash, and it made it through to the end! I ended up with a dodgy looking screen telling me 'Can't load GDM' (which I think is Gnome?). I then hit control/alt/1 (just the number), was trying anything, and it took me to a prompt and gave me this:

HOME login: ****
Password:

... both of which I filled in. And yes, I do have the right password, because I tried another and was told it was wrong! The correct one draws this response:

No directory, logging in with HOME=/
-bash: cannot create temp file for here document: Read-only file system

Which I imagine means HOME directory = my root directory. Which makes me wonder why things are suddenly read-only! If I could change that then I might be able to fix the problem. 

So I log in as root@home and open /etc and open modules in nano. Remove what I think to be the culprit, the ndiswrapper entry, but try to save changes and it won't let me - read-only file! I will hunt for how I might change these permissions. Is this actually to do with the ndiswrapper, or has that created other problems?

My laptop had been dual-booting Vista and Ubuntu Studio like a dream since just after christmas and I had no idea moving ndiswrapper into /etc/modules was going to create such chaos. That's when it started but some of these problems seem unrelated, so as a newb, bamboozled and possibly overlooking something obvious. :confused:

---

### Post by Bucky Ball on 2008-02-22
Laptop: HP DV6305us, AMD Turion 64 x2 TL-50 1.60 GHz, 2Gb RAM, Broadcom 802.11b/g WLAN, Optiarc DVD, NVIDIA GeForce Go 6150 (Vista Basic/Ubuntu Studio)

Okay,this is where I'm currently up to after spending some more(!) hours on this problem.

Managed to get to root@HOME and into my directories and files, but some odd things are happening. 

*
HOME login: user
Password:

No directory, logging in with HOME=/
bash: cannot create the temp file for the here document. Read-only file system

user@HOME:~#
*

Now, from here, I can get to my files. I can even sudo su and log in as root@HOME:~#. But when I try to go into nano to change any files, as you can imagine from what I mentioned above, I can't write anything to the file or directory. Read-only. This prevents me from removing ndiswrapper from /etc/modules, which is when the problems started to occur - after I put it in there and rebooted.

Here are a few other details:

I input:

*
ndiswrapper -i bcmwl6.inf
Driver already installed.
*

bcmwl6 is the driver for my Broadcom wireless card. I then try this:

*
iwconfig
lo       no wireless connection
eth1  no wireless connection
*

?

I also get this message at regular intervals:

irq7: nobody cared (try booting with "irqpoll" option)

I tried adding 'irqpoll' to the kernel line at the grub menu then boot. No different. & this ...

lp: driver loaded but no device found
lo: Disabled privacy extensions
ADDCONF(NETDEV_UP): eth1: link is not ready

Hope I don't seem like I am banging on, but figure I should try and provide the latest details of where I've gotten to in case anyone eventually gets to this thread.

Still battling but clutching at straws at this point ... here's hoping. :)

---

### Post by Bucky Ball on 2008-02-23
Well, don't seem to be getting a lot of response, here. Still scouring for some solutions. I would probably have this fixed by now except for the fact that I have a Read-only disk and can't change any permissions or files, root or not. Really don't know what has gone on here. About to start uni and instead of showing off my sweet Vista/Linux laptop and making a few converts, it's back to the tedium of windows for the rest of the year (really don't have much time to spend on this during the year - especially not the month and a half I have spent trying to get this happening and now can't get Ubuntu running on desktop or lappy). I've learnt a lot but obviously not enough.

Here's where I am at and pray to the heavens someone can help (although I will persist but need to quit and set up my systems the way they are going to be in a few days). Who knows, maybe I'll have a eureka moment.


ndiswrapper -l
bcmwl6: driver installed
device (14E4:4311) present (alternate driver: bcm43xx)

I would blacklist the alternate driver if the permissions would let me.


rrmod ndiswrapper
ERROR: module ndiswrapper in use

Red light on the machine indicates no wireless. I guess I could post another million error messages here but imagine they are all pointing to one place anyhow. One good thing is, as I say, haven't been able to change much so must still be the original problem, whatever it is. Would try replacing driver but again, won't let me.

Refresh: I ndiswrapper-ed the bcmwl6 driver for my wireless card. iwconfig and ifconfig showed me all was present and correct. Reboot and the result is can't get into Ubuntu, crashes halfway through loading and I eventually get to a messy screen telling me can't load gdm GUI. I can then get to a prompt:

HOME login: *****
Password

No directory, logging in with HOME=/
-bash: cannot create temp file for here document: Read-only file system.


Strange thing is, all r/w options seem to be correct when I check. I also get the 'IRQ 7: nobody cared' error often.


In fstab:

/dev/sda6     /     default: error-remount ro 0


I read somewhere this can happen if the disk has been unmounted incorrectly.

Any further required information happily provided. In the meantime, I better get on with my life for awhile and get back to this later. Fingers so crossed I'm cramping up!

(ps: would just re-install but have done that a million times, but more importantly, as this install was up and running fine for about 3 weeks before this happened, it is tweaked and has Skype working and also my D-Link router's printserver, both thanks to the forums :). Don't really want to do all that again. Plus it is a hybrid with KDE I have grown fond of ... but if the bottom line is ...)

---

### Post by Bucky Ball on 2008-02-25
Well I seems to be flying solo here, but I am going to keep it going just in case this thread is of use to anyone else.

Okay. Original problem - added the line ´ndiswrapper´ to /etc/modules file. Rebooted and loading crashes and I wind up at a prompt, but my Ubuntu partition has become read-only, so can´t take that line out of modules to see if that fixes the problem.

Solution: to make my Ubuntu partition (sda6) read/write again, at the prompt I used this -

mount -o remount,rw /dev/sda6

(Note, replace sda6 with the hard drive or partition you are trying to ´unlock´.)
Vóila! I´m in!. So I remove the line ´ndiswrapper´ from /etc/modules, reboot and I am now typing this on my sadly missed but still as beautiful as ever hybrid Ubuntu Studio, KDE desktop open source wonder laptop. It lives!

Now I need to get back to the drawing board on unistalling ndiswrapper and installing the correct driver, which I think could have been a problem anyhows (bcmwl6, not bcmwl5 - this new one seems to tell me that Pv6 router not available, and it isn´t, only Pv4 so will try with bcmwl5 this time).

Just one thing if there is anybody out there reading this by now and they have any idea. 
Which is the way to go, ndiswrapper or fwcutter for my Broadcom wireless card? (it is of the 43** flavour). Here&#347; hoping. 

With the help of the forum and community, the read-only problem fixed , so, as usual, many thanks to all once again. :)

---

