---
title: "Can I bypass the GNU GRUB boot menu"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by MauiWowee on 2011-02-22
I am running Ubuntu on a computer with a timer to collect data. Every once in a while the computer gets stuck on the following GNU GRUB boot menu:

[INDENT]_GNU GRUB version 1.98+20100802-5ubuntu3_
Ubuntu, with Linux 2.6.35-22-generic
Memory test (memtest86+)
Memory test (memtest+, serial console 115200)[/INDENT]

 and then it will wait for the user to make a selection. If the computer goes to this menu screen just once, then it every consecutive re-start it will go to the same menu screen until I retrieve the computer and select an option. I tried editing the grub file to disable the recovery mode menu entries thinking that would stop the menu from appearing, but it the menu still came up just w/o the recovery mode option.


Is there a way to reconfigure the GRUB in order to completely bypass this menu? 

Thank you for any help!
-Matt

I am using Ubuntu 10.10

---

### Post by Ben Page on 2011-02-23
If I understood correctly, you want to disable the GRUB menu at startup i.e. boot without any prompts, right?

To do this, download the startup manager

```
sudo apt-get install startup-manager
``` 

Then go to system > administration > startup manager
In the "Boot Options" tab under "Timeout" set the timeout seconds to 0 or something smaller like 1 or 2. And be sure to select the default operating system correctly, GRUB will boot to this selection from now on.

---

### Post by MauiWowee on 2011-02-23
Thanks Ben, I will give it a shot. What exactly does the 'startup-manager' do?

---

### Post by Hedgehog1 on 2011-02-24
> **MauiWowee said:**
> Thanks Ben, I will give it a shot. What exactly does the 'startup-manager' do?

Startup Manager is a friendly GUI to set the more common things folks want Grub to do.  You can achieve all the same changes using CLI (Terminal) - but if your needs are 'typical' (and yours are in this case) it saves you the trouble of remembering the grub commands and editing scripts.

:KS

---

### Post by MauiWowee on 2011-02-25
I tried using the start up manager. I tried adjusting those settings using 'sudo vi /etc/default/grub'.

I think I found a solution to my problem on this site:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:recordfail](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:recordfail)

Basically, it makes a record anytime there is a boot fail or a shut-down fail. Then when it powers back up the next time, and there is a 'recordfail' it doesn't perform a countdown before starting up the default OS but instead waits for the user.

I edited the file mentioned in the link and have been testing the computer by powering in on and off to see if it gets stuck on the GRUB boot menu screen again.

---

### Post by Dennistheawesome on 2013-04-03
> **Ben Page said:**
> If I understood correctly, you want to disable the GRUB menu at startup i.e. boot without any prompts, right?

To do this, download the startup manager

```
sudo apt-get install startup-manager
``` 

Then go to system > administration > startup manager
In the "Boot Options" tab under "Timeout" set the timeout seconds to 0 or something smaller like 1 or 2. And be sure to select the default operating system correctly, GRUB will boot to this selection from now on.

How would I get it back to boot into Linux?

---

### Post by Adler on 2013-11-21
MauiWowee,

Thanks for that! It did the trick of getting rid of my GRUB Menu on boot-up. I followed your link, and used 

> Open the file 00_header via     gksudo gedit /etc/grub.d/00_header
Look for  

  if [ ${recordfail} = 1 ]; then
     set timeout=-1
 else
    set timeout=${GRUB_TIMEOUT}
 fi

Change it to 

#if [ \${recordfail} = 1 ]; then
   #    set timeout=-1
   #else
       set timeout=${GRUB_TIMEOUT}
   #fi

Save the file and run 

      sudo update-grub

Thanks again!

Adler

---

### Post by philinux on 2013-11-21
Closed - Old thread.

---

