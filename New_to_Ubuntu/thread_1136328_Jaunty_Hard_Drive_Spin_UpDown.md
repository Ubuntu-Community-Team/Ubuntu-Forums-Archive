---
title: "Jaunty Hard Drive Spin Up/Down"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by ertw1 on 2009-04-24
I recently upgraded to Jaunty on my laptop and I noticed that the hard drive spins up and down constantly.  This is a nuisance when I have to wait for the hard drive to spin up when accessing files.

I didn't hear the "clicking" of my hard drive heads indicating the load cycle bug (a problem I had in the past).  I still have this issue after I enter the command, "sudo hdparm -B254 /dev/sda" or have it run on startup.

I didn't have this issue in Ibex or Hardy.  Has Jaunty implemented some new power management scheme?  Why is it overriding me when I set the power management level to 254?

Thanks in advance!

---

### Post by victorgreen on 2009-04-27
Same problem. I have to deal with this every single upgrade/install and do it a different way each time. This'll take forever to hunt down online... great.

---

### Post by MontelEdwards on 2009-04-27
Do you know which filesystem you are using?
When I was using XFS I got the same thing.
EXT4 is great to me.

---

### Post by victorgreen on 2009-04-27
Im still using ReiserFS. Ill probably switch to ext4 the next time I wipe and reformat this thing.

---

### Post by MontelEdwards on 2009-04-27
You should.

---

### Post by victorgreen on 2009-04-27
Anyhow, you are not noticing undue/disruptive spin down with ext4? Cause the relase before Jaunty PM was so aggressive by default that it completely spun down the disk every 30secs or so to the point that movies would stop/hang and then the picture'd get all corrupted. Stupid upgrade wiped my config file [that was my fault], though so far with my limited testing looks like its not quite that bad. 

On a totally unrelated note, have you noticed worse batt life with Jaunty? Every release i get a half hour or so less on my x61 with extended battery. Its down to 4 hours with wifi :(

---

### Post by MontelEdwards on 2009-04-27
No, none at all. When Jaunty was in Alpha, i did but not now because i did a clean install with the stable. And no, I am not sure about the battery life. I use a workstation.


But I did find a little tip on it here > [http://www.totalnetsolutions.net/2007/08/13/how-to-increase-battery-life-in-ubuntu-or-debian-linux/](http://www.totalnetsolutions.net/2007/08/13/how-to-increase-battery-life-in-ubuntu-or-debian-linux/)

---

### Post by inobe on 2009-04-27
> **victorgreen said:**
> Im still using ReiserFS. Ill probably switch to ext4 the next time I wipe and reformat this thing.

man i haven't used reiser since suse 9.2.

---

### Post by MontelEdwards on 2009-04-28
Well Reiser is mainly for small files, so that could explain the problem with the videos. Reiser would be good for say like you have Wordpress or something installed on a old computer. I think Novell discontinued ReiserFS on SUSE because he was convicted of murder of his wife,  Nina Reiser

---

### Post by victorgreen on 2009-04-28
He was. I dont care, the filesystem isnt gonna murder me.

---

### Post by MontelEdwards on 2009-04-28
> **victorgreen said:**
> He was. I dont care, the filesystem isnt gonna murder me.
I can imagine a your HDD turning to a monster.

---

### Post by steeeb on 2009-04-30
> **ertw1 said:**
> I recently upgraded to Jaunty on my laptop and I noticed that the hard drive spins up and down constantly.  This is a nuisance when I have to wait for the hard drive to spin up when accessing files.

I didn't hear the "clicking" of my hard drive heads indicating the load cycle bug (a problem I had in the past).  I still have this issue after I enter the command, "sudo hdparm -B254 /dev/sda" or have it run on startup.

I didn't have this issue in Ibex or Hardy.  Has Jaunty implemented some new power management scheme?  Why is it overriding me when I set the power management level to 254?

Thanks in advance!

same exact problem here.
interestingly enough, hdparm.conf is entirely commented out (not sure if it was before upgrade to jaunty).

---

