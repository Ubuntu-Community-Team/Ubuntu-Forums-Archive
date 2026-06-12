---
title: "Error upgrading 10.10 to 11.04 via update manager"
date: 2011-05-03
forum: New to Ubuntu
---

### Post by Inphernal on 2011-05-03
Hi all,
I'm trying to upgrade 10.10 64bit to 11.04 on my laptop. However, several minutes into the "setting new software channels" (*Calculating the changes*) step, a window pops up saying:

```
Could not calculate the upgrade

An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.
```

Can anyone help?

---

### Post by THE CARTER on 2011-05-03
You might want to upgrade from a live usb drive or a live cd. It takes a lot less time and usually has less errors.

That's what I had to do at least.

You can download the disk image at ubuntu.com. They provide a step by step way to upgrade easily.

---

### Post by andrewthomas on 2011-05-03
> **Inphernal said:**
> Hi all,
I'm trying to upgrade 10.10 64bit to 11.04 on my laptop. However, several minutes into the "setting new software channels" (*Calculating the changes*) step, a window pops up saying:
 
```
Could not calculate the upgrade
 
An unresolvable problem occurred while calculating the upgrade:
E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
 
```
 
Can anyone help?
Try using aptitude, it is better at resolving such problems.
 
First install aptitude if you don't have it.
```
 
sudo apt-get update && sudo apt-get install aptitude

```
then change your sources over from maverick to natty
```
sudo sed -i 's/maverick/natty/g' /etc/apt/sources.list

```then upgrade
```
 
sudo aptitude update && sudo aptitude dist-upgrade
 

```

---

### Post by Inphernal on 2011-05-03
> **andrewthomas said:**
> Try using aptitude, it is better at resolving such problems.
 
First install aptitude if you don't have it.
```
 
sudo apt-get update && sudo apt-get install aptitude

```then change your sources over from maverick to natty
```
sudo sed -i 's/maverick/natty/g' /etc/apt/sources.list

```then upgrade
```
 
sudo aptitude update && sudo aptitude dist-upgrade
 

```

I did this, and it all went fine. But now when I try to launch Ubuntu, all I get is a black screen. GRUB loads (looks different now; smallerfont and "previous linux versions" appears), but neither the new kernel nor the one from the previous menu work

---

### Post by andrewthomas on 2011-05-03
You aren't using any restricted video drivers, are you?

---

### Post by Inphernal on 2011-05-03
> **andrewthomas said:**
> You aren't using any restricted video drivers, are you?

I don't think so, I don't remember ever changing them from what 10.10 set up initially.
Was using edgers PPA, is that it?

---

### Post by andrewthomas on 2011-05-03
When using the xorg-edgers ppa, you should purge the ppa before doing the update, then you can reenable them after the update. 

[QUOTE=https://launchpad.net/~xorg-edgers/+archive/ppa]*IMPORTANT NOTICE* - If you are upgrading from one release to another and are using this PPA, be sure to install ppa-purge and use it to downgrade all of this PPA's packages before the upgrade or you will have a broken system.[/QUOTE]

[https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

---

### Post by Inphernal on 2011-05-03
> **andrewthomas said:**
> When using the xorg-edgers ppa, you should purge the ppa before doing the update, then you can reenable them after the update. 



[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")

Thank you for the advice. How do I do this not being able to access the Ubuntu desktop?

---

### Post by andrewthomas on 2011-05-03
You can <CTL>+<ALT>+<F2> to get to a console prompt

```
sudo ppa-purge ppa:xorg-edgers
```Should do the trick.  

But, it won't hurt to :
```
sudo apt-get update && sudo apt-get upgrade
``````
sudo reboot
```

---

### Post by Inphernal on 2011-05-04
> **andrewthomas said:**
> You can <CTL>+<ALT>+<F2> to get to a console prompt

```
sudo ppa-purge ppa:xorg-edgers/ppa
```Should do the trick.  

But, it won't hurt to :
```
sudo apt-get update && sudo apt-get upgrade
``````
sudo reboot
```

Pressing those keys does not open the console.
Launching the (recovery) kernel worked and I did all that through the root option in that.
For the first part: not found.
The second two seemingly worked fine (though a couple 404 errors at the end of update) but did not fix the problem.
I get the Ubuntu loading screen and after just a black screen.

---

### Post by andrewthomas on 2011-05-04
> **Inphernal said:**
> 
For the first part: not found.

Then install it

```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:xorg-edgers
```

---

### Post by Inphernal on 2011-06-01
> **andrewthomas said:**
> Then install it

```
sudo apt-get install ppa-purge
sudo ppa-purge ppa:xorg-edgers
```

Did this still get error:

```
W: failed to fetch http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu/dists/mavericks/main/sources/Sources 404 not found
W: failed to fetch  http://ppa.launchpad.net/lorenzo-carbonell/atareao/ubuntu/dists/mavericks/main/binary-amd64/Packages  404 not found
e: some index files failed to download
```

---

### Post by Inphernal on 2011-06-11
Bump for help

Tried to remove the lorenzo-carbonell ppa with ppa-purge and dropped my laptop off of the bed... Now I can't get into recovery mode, but windows works fine and regular ubuntu still does the loading screen then black screen thing >.<

---

### Post by stoneage on 2011-06-11
Try booting with the 'nomodeset' option.

If you can get to the grub menu, select the kernel, press E to edit and replace 'quiet splash' with nomodeset, then CTRL+X to continue the boot.

You should be able to install graphic drivers once you get logged in.

More info:-
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by Inphernal on 2011-06-11
> **stoneage said:**
> Try booting with the 'nomodeset' option.

If you can get to the grub menu, select the kernel, press E to edit and replace 'quiet splash' with nomodeset, then CTRL+X to continue the boot.

You should be able to install graphic drivers once you get logged in.

More info:-
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

Thank you for the advice.
I did this and it stops at
```
CHECKING BATTERY STATE                                                                             OK
```

---

