---
title: "Frustrated with Fedora, so..."
date: 2009-07-08
forum: New to Ubuntu
---

### Post by IHeequ5i on 2009-07-08
I've been using Fedora for a while, and I'm getting progressively more frustrated with it. So I'm looking at converting to Ubuntu. I'm downloading the 9.04 Desktop iso file as I type this.

The current plan is to back up all my data and config files to DVD, wipe my Fedora partitions, and install Ubuntu. 

The *only* problem I forsee is that my PC is dual-boot with Fedora and Windows XP.  I use grub as my boot loader, and I don't want to lose my Windows partition.

Anything special I should do / not do?

---

### Post by snowpine on 2009-07-08
The Ubuntu installer is "smart" enough to recognize your existing Windows partition and set up the dual-boot in Grub.

---

### Post by starcraft.man on 2009-07-08
The GRUB on Ubuntu is the same as Fedora. When you get to the partition step just make sure you manually make your own partitions and don't touch the NTFS partition that has the XP install. At the end of the process, GRUB autodetects any other OS 99.9% of the time (could have a tri-boot if you left Fedora there and made more space for Ubuntu, up to you, could even share home, just make different usernames).

Just a note on Fedora, I think they default to LVM instead of partition use no? If your familiar with that and want it for Ubuntu as well, it works, but not with the default live install (pretty sure not), you'll have to down the alternate cd and install via that. At the partitioner step there you've the option to make a new LVM. If your not an LVM user, forget I said anything.

---

### Post by skyjacker on 2009-07-08
> **Doomspark said:**
> I've been using Fedora for a while, and I'm getting progressively more frustrated with it. So I'm looking at converting to Ubuntu. I'm downloading the 9.04 Desktop iso file as I type this.

The current plan is to back up all my data and config files to DVD, wipe my Fedora partitions, and install Ubuntu. 

The *only* problem I forsee is that my PC is dual-boot with Fedora and Windows XP.  I use grub as my boot loader, and I don't want to lose my Windows partition.

Anything special I should do / not do? I think you are going to REALLY like ubuntu. its very easy to get used to.  Good luck on your install. Remember, if you need help, this is the place to come... I have learned a lot from this forum.

---

### Post by binbash on 2009-07-08
Ubuntu Live cd will detect your windows like Fedora.

---

### Post by dstarzfn72 on 2009-07-08
I was using Kubuntu for a while then my computer decided to take a dump on me and since I didn't have my Kubuntu disk handy I went to Fedora 11 that a friend of mine had. After using Fedora for about 2 weeks and not being able to get my video card drivers to work or my sound I went back to Kubuntu and needless to say I am much happier now. With Kubuntu I have no problems getting eveything to work. I am betting that once you get it set up you will be as happy with it as I am.

---

### Post by scrooge_74 on 2009-07-08
Hey only warning around would be if you are using an ATI or Nvidia card seems there are problems with the drivers and you may have to use previous version of them

---

### Post by pirattrev on 2009-07-08
Just beforehand, make sure you know which partition (double check, that is, with the dev names) to make sure you remove the correct one. It should autoknow the Unix one versus the Windows one, but it's always a good idea to know yourself, just in case one partition is labeled as 'Unknown' and you're not sure. The device sigs are always the same, so learn those quick.

---

### Post by IHeequ5i on 2009-07-08
I have two physical hard drives in my PC.  The small one is XP and the large one is currently Fedora but going to be something else in fairly short order. I figured it would be easier to split by physical driver rather than by partition. 

I think I'm using LVM, but not 100% sure.

When I installed Fedora, I had to go through a lot of pain to get the bootloader working properly so that I could dual-boot. I hope Ubuntu will be kinder to me.

I have an Nvidia GeForce 7000-series video card. One of the reasons I'm moving away from Fedora is the generic driver they include with FC11 that doesn't allow the card to use hardware acceleration (which trashes all my games). This is progress? I think not! I'm hoping to have fewer headaches with Ubuntu. From what I've read, it's friendlier.

Software that absolutely needs to work properly (hardware is a *must* obviously):
Echolink - I'm a ham.
Dosbox
Basket
OpenOffice 3.5
Firefox
Thunderbird
Wine 
GIMP
A CD/DVD burner that knows how to handle .iso files
Music player that can handle .ram, .mp3, and .wav files
DVD player is nice but not mandatory

---

### Post by scrooge_74 on 2009-07-08
> **Doomspark said:**
> 

Software that absolutely needs to work properly (hardware is a *must* obviously):
Echolink - I'm a ham.
Dosbox
Basket
OpenOffice 3.5
Firefox
Thunderbird
Wine 
GIMP
A CD/DVD burner that knows how to handle .iso files
Music player that can handle .ram, .mp3, and .wav files
DVD player is nice but not mandatory

Echolink - I have something new to learn
Dosbox works
Basket have no clue
OO 3.5 no problems there
sames as with FF y Thunderbird I like them both, but prefer Opera and I'm using evolution now days for my mail (I was lazy to download thunderbird)
Wine or Cross OVer (works no problem, games some work some dont)
GIMP always gives me a hand
Brasero for my everyday needs to burn iso files, in fact Im doing that right now.
DVD player no problems there by default after you follow the Multimedia Howto and install what you need

---

