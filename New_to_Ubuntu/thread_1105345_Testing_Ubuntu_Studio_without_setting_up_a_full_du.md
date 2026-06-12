---
title: "Testing Ubuntu Studio without setting up a full dual-boot?"
date: 2009-03-24
forum: New to Ubuntu
---

### Post by Noise... on 2009-03-24
Right now I have Windows Vista Home Premium. I don't like it much, but I need it for gaming. I downloaded Ubuntu Studio a while ago, but never got around to installing it or testing it. 

Is there a way that I can test out Ubuntu without doing a full installation onto my hard drive? I want to make sure that everything on my notebook works in it, and check out the interface. I've never used anything other than Windows, so I want to make sure I like the feel and setup of Ubuntu before I do a full fledged install. 

I'd really appreciate any advice!

---

### Post by BDNiner on 2009-03-24
Ubuntu studio only comes as an alternate CD install. You would need to take the plunge or do a lot of heavy research into your hardware before making the plunge.

---

### Post by Noise... on 2009-03-24
So I would need to do a full install to test it?

---

### Post by mcduck on 2009-03-24
Yes.

But if you don't need to test Ubuntu Studio-specific features you could just use a normal Ubuntu CD to check if it runs on your machine. In the end they are one and the same OS, only difference being default included applications and some extra tweaks for audio purposes in Ubuntu Studio.

---

### Post by Noise... on 2009-03-24
That's my issue - I have mobile broadband, and a 1GB+ download just can't happen. I only have 5GB of monthly bandwidth, so I can't redownload Ubuntu. 

If I would partition my hard drive and install it, how hard would it be to completely reverse the partition and delete Ubuntu if it doesn't work properly, or I just don't like it? 

Also, is Ubuntu compatible with Verizon Mobile Broadband? I'm basically looking at switching to Ubuntu for everything but gaming, but if I won't be able to go online it pretty much defeats the purpose of installing it at all.

---

### Post by lisati on 2009-03-24
If downloading a "Live CD" isn't a pratical option (for whatever reason) you might want to consider requesting a free CD from [https://shipit.ubuntu.com/](https://shipit.ubuntu.com/) 
 Based on your interest in the features of Ubuntu Studio, I'd recommend the "Desktop" version

---

### Post by Kareeser on 2009-03-24
The problem is that due to the precompiled and included packages, UbuntuStudio only comes on DVD, and then, only on an alternate CD, not a live CD.

---

### Post by Noise... on 2009-03-24
Ok. So a quick test is out. But I do still want to try Ubuntu.

If I would go ahead and put a drive partition in and do an install of Ubuntu Studio, how easily would it be reversed?

---

### Post by 73ckn797 on 2009-03-24
> **Noise... said:**
> Ok. So a quick test is out. But I do still want to try Ubuntu.

If I would go ahead and put a drive partition in and do an install of Ubuntu Studio, how easily would it be reversed?

You would only have to delete the partition. It will probably over write the Windows MBR upon installation. You can boot from the Windows CD and go to recovery and fixboot after removing. I do not know whether you can resize the partition in Windows. If you do not have a Ubuntu LiveCD to do that with you would have to find a Windows way.

I recommend defrag of Windows prior to installing Ubuntu.

---

### Post by markbuntu on 2009-03-24
You can test your system with a live cd and then install from that. Then you can put your ubuntustudio dvd in the drive and get all the ubuntustudio packages from that. Ubuntustudio is just a bunch of add-ons so the system is pretty much the same.

With a new machine or a new dstro I usually run the live cd to make sure there are no problems and then install and then get the ubuntu-studio meta packages from the repository with Synaptic. You can use the ubuntustudio dvd as a repository with Synaptic to avoid all that downloading.

I would also reccommend using 8.04 as the rt kernel is not working in 8.10 and that is critical for live recording and performance. 

If you can find someplace to plugin to avoid that mobile limit you should because even if you use the cd/dvd you will get inundated with a zillion immediate updates.

---

### Post by mcduck on 2009-03-24
> **Noise... said:**
> Ok. So a quick test is out. But I do still want to try Ubuntu.

If I would go ahead and put a drive partition in and do an install of Ubuntu Studio, how easily would it be reversed?

Very easy, as long as you have the windows CD around.

Simply boot the machine with the Win CD (or boot to Windows safe mode) and run "fixmbr" to remove Grub and make the machine boot into Windows. Then you can use the Disk Management in Windows to remove Ubuntu's partitions and format them into some file system Windows can use.

Shouldn't take more than a couple of minutes to do, plus the time formatting the partitions takes.

---

### Post by kansasnoob on 2009-03-24
Markbuntu made a very good point!

I'd first try running a Ubuntu Live CD to see if your hardware likes it or not.

If that seems cool then I'd follow a guide like this:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

to actually install Ubuntu. You can then install Ubuntu Studio by simply going to terminal and running:

```
sudo apt-get install ubuntustudio-desktop
```

After restarting you should run:

```
sudo apt-get -f install
```

just to clean up, and you'll have to change some themes (possibly), like the gdm theme, usplash theme, etc.

I'm using a testing drive right now for Jaunty. I'll give it a test drive!

---

### Post by markbuntu on 2009-03-24
I am already testing this on jaunty and my method works but, the rt kernel for jaunty, which has just showed up, is only partly working for some people and pulseaudio is still a mess with 0.9.14.

Personally, I am not expecting to see any real working rt again until the 2.6.29 kernel which we will see in Koala 9.10 and which is getting the most attention right now. The same with pulse0.9.15 which is vastly improved over 0.9.14 which is mostly just bug fixes from 0.9.10. Koala LTS will be sooo good.

Luckily for me I am a patient person. I have Hardy 386 and amd64 ubuntustudio along with Intrepid and Jaunty which I use strcitly for testing purposes. I will probably stick with Hardy as my main until a few months after Koala comes out. I have no plans or need at all to stay with either Intrepid or Jaunty, bumps in the road those two.

---

### Post by kansasnoob on 2009-03-24
Well, my idea seems to work - in as far as not causing breakage - but all themes would have to be changed, and many packages are not installed by default so you'd have to install and/or remove many, many packages.

So basically forget changing Ubuntu to Ubuntu Studio if you're a beginner.

Look here for a text install method:

[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

Just be sure to resize Vista using it's own tools as shown in the APC guide - it will save you hours of grief!

---

### Post by BDNiner on 2009-03-24
The real time kernel is essential to running ubuntu studio. So you may want to run the last LTS version of ubuntu instead of 8.10 or 9.04 when it comes out.

---

