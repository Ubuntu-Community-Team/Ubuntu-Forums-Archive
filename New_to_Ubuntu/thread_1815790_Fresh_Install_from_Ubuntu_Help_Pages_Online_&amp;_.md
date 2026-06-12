---
title: "Fresh Install from Ubuntu Help Pages Online &amp; Using Ubuntu 64bit 11.04 Natty mount pr"
date: 2011-07-31
forum: New to Ubuntu
---

### Post by djpurity on 2011-07-31
I had a few issues (well a lot of issues) with my installation of Natty somehow. I have an **AMD 64-bit processor** so I originally started with a **live CD of Ubuntu 64-bit 10.10** to install on a freshly formatted hard drive that I bought (a WD 500 GB) for my Acer laptop. After it asked me after an upgrade if I wanted to upgrade to **11.04 Natty**, I said yes of course, and installed. But then the problems began.

It took* a lot* of trial and error with the new **Unity** layout system, and I lost access to my launchpad on the left and the top bar at the top while playing with **compiz config editor**. But anyway, I learned _not_ to fool with that.

So then anything I ever installed or uninstalled from the **Ubuntu Software Center**, it always ended in an ***error code 2***, and it said the installation or removal ***failed***, even though the software would *appear* to work or *appeared* removed. (I am dealing with this specific issue in another forum. So my problem I ask about today is after this part :P)

Anyway I found a page on **Ubuntu's Help Pages** online about "***Getting a Fresh Installation***" or how to revert to a fresh installation. I thought I would try it out and maybe see if I reverted to a *fresh* install of **Natty**, it would fix the problems.

So I did the whole thing about using **Synaptic** to find all the installed third party applications, and then disabling them, even though I accidentally went too far and *_uninstalled_* _*all*_ of them. I then updated my repositories and everything, and then closed **Synaptic**. It wanted me to insert a **Natty installation disc** for update manager to update the repositories. All I have is a complete download **iso** file of an **AMD64-bit 11.04 Desktop installation** that I got off an *authorized* and authentic site, so I burned *that* to a CD, because I just double clicked on the **iso** file and that was what it asked me if I wanted to do, burn it using an image burning program.

Anyway, I made the CD but it just stopped at the part "***creating checksum***" for the CD, and I let it run overnight. And it never moved an inch. So I just ***canceled*** and removed the CD, which it said was finished and complete! And I re-inserted it and it seemed to fulfill the **update manager**'s repository update request for a CD, and it updated all kinds of repositories and packages, and I ran **update manager** a few times and it always was as fresh an install as possible. I edited the source for update manager to use some disabled sources that natty had disabled (it said so in their descriptions).

_**So here is my problem:**_ ):P

**However, when I try to mount the CD or insert it into my drive, it always gives me a mount error and this:**
> 
Error mounting: mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
But I then am able to get on the what-appears-to-be-mounted drive on my desktop, and I can fully explore the "mounted" CD drive. I can chose to "unmount it" if I right-click on the "mounted image" ... I am confused.

I know this was the "***Desktop version***" of the **11.04 AMD 64-bit installation of Natty**, so I don't know what would happen if I just rebooted off of it. I followed the instructions on the page of how to get a fresh install, where it then said to "re-enable all third party packages/repositories" in **Synaptic**, but I checked and of course I had uninstalled/removed them all by accident and misunderstanding.... oh well, I am still up and running. I reinstalled **Google Chrome**, and it _**did not**_ end in *any* errors this time, like an **error 2**, like it used to when I used the **Software Center**.

***So is it fixed***? But what's up with the ***mounting*** of this CD? Is it a boot disc? Or should I use **Firefox** to download another version of 11.04 64-bit AMD of Natty install to burn to a CD as a boot disc? I just used CD/DVD maker or the default app that came up when I inserted a blank CD and I double clicked on the iso on my desktop (I think that is what I did, I can't believe I wasn't really paying attention), but anyway, like I said, the checksum never finished on the making of this CD, so I am afraid it is flawed.

Any help or advice on how I can fix my O/S to a "***REAL***" **FRESH INSTALLATION** of **11.04** even though I originally started with **10.10 64-bit **and *_upgraded_* to **11.04 64-bit**? I don't want to lose any data. I think most of the third party stuff I removed was all stuff I knew I could lose anyway and not hurt my system, but one of them was ***Google-beta-installation*** but once the **update manager** rebuilt the repositories, it appeared in my **Ubuntu Software Center** under **Google**, which was *enabled* when I _*checked*_ all the ***disabled*** source places (except "*source code*") for the upgrades. And **Google's beta version** was there, the regular operational version was there, another couple versions were there... so I just installed the regular non-beta version. But I am using **Firefox** right now anyway. 

So did I do well or did I mess up? Anyway to know for sure? Anything I should run to reveal the status of my machine? :confused:

How is my CD read-only? Isn't any CD or DVD burned read-only? Is it because I marked it as closed? I didn't leave it open. I thought it should be a closed image disc.

**Thanks**! :KS I enabled some suggestions in **Synaptic**, which all installed just fine, no errors.

*Also, now when I insert the CD-ROM, it mounts just fine on my desktop... I wonder if it was something I just installed in **Synaptic**? I am so confused... please all I am asking is how to use the **desktop installation** **iso** of **11.04 AMD 64-bit** to install a fresh version of **11.04** when there have been problems installing and uninstalling software packages and such from **software center**? Can I made it into a boot disc? How does one use the **Desktop disc** for anything?*

---

### Post by waynefoutz on 2011-07-31
Upgrades can be messy. I usually don't bother with them. I back up everything in my /home directory on an old hard drive I converted to an external drive and go with a clean install. Makes things much easier in my opinion. Back in the early days of Ubuntu, upgrades were pain free, but not so much anymore.

---

