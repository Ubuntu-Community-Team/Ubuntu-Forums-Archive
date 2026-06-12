---
title: "Best/Effecient Win7/Linux Ubunto setup!"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by chris1neji on 2010-03-12
So i will be installing a new HDD (WD800AAJS) 80GB/7200RPM
My old one is 640GB/7200RPM.
I want to have dual boot with windows 7/64x
So i was thinking 50GBs for win7/the rest for Linux

My 640gb one will be use for Movies/backups/documents/games/majority of installations will be save here ( i like to this drive Media)

My primary OS is windows7 then Linux

Another thing that is worrying me is that have Acronis(software) which made a recovery boot partition.(press F__ to load recovery partition) So i imagine that is in the MBR...would that need to be remove before adding linux?

Lets pretend windows has an error and cant load. I use windows 7 start-up repair disc and it removes Linux from the loading menu...would i be force to reinstall Linux?

Would it be better to run windows 7 on its own HDD and Linux on opposite HDD but in separate partitions?

Anything i should be aware of ? With hardware incompatibility maybe?

Here is my basic overview
MS Windows 7 Ultimate 64bit OS
AMD phenom X4  9100e (agena 65nm Technology)
4GB Dual Channel DDr2 5-5-5-18
Gateway RS750(AM2)~~~~AMD780G chipset
ATI Radeon HD4650 FXF
PSU antec 550Watt

---

### Post by rockerphil on 2010-03-12
ok, as far as the recovery partition goes you can go ahead and wipe that out if you want since you've got the Windows recovery disc, and  50 GB to Windows and the rest for Linux is just fine, just remember to install Windows first then install your Linux OS thus giving you a nice GRUB boot loader, and no, you won't be forced to reinstall Linux if you're forced to reinstall your Windows OS, all you'll have to do is reinstall GRUB since Windows has a nasty habit of wiping the MBR upon reinstall, just search around on the forums on how to do that, it's not extremely difficult. as far as hardware support goes Ubuntu has some of the best hardware support for Linux, so there shouldn't be any issues. hope this info helps,

Phil

---

### Post by MichealH on 2010-03-12
As a matter of fact I have a 111GB HDD:

10GB OEM (Which I WONT Touch)
50.7GB Win7
50.7GB Ubuntu

I split up my HDD In half basically! Oh and who cant forget the 50.7 GB Ubuntu gets split again so the / mount is 4/5 GB and the /home is the rest =)

---

### Post by chris1neji on 2010-03-12
Well if my set up is okey time to open this rig up and add a few screws in ...still waiting for sata cables to arrive :(

---

### Post by chris1neji on 2010-03-12
Since this is about most efficient Linux Ubunto. I ran into a problem.
I cant find the latest version of Ubunto 64bit.

Am i forced to download 32bit OS?
If so will my 4GB's of RAM be allocated and used by Linux?
Will there be a issue running Win64bit/Linux32 bit? as far as drivers go?

---

### Post by sandyd on 2010-03-12
> **chris1neji said:**
> Since this is about most efficient Linux Ubunto. I ran into a problem.
I cant find the latest version of Ubunto 64bit.

Am i forced to download 32bit OS?
If so will my 4GB's of RAM be allocated and used by Linux?
Will there be a issue running Win64bit/Linux32 bit? as far as drivers go?

the option is hidden...
[http://mirrors.us.kernel.org/ubuntu-releases/karmic/ubuntu-9.10-desktop-amd64.iso](http://mirrors.us.kernel.org/ubuntu-releases/karmic/ubuntu-9.10-desktop-amd64.iso)

---

