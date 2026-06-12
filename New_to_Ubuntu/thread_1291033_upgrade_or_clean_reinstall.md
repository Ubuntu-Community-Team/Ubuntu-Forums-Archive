---
title: "upgrade or clean reinstall?"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by smileyguy on 2009-10-14
Don't know why I couldn't find this topic so easily when searching the forums quickly but:

When Karmic Koala comes out, is there a "best way" to upgrade from 9.04?

I am referring to opting to upgrading/updating the installation over my existing installation or completely wiping the hard drive and starting from scratch again.

I am not really worried about my files or settings, I just know with Windows, a clean reinstall was always the best way to remove any old problems.

---

### Post by s.fox on 2009-10-14
Hello,

I am not sure that a "best" way to get the latest version exists.

From personal experience I have never had any issues with just upgrading rather than clean install.  That said, I usually wait 3-4 months after the release before upgrading just to be on the safe side.  

Sorry can't really give a definite answer.

-Silver Fox

---

### Post by DougieFresh4U on 2009-10-14
> **smileyguy said:**
>  a clean reinstall was always the best way to remove any old problems.

You answered your own question.
I always update/upgrade, as I feel there are 'no old problems' for me to get rid of.

---

### Post by j7%&lt;RmUg on 2009-10-14
Well, there is no "best way" to get karmic, but their are several benefits of clean installing over upgrading:

- It has a much higher success rate(there is a chance that upgrading can fail or show errors)
- You can only upgrade your bootloader if you clean install(its very difficult to manually upgrade)
- You can choose between 32 and 64 bit when clean installing but not when upgrading
- you can choose ext4 over ext3 when clean installing but not when upgrading
- You can more easily repartition your hard drive when clean installing

For example, when karmic comes out im doing a clean install for the following reasons:
- Want grub 2 bootloader
- Switching from ext3 to ext4
- Switching from 32-bit to 64-bit

Ultimately its up to you but if you are unconcerned about your data and want ext4, grub 2 or 64-bit then i highly recommend you clean install.

---

### Post by jrandolph on 2009-10-14
In my experience I find its easier to do a fresh install 
Dont know if its the best option but its what I always do
But like it was said before I also wait a while before doing so just to let the bugs get worked out

---

### Post by MelDJ on 2009-10-14
+1  to clean  reinstall. just have to backup your files and put them back after reinstallation

---

### Post by MoebusNet on 2009-10-14
I think you will be happiest with a clean installation, especially if you don't care about saving your configurations or data. On the assumption that you will be using your system in the future for accumulating documents, music and other data files you would prefer to keep, please allow me to recommend that you do your clean install with a separate /home partition.

The advantage of this is that if you ever need to reinstall your operating system, you can almost always do so without losing your data and settings.

These links will give you more information:

[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

If you haven't read any of aysiu's writing on Ubuntu & Linux I highly recommend it:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

Best of luck!

---

### Post by coldReactive on 2009-10-14
Personally, I always did a clean install of Ubuntu each time a new version came out.

---

### Post by CharlesA on 2009-10-14
> **coldReactive said:**
> Personally, I always did a clean install of Ubuntu each time a new version came out.

I usually try to do this. Even if it means I have to spend some more time doing config.

---

### Post by BDNiner on 2009-10-14
I normally do a clean reinstall after making a backup.

---

### Post by coldReactive on 2009-10-14
> **BDNiner said:**
> I normally do a clean reinstall after making a backup.

And I always save my documents to a flash drive, so no worries there :)

---

### Post by Mighty_Joe on 2009-10-14
I got burned in the Gutsy upgrade.  It left me with a very unstable system and no way to get back to the stable Feisty.  Never again.  My procedure now is:
- wait a few weeks until the community discovers resolves the common issues.
- test the new release for a week or so with a Live USB install so I'm sure it works on my hardware
- back up my files and do a clean install.

---

### Post by QIII on 2009-10-14
> **nisshh said:**
> 
For example, when karmic comes out im doing a clean install for the following reasons:
- Want grub 2 bootloader
- Switching from ext3 to ext4
- Switching from 32-bit to 64-bit

Ultimately its up to you but if you are unconcerned about your data and want ext4, grub 2 or 64-bit then i highly recommend you clean install.

Although I generally agree with a clean install, I can't say it is for the first two reasons above.

You can update Jaunty to GRUB2 already.

You can update your file system to ext4 already.

I'm running GRUB2 and ext4 on my 32 and 64 bit Jaunty machines already.

Going from 32 to 64 bit is certainly an issue, unless you are already running 64 bit and want to keep it that way.

---

### Post by bhishan on 2009-10-14
backup ur stuff and do clean install

---

### Post by LewRockwell on 2009-10-14
> **mighty_joe said:**
> i got burned in the gutsy upgrade. It left me with a very unstable system and no way to get back to the stable feisty. **never again**.

My procedure now is:
- wait a few weeks until the community discovers and resolves the common issues.
**- test the new release for a week or so with a livecd/liveusb test-drive so i'm sure it works on my hardware!!!!!!!**
- back up my files and do a clean install.

+ 1,000,000,000,000,000,000,000,000,000,000,000,000

.

---

### Post by Kaizzer on 2009-10-14
from what if read [here]("http://ubuntuforums.org/showthread.php?p=8104667")

clean install is the best way to go..also .. waiting a few month till it has been community proven seems very wise... 

Regards.

---

### Post by bwallum on 2009-10-14
Put your home folder in a separate partition to save all your stuff. It's really good if you can put that partition on a new hard drive. (label it HomeHD or something similar) Then do a fresh install 3 weeks after the release (allows for any last minute major bugs to surface and be fixed). To link in your 'HomeHD' put this line at the bottom of the /etc/fstab file on your newly installed Karmic drive:
```
LABEL=HomeHD	/home	ext3	relatime	0	2
```
That's safe and you get to keep all your settings. You lose any past tinkerings in the system (like proprietory drivers) and get a clean start-again system.

....well thats what I'll be doing anyway and I have been updating Karmic from alpha. Its good to have  a flush in my opinion.

---

### Post by Mighty_Joe on 2009-10-15
> **bwallum said:**
> Put your home folder in a separate partition to save all your stuff. 
It's a good idea to keep your data separate from the OS, however, it can introduce other problems. Many applications save settings in your home directory and every once in a while an upgrade will have incompatibilities with previous version's settings (ask me how I know) :mad:

---

### Post by Ekeluo on 2009-10-15
Wow, I must be the black sheep of this topic. I upgraded my 'acceptably working' jaunty (after converting - not reformatting, **converting** the hard drive to ext4) to karmic beta and, though it's not perfect, it's better than how I started of with jaunty. I'm just saying an upgrade is **very possible**, but if you can afford it still go for the reinstall though (I can't not yet). Regardless, a separate home partition is still highly recommended.

---

### Post by cmcanulty on 2009-10-15
So can we upgrade to ext4 file system without losing our documents? Very helpful advice as I was planning to upgrade on Oct 29th!

---

### Post by QIII on 2009-10-15
ALWAYS do back ups before you do anything like this!  You shouldn't, under normal circumstances, lose anything.  But how often do you encounter "normal" circumstances?

DO BACKUPS FIRST!


You can, in fact, upgrade to ext4 and GRUB2.

This guy has a good method for upgrading to ext4

[http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21](http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21)

And here's a good bit on installing GRUB2.

[http://www.howtoforge.com/how-to-install-grub-2-on-ubuntu-9.04](http://www.howtoforge.com/how-to-install-grub-2-on-ubuntu-9.04)

If you install GRUB2 and are dual booting, also run:

```
sudo apt-get install os-prober
``````
sudo os-prober
``````
sudo update-grub2
```

---

### Post by Ingvar G. on 2009-10-15
One more point for clean install.

Good luck!

---

### Post by gdonwallace on 2009-10-15
For me, at least this time around I will be doing both.  I have been running the beta on my laptop and getting daily updates, so when the final release comes out, there should not be any problems.

As to the complete re-install.  I have to do that on my desktop at work.  So yes, I will be backing up some data and folders, but I feel better about the complete install on that machine.  I want to make sure that there are no problems, because this is the machine I do all my work on.

---

### Post by Penguin Guy on 2009-10-15
Upgrade, unless you have a good reason for doing a fresh install. When I did a fresh install I realised just how much I had customized my Ubuntu.

---

### Post by KhanTG on 2009-10-15
I tried upgrading with hardy and jaunty and still ended up having to do a clean install.  I, personally, am going to avoid the upgrade method for quite some time... you might also consider NOT upgrading; if what you have is working well for you, why bother (I have no room to talk, I constantly get betas and try out new {to me} distros). So...
 
  If you don't care and just want new stuff, flip a coin.
  If you have "mission critical" information; back it up OFTEN and stay with what works for you.

---

### Post by caco on 2009-10-29
Clean install works best ... don't forget to backup first! ;)

---

### Post by Zoot7 on 2009-10-29
Clean install with a seperate home partition is what i do these days. :)
Gave up on upgrades after Hardy to Intrepid broke everything.

---

