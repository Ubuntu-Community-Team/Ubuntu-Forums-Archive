---
title: "Very Frustrated User"
date: 2011-06-23
forum: New to Ubuntu
---

### Post by Mo-ayad on 2011-06-23
I've been using uBuntu for a while and I kind of like it. the first version I use was 10.10 so while updating to 11.04 it produced lots of errors like it claims my version is not genuine.

I thought of simply installing it all over. I downloaded the new version, burnt it, installed it (I chose to install it instead of not alongside the old buggy 11.04) and life is good.

While installing my usual softwares just now I found that it doesn't read any drives from my hard drive. I checked the file system drive and I was shocked: all of my drives are now fused into one. and of course you know that means everything has been completely and mercilessly annihilated. it happened without giving any notification in advance that this would happen.

I've very disappointed, upset and frustrated. You can never guess how my life depends on the data I "had". *BIG sigh* But it's futile now to cry and sit idle I can imagine.

What I wish for now are three things:
1) How to avoid such a problem in the future?
2) How to recreate partitions again in a simple way (I don't mind using that bloody installation disk again if it's going to help).
3) The best way to recover what is there to recover if possible.


Quick reply is more than appreciated and thank you very much in advance

---

### Post by haqking on 2011-06-23
> **Mo-ayad said:**
> I've been using uBuntu for a while and I kind of like it. the first version I use was 10.10 so while updating to 11.04 it produced lots of errors like it claims my version is not genuine.

I thought of simply installing it all over. I downloaded the new version, burnt it, installed it (I chose to install it instead of not alongside the old buggy 11.04) and life is good.

While installing my usual softwares just now I found that it doesn't read any drives from my hard drive. I checked the file system drive and I was shocked: all of my drives are now fused into one. and of course you know that means everything has been completely and mercilessly annihilated. it happened without giving any notification in advance that this would happen.

I've very disappointed, upset and frustrated. You can never guess how my life depends on the data I "had". *BIG sigh* But it's futile now to cry and sit idle I can imagine.

What I wish for now are three things:
1) How to avoid such a problem in the future?
2) How to recreate partitions again in a simple way (I don't mind using that bloody installation disk again if it's going to help).
3) The best way to recover what is there to recover if possible.


Quick reply is more than appreciated and thank you very much in advance

1) backups
2) Gparted or use the partitions manager during install (but read up on best practices first, 7 p's (proper planning and preparation prevents p*** poor perofrmance
3) as for recover, if you cna browse the contents of your disks then back the data up to an external drive before further loss.

also it wont use all the space for install unless you give it permission to during installation ;-)

---

### Post by wildmanne39 on 2011-06-23
> **Mo-ayad said:**
> I've been using uBuntu for a while and I kind of like it. the first version I use was 10.10 so while updating to 11.04 it produced lots of errors like it claims my version is not genuine.

I thought of simply installing it all over. I downloaded the new version, burnt it, installed it (I chose to install it instead of not alongside the old buggy 11.04) and life is good.

While installing my usual softwares just now I found that it doesn't read any drives from my hard drive. I checked the file system drive and I was shocked: all of my drives are now fused into one. and of course you know that means everything has been completely and mercilessly annihilated. it happened without giving any notification in advance that this would happen.

I've very disappointed, upset and frustrated. You can never guess how my life depends on the data I "had". *BIG sigh* But it's futile now to cry and sit idle I can imagine.

What I wish for now are three things:
1) How to avoid such a problem in the future?
2) How to recreate partitions again in a simple way (I don't mind using that bloody installation disk again if it's going to help).
3) The best way to recover what is there to recover if possible.


Quick reply is more than appreciated and thank you very much in advance
Hi, you can use testdisk from the livecd, but you must dont boot your real hard drive until you are done.
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd)

---

### Post by LowSky on 2011-06-24
It did warn you. You just didn't read carefully.

With any OS install you should always backup your data.

---

### Post by cheapie on 2011-06-24
> **Mo-ayad said:**
> it produced lots of errors like it claims my version is not genuine.

Ubuntu is capable of displaying that?

---

### Post by Sealbhach on 2011-06-24
In future you would be best to have a separate root and /home partition. That way, when you are intalling, you would choose manual (advanced) partitioning and just install the new version of Ubuntu on the root / folder, leaving all your files on your /home folder intact.

Installing an OS is not a trivial change, and bad things can happen if you don't read up on what you are doing beforehand. :(
.

---

### Post by Bucky Ball on 2011-06-24
> **Sealbhach said:**
> In future you would be best to have a separate root and /home partition. That way, when you are intalling, you would choose manual (advanced) partitioning and just install the new version of Ubuntu on the root / folder, leaving all your files on your /home folder intact.
.

+1. I would add to this that you make sure that /home (and /swap but not so important) are not about to formatted in the manual install process (there is an option), only /.

* Wildmanne, haqking: What was the point in you both quoting the entire first post in this thread??? Your's were second and third posts, straight after the first, so there is not really any mistaking which post you were referring to. It just means more scrolling for all. :(

PS: The OP also has a name.

---

### Post by jtarin on 2011-06-24
> **Bucky Ball said:**
> 
PS: The OP also has a name.And that would be.......???

---

### Post by Bucky Ball on 2011-06-24
jtarin, on here the OP's name is [Mo-ayad.]("http://ubuntuforums.org/member.php?u=1323514")

... which may also be the case in the offline world. ;)

---

### Post by jtarin on 2011-06-24
> **Bucky Ball said:**
> jtarin, on here it is [Mo-ayad.]("http://ubuntuforums.org/member.php?u=1323514")

... which may also be the case in the offline world. Not relevant to this situation either way. ;)I know what it is ;)....but you seem to fail in your own instruction in that post. Admonishing members in their attempt to help......or have I read that totally wrong? If so pardon me. :P

---

