---
title: "Upgrading to 10.04"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by BobJam on 2010-05-13
I've read some posts on this forum where users have cursed the 10.04 upgrade . . . of course, the vast majority probably have had no problems and wouldn't really bother to come here and just say "Atta boy".  I mean, a forum is likely skewed because it's a discussion of WHAT WENT WRONG.

In any case, I'm a bit reluctant to make the leap from my 9.10 (which works just fine) to 10.04.  However, I would like to reap any improvements that have been made.  So, I'm pretty much on the fence.

I started with 8.04, and as I recall I had no problems upgrading to what I have now.  I have the "notice" that 10.04 is available through my Upgrade Manager.  I think that is how I did it before.

I don't recall burning any upgrade CD's and installing from them, so I'm pretty sure I did it via Upgrade Manager.

That "upgrade" button in Upgrade Manager keeps tempting me and I will no doubt do it sooner or later.

Which brings me to my question:

[LIST]
[*]Is there anything I should do to prepare for this, or can I just press the "upgrade" button and be done with it?
[/LIST]
I've looked at some known issues, and none of it would seem to pertain to my system.

Another question:

[LIST]
[*]Does anyone have a link to a site that discusses any kind of preparation that would be prudent?
[/LIST]
I don't want to find myself unable to connect or otherwise losing any of my software.  I know that's always a risk, but I would like to minimize that risk as much as possible.

---

### Post by mörgæs on 2010-05-13
A good first step would be booting with a live CD. This gives a good indication of how well your system likes 10.04.

---

### Post by pizza-is-good on 2010-05-13
> **mörgæs said:**
> A good first step would be booting with a live CD. This gives a good indication of how well your system likes 10.04.

Good idea. Do try that.

Also, and just as security, do back up your home directory or wherever you save your files.
You should not loose any of the programs that you have installed (I never have, when I do upgrade. Most of the time I just do clean installs.).

Good luck!

~pizza

---

### Post by Iowan on 2010-05-13
I've upgraded a couple of times without incident - maybe I've just been lucky. Keep in mind that you probably won't upgrade to ext4, or grub2... (although I have no proof to back me up).

---

### Post by ranch hand on 2010-05-13
If you are on ext3, likely seeing how you have been upgrading, you will miss a lot of the advantages of 10.04.  Yes there are instructions for changing to ext4 from ext3.

I did that in testing just to see  and can tell you it is not the same as the real thing at all and not really worth the bother.

More important, to me, is a little more information on your box.  Is Ubuntu the only OS installed?  What is your video card (or controller)?  Are you installed on one partition or two (or more)?  Do you have a /boot in particular?  What size is your drive?

The upgrade, as you say, goes well for most folks.

This is an LTS and will be around for a long time.  If I were you I would think about waiting a bit.  LTS releases have "point" releases during their life span.  10.04.1 is due out the end of July.  This should take care of all existing important bugs, not only in the OS but in the ISO itself.

If you are not in a big hurry, I would wait.

That said, a new OS is a lot of fun to explore.  I spend most of my time on 10.10-testing (pretty much just 10.04 right now but we do have a new kernel coming) so I can understand wanting the new thing.

Give the above info and it will make a difference in the recommendation.

---

### Post by BobJam on 2010-05-14
> **ranch hand said:**
> If you are on ext3, likely seeing how you have been upgrading, you will miss a lot of the advantages of 10.04. Yes there are instructions for changing to ext4 from ext3.So can you give me a link for these "instructions"?

> **ranch hand said:**
> I did that in testing just to see and can tell you it is not the same as the real thing at all and not really worth the bother.Not sure I'm understanding what you're saying here.  Do you mean that keeping my file system as ext3 would not be worth the effort of going to 10.04?

> **ranch hand said:**
> Is Ubuntu the only OS installed?On one machine, NO.  It's a dual boot, with Windows XP HE SP2.  That's an HP ze4700 Laptop, vintage 2004.  That one really is my "backup" machine, and I don't use it much.  Perhaps that would be a good one to 'speriment with.

On my other machine, which is my main machine (the one I'm on now and use regularly) and is a Dell Inspiron 1545N laptop . . . YES, Ubuntu is the ONLY OS on it.

> **ranch hand said:**
> What is your video card (or controller)?
On the HP, it's a RADEON IGP 320M.

On the Dell, it's a Mobile 4 Series Chipset Integrated Graphics Controller

> **ranch hand said:**
> Are you installed on one partition or two (or more)?
On the HP, I have one partition of course dedicated only to Windows, and then BOTH my root and home Ubuntu directories on the same partition.

On the Dell, where I have ONLY Ubuntu (no dual boot), I have the root on one partition and home on another.

> **ranch hand said:**
> Do you have a /boot in particular?Answered above?

> **ranch hand said:**
> What size is your drive?On the HP, the HDD is 120GB.

On the Dell, the HDD is 250GB

> **ranch hand said:**
> If I were you I would think about waiting a bit. LTS releases have "point" releases during their life span. 10.04.1 is due out the end of July. This should take care of all existing important bugs, not only in the OS but in the ISO itself.Yes, I was thinking that.  Did not know about those "point" releases.  Makes sense to wait.  Will likely do that.

> **ranch hand said:**
> If you are not in a big hurry, I would wait.No, I'm certainly not in a big hurry.  This was EXACTLY the kind of advice I was looking for . . . thanks VERY much.

> **ranch hand said:**
> Give the above info and it will make a difference in the recommendation.If you need anything more, let me know.  Thanks again.

---

### Post by nhasian on 2010-05-14
i've upgraded several machines from 9.10 to 10.04 with no problems.  that said since you are still running EXT3 and the old grub, i would just suggest a fresh install for you instead.  back up your /home to a usb thumbdrive or external hard disk.  repartition your hard disk for EXT4, copy the /home back and start the fresh install.  do not format the partition with your /home data during the install process.  all your settings will be saved, you will just need to reinstall any programs you had before.

---

### Post by ranch hand on 2010-05-14
@BobJam
First;

[http://www.debian-administration.org/article/Migrating_a_live_system_from_ext3_to_ext4_filesystem](http://www.debian-administration.org/article/Migrating_a_live_system_from_ext3_to_ext4_filesystem)

If you read the page it will tell you that the files need over written to become ext4.  This is true.  However, I did this in testing where we were getting upgrades at about 110MB per day.  I keep the converted OS' (2) for two months of this.  That is more over writing than you will see in a year or two.

I could see no difference in performance compared to the same OS (10.04) installed on ext3.  The difference was quite noticible between those ext3 and "converted" ext4 OS' and any of my other versions of 10.04 installed on ext4 including upgrades from 9.04 (yes I have been using ext4 with no problem from 9.04 on).

That should take care of your first 2 questions.

To show my extensive knowledge of MS systems I assume that XP HE SP2 means;
XP>I am aware there is a release by this name.
HE>Horrendous Excrement?
SP2>Super Pissy Too?

I have never had a lot of luck with the ATI driver and do not like the effects so my box runs on the open driver with effects set to "none".  However, in testing 10.04 I did have compiz (hate it) running on one of my installs, with the open driver and effects set to "extra" with no problem.

I also believe that the Intel drivers are much better in 10.04 too.

With the size of your drives I would not hesitate to upgrade the HP and maybe make a couple small partitions (/=10Gb and /home=20Gb) on the Dell and dual boot it.

I think that you may want to edit the menu entry to not have a splash as plymouth is buggy on some hardware but yours may be fine.  The folks for whom it works have tremendous boot up speeds even with fairly slow HDDs.

My box is not one of those and I have had to modify my boot menu and drop ureadahead on my upgraded to 10.04 installs.  The clean installs do better, even with a splash.  They do better without the splash too though.

Had to wait until I was back on my test drive to have the link for the ext3-4 stuff.  I leave my box on running boinc all the time but at night I use a stable (9.04) install instead of a testing install.

Hope that helps or at least confuses you.

---

### Post by XCan on 2010-05-15
As far as I know, simply wanting ext4 over ext3 alone never warrants a clean install. Ext4 just does not seem to be what it was designed and thought to be. :(

---

### Post by ranch hand on 2010-05-15
Well,  I am not sure what you mean by that.

I do know that it is faster on my box and that is true with several others that I know of.

I also get much better performance from saved video file playback.

---

### Post by 12_String on 2010-05-15
I'm not saying don't switch, just be warned. I had nothing but trouble and even had weird lines cutting across the screen and everything. Nothing worked, unless it was extremely slow. I had to switch back.

---

### Post by ranch hand on 2010-05-15
That is real interesting.  Must be that it likes some hardware a lot better than others.

I like your sig a bunch.

---

