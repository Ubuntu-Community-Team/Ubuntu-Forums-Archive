---
title: "Fresh install Karmic"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by Cheeky Charlie on 2009-11-21
Hi,

"Interesting" back story:
I got 9.04 a little while ago, installed as dual boot, but couldn't connect to my bt home hub and got a bit bored.  When Karmic came out I decided to have another go.  I read two key things: (1) Karmic has better wireless support and (2) that I would need to apply all the upgrades to Jaunty before upgrading the system - with no internet on my ubuntu install I realised this wouldn't be possible so have torrented and burned a Karmic iso (in Vista).

Now I am stuck :(

Problem:
When I boot from the CD and try to install the OS, I only get three options:
(1) Install alongside - where 9.04 is left in place, and 9.10 takes a further chunk out of my Vista partition (I have no desire to maintain an Ubuntu archive on my HDD).
(2) Kill everything else (no)
(3) Manual - I suspect this is the way to go (given the immediacy of failure in the other two choices) but then I get to a place where I don't know what to do, in the menu that comes up, I try selecting the ext3 partition and going forward but it tells me I haven't done something to the partition and stops (sorry, recollection is hazy as I have to back out, and restart in Vista to get on the interweb to ask questions).

Thanks for reading, sorry for obscene length.

tl;dr - how do I fresh install Karmic Koala over Jaunty Jackalope?

Thanks,
CC

PS - I'm sure this is very simple, I'm sure it has beeen asked before, I have searched for about 45 minutes and read several articles, unfortunately, most of the content I find seems to "gloss over" this bit - presumably it's easy when you know how.

---

### Post by peculiar penguin on 2009-11-21
> 3) Manual - I suspect this is the way to go (given the immediacy of failure in the other two choices) but then I get to a place where I don't know what to do, in the menu that comes up, I try selecting the ext3 partition and going forward but it tells me I haven't done something to the partition and stops (sorry, recollection is hazy as I have to back out, and restart in Vista to get on the interweb to ask questions).You need to select the partition, click the Edit or Modify or whatever it's labelled button below, choose a file system (ext3 or ext4), mount point ("/" if you use a single partition for Ubuntu) and tick the Format partition checkbox.

---

### Post by kansasnoob on 2009-11-21
Figure out your partition numbers before even beginning. Quite often just the output from Terminal of the following command is enough to figure it out:

```
sudo fdisk -l
```

BTW that's a lower case L.

If you're totally unfamiliar with the way partitions are numbered in Ubuntu post that output here and we'll try to help you figure it out.

---

### Post by Temposs on 2009-11-21
Essentially, you're going to need to overwrite the Jaunty partition. In the manual partition setup, select the ext3 partition(presumably where Jaunty is installed), and set it to be deleted(use the Delete option). It will not delete until you set everything up, so don't worry. Then, it should show just your Vista partition and a bunch of empty space.

What we want to do now is make it easy for you to be able to reinstall your Ubuntu any time you want without having to overwrite your personal data in your home directory. For this we need to make one small partition that will hold the system files of your install. The second large partition should hold your home directory.

Root partition:
Right click on the empty space and click "New". Make this new partition about 8-14gb, depending on how large your HDD is and how much you want to devote to system files. It should be set as the primary partition, set it as bootable, with ext4 as the filesystem. Probably make sure it's at the beginning of the free space. In the part that says "Mount to", put a forward slash(/). Click Add/OK, and you should then see your new small ext4 partition.

Home partition:
Right click on the empty space and click "New". Make this new partition as large as you want, probably you just want to take up the rest of the free space. It should NOT be a primary/bootable partition. You can choose ext3 or ext4 as the filesystem. In the part that says "Mount to", we'll put the home directory(/home). Click Add/OK, and you should then see your new large home partition.

Continue the install like this. Now, whenever you need to reinstall, you just overwrite the small root partition, and your home directory will stay perfectly in tact :-)

---

### Post by Cheeky Charlie on 2009-11-21
I am such an impatient idiot.

So,

Thank you very much for getting back to me.  I think I probably would have been able to follow peculiar penguin's advice, if it weren't for problems in my brain...

Please bear in mind, I have been searching for quite some time on this topic and have reached an end-of-tether type situation... I found one more link... I right-clicked My Computer -> Manage -> hard disks... I *deleted* the partitions (ubuntu & swap) for ubuntu. 

NB Noobs, don't do ^that^ !

The plan was - "if that bit of HDD is free space again - I will be able to install into it".  But it would not install (lots of code, unexpected error - expectation being "the user is not a total prat" - perhaps).
Then I got this problem, in a big way.
[http://www.linuxquestions.org/questions/linux-newbie-8/grub-error-22-deleted-partition-377590/](http://www.linuxquestions.org/questions/linux-newbie-8/grub-error-22-deleted-partition-377590/)
This demonstrated to me the value of patience, and helped me to recolour my pants.

Even booting direct from the CD, the "nearest" option to Vista is boot from 1st HD - i.e. GRUB - i.e. busted.

Sooooo, I booted to the KK CD, and selected "install without affecting windows (I think this is the virtual environment option???) - Once running in this, I then elected to install the OS proper - which DID allow me to select the liberated 20Gb I had set aside for Ubuntu, (currently 84%) I hope that this will refresh GRUB record.

So, it may work, and I deserve my panic, and *most importantly, I must apologise for **asking a question and not waiting longer for an answer **because I believe that is **rude**, so sorry about that*.  (I did wait for over half an hour - but, clearly, just another 15 minutes would have had me going in the right direction.

Thanks,
CC

PS - please do get back to me with more help (and tell me in what way I continue to be a prat) - if you like, you could write a preliminary post saying something like "CC, being a thoughtful and charitable citizen, I am going to write you a worthy and well-thought answer, this will take a few minutes, try not to be a total pillock in the intervening time" - this would help me immensely

---

### Post by Cheeky Charlie on 2009-11-21
Update:

The install I described above worked - everything is jazzy, I can load into either OS no probs and my life has meaning once more.

When I become more familiar with Linux, I will install the next release as per Temposs's wonderful instructions so I can keep my personal settings/documents.  As it stands, I think I may be better served overwriting any edits I make in my first few weeks... in any case, all my stuff is on Windows atm.

Thanks all for the help.

---

