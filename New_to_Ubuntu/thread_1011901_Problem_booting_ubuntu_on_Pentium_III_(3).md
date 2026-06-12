---
title: "Problem booting ubuntu on Pentium III (3)"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by ubfu on 2008-12-15
Ubuntu 8.04
Pentium III 667x5.0
128mb ram
20GB hard disk 
Window 98

I plan to boot ubuntu on a pentium 3 but I myself fail to since I can't find any option at bios to set the cd rom to boot first.

So I inserted the disc and run it using window 98.Once it run and select not able to boot manually.It'll then installing something which I have option to choose ubuntu or window.

Once I reboot , under the option , I choose ubuntu.It said that "assume I have a ACHI" what is that actually?.
Now it takes like ages to load.I had waited 2 hours but nothing shows up.At the first , it show a list of loaded file [Ok] which take almost 1 hour.Then it just gone to a black screen with dash at the top left of the LCD screen.Keep on waiting and still no sign of a ubuntu showing up.

What would be the problem ? :confused:

---

### Post by snowpine on 2008-12-15
Hi Ubfu,
Unfortunately, the minimum ram for Ubuntu is 384mb. I would suggest a ram upgrade, installing Xubuntu using the alternate CD, or better yet, a distro designed for older hardware such as Puppy Linux. Good luck!

---

### Post by nandemonai on 2008-12-15
AHCI -> [http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface](http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface)

I'm thinking though your main problem is amount of RAM. If your trying to boot the gnome gui your probably going to be out of luck.

Minimum requirement is 256mb.

---

### Post by ubfu on 2008-12-15
Sorry for the trouble opening a post.I went and search come out this thread similar with mine.
[http://ubuntuforums.org/showthread.php?t=1009957](http://ubuntuforums.org/showthread.php?t=1009957)

Seems like ubuntu need higher ram.
After reading other post about pentium 3 , they suggest using puppy linux.The reason I choose to try on ubuntu is because the pentium 3 machine having problem with the network card.I wanted to test whether the network card still functioning.

Which light linux distro able to go online using ADSL LAN cable on a router ? which it's linksys and able to enter to the router config 192.168.1.1 ?

Sorry , i don't know much about this.Learning now . Thank you :)

---

### Post by snowpine on 2008-12-15
Puppy has very good hardware detection, especially for older computers. Some might say better than Ubuntu. :) I would recommend searching for your specific network card model number over on the Puppy forums.

ps Puppy is designed to run as a Live CD, so you can boot it up and test your network card without actually installing or making any changes to your computer.

---

### Post by handydan918 on 2008-12-15
> **ubfu said:**
> 

Which light linux distro able to go online using ADSL LAN cable on a router ? which it's linksys and able to enter to the router config 192.168.1.1 ?

Sorry , i don't know much about this.Learning now . Thank you :)
Any distro should be able to "just work" with this setup. Puppy has (or had!) a really nice wizard to config net connections. Give it a shot.

---

### Post by ubfu on 2008-12-15
> **snowpine said:**
> Puppy has very good hardware detection, especially for older computers. Some might say better than Ubuntu. :) I would recommend searching for your specific network card model number over on the Puppy forums.

ps Puppy is designed to run as a Live CD, so you can boot it up and test your network card without actually installing or making any changes to your computer.

Thanks how do I find the network card ? Using window 98.Sorry again , i don't know how to view hardware model.

Btw , since I had install a grub ( ubuntu boot loader) , will it conflict with puppy linux ?

---

### Post by philinux on 2008-12-15
> **nandemonai said:**
> AHCI -> [http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface](http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface)

I'm thinking though your main problem is amount of RAM. If your trying to boot the gnome gui your probably going to be out of luck.

Minimum requirement is 256mb.

Thats the minimum to run it once installed, the live cd needs minimum 384 to run.

---

### Post by snowpine on 2008-12-15
> **ubfu said:**
> Thanks how do I find the network card ? Using window 98.Sorry again , i don't know how to view hardware model.

Btw , since I had install a grub ( ubuntu boot loader) , will it conflict with puppy linux ?

If you are running Puppy from a Live CD, the Grub on your hard drive makes no difference at all.

However you mentioned your CD drive has problems. In that case, you might want to try a "frugal install" of Puppy (though again I think your low ram may be an issue): [http://puppylinux.org/wiki/how-tos/general/frugalvsfullinstall](http://puppylinux.org/wiki/how-tos/general/frugalvsfullinstall)

---

### Post by ubfu on 2008-12-15
> **snowpine said:**
> If you are running Puppy from a Live CD, the Grub on your hard drive makes no difference at all.

However you mentioned your CD drive has problems. In that case, you might want to try a "frugal install" of Puppy (though again I think your low ram may be an issue): [http://puppylinux.org/wiki/how-tos/general/frugalvsfullinstall](http://puppylinux.org/wiki/how-tos/general/frugalvsfullinstall)

Yeh , I mean when I can't set at bios to boot orderly booting first on a cd drive.I choose to install ubuntu (boot loader)

Once I reboot the PC , it'll show 2 option with a 30 sec count down time.
Window
Ubuntu

So if i went and try puppy linux , will it able to boot on a cd drive ?

Saw the Full install.The problem is I still wanted to retain the my window 98.If install puppy fully  , it'll delete my window 98

---

### Post by snowpine on 2008-12-15
> **ubfu said:**
> So if i went and try puppy linux , will it able to boot on a cd drive ?

Saw the Full install.The problem is I still wanted to retain the my window 98.If install puppy fully  , it'll delete my window 98

A Puppy frugal install will not destroy your windows install at all. All you need to do is copy a few files to your C drive and then add some lines to your Grub. I am sorry but I am not really a Puppy user, more of an Ubuntu guy. :) I tried a frugal install of Puppy once and it was pretty easy, but I honestly don't remember the steps well enough to walk you through it. You will get better Puppy support over on their forums.

---

### Post by cmnorton on 2008-12-15
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

I would try the "alternate CD" installation, or try a text mode install. An Ubuntu installation should not take as long as you indicate.

---

### Post by ubfu on 2008-12-16
But it really takes that much of time loading those driver with an [Ok] sign.
About command line , how do I keep my window 98 or installing without interfering my other window ? moving files to other partition and install xbuntu ?

---

### Post by ubfu on 2008-12-16
I need a bit of help here.
I uninstall the grub and put in puppy linux.But the problem is the pc doesn't read cd drive first.It just load the window 98 even though I had a cd at the cd rom.Tried even on knoppix live cd still the same.

How to set window 98 boot loader to load them ? I went to BIOS setting but not able to select the cd rom to boot first.

---

### Post by Keen101 on 2008-12-16
That's not very much ram. Even for a pIII.

---

### Post by ubfu on 2008-12-16
I know about that , but the problem I am facing now is not able to set the cd rom to read first in a order.

Like before , even I insert the ubuntu but it doesn't read it on the cd rom.I have to manually install grup boot loader to select ubuntu.
Now I'd like to know to set cd rom to read first before the hard disk or modified the boot loader to let it read the cd rom .

---

### Post by nandemonai on 2008-12-16
> **philinux said:**
> Thats the minimum to run it once installed, the live cd needs minimum 384 to run.

I'd wondered about that cause I've seen conflicting numbers. Cheers for clarifying. ;)

---

### Post by ubfu on 2008-12-16
I know.

**Can someone just tell me how to set it the booting to read on cd rom ?**

---

### Post by snowpine on 2008-12-16
The option should appear in your bios menu when you press one of the F keys (depends on the manufacturer) at startup.

If not, try checking the manufacturer's webpage to see if there are any bios updates available for your computer.

Some older computers simply don't have that capability...

---

### Post by ubfu on 2008-12-16
I press del at the start up when showing the processor and ram speed.

F keys ? Lets say if the bios doesn't allow cd rom booting or only floppy disk booting.What should I do ? any floppy booting program ?

---

### Post by ubfu on 2008-12-16
I had deleted the wubi thing that install on window 98 but when I start my pc , it still display Ubuntu.
**How do I remove it ?**

---

