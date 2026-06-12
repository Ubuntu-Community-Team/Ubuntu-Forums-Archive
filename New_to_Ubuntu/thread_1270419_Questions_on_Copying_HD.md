---
title: "Questions on Copying HD"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by ovid9 on 2009-09-19
My machine current has a 20 gig HD as the primary drive.  I use an 80gig external as extra storage.  The 20gig has started making some odd sounds and reading slow at times.  I have access to another 80 gig HD and want to copy my system from the 20 to another 80 (giving me 1 internal 80 as my system, an external 80 for mass storage, the 20 sitting on a shelf as a desperation back)

This handy dandy thread [here]("http://ubuntuforums.org/showthread.php?t=1100701&highlight=copying+Hard+drive") gave me lots of info and I believe I'm going to use the dd command to do this.

However, final questions before I take the plunge.  

First, I would assume I need to format the new HD to the same filesystem type as my current HD right?   ext3

Second, after the copy, I can just unplug the 20 gig, plug in the new 80 gig and it SHOULD boot right off of it?  Right?  or, is there another step in there?

Third, any potential issues you all see with this that I don't even know about.  Please tell me!

Thanks!

---

### Post by mapes12 on 2009-09-19
I've done this and dd works. I used a "raw" drive that was not formatted but I can't see formatting ahead of the job being a problem. You may have to juggle around the master/slave jumper settings as you go.

This is what I did:

To make an exact copy of a drive install the new drive. Then boot from a Live CD like Gparted. Go to Terminal and enter:
```
dd if=/dev/sda of=/dev/sdb
```
#where sda is the old drive and sdb is the new drive. 

Then disconnect sda from its IDE channel, connect sdb into sda's IDE channell (thus making it sda). And vice versa for sdb. Boot from a Gparted Live CD. Format sdb (the old HDD). Reboot, removing the GParted CD and everything will boot from the new HDD.

---

### Post by ovid9 on 2009-09-19
Ahah!  

A snag in my plan.  So, I need to boot of a live CD to do this?  I suppose it makes sense as I would need to be using sda while trying to copy it to sdb.   

Now the fact my computer is archaic and has no CD burner becomes a problem. 

But, if I do get a live CD and boot off of it, then I can just do the sda to sdb copy and all should be good right?

---

### Post by mapes12 on 2009-09-19
> I suppose it makes sense as I would need to be using sda while trying to copy it to sdb. Correct.

---

### Post by ovid9 on 2009-09-19
Thanks.  Since I now have to burn a live CD (mine met our cats, the cats somehow triumphed) I probably won't get to this today.  

I'm very novice at all this stuff so I'll make sure to follow up and let people know how it went.  

I think I'll copy things like bookmarks and pictures to my other HD just in case I just to a new install.

Thanks again!

---

### Post by jerrrys on 2009-09-19
may want to go this route

[http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu](http://www.osdisc.com/cgi-bin/view.cgi/products/linux/ubuntu)

---

### Post by ovid9 on 2009-09-19
well, here's what i did.  using my wife's windows machine, i burned a couple copies of a liveCD.

Booted up fine.  I attempted to use the dd command, but, I couldn't tell it was doing anything.  It was sitting there and sitting there and not doing anything.

So, I tried a route I saw on here somewhere.  I copied the hidden files from my /home folder, backed them up, put in the new hard drive and did a fresh install.

Not how I wanted to do it, but good enough.  I wish I knew why "dd" didn't seem to do anything though.

---

### Post by halitech on 2009-09-19
You also could have used Clonezilla, it is designed for just this type of thing.

---

### Post by ovid9 on 2009-09-19
well, if I get things set up on here as i like again.  When I build my new computer (sometime in the next 3-5 months) I will probably try using that! 

This worked, but, it has created annoyances.

---

