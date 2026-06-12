---
title: "[SOLVED] Help With Many Things In Feisty!"
date: 2007-05-21
forum: Networking &amp; Wireless
---

### Post by pHreaksYcle on 2007-05-21
This is going to be long whether I like it or not, so I will TRY to keep it short...thanks for your time in advance whoever is brave enough to help! (and yes, I did try Google for all this stuff first!) Any questions about this, please respond here or to dknoll {[at]} sjci DOT (((COM)))

I am using a:
Dell Inspiron 1501 LAPTOP (WXGA wide screen)
AMD Turion 65 (2.0GHz/512KB)
80GB Hdrive
ATI RADEON Xpress1150 w/ 256MB of RAM
Came with Image Restore on Disk
Windows Version=Vista

Have Intermediate to Advanced knowledge across the board. I know lots of stuff, but have little things missing here and there. (That is what G00gle is for right?)

I installed Ubuntu Feisty Fawn, using it for school for about one month/month and half, works great for taking notes etc. One problem, NO WiFi, just wired, which=pain in ****. No matter what I do, no matter how many guides I follow, programs/firmwares I install (ie: ndiswrapper) it just wouldn't work. (Still doesn't)

I also wanted to get Beryl to work. No good there either, followed all of the steps, tried every guide I could follow, nothing.

I have been using this site [http://www.ubuntu1501.blogspot.com](http://www.ubuntu1501.blogspot.com)
and it's guides, no good. (Did mail out for the free sticker though!)

My question is how to get WiFi working and Beryl or Compiz or whatever the hell it is! The jigglyz and the desktop cube! That is all I ask!

IN ADDITION, to these problems, while trying to get these two problems to work, WiFi and Beryl (jigglyz ), I installed Uberyl. This is a not-very-known Spanish distro and it is supposed to have Beryl and WiFi on laptops working "out-of-the-box". (Or off the CD I suppose...) Needless to say, since I am posting this, none of this crap worked! Trying countless re-installs of Feisty and Uberyl (which is Ubuntu version Edgy), and not knowing ANYTHING about partitioning except where Windows is located, I have ended up with FOUR OS's ON MY LAPTOP! That is a secondary issue, but one I would like to take care of if possible. I do not want to screw up my Vista installation, but if that is part of someones grand scheme to make these things work, I'm down! I have no qualms about wiping the slate clean if that is what it will take and I have instructions on how. I am trying to at least wipe all Ubuntu from my system and start over with just Vista.

BTW, this is the output from GRUB on boot-up if it helps (or even if it doesn't, I guess...)

Ubuntu Kernel 2.6.20-15-generic
"SAME THING" recovery mode
then the Ubuntu memtest option
Other:
M$ Vista (loader)
Ubuntu 2.6.17-11-generic (on /dev/sda5)
Ubuntu 2.6.17-11-generic revovery mode on (/dev/sda5)
Ubuntu 2.6.17-10-generic (on /dev/sda5)
then the Ubuntu memtest option.

I assume the -10 is Uberyl because Uberyl is Edgy and that is an older verions which=older number...
Sorry if I rambled a little bit, but it's late and I am strung out about this.
I would like to stay with Linux (specifically Ubuntu, cuz it has a very strong community it seems), but this is starting to discourage me lots... Thanks SO MUCH for your help in advance if any is available!!!

---

### Post by spin2cool on 2007-05-21
Sigh...  

Step 1: learn to use punctuation and sentence structure properly.  A well-crafted post is much easier to respond to.

Problem 1: Beryl doesn't work:

Beryl doesn't work for a lot of people.  That's why it's development software, and not included in Ubuntu.  If you've followed the how-to guides and scoured the forums and still can't get it to work, you may just be out of luck for now.  If you haven't done these things, try them before giving up.

It's worth noting that linux is an operating system, not an video card demo.  Most of us are more concerned with a solid system than we are with shiny pretty wobbly things.

Problem 2:  Mulitple OSes installed.
Several of those OSes are just different kernel versions.  When a kernel update comes through, Ubuntu gives you the option to book into the old one, in case the updates screw something up.  Search these forums for something like 'remove old kernel' to find out how to remove them.

To get a better idea of how your partitions work and are set up, take a look at gparted.

```

sudo apt-get install gparted
sudo gparted

```

It'll show you what partitions you have set up and their sizes.  It will also allow you to change your partition table, so be careful not to commit any changes that you don't want.

Problem 3: Wireless
Sorry, I can't help you with this one. Try searching these forums for your computer model/network card model to see what others have done.

---

