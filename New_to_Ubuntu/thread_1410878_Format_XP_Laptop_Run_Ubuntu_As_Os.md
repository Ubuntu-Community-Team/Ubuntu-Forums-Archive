---
title: "Format XP Laptop Run Ubuntu As Os"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by AlistairD on 2010-02-19
I have an old laptop that has a crappy incomplete reinstall of XP and no  internet access. I want to run only Ubuntu on the laptop. Can I  download Ubuntu to a external hd on another computer and boot it up to  install on the laptop through usb?

---

### Post by undecim on 2010-02-19
I'm guessing there is no working CD drive on this laptop?

You should be able to use unetbootin from another Windows or Linux machine to make any USB drive (hard drive or thumb drive) into a live USB (just like a live CD, but through usb)

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Anuovis on 2010-02-19
EDIT: nevermind, you probably do not have the cd-rom drive

---

### Post by AlistairD on 2010-02-19
Yes the CD drive is working, is that a better option?

---

### Post by undecim on 2010-02-19
> **AlistairD said:**
> Yes the CD drive is working, is that a better option?

It's usually easier. Either method will install Ubuntu the same way, but if you would rather not (or cannot) burn a CD, the USB drive is an excellent alternative.

---

### Post by amsterdamharu on 2010-02-19
If you cannot boot off usb you can copy the iso and unetbootin to the windows partition of the laptop.

Re-size the windows partition in windows (do not break windows). Later you can use the windows partition as your home dir, ubuntu only needs about 10G and the amount of memory for swap.

Run unetbootin and show it where the iso is, it will extract the iso on your windows partition and when it's done tells you to reboot.

When you reboot the cd will run off your hard disk and you can install using the free space, when everything works (make sure it does for a couple of days) you can reclaim the windows partition and use it as your home dir.

---

### Post by Anuovis on 2010-02-19
> **AlistairD said:**
> Yes the CD drive is working, is that a better option?

Why not just burn the CD and run the simple Ubuntu install then? It formats your HD automatically. If Ubuntu is the only system you want to have, there is no simpler way of doing this.

Although, are you sure you want to get rid of Windows XP? Eithet I can not understand your problem, or you are very inexperienced with Ubuntu. Not that I am any different, so sorry if I misunderstood something.

---

### Post by AlistairD on 2010-02-19
Ok so if I just burn the latest CD (after formatting my C:\?) I insert it and follow the prompts? 

I am not very experienced with Ubuntu (or computers for that matter) but I have a working desktop with Win7 that is my main comp so if I screw up the laptop its no biggie as I have backups already, I want to run Ubuntu on my laptop as a project of sorts to learn a bit more and may run XP through a VM. 

I just get the feeling that in the not too distant future us noobs will represent a big chunk of Linux users when it becomes super user friendly.

---

### Post by audiomick on 2010-02-19
Hi.
You don't even need to format before you start. The installer will take care of that.
have a look at this,
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall),
particularly this link
 [BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto"). 
from there, with particular attention to the bit about the md5sum.

the things that can trip you up are
that your computer isn't set to look at the CD drive during boot - needs to be set in BIOS
that the CD is corrupted - do the md5sum check before you burn it, burn it at the slowest possible speed, let the CD check itself using the "check CD option in the CD boot menu

It is a good idea, once you are confident that the CD is good, to boot from it using the "try without changing" option from the CD boot menu. This will boot you into the "live environment", i.e. the OS is loaded into the RAM and runs from there. This will show you if the laptop runs well with Ubuntu before you install it.

---

### Post by AlistairD on 2010-02-19
Thank you so much AudioMick

---

### Post by AlistairD on 2010-02-19
Ok I've verified the md5SUM in the Win app and it checks out and I see that you just right click burn in Win7 so I'm all set. ty everyone for your time.

---

### Post by amsterdamharu on 2010-02-20
Noooo, you don't know if Ubuntu is going to run well on your laptop, if you have enough space on your harddisk you should have made a partition in windows. Keep windows in case Ubuntu does not work well and you want to try another distro.

[https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions)

---

### Post by AlistairD on 2010-02-20
I just booted it off the cd, it runs fine but I think I either have a graphics card issue or the fan etc is all dirty as its running really hot.

---

### Post by amsterdamharu on 2010-02-20
This is not the first time I read about the fan, never seen a solution though. It seems that 9.10 is the Vista for ubuntu, it might run great on most peoples computer but seeing the amount of posts about it it doesn't on a great many others.

You can try version 8.04, called hardy. This is the long term support version. Later this year the long term support version 10 will be out, I am using it now on my laptop and it runs fine.

When you plan to install I'd advice you to get the alternate install, this is non graphic but at least it works.

[http://releases.ubuntu.com/hardy/ubuntu-8.04.4-alternate-i386.iso](http://releases.ubuntu.com/hardy/ubuntu-8.04.4-alternate-i386.iso)

---

### Post by AlistairD on 2010-02-20
Actually it was running hot for the last few days in XP before I booted Ubuntu. The NVidia card has been rplaced 3 times by Dell. Previously I was running Ubuntu through wubi and it was fine. I don't think it's an Ubuntu thing although I did try to install a driver in wubi last week that failed and I just deleted wubi and reinstalled because I was unsure.

---

### Post by wilee-nilee on 2010-02-20
There is a dell fan control in synaptic part of gkrellm called i8kutils at least thats the package your looking for. Follow this installation link to the forth, gkrellm controls the temp fan change and other utilities. If you want it to start automatically you can just put gkrellm in the startup addons in system-preferences-startup manager.
[http://ubuntuforums.org/showthread.php?p=5275415#post5275415](http://ubuntuforums.org/showthread.php?p=5275415#post5275415)

This is for a install I don't think it will work with a live cd.

---

### Post by 3rdalbum on 2010-02-20
> **amsterdamharu said:**
> This is not the first time I read about the fan, never seen a solution though. It seems that 9.10 is the Vista for ubuntu, it might run great on most peoples computer but seeing the amount of posts about it it doesn't on a great many others.

You can try version 8.04, called hardy. This is the long term support version. Later this year the long term support version 10 will be out, I am using it now on my laptop and it runs fine.

Ubuntu 10.04 is based on 9.10, so your advice is quite conflictory.

---

### Post by HermanAB on 2010-02-20
Howdy,

"us noobs will represent a big chunk of Linux users when it becomes super user friendly."

Actually, Linux is already super user friendly - the problem is that Ubuntu isn't - it is sort of intermediate to hard.

The super friendly distributions are:
Puppy Linux - Super user friendly to the point of being almost childish.  It is especially geared towards older hardware and older/younger users.  It has the feel of a grandpa/grandchild system.

Mandriva Linux - Almost a clone of Windows 2003 Server and has wizards for *everything* (Actually, Win2003 Server is almost a clone of Mandriva, since Mandriva is older!).  You can run a complex Mandriva server or desktop system without ever using the command line.

Other distributions all have their strengths and weaknesses.  Ubuntu is extremely popular probably because it holds the middle ground, so both new and experienced users feel mostly OK with it.

---

### Post by amsterdamharu on 2010-02-20
> Ubuntu 10.04 is based on 9.10, so your advice is quite conflictory.

I skipped 9 altogether, running hardy on my desktop and copied it to my laptop. Both worked fine but was curious to see how 10 would run. Can always copy 8 back on it so gave it a shot.

Maybe I am lucky, many posts here are about not booting and hardware not working after upgrade/update. This could be because most users don't bother with older versions and don't want unstable pre release and Ubuntu is pushing 9.10 on their site.

Advised 8.4 because it's lts and never had any big problem with it, give 10 a try when it's released.

---

### Post by AlistairD on 2010-02-21
So if I were to format using the Ubuntu boot cd what happens to my drivers? Will I just need to download them again? And what ones?

---

### Post by J V on 2010-02-21
All drivers will work out-of-the-box, no going to websites and downloading necessary...

---

### Post by AlistairD on 2010-02-21
I have just gone through the instilation process (location, time zone etc) it got to 100% and then my screen went black, my fans are running high but the HD light is off. Anyone? I burned my iso in Win7's default burner fwiw, would that have been too fast? False alarm I pressed power and I got a you have to restart message. It's up and running.

---

### Post by mörgæs on 2010-02-21
Congratulations! If the machine overheats, I would give 9.04 a try, but else you are all set to go.

---

### Post by AlistairD on 2010-02-21
Actually the fans are still running high and when I opened up power management both cpu's are running close to 90% on a bare bones install.

---

### Post by mörgæs on 2010-02-21
Since this is a new installation, it could be because of packages updating. It is only worrying if it continues.

---

### Post by AlistairD on 2010-02-21
Ok thanks mate, so give it a few hours?

---

### Post by AlistairD on 2010-02-22
Still seems to be getting hot. I had it switched off for a few hours and then it ran fine for 15mins and the fans went crazy again.

---

### Post by mörgæs on 2010-02-22
If you run the command **top**, can you see some heavy processes? 

If there is nothing special here then it seems you have the 9.10 bug. I would go for a 9.04 installation rather than trying to solve it.
[http://www.releases.ubuntu.com/](http://www.releases.ubuntu.com/)

Push 'q' for quitting top.

---

### Post by theozzlives on 2010-02-22
Make sure your laptop is on a smooth hard surface, and if there's debris (like dust, etc) use compressed air to clean your fan.

---

### Post by icelandvacationinfo on 2010-02-22
Is it very easy to do formatting with the use of Ubuntu

---

### Post by AlistairD on 2010-02-22
> **mörgæs said:**
> If you run the command **top**, can you see some heavy processes? 

If there is nothing special here then it seems you have the 9.10 bug. I would go for a 9.04 installation rather than trying to solve it.
[http://www.releases.ubuntu.com/](http://www.releases.ubuntu.com/)

Push 'q' for quitting top.

There is a copy of the results of the top command:

alistair@alistair-laptop:~$ top

top - 00:40:15 up 7 min,  2 users,  load average: 0.02, 0.06, 0.02
Tasks: 144 total,   2 running, 142 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.0%us,  0.8%sy,  0.0%ni, 95.4%id,  1.6%wa,  0.2%hi,  0.0%si,  0.0%st
Mem:   2060652k total,   461812k used,  1598840k free,    40144k buffers
Swap:  4016208k total,        0k used,  4016208k free,   208680k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1919 alistair  20   0  274m  87m  27m S    3  4.4   0:26.53 firefox            
 1473 root      20   0  306m  25m 6616 S    1  1.3   0:14.35 Xorg               
 1981 alistair  20   0 37860  12m 9488 S    1  0.6   0:01.17 gnome-terminal     
 1672 alistair  20   0  7476 4468 2160 S    0  0.2   0:00.31 gconfd-2           
 1715 alistair  20   0  3168  912  732 S    0  0.0   0:00.13 syndaemon          
 2002 alistair  20   0  2472 1176  884 R    0  0.1   0:00.22 top                
    1 root      20   0  2664 1540 1128 S    0  0.1   0:01.03 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.02 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.01 events/0           
   10 root      15  -5     0    0    0 S    0  0.0   0:00.02 events/1           
   11 root      15  -5     0    0    0 S    0  0.0   0:00.00 cpuset

---

### Post by _khAttAm_ on 2010-02-22
^nothing out of the ordinary here.

---

### Post by AlistairD on 2010-02-22
So it's either hardware, Ubuntu or I had suffocated it (I was running it on a laptop fan)?

---

### Post by mörgæs on 2010-02-23
There are some reports that upgrading the BIOS solves the problem, but chances are not big.

---

### Post by AlistairD on 2010-02-23
Actually I think the right fan is not working, before the left fan was going crazy and I looked inside the right fan which was not running. The left side was cool and the right side was hot so that kind of verifies it. I may get a techie to look at it.

---

### Post by AlistairD on 2010-02-24
Someone at a computer shop suggested to flash the bios to possibly fix the fan. I have a Dell XPS M1710 can someone please point me in the right direction? I have no clue after reading a plethora of googled stuff. I don't know much about terminal use at all.

---

### Post by amsterdamharu on 2010-02-24
[http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R160083&SystemID=XPS_M1710&servicetag=&os=BIOSA&osl=en&deviceid=10431&devlib=0&typecnt=0&vercnt=7&catid=-1&impid=-1&formatcnt=0&libid=1&typeid=-1&dateid=-1&formatid=-1&fileid=214244#1](http://support.dell.com/support/downloads/download.aspx?c=us&cs=19&l=en&s=dhs&releaseid=R160083&SystemID=XPS_M1710&servicetag=&os=BIOSA&osl=en&deviceid=10431&devlib=0&typecnt=0&vercnt=7&catid=-1&impid=-1&formatcnt=0&libid=1&typeid=-1&dateid=-1&formatid=-1&fileid=214244#1)

Look for installation instructions.

---

