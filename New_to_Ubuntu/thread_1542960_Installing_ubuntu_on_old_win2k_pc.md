---
title: "Installing ubuntu on old win2k pc"
date: 2010-07-31
forum: New to Ubuntu
---

### Post by owens88 on 2010-07-31
Hi
My intention is to install ubuntu on a spare machine. However that machine does contain one or two pieces of software that we don't have elsewhere (Macromedia and Corel Draw)and for which we don't have the install disks anymore.  There is also a fair bit of data held in docs, xls and images.

[B]If I install ubuntu to displace win2k (i.e use the whole disk) will applications like macromedia still run?
Will the installation 'wipe' programs and data?[/B]

I have tried running ubuntu from the cd (very slow) and it doesn't let me 'see' Macromedia or Corel. I tried some wimple word files and it was a bit haphazard with them. I tried an xl file and it culdn't find one element. Yet these work fine in win2k.

Thanks in advance

John

---

### Post by Megaptera on 2010-07-31
If you use the whole disc it'll wipe everything on there. Consider a dualboot?

What ram on the spare machine? Is it sufficient for Ubuntu? See here:
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by howefield on 2010-07-31
If you use the whole disk option to install Ubuntu, you will wipe out everything on your hard disk, applications, data, documents..everything.

The installation process will give you the option to resize the disk and install Ubuntu side by side, keeping your windows install and all its data.

Either way, it makes sense to back up all your documents prior to doing anything with your disk. Defragmenting your windows installation might not be a bad idea either.

---

### Post by finny388 on 2010-07-31
Ubuntu and Windows are different platforms for software. Software written for Ubuntu won't work for Windows and vice versa. There are ways to make it work with virtual OS layers like 'WINE'.

However, without the install files, you cannot install those 2 apps on Ubuntu.

You can't just displace Windows with ubuntu, it doesn't work that way.

But Megaptera offers a good option. It depends on your reasons to switch.

---

### Post by Cavsfan on 2010-07-31
I have always used the custom install option at the bottom as I dual boot Windows 7.
That has always been the best way for me. I do not know anything about side by side.
I used disk manager in windows 7 to "shrink" my C: drive and free up 100GB of my 500GB HD.
I also had to defragment it before it would allow me to do that. Now I have 3 partitions:
1 - for windows 7
1 - for 8GB swap (which I am realizing is too big now, but was told to double my ram size)
1 - for Ubuntu 100GB - 8GB roughly 93GB or so

---

### Post by Sef on 2010-07-31
If the data is that valuable, then I would buy another hard drive and install ubuntu on that.

---

### Post by snowpine on 2010-07-31
Hi John, 

Before proceeding, you should compare your hardware specs against the [Ubuntu system requirements]("https://help.ubuntu.com/community/Installation/SystemRequirements"). 

> Ubuntu Desktop Edition

    * 1 GHz x86 processor
    * 1 Gb of system memory (RAM)
    * 15 GB of hard-drive space (although this can be split onto 2 drives, a 5Gb / and a 10Gb /home fairly easily)
    * Graphics card and monitor capable of 1024 by 768
    * Either a Cd/Dvd-drive or a Usb socket (or both)
    * Internet access is helpful 

If your specs fall short of the minimum, it explains why Ubuntu is running very slowly, and you might be better of with its lightweight cousin Xubuntu (or an even lighter distro like Puppy).

One thing that cannot be stressed enough is that you need to back up your existing data to an external drive (I would recommend cloning the entire partition so you can easily restore the current machine state) and you should keep Windows if you need certain Windows applications.

I applaud your decision to experiment with Ubuntu on a spare machine, however in this case it does not sound like the machine is really a "spare" and so I encourage you to proceed with caution. :)

---

### Post by darrelljon on 2010-07-31
The latest Ubuntu will be too slow on an old win2k PC. And yes installing it on the entire disk will wipe all data (programs and documents). Try a smaller distro such as Puppy 3, SliTaz, INX or Ubuntu Minimal.

---

### Post by mapes12 on 2010-07-31
Here's a good how to for dual booting:-

[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

I have successfully run Ubu on much smaller spec than the recommended criteria.

---

### Post by -kg- on 2010-07-31
@ Snowpine:

> Ubuntu Desktop Edition

* 1 GHz x86 processor
* 1 Gb of system memory (RAM)
* 15 GB of hard-drive space (although this can be split onto 2 drives, a 5Gb / and a 10Gb /home fairly easily)
* Graphics card and monitor capable of 1024 by 768
* Either a Cd/Dvd-drive or a Usb socket (or both)
* Internet access is helpful 

Those are the *_suggested_* minimum requirements, not the absolute.  It will run on less, though more slowly.  Of course, the whole computer will run more slowly than modern machines no matter *what* OS you're running.

> If your specs fall short of the minimum, it explains why Ubuntu is running very slowly,

Actually, the OP said he was running it from the Live CD:

> I have tried running ubuntu from the cd (very slow) 

It will run slowly from the Live CD even if you're running it on the hottest modern computer available.  The speed bottleneck will be the speed of the optical drive you're running it from.

You say the machine is currently running W2K...is that W2K Pro or W2K ME?  What is the size of your hard drive?  I have an old laptop that originally came with W2K ME, and the hard drive is 8 GB.  I upgraded RAM to 364 MB and upgraded to XP some years ago, and there's barely enough room for XP to run.  If you don't have much room on your hard drive, you won't be able to install Ubuntu side by side *_unless_*...

> If the data is that valuable, then I would buy another hard drive and install ubuntu on that.

That would be your best option, if you're able to do that.  If your computer is a laptop, that might be problematic, but if your computer can boot to a USB device, you could make the installation on an external hard drive.

What kind of computer is it, and what are its specs?  The specs would be useful to us in order to help you further.

I have seen that there have been some issues with Corel files under Ubuntu (check out Inkscape, available in the repositories).  When you say "Macromedia," are you talking about the Flash Player?  You can install the Flash player by installing the "ubuntu-restricted-extras" from the repositories.

---

### Post by snowpine on 2010-07-31
> **-kg- said:**
> Those are the *_suggested_* minimum requirements, not the absolute.  It will run on less, though more slowly.  

I am not an Ubuntu user, so I will take your word for it. :)

I will however quote this warning:

> Most users (especially those new to Ubuntu) risk frustration if they ignore these suggestions.

---

### Post by -kg- on 2010-07-31
Yes, I saw that, but I think it refers more to speed issues than anything else.  While Linux will speed up a computer's operation, sometimes new users will expect too much from it.

Right below where you got the "frustration" quote, it says:

> Ubuntu Desktop (GUI) Installation...

...512 MiB of system memory (RAM)

That knocks the RAM requirement in half.  Further down:

> Minimum system requirements for Xubuntu would fall roughly between Ubuntu Server and Desktop:

    * 256 MiB of system memory (RAM)
    * 2 GB of disk space
    * Graphics card and monitor capable of 800x600 resolution 

There's always a way.  Yes, with diminishing hardware capabilities, you have diminishing capabilities of running certain parts of Linux with any respectable amount of speed, and some things might not work.  But if one wants to recycle an old machine, they (hopefully) should be able to set up either Kubuntu (with the decreased suggested minimum hardware requirements) or a minimal installation as was suggested.

Of course, there are the absolute minimal distros.  I've not used the others, but Puppy Linux certainly will run on most even *remotely* modern computers.  After loading, it runs totally from a RAM disk and has around a 64 MB footprint (before loading your desired software, of course).

The OP should at least be able to install Xubuntu on a Windows 2000 machine...even a Windows 2000 ME computer, let alone one that runs Windows 2000 Pro.

---

### Post by Ducatiboy Stu on 2010-07-31
I would go  with installing Ubuntu on a 2nd Hdd or even a USB stick if the BIOS will allow booting from USB...

That way you keep your W2k safe and you would still be able to access data thru Ubuntu

---

### Post by Windows Nerd on 2010-08-01
> **-kg- said:**
> I have seen that there have been some issues with Corel files under Ubuntu (check out Inkscape, available in the repositories).  When you say "Macromedia," are you talking about the Flash Player?  You can install the Flash player by installing the "ubuntu-restricted-extras" from the repositories.
Macromedia makes much other things other than their flash player. Most of it's applications though (such as Dreamweaver and Fireworks) are media applications, new, and require higher-end machines to run.

Though I thought Adobe owns (or at least bought) Macromedia because Flash is on Adobe's website.

Scott

---

### Post by Stancel on 2010-08-01
Ubuntu cannot run on old Windows 2000 PCs. I tried it before (back in 2007), and had to deal with a perpetual loading screen. Try a different, more lightweight distro.

---

### Post by lkraemer on 2010-08-01
I also think you would be much better off trying:
1. Puppy
2. Crunchbang
3. Damn Small Linux (DSL)
4. Tinycore

or some other lighter Distro, because you won't be satisfied with the
performance.

I've used several on my old Win 2K Laptop as Dual Boot with Win 2K, and
at the moment I'm running Crunchbang.

lk

---

### Post by darrelljon on 2010-08-01
If you're a new user, I wouldn't recommend struggling with performing anything (minimal install, dual-boot etc.) but the basic installation method until you're more confident with Linux. Don't blame the live CD functionality, even a minimal install of Ubuntu 10.04 will be slow on what could be a Pentium II machine. Therefore I wouldn't recommend using the latest Ubuntu on a Win2k era machine.

By the way there is no such thing as Win 2K ME.

I don't think the answer should be spend more money on hardware. If Win 2K can run on it, Linux ought to be able too. Use Puppy Linux 2 or 3. Puppy Linux will happily work on a 6Gb HDD 256Mb RAM machine. As for the supposed functionality hit you'll have to suffer with Puppy over Ubuntu (or Win2k), I don't see it.
With Puppy you can install in less than 200Mb, have OOBE tabbed web browser, html editor, instant messenger (supporting MSN, AIM, ICQ and Y!), Gxine media player, up to 8 virtual desktops, customisable taskbar, GTKSee photo management, word-process with ODF, DOCX and DOC support, spreadsheet with ODF, XLSX and XLS support, view and create PDF, burn discs with Grafburn, Torrent with transmission, Xarchive with RAR, ZIP and 7Z.

If you really want Ubuntu try [the GTK Remix]("http://kmandla.wordpress.com/ubuntu-gtk12-remix/").

---

### Post by owens88 on 2010-08-01
Thanks all.
 
The machine is a 1.5gh pentium 60Gb hard disk. It is 'showing' 256k ram but I seem to recall having it upgraded to 750 (asymettric 512 and 256). Perhaps some of the dimms are not working or not registering with windows. (w2k pro)
 
The macromedia need is for intermittent web editting.
 
The prime reason I am trying ubuntu is because I have an external hard drive previously accessible through a nas box. I think the nas box has failed and therefore setting up a linux pc might save my bacon. I will loook at the lightweight options.
 
John

---

### Post by sydbat on 2010-08-01
> **owens88 said:**
> Thanks all.
 
The machine is a 1.5gh pentium 60Gb hard disk. It is 'showing' 256k ram but I seem to recall having it upgraded to 750 (asymettric 512 and 256). Perhaps some of the dimms are not working or not registering with windows. (w2k pro)
 
The macromedia need is for intermittent web editting.
 
The prime reason I am trying ubuntu is because I have an external hard drive previously accessible through a nas box. I think the nas box has failed and therefore setting up a linux pc might save my bacon. I will loook at the lightweight options.
 
JohnI just skimmed through this thread, but I suggest that if Win2K is running fine, don't do anything. 

You might do as others have suggested and get a second hard drive to install a Linux variant on it (Ubuntu should work) and access your info/Macromedia programs via WINE.

However, before doing ANYTHING, back everything up.

---

### Post by owens88 on 2010-08-01
Thanks

I thought you might be interested to learn what it says on the package `10.04 LTS Desktop edition'

This edition will run on most pc's..............
To use Ubuntu you should have a PC with at least 256MB of Ram. And to install it, you should have at least 4 GB of disk space.


John

---

### Post by waynefoutz on 2010-08-01
I have found that Lununtu, Peppermint, and PCLinuxOS LXDE runs pretty acceptable on an older machine with 256 megs of ram. It's nothing to write home about, but the LXDE desktop is the best choice for older machines like this.

---

### Post by PremiereWebDesign on 2010-08-01
> **owens88 said:**
> Thanks all.
 
The machine is a 1.5gh pentium 60Gb hard disk. It is 'showing' 256k ram but I seem to recall having it upgraded to 750 (asymettric 512 and 256). Perhaps some of the dimms are not working or not registering with windows. (w2k pro)
 
The macromedia need is for intermittent web editting.

I recently installed Ubuntu on a machine with very similar specs with no problems. What I have found is that if it will run the Live CD, then you usually will not have problems....
As for needing Macromedia for web editing. What you may want to consider is switching to Kompozer. You can install it from the "Ubuntu Software Center". It does a very good job. If you want to find out more about it, [here is a link]("http://www.kompozer.net") to the Kompozer site. 


 Since you mentioned that it was Macromedia, I can only assume is that what you are using is an older version of Dreamweaver (MX or possibly 8 at the latest). If that is the case, Kompozer, in my opinion, is better than MX and as good as Dreamweaver 8.

---

### Post by owens88 on 2010-08-03
Many thanks all.  If I get it all working I will wean off Macromedia.

UPDATE.  Using live CD I can now 'see' the files on the errant external hard drive.  I haven't yet installed ubuntu as a)it stopped giving me option of automatic install to dual boot suggesting partitions to me (I am 'fearing to tread' on manually doing partitions for the mo)and b) I may follow the forum advice and put a distro on instead (puppy?).

HOWEVER the newly accessed files all show an x in the icon and won't open. Properties show that they are 'owned' by user 501 and are protected. (NB I have NOT set up any groups or users yet) 
**_I wonder whether_** i) this is because I am using live cd ii) the problem would go away if I did set myself up as user 501 or iii) the problem would not occur in a distro because they don't set up users?



I know  that this is stretching this thread to the max. Any other questions I have I will research first and start a new one if necessary. But if anybody could give me insight into the 501 problem it might shortcut a lot of my effort.

Thanks in advance.

John

---

### Post by giddyup306 on 2010-08-03
A couple of comments.

I have Lucid on two different desktops.  Both are pretty old.  One (the good one - HP Media Center 876x) has a 2.4 GHZ processor (dual virtual cores) and 1.5 GB/RAM.  I pulled out the OE DVD reader the other day and it was made in '03 so the other desktop is even older.  The other (HP Pavilion 750c) has a 1.8GHZ processor (single virtual core) and 512 MB/RAM.  According to the link Ubuntu needs a 1 GHZ processor and 1 GB RAM.  I noticed on the slower machine that it pegs out the processor really easy, and on both it is hard to hit 1GB just doing "normal" tasks.  If you're just browsing the net and watching a video maybe writing a word processor sheet then you're probably fine with 512 MB ram.  Most of the time if I'm just browsing the net I'm around 256 MB/RAM (right now I'm around 330 but I'm running other things).  If you want to run a virtual machine, compiler, or video editor (or any combination of them) then that's a different story.  Something else I would like to say is that "an old win2k" machine can be no worse than "an old XP" machine.  They came out only one year apart from each other. So an XP machine could be as old as 2001 or as new as refurbished unit that had XP installed on it since they are planning on supporting XP 'till '20.  Another thing I'd like to mention is that 2000 is MUCH slower than XP.  So if you're running Ubuntu, you'd probably see a performance increase.  Granted there probably other, better alternatives if your machine is super slow.

---

### Post by jtarin on 2010-08-03
> **-kg- said:**
> 

You say the machine is currently running W2K...is that W2K Pro or W2K ME?  What is the size of your hard drive?  I have an old laptop that originally came with W2K ME, and the hard drive is 8 GB.  I'm not familiar with W2K ME.....was that an experimental foray by MS?

---

### Post by owens88 on 2010-08-03
W2K ME is a red herring accidentally introduced by another poster I think.

---

### Post by rolnics on 2010-08-03
I'm currently running a PIII 733Mhz with 512mb ram, it runs 9.10 ok, but slowly if you try to multi-task. I was tempted at trying Lubuntu, but never actually got round to it. But I'm still tempted, when I get the time!

I see darrelljon mentioned puppy, I'm currently running puppy501 which does run smoother than ubuntu, but it also seems to have it's slow moments, compared to my P4 running Hardy...when I eventually get it running again! If you're feeling adventurous you could download the server edition of ubuntu and build from there or one of the minimal install iso's out there, they would give you a basic base and you could add programs and stuff you need.

---

### Post by jtarin on 2010-08-03
> **owens88 said:**
> W2K ME is a red herring accidentally introduced by another poster I think.
Please say it isn't so.:shock:

---

