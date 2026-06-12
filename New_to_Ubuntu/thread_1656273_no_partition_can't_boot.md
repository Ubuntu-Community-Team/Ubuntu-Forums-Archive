---
title: "no partition can't boot"
date: 2010-12-30
forum: New to Ubuntu
---

### Post by cmcanulty on 2010-12-30
I have been having progressively worse problems with one of our desktop library computers and then it stopped booting. I could load the Ubuntu CD but it won't install so I used puppy CD which will run in live mode  and deleted the partitions to format them new. Big mistake! Now puppy won't let me repartition them so I have no MBR no partition. I can't boot knoppix either but it seems if I can use puppy and even connect to web on it there ought to be a fix for Ubuntu. I am typing this on another machine please help we close at 7pm and I really need to get this fixed or at least start thank you

---

### Post by TeoBigusGeekus on 2010-12-30
Could it be a failing hd?

---

### Post by skyzthelimit230 on 2010-12-30
sounds like either a failing hdd, or a logic failure in which case you might have to reformat the entire drive

---

### Post by cmcanulty on 2010-12-30
I really doubt that as things got drastically worse when I tried and failed to reformat /. But i have puppy live on and it doesn't see any hard drive!I was trying to reformat / and got errors so I deleted it and planned to reformat a fresh partition but now puppy only see the cd drive.

---

### Post by TeoBigusGeekus on 2010-12-30
Let's try to eliminate hardware malfunction first.
Turn it off, unplug it, open the box and try unplugging and replugging the hard disk. Could be a circuit overloading, who knows?

---

### Post by cmcanulty on 2010-12-30
ok trying that

---

### Post by cmcanulty on 2010-12-30
OK no difference

---

### Post by cmcanulty on 2010-12-30
OK now I have a /formatted to ext 4 and a swap do I need anything else and how do i repair boot

---

### Post by TeoBigusGeekus on 2010-12-30
Ok, so when you boot up with ubuntu (or puppy) nothing appears as a hard drive?
If so, try to connect the drive to another computer, even a windows one, to see if it's recognized.
I insist on the hard disk failure, even considering the fact that it got worse after your formating attempt. Perhaps it was too much for the poor thing...

EDIT: Just read your last post. You could create a separate home partition and install grub; you should be ok after that.

---

### Post by cmcanulty on 2010-12-30
InstallingGRUB is what I don't know, I've always used the ubuntu CDs whuch worked and did that. When I reboot from puppy cd it now shows /dev/sda1 ext 4 73GB and /dev/sda2 linux swap 3gb but it still won't boot from HD or Ubuntu CD but puppy runs fine live. I supposedly installed puppy just now but won't boot without the puppy cd

---

### Post by TeoBigusGeekus on 2010-12-30
Go to [this]("https://help.ubuntu.com/community/Grub2") page and scroll down to reinstalling grub2 from live cd.

---

### Post by cmcanulty on 2010-12-30
OK will that work from puupy cd as the ubuntu cd, I tried several won't go live

---

### Post by TeoBigusGeekus on 2010-12-30
I don't know, does puppy use grub2 or legacy?

---

### Post by cmcanulty on 2010-12-30
Well we have to close I will try again later thanks for all your help!

---

### Post by TeoBigusGeekus on 2010-12-30
Don't mention it.
Just post us with your progress.
Good luck!

---

### Post by cmcanulty on 2010-12-31
I am going to mark this thread solved and start one on the GRUB issue from puppy thanks again

---

