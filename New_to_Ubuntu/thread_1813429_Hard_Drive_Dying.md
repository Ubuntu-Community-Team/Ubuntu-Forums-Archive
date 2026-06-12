---
title: "Hard Drive Dying?"
date: 2011-07-27
forum: New to Ubuntu
---

### Post by kamitsukai on 2011-07-27
I'm having problems in both Ubuntu 11.04 and Windows XP where the whole operating system will totally freeze with no response from the keyboard or touchpad. is there a way to check the integrity of the hard drive?

---

### Post by redbikemaster on 2011-07-27
In Ubuntu you could open Disk Uility and check the S.M.A.R.T. status of the drive. You could also run a self-test to check it. I'm sure there's a Windows program but none come to mind. Keep in mind a bad motherboard would also cause this.

I've gone through two hard drives in the past month, so I know how frustrating it is.

---

### Post by kamitsukai on 2011-07-27
> **redbikemaster said:**
> In Ubuntu you could open Disk Uility and check the S.M.A.R.T. status of the drive. You could also run a self-test to check it. I'm sure there's a Windows program but none come to mind. Keep in mind a bad motherboard would also cause this.

I've gone through two hard drives in the past month, so I know how frustrating it is.

Thanks the S.M.A.R.T says that the disk is healthy, it could well be the motherboard as this laptop has been droped and banged an incalculable amount of times;) and it's really coming to the end of it's life...

---

### Post by JustinR on 2011-07-27
For Windows,

[HDDLife]("http://hddlife.com/index.html")

---

### Post by redbikemaster on 2011-07-27
Good to know, thanks JustinR. 

@kamitsukai, that would definitely be a suspected cause, then.

---

### Post by sbraz on 2011-07-27
for linux:

install GSmartControl from ubuntu software center, run it, save the drive's report somewhere and post it here. :)

---

### Post by sirgogo on 2011-07-27
Yup, doesn't sound like a HDD integrity problem, could be a motherboard problem. Pop in a liveCD and run a memtest86+, might be RAM. It could also be that your HDD is very fragmented, so running a defragger would be useful.

---

