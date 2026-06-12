---
title: "I'm going to want to upgrade..."
date: 2009-10-23
forum: New to Ubuntu
---

### Post by rockstarrem on 2009-10-23
But, it seems that everyone is doing a fresh install. I really don't want to do this as I have everything as I want it in my current install. Is there a way I can do an upgrade install perfectly? I see there are a lot of differences that can affect hardware and other things, like the new sleep system and GRUB2, but is there a way? If it's going to significantly screw with my desktop then I'll do a clean install, but I need to know.

Thanks!

---

### Post by Mariane on 2009-10-23
In my experience upgrades are painless. You type: 

```

sudo apt-get update

```

and then 

```

sudo apt-get upgrade

```

and if you want a new version of Ubuntu (and if one is available) you type

```

sudo apt-get dist-upgrade

```

You should do these in that order, regularly. The less time you spend between two upgrades the lesser your chances of something going wrong. Sometimes it takes a while. 

Mariane

---

### Post by rockstarrem on 2009-10-23
Right, but why are so many people doing clean installs on this new version (9.10)?

---

### Post by Paul41 on 2009-10-23
I have never had a problem upgrading either. In the past several versions the system has notified you when the new release is available and you just click a button to upgrade. Keep in mind that the first few days of the release the servers are hit hard and the upgrade is SLOW. After a couple days it usually gets better.

---

### Post by Paul41 on 2009-10-23
> **rockstarrem said:**
> Right, but why are so many people doing clean installs on this new version (9.10)?

There is always a large group of people that prefers a clean install. Most of them think that is the cleanest way. I am like you and have things set the way I want and don't want to redo it. There is no right or wrong way, it's just a preference.

---

### Post by Penguin Guy on 2009-10-23
> **rockstarrem said:**
> Right, but why are so many people doing clean installs on this new version (9.10)?
Geek's idea of fun?

---

### Post by Mariane on 2009-10-23
I just did it and it went perfectly. I didn't even have to reboot, my computer still seems to be exactly as it was before. 

This one does take a while, though, and I think it is better not to do anything with it while it is upgrading. I am certain you should never interrupt an upgrade. 

I don't know why people would do a clean install, it sounds like much more trouble. 

Mariane

---

### Post by QIII on 2009-10-23
If you are dead set against a complete install, I would BACK UP WHAT I WANTED TO KEEP, then:

Update Jaunty to GRUB2 now ...

[http://linuxhub.net/2009/07/install-grub-2-on-ubuntu-jaunty-jackalope/](http://linuxhub.net/2009/07/install-grub-2-on-ubuntu-jaunty-jackalope/)

Update to ext4 now ...

[http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21](http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21)

With the above, please read carefully.  You do this from the LiveCD so your drive is not mounted.


Then, if you have a dual (or multi) boot system ...

```
sudo apt-get install os-prober
``````
sudo os-prober
``````
sudo update-grub2
```Then, instead of "dist-upgrade" I would do

```
sudo apt-get install update-manager-core
```in case it is not installed, and then

```
sudo do-release-upgrade
```

---

### Post by Paqman on 2009-10-23
> **rockstarrem said:**
> Right, but why are so many people doing clean installs on this new version (9.10)?

The upgrades used to be less reliable. Old habits die hard.

---

### Post by Paqman on 2009-10-23
> **Mariane said:**
> I just did it and it went perfectly. I didn't even have to reboot, my computer still seems to be exactly as it was before. 


If you haven't rebooted, then you haven't finished upgrading. Karmic uses a different kernel version from Jaunty, and you can't switch to a new kernel without a reboot.

---

### Post by Mariane on 2009-10-23
Suspense still on, then :) 

Mariane

---

### Post by Dougie187 on 2009-10-23
> **Paqman said:**
> The upgrades used to be less reliable. Old habits die hard.

Also it's a party. I mean I'm use to installing my system fresh every 6 months or so from my windows days.

But yeah, older versions had pretty unreliable upgrades. That's what drives me to do a clean install. Just because I know when I use to do it, it wouldn't work, but clean install always works. And I get to clean house a bit.

---

### Post by philinux on 2009-10-23
Updating to ext4 will not deliver the full performance gains.
[http://kernelnewbies.org/Ext4#head-3891522e0601162aab24c73c1f148a1e28c6a9d4](http://kernelnewbies.org/Ext4#head-3891522e0601162aab24c73c1f148a1e28c6a9d4)

Good read in any case.

This is my take. This release with grub2 and ext4 have made me decide to do a clean install including my separate home partition.

So I'm going to backup all my personal stuff to dvd, and to my spare HD. Then I'm going to backup my firefox profile and evolution folder. Reinstall.

I'm not bothered about any other config files as it takes 2 mins to get my desktop looking fine. 

Think of it like moving home, time to ditch some junk.

---

### Post by Mariane on 2009-10-23
Well, my upgrade failed. It told me I didn't have the right user name or something. Like when I go root here, it always tell me: 

sudo: unable to resolve host tux-laptop

Only there it was looking for tux-laptop0 or something. Anyway, it booted fine under the previous version and I am NOT going to try and fix the new one today. I already brought one laptop to the workshop today, I'll see about fixing this one once I get the new one back. If it doesn't break down completely until then. 

Mariane

---

### Post by QIII on 2009-10-23
Yes.  ext4 upgrade will leave what is there already in ext3 legacy format.

As for the /home partition, I wish that the default installation made one.  I've always had one.

I save it off, reinstall the OS, reinstall the applications (easy methods to do this for stuff from Synaptic) and then just chunk the contents of my /home back in.

In this case, however, FireFox profile will be in .mozilla/firefox rather than (if you upgraded) the Shiretoko profile folder.

So, after you start FF the first time, you'll get a new empty FF profile folder.  Just note the xxyyyy.default name, drag your old profile (and the .ini) in, rename it to whatever the newly generated .default name is, or edit the .ini file to whatever the old one was...

Same sort of procedure will be necessary for evolution, thunderbird, etc.

---

### Post by Dullstar on 2009-10-23
Wait, you mean the distro upgrades are now safe to do?!
...and I wasted all that time on a fresh install.

---

### Post by QIII on 2009-10-23
> **Dullstar said:**
> Wait, you mean the distro upgrades are now safe to do?

We used have a saying when a non-fatal accident occurred when destroying unexploded ordnance:

"Nobody got hurt?  Hmmm.  Musta been safe, then..."

---

### Post by Georgia boy on 2009-12-17
Okay, from what I've been reading in this thread is it's okay to do an upgrade. But, I'm using Hardy Heron and dual booting with XP. So, when the next LTS 10.04(?) comes out in April I want to get rid of XP completely  and just have the next LTS installed. So, that means for me I would need to get a Live CD for that and just have it do a complete install right? As far as the back up goes, I don't have a separate /home so anything I really want to keep I can send over to good old Yahoo and then get back when completion of new install is done right? 
I mean, that all I have to do is tell it to do a complete install and it all gets installed on the whole hard drive?

Thanks

Tom

---

### Post by Merk42 on 2009-12-17
> **Georgia boy said:**
> Okay, from what I've been reading in this thread is it's okay to do an upgrade. But, I'm using Hardy Heron and dual booting with XP. So, when the next LTS 10.04(?) comes out in April I want to get rid of XP completely  and just have the next LTS installed. So, that means for me I would need to get a Live CD for that and just have it do a complete install right? As far as the back up goes, I don't have a separate /home so anything I really want to keep I can send over to good old Yahoo and then get back when completion of new install is done right? 
I mean, that all I have to do is tell it to do a complete install and it all gets installed on the whole hard drive?

Thanks

Tom

You don't have Ubuntu installed via WUBI do you?
If not, you can upgrade without a LiveCD (though I'd recommend you use a LiveCD).
You can just format the Windows Partition and run update-grub2.

If you want to use the LiveCD and make a separate /home partition I recommend 3 things
[list=1][*]Wait until April, much closer to 10.04's release
[*]Look for a thread already addressing someone wanting to do it
[*]If one is not found make a different one (don't post it in this thread)
[/list]

---

