---
title: "unwanted disk icon on desktop after /etc/fstab additon"
date: 2011-07-08
forum: New to Ubuntu
---

### Post by Old Jimma on 2011-07-08
Hi Ubuntu Community:

After a fair amount of suffering, I learned how to automatically mount shares that are on a server to a client. The instructions are given at

[[COLOR="Green"]**http://ubuntuforums.org/showthread.php?t=249889**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=249889")

After adding 

[COLOR="Red"]**192.168.1.66:/home/philipsmith/Documents /home/camillesmith/Documents nfs rsize=8192,wsize=8192,timeo=14,intr**[/COLOR]

to my /etc/fstab I could access the shares, but there is a [COLOR="Red"]**hard disk icon**[/COLOR] on my desktop now.

I don't like that thang. [-X

How to I get rid of that icon, but continue to maintain the mount?

THank you!

Phil Smith de Duluthistan, GA

---

### Post by bodhi.zazen on 2011-07-08
Depends on what desktop you are using, look at the nautilus options and see how to configure icons on desktop ;)

Another option is to mount the share in /mnt/Documents and use a symbolic link to link it to home.

---

### Post by Old Jimma on 2011-07-08
What have I done to be so fortunate to receive a reply from the Great Zazen?

So many thanks!

Sincerely,
Phil

---

