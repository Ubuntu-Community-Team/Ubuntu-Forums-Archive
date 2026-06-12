---
title: "trouble with wireless cards 8.04"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by ravelink69 on 2008-05-21
Im trying to install what i think is the right driver for my BCM94311MCG by doing this tutorial : [http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/)

everything seems to be going smoothly until i get down to step 5

here is what im doing :

```
sudo apt-get update
```
It updates with a bunch of lines of whatever its doing so i move on.
```

sudo apt-get install build-essential

```says that it is setting up the build-essential and then finishes.
```

sudo apt-get install linux-headers-`uname -r`

```says:```

Reading Package lists...Done
Building Dependency tree
Reading state information...Done
linux-headers-2.6.24-16-generic is already newest version.
0 upgraded, 0 newley installed, 0 to remove and 0 not upgraded.

```
(i obviously replace uname -r with the appropriate thing but im still new to ubuntu so i dont quite know what happened here but everything looks ok so i move on)

```
sudo ln -s /usr/src/linux-`uname -r`
```
again replacing the uname -r but this is where im confused because when i push enter it just goes to the next line with myname@myname-laptop:~$ like nothing happened, so i move onto the next line and i get the same thing...is this ok? it doesnt seem like its doing anything. 

if its ok ill move on but if something is suppose to happen and its not, what do i do. im running a fresh install of 8.04 the onlything i have done other than try this is install my nvidia graphics card. im running an HP Pavilion dv6000

Thanks in advance

---

### Post by Ayuthia on 2008-05-22
> **ravelink69 said:**
> 
```

sudo apt-get install linux-headers-`uname -r`

```says:```

Reading Package lists...Done
Building Dependency tree
Reading state information...Done
linux-headers-2.6.24-16-generic is already newest version.
0 upgraded, 0 newley installed, 0 to remove and 0 not upgraded.

```
This just means that the package is already installed.  linux-headers now is installed by default in Hardy.

> (i obviously replace uname -r with the appropriate thing but im still new to ubuntu so i dont quite know what happened here but everything looks ok so i move on)
You don't really have to do that.  The backticks "`" helps the system know that it needs to execute that command and replace the info with it.
> ```
sudo ln -s /usr/src/linux-`uname -r`
```

This looks like it is missing something.  Were you doing:
```
sudo ln -s /usr/src/linux-`uname -r` /usr/src/linux
```

If so and nothing comes back, it is ok.  That means that it was able to do what you asked.  If you do:
```
ls -l /usr/src
```
you should be able to see that /usr/src is now pointing to /usr/src/linux-`uname -r`

You can definitely go this route and try to compile NDISwrapper, but I think that the one in the live CD works also.  Just install ndiswrapper-common and ndiswrapper-utils-1.9.

If you are going to do this, make sure that you have the most up to date version.  1.49 does not compile in 8.04.

There is another thing to know.  In 8.04, the Linux native Broadcom drivers have changed to use b43 and ssb instead of bcm43xx.  You will need to also blacklist b43 in addition to bcm43xx (step 2).  That should cover it for you.

---

### Post by ravelink69 on 2008-05-22
sweet, i am headed to work but will try that tonight when i get home.

---

### Post by ravelink69 on 2008-05-22
> **Ayuthia said:**
> ...If you are going to do this, make sure that you have the most up to date version.  1.49 does not compile in 8.04.

...



What needs to be updated?

---

### Post by Ayuthia on 2008-05-22
> **ravelink69 said:**
> What needs to be updated?

If you are getting NDISwrapper from the NDISwrapper website ([http://ndiswrapper.sourceforge.net](http://ndiswrapper.sourceforge.net)), then make sure that you download 1.52 instead of 1.49.

---

### Post by Roel1963 on 2008-05-22
> **Ayuthia said:**
> If you are going to do this, make sure that you have the most up to date version.  1.49 does not compile in 8.04.

Sorry to hop in here, but are you sure 1.49 doesn't work in 8.04? Because I can't get MY wireless started in Hardy (works GREAT on Gutsy) and I was thinking about installing Hardy with an old ndiswrapper (1.43 or 1.49).

---

### Post by Ayuthia on 2008-05-22
> **Roel1963 said:**
> Sorry to hop in here, but are you sure 1.49 doesn't work in 8.04? Because I can't get MY wireless started in Hardy (works GREAT on Gutsy) and I was thinking about installing Hardy with an old ndiswrapper (1.43 or 1.49).
From what I can tell, you will have to make modifications to the Makefile to see if it will compile.  I have not played with it much, but I just know that it will not compile right off the bat.  It will give you a message of having to add EXTRA_CFLAGS.  It will then exit and not compile.

The 1.50 notes mention that it now provides 2.6.24 support.

If you have some knowledge about compiling, you can try.

---

### Post by ravelink69 on 2008-05-22
on this step
```
sudo vim /etc/modules
add this line “ndiswrapper” (without “”)

```

how do i save the file in terminal?

---

### Post by Ayuthia on 2008-05-22
> **ravelink69 said:**
> on this step
```
sudo vim /etc/modules
add this line “ndiswrapper” (without “”)

```

how do i save the file in terminal?
You will have to hold the Shift key and press z twice.

It might be easier to just do this at the Terminal:
```
echo ndiswrapper | sudo tee -a /etc/modules
```

vim is a hard editor to learn. :)

---

### Post by ravelink69 on 2008-05-22
ok thanks for that...rebooting now, lets see if it worked

---

### Post by ravelink69 on 2008-05-22
nope still no blue light :( this saddens me, i dont know what else to do...im going outta town tomorrow and the only connection i will have is the hotels wireless...

---

### Post by Ayuthia on 2008-05-22
> **ravelink69 said:**
> nope still no blue light :( this saddens me, i dont know what else to do...im going outta town tomorrow and the only connection i will have is the hotels wireless...

Do you know where you got your Windows driver?  Was it from the site that you posted earlier?  If so, we do have other driver options.

I have a dv6000 series also with the same card.  I am pretty certain that we should be able to get it up and running.

Have you tried the following:
```
sudo modprobe -r b43 ssb bcm43xx ndiswrapper
sudo modprobe ndiswrapper
```

That might be all you need.  If this works, there are some other steps that will be needed to make it permanent.

---

### Post by ravelink69 on 2008-05-22
wow your good, that turned on the blue light.

now i guess we need to do what you were saying to make it perminate. also is it possible to make it scan for access points?

i really appreciate your help.

---

### Post by ravelink69 on 2008-05-22
oh wow, even better, i figured out the whole finding all wireless access points.

---

### Post by Ayuthia on 2008-05-22
> **ravelink69 said:**
> oh wow, even better, i figured out the whole finding all wireless access points.

You should only have to add:
```
echo b43|sudo tee -a /etc/modprobe.d/blacklist
```

That should do it!  If not, just come back and we will see if other modules need to be blocked.

---

### Post by ravelink69 on 2008-05-22
i did that, then rebooted. the blue light did not come on at boot but i entered the two lines you posted earlier and got this:

```

sudo modprobe -r b43 ssb bcm43xx ndiswrapper

WARNING: /etc/modprobe.d/blacklist line 41: ignoring bad line starting with 'b43'

WARNING: /etc/modprobe.d/blacklist line 41: ignoring bad line starting with 'b43'

WARNING: /etc/modprobe.d/blacklist line 41: ignoring bad line starting with 'b43'

WARNING: /etc/modprobe.d/blacklist line 41: ignoring bad line starting with 'b43'

```

then

```

sudo modprobe ndiswrapper

WARNING: /etc/modprobe.d/blacklist line 41: ignoring bad line starting with 'b43'

```

but the blue light still came on and im able to connect wirelessly.


i have copied those 2 commands to a text editor and saved it to my desktop incase we cant get it fixed tonight.

but if you still have time to help...what should i do?

---

### Post by Ayuthia on 2008-05-22
> **ravelink69 said:**
> i did that, then rebooted. the blue light did not come on at boot but i entered the two lines you posted earlier and got this:

```

sudo modprobe -r b43 ssb bcm43xx ndiswrapper

WARNING: /etc/modprobe.d/blacklist line 41: ignoring bad line starting with 'b43'

WARNING: /etc/modprobe.d/blacklist line 41: ignoring bad line starting with 'b43'

WARNING: /etc/modprobe.d/blacklist line 41: ignoring bad line starting with 'b43'

WARNING: /etc/modprobe.d/blacklist line 41: ignoring bad line starting with 'b43'

```

then

```

sudo modprobe ndiswrapper

WARNING: /etc/modprobe.d/blacklist line 41: ignoring bad line starting with 'b43'

```

but the blue light still came on and im able to connect wirelessly.


i have copied those 2 commands to a text editor and saved it to my desktop incase we cant get it fixed tonight.

but if you still have time to help...what should i do?

Sorry, I messed up.  I meant to add blacklist b43 instead of b43.

What you need to do is go into an editor and add the word blacklist in front of b43:
```
gksu gedit /etc/modprobe.d/blacklist
```
This should get you into a GUI editor so that you can modify and save your changes.

---

### Post by ravelink69 on 2008-05-22
that gets rid of the error when typing in those 2 commands, but i still have to type those in after i boot the machine. is that what we are going for or are we still trying to make it permanent?

---

### Post by Ayuthia on 2008-05-22
> **ravelink69 said:**
> that gets rid of the error when typing in those 2 commands, but i still have to type those in after i boot the machine. is that what we are going for or are we still trying to make it permanent?So you are saying that the error is gone, but you still have to do the two modprobe commands to make it work.  Can you post the results of:
```
cat /etc/modprobe.d/blacklist|grep -i -e bcm43xx -e b43 -e ssb -e ndiswrapper
cat /etc/modules|grep -i -e bcm43xx -e b43 -e ssb -e ndiswrapper
```

We are missing something in the blacklisting or the loading of a module.

---

### Post by ravelink69 on 2008-05-22
first one gives this :
```

# replaced by b43 and ssb.
blacklist bcm43xx
blacklist b43

```

the second one is :
```

ndiswrapper
ndiswrapper

```

---

### Post by Ayuthia on 2008-05-22
> **ravelink69 said:**
> first one gives this :
```

# replaced by b43 and ssb.
blacklist bcm43xx
blacklist b43

```

the second one is :
```

ndiswrapper
ndiswrapper

```

The second ndiswrapper is not needed in /etc/modules.  You should remove it:
```
gksu gedit /etc/modules
```

Let's go ahead and blacklist ssb also:
[CODE]echo blacklist ssb|sudo tee -a /etc/modprobe.d/blacklist

---

### Post by ravelink69 on 2008-05-22
ok...sorry for the delay

i did that and rebooted, no blue light on reboot.

---

### Post by Ayuthia on 2008-05-22
> **ravelink69 said:**
> ok...sorry for the delay

i did that and rebooted, no blue light on reboot.

Do this:
```
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper
```

This will add additional code for b44 and ssb that is not needed, but it does the same thing as the modprobe statements.  I am not for sure why it is not taking without this.

---

### Post by ravelink69 on 2008-05-22
wow long code...

anyways here what came up...
```

#Hardy ssb/ndiswrapper workaround, added Thu May 22 22:28:00 CDT 2008
install ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;

```

rebooting now

---

### Post by ravelink69 on 2008-05-22
yay that did it, blue light upon startup and connected right up, at first it only connected at 60% and its right next to the wireless but it went up to 99% soon after.

i really appreciate your help, hopefully this can be helpful to others aswell.

---

### Post by Ayuthia on 2008-05-22
> **ravelink69 said:**
> yay that did it, blue light upon startup and connected right up, at first it only connected at 60% and its right next to the wireless but it went up to 99% soon after.

i really appreciate your help, hopefully this can be helpful to others aswell.

Glad to see it working!  Sorry it took so long.

---

