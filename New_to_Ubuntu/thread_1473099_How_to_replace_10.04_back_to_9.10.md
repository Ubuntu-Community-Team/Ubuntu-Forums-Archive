---
title: "How to replace 10.04 back to 9.10?"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by jkmacr on 2010-05-04
I have completely messed up my system - 

[LIST]
[*]Upgraded 9.10 to 10.04 on the weekend
[*]Hoped it would address issues with slow DVD RW performance (best is 4x) and SATA HD file performance. It did not.
[*]Found 10.04 and new nVidia drivers broke the video performance - could no longer play HD video.
[*]Started playing with nVidia drivers, to go back to 185 (which worked) from 195
[*]Seriously broke something - lost access to Gnome
[*]Was able to get to terminal a few times. More messing about trying to get Aptitude to re-install stuff properly. (but I really don't know what I am doing)
[*]Stuck with just the terminal mode (which is progress) - no boot options, no GUI, no recovery mode option - just the terminal log-in prompt. Shades of 1980.
[/LIST]
I would like to simply re-install 9.10 from CD. When I boot the CD, I have the option of installing it beside 10.04 or wiping the disk. I want to blow 10.04 away and put 9.10 back. And, I would rather not wipe the drive.

System is Zotac Atom Ion, 4GB RAM, 1TB SATA drive + SATA DVD RW, set  up as an  HTPC. Drive is configured with 100 GB EXT4 boot partition, EXT3 for  files, and 10GB swap space.

I am old enough to know better than to try new releases. Especially when the system was stable even with the sub-par drive performance. Stupid on my part.

j

---

### Post by SR_ELPIRATA on 2010-05-04
It all depends on how you configured the drive and where your data is. Since I dont consider myself a guru in Ubuntu... most I would recommend is to use an external drive and a live CD to get the HTPC data out, which I suppose is as vital as mine is.

Once your very important data is out, just start over with the 9.10 live cd and use the whole drive. One thing you can do, to avoid this from happening again, is to partition the drive so that your data and the main system are in separate places.

I understand that you can even have the /home/ set so that is sitting in a separate partition but I've never done this personally, once your data is safe... I guess you could try it out :)

I'm intrigued, though, on how big your swap area is. I also have a HTPC as you can see on my signature and usually the swap space is related to how much ram you have, but, far as I remember, my swap has never been bigger than 1.4GB, and when you have a lot of ram... the use of swap is not the best option, but I dont really know why you have it set so high.

I use my HTPC for HD stuff mostly, but also contains a lot of SD movies and tvshows, and my music collection.

Anyways, hope the going back to 9.10 goes smoothly.

ELP

---

### Post by JigglyWiggly_ on 2010-05-04
Just tell it to use the whole disc, oh and just backup your home folder if you want your stuff.

---

### Post by jkmacr on 2010-05-04
I did set up the /home/ drives for the user on the data partition. The system is on its own partition. 

I am going by memory on the swap drive size, it might be different.

If as JigglyWiggly_ suggests, I end up having to wipe the whole drive, I expect I will switch OS and chalk it up to experience. Cheaper than springing for an external drive.

---

### Post by uRock on 2010-05-04
If you have the separate home, then just do a clean install and be sure to highlight the /home for what it is and make sure it isn't set to format it.

---

### Post by jkmacr on 2010-05-05
So when I put in the 9.10 disk, the options presented are
- install side-by-side
- wipe the entire disk and install
Neither really what I want

Where can I find instructions to replace the existing OS with the older version?

---

### Post by uRock on 2010-05-05
> **jkmacr said:**
> So when I put in the 9.10 disk, the options presented are
- install side-by-side
- wipe the entire disk and install
Neither really what I want

Where can I find instructions to replace the existing OS with the older version?

There should be a third option which offers to choose partitions manually. Which partition setup do you already have?

---

### Post by jkmacr on 2010-05-05
Dove in an used the option you suggested, seemed to have got 9.10  reinstalled and recognizing my /home folder on its partition.
 
 Now have to recreate the steps I had to go through to get the wireless,  video and HDMI sound to work again. (And I know, I should have taken  notes.)
 
 thanks.

---

### Post by cdude42 on 2010-05-05
cool, it worked

---

### Post by uRock on 2010-05-05
> **jkmacr said:**
> Dove in an used the option you suggested, seemed to have got 9.10  reinstalled and recognizing my /home folder on its partition.
 
 Now have to recreate the steps I had to go through to get the wireless,  video and HDMI sound to work again. (And I know, I should have taken  notes.)
 
 thanks.
It's sad that you had to go back a release, but I am glad you didn't lose your data. I kinda try to keep a log of anything special I do to my system just in case I have to recover it. I just write out an email of what I did, and send it to my storage account, yahoo has to be good for something.;)

---

