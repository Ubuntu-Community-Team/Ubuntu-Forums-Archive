---
title: "grub disappeared, AGAIN"
date: 2011-08-15
forum: New to Ubuntu
---

### Post by Buntu Bunny on 2011-08-15
This is my 2nd go-round with the same problem. It was first addressed (and successfully resolved)in this thread - [http://ubuntuforums.org/showthread.php?t=1609474&highlight=buntu+bunny](http://ubuntuforums.org/showthread.php?t=1609474&highlight=buntu+bunny)

I have a dual boot with windows 7 & lucid on my Dell Inspiron 540. The problem is, after exiting windows, grub is gone. When I boot the computer I get

[INDENT][I]No module name found
Aborted. Press any key to exit.[/I][/INDENT]
Then:

[INDENT][I]No boot device available
Strike the F1 key to retry boot
SATA0: Installed
SATA1: Installed
SATA2: None
SATA3: None[/I][/INDENT]
The last time I had this problem, I was advised to boot from my Ubuntu Live CD, and instructed how to recover grub (see previous thread). This worked successfully and I haven't used windows again, until today.

I retried to boot from my ubuntu live cd, it tries to load, then I get:

[INDENT]*unable to find a medium containing a live file system*[/INDENT]
There is a list of built in commandds under help, but I do not know what to do with these. 

Is it hopeless? Has McAfee (which apparently did not uninstall) completely destroyed my machine?

I'm at the public library, so if I do not respond to replies immediately, I will do so tomorrow. I only have about 40 minutes left this session. 

Thanks.

---

### Post by JC Cheloven on 2011-08-15
> **Buntu Bunny said:**
> I retried to boot from my ubuntu live cd, it tries to load, then I get:

[INDENT]*unable to find a medium containing a live file system*[/INDENT]
There is a list of built in commandds under help, but I do not know what to do with these. 


I think this is a different problem: you should be able to boot a live session despite what McAffe may have done to your HD. If the live CD tries to boot but don't "find a medium containing a live file system", this rather means that your cd is dirty, or damaged. 

Can you please try another boot medium (burn a new cd at low speed for example, or even better, make an usb boot pendrive if your bios can boot from that). 

EDIT: Oh, and don't dispair. It's only a pc, it will run whatever you'll feed it with; "hopeless" is only applicable to hardware-broken or very old ones :) In the worst case (if something inside win2 insists in breaking your system), downloading a vanilla OS from microsoft and reinstalling it with your license number, would fix it. In fact, I've found this a nice way to get rid of all the crap that comes with preinstalled win2 OSes !

---

### Post by kansasnoob on 2011-08-16
First of all, something I would no longer live without is this disc:

[http://www.bootproblems.com/super-grub2-disk/](http://www.bootproblems.com/super-grub2-disk/)

The download link is at the bottom of the page. As it says there, "Super GRUB2 Disk can only be used to boot a broken system, it cannot fix it directly." But I prefer to use only Ubuntu tools and packages to fix Ubuntu's grub2 anyway!

I've found the "Detect any OS" option to work very reliably. Expect it to be slow, like maybe even a couple of minutes slow booting. But it's a great tool to have tucked away just for when these unexpected things pop up :)

But your specific problem is likely this:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)

**[COLOR="Red"]Note however[/COLOR]** that I do not recommend going ahead with any of the prescribed "solutions" until you've investigated a bit further :)

In order to properly troubleshoot this problem it would be best to download and run the Boot Info Script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Then if you will post the RESULTS.txt output here we could look at that and try to come up with a sensible, permanent, and harmless, solution.

---

### Post by Buntu Bunny on 2011-08-17
OK, have just been able to get back to the library to check for replies, Thank you so much JC Cheloven and kansasnoob. 

I was finally able to get live cd to load (not sure how) and checked the disk, no errors. I was able to reinstall grub. This morning I had to go to windows again for Dell tech support. Again, lost grub. From terminal, I can mount the linux partition. From there, the problem begins. 

sudo mount /dev/sda5 /mnt
sudo chroot /mnt
sudo grub-install /dev/sda
sudo: unable to resolve host ubuntu
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?)
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules'
sudo grub-install --recheck /dev/sda
sudo: unable to resolve hoset ubuntu
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?)
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules'

I don't know what to do with this because it worked to reinstall grub twice before. 

In the meantime, I will definitely look into finding a more generic OS from Microsoft, good idea.

I will also take a look at the links you suggest Kansasnoob. They look very helpful and hopeful.

I'm at the library again, on limited computer time. I will get back on this to check for further responses and report my progress. 

Thank you!!

---

### Post by kansasnoob on 2011-08-18
This recent post may be helpful to you:

[http://ubuntuforums.org/showpost.php?p=11163493&postcount=8](http://ubuntuforums.org/showpost.php?p=11163493&postcount=8)

---

### Post by Buntu Bunny on 2011-08-18
Kansasnoob, I found the immediate answer at the sourceforge link you gave me. After mounting my linux partition, this worked... 

*sudo grub-install --recheck --root-directory=/mnt /dev/sda*

As you can imagine, this is a tremendous relief and I definitely need to investigate further with the other links you recommend. My more pressing problem now, is that I cannot get online. The network icon in the system tray says "no network devices available." However, that's another topic and needs another thread.

---

### Post by JC Cheloven on 2011-08-18
> **Buntu Bunny said:**
> In the meantime, I will definitely look into finding a more generic OS from Microsoft, good idea.

Probably needless to say, but you have to choose the exact windows version you've got a license for. 
Not that I specially like to give advice for that, though ;)

---

