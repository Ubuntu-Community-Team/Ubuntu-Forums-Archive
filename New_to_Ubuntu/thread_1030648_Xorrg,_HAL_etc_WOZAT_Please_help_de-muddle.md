---
title: "Xorrg, HAL etc WOZAT? Please help de-muddle"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by zipher on 2009-01-04
OK, so just when i think I'm starting to get the hang of this code malarkey, some trouble brews up.

Particularly. I'm trying to install a graphics tablet (UC=LOGIC WP5540U as it happens) Only, I cannot work out whether the 

xorg.conf

file that I've adjusted is actually the one being read by my system.
Meanwhile, I've been dancing a merry jig installing my graphics card, (GeForce 4 420 GO) along with accelerated graphics with Nvidia that I didn't even know existed until trying to install the tablet.

What typically happens is, that I edit the xorg.conf file according to ubuntu wiki 'Wizardpen' guide and upon restarting my screen goes blank.

I think, that Xserver then sends a default, time-earmarked replacement such as xorg.conf.200903012359, and this is then used to 'restore functionality'

So, in 

/etc/X11/ 

I've got several config files gathering dust 
THEN

I decide to try using wizardpen-0-7-0-alpha1, and next thing I'm told that the "Hardware Abstraction Layer" is the "new" xorg.conf platform or something.
So in effect I have several zipped, unzipped, semi-configured and semi-calibrated versions of a driver but only 2 hints of possible functionality.:popcorn:

Meanwhile reading all this stuff about Nvidia 'woes' I'm wondering how to achieve the following:

1)get rid of all extraneous xorg files
2)delete all scraps and packages of the wizardpen driver
3)Install the working wizardpen driver and calibrate it so the tablet works, for example in Gimp, and
4)Do this without de-stabilising my lovely Nvidia display.

Please can someone:KS guide, or point me in the right direction??

Many thanks in advance.

Jon:confused::o

---

### Post by stderr on 2009-01-05
Hi Zipher

Are you running Intrepid Ibex? The Xorg arangement changed somewhat after Hardy to include more auto configuration at boot time (and yes this is largely done by HAL I assume). Consequently, there's much less configuration needed in the xorg.conf

As for which xorg.conf is being used... it should always be /etc/X11/xorg.conf AFAIK. You should be able to remove any other xorg.conf.whatevers in the /etc/X11 folder. It's always nice to leave the working ones, appropriately named, e.g. xorg.conf.20090104-1screen-ati-ok or something, "in case".

Are you installing wizardpen from the ubuntu repositories, or are you downloading them from the web and compiling/installing a deb/rpm? 

I'll try to have a look over the ubuntu article you referred to tomorrow. Now, it's time to sleep :)

---

### Post by zipher on 2009-01-05
Hi stderr,

Thanks for looking at this mess.

1)Yes I'm running Intrepid 8.10
2)I've tried installing wizardpen drivers from tarballs and unziping / compiling, IOW deb/rpm packages 

Currently all files and directories with the string 'wizardpen' in the title have been deleted. Same treatment for pseudo-duplicate xconfig files. I know this probably sounds rash, but the rationale is:

Trying to understand exactly which 'bits' make the computer 'go'

So I'm basically starting afresh.:)

---

### Post by stderr on 2009-01-05
Right, to compile things, you'll most likely need *at least* build-essential installed (and probably more):

```
sudo apt-get install build-essential
```

Could you provide the URLs of the drivers you tried installing so we can see (and possibly test) exactly what you're trying to install?

Although, I've located [this]("http://digitalbluewave.blogspot.com/2008/10/genius-wizardpen-with-intrepid-ibex.html") guide for Intrepid Ibex which may well prove more useful than the ones on ubuntu wiki, as ubuntu wiki says you should use that guide for 8.10, as opposed to the guide on the wiki.

If you follow that guide instead, I would advise to first check that no wizardpen drivers are in the following location:

```
ls -l /usr/lib/xorg/modules/input
```

and to try to follow the instructions on building from source. Install the packages it mentions, and if ./configure or make give any errors, post them here.

The bit on configuring HAL should work a lot better than the xorg method, hopefully :) Let us know how you get on

---

