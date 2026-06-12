---
title: "Changing Live CD hostname"
date: 2011-02-17
forum: New to Ubuntu
---

### Post by Pas_sa on 2011-02-17
Hi guys,

I have a persistent live Ubuntu environment booting off a USB. I need to change the hostname but the usual method (editing /etc/hostname or something like that) does not work. On reboot, it is still "ubuntu".

How can I change the hostname of my live USB? I found some instructions in the manual but it was very confusing and seemed to be above what I actually needed to do.

---

### Post by Keiran230 on 2011-02-18
> **Pas_sa said:**
> editing /etc/hostname

You can edit the hostname on a full install via System->Administration->Networking or by editing **BOTH**
*/etc/hostname* and */etc/hosts*. It should work the same for a live USB, especially one that's persistent.

---

### Post by ezwrighter on 2011-02-23
I have the exact same problem!  

Used the easy usb creator on windows from pendrivelinux.com with ubuntu 10.10.   Edited /etc/hostname on the machine, rebooted, and now it's back to "unbuntu".  Tried multiple times with no success.

Probably should post this on pendrivelinux forums, but saw this thread and figured I would add in my frustration :-)

---

### Post by coffeecat on 2011-02-23
> **ezwrighter said:**
>    Edited /etc/hostname on the machine, rebooted, and now it's back to "unbuntu". 

> **Keiran230 said:**
> You can edit the hostname on a full install via System->Administration->Networking or by editing [SIZE=4]**BOTH**[/SIZE]
*/etc/hostname* and */etc/hosts*. It should work the same for a live USB, especially one that's persistent.

@ezwrighter, I've enlarged the critical word in the quote from Keiran230's post. Did you edit both?

---

### Post by Peacepunk on 2011-06-03
I confirm - changing [COLOR="Red"]BOTH[/COLOR] files by hand, and issuing the command '*sudo hostname <yourdesiredname>*' for good measure doesn't stay, keeps coming back as '@ubuntu' on a persistence-enabled pendrive.

Same applies for the /etc/init/tty[1-6].conf files BTW. 

This is the furthest and closest I've got, from user [[COLOR="Blue"]efflandt[/COLOR]]("http://ubuntuforums.org/member.php?u=937632") 

[[COLOR="Blue"]http://ubuntuforums.org/showpost.php?p=9664198&postcount=8[/COLOR]]("http://ubuntuforums.org/showpost.php?p=9664198&postcount=8")

> For a live/install iso the system boots before persistent data is mounted, so you might need to ***copy those /etc/hostname and /etc/hosts to the home directory of the default ubuntu user***, edit how you want them, then add these lines to .profile of ubuntu user:
[QUOTE]
sudo cp /home/ubuntu/hostname /etc/hostname
sudo cp /home/ubuntu/hosts /etc/hosts
[/QUOTE]

Makes sense... 

[COLOR="DarkRed"]The above solution **does set the name** - before you actually log in, and even in the .profile file of user 'ubuntu' when you log as another user.[/COLOR]

what does NOT work is to simply add 'hostname <yourname>' in the *.profile* file. Also, I only did with the /etc/hosname file, not the /etc/hosts file ;)

I still have that TTY problem, too: the consoles stays ubuntu@ubuntu, no way to change that at startup yet.

---

### Post by TheWeirdness666 on 2011-07-20
I've found the real fix. [https://help.ubuntu.com/community/LiveCDCustomization#Removing%20the%20%28Casper%29%20Autologin](https://help.ubuntu.com/community/LiveCDCustomization#Removing%20the%20%28Casper%29%20Autologin)

You need to follow the directions for extracting and editing the "casper/initrd.lz" file.  Once done, repackage the initrd.lz, and replace the existing initrd.lz with the new modified one.  You need to modify the file within the initrd.lz which is "etc/casper.conf".  Hope this helps!
:guitar:

---

### Post by TheeMahn2003 on 2012-02-26
This I suppose this is off topic, however I do understand what remastersys is attempting to do.  Every almost single build I have done starting from Edgy Eft on.  I have had to re-write all the things they change.  I have never personally used remaster's system to build one of my incarnations.  I have used reconstructor in the past as a dev.

Ubuntu has hard coded a ton of info into the O/S.  This is slowly diminishing & they finally agree that it is considered a bug.  I can do anything I want as far as building an O/S minus upgrading the kernel.  I do everything by hand.  I have found a few breadcrumbs in my journey to excellence.  casper filesystem involved across both initrd.lz, .disk and in /etc/casper.conf in the squashfs is the cause of the situation.  Learn, Learn, Learn ;)

They claim it is now history in percise.  I would not know it is too unstable to run currently.

---

