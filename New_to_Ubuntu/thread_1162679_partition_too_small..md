---
title: "partition too small."
date: 2009-05-17
forum: New to Ubuntu
---

### Post by Purd2 on 2009-05-17
I have installed Ubuntu 9.04 and have only 2.4 GB partition. I don't know how to fix this. I have tried to reinstall and edit partition size but the changes are not accepted. Can I uninstall and start from scratch?  Thanks in anticipation P

---

### Post by presence1960 on 2009-05-17
> **Purd2 said:**
> I have installed Ubuntu 9.04 and have only 2.4 GB partition. I don't know how to fix this. I have tried to reinstall and edit partition size but the changes are not accepted. Can I uninstall and start from scratch?  Thanks in anticipation P

Why dont you open a terminal and run ```
sudo fdisk -l
``` and post the output here so we can see your partitions structure. BTW that is a lowercase L

---

### Post by Purd2 on 2009-05-17
ok I will try that.AND it is today here in Australia!!   LOL

---

### Post by -kg- on 2009-05-18
It is tonight (and time to go to bed for me) at my location, so I'm making this post to keep track of this thread.

You can find more information on the subject on the following page:

[https://help.ubuntu.com/community/HowtoPartition]("https://help.ubuntu.com/community/HowtoPartition")

---

### Post by presence1960 on 2009-05-18
If you cant boot into Ubuntu run ```
sudo fdisk -l
``` from the Live CD

---

### Post by presence1960 on 2009-05-18
Purd, I am going to bed. Post the output here so someone else can help you. if not I will check in the am.

---

### Post by Purd2 on 2009-05-18
Sorry , I had to leave to attend a funeral. I didn't think this would be so difficult.

 I have had Ubuntu for a few days and know nothing much about it, rather than it is open sourced and I want give MS the Kyber pass!

 SO, what is sudo fdisk-l       I tried it in XP but then realised this must be a Linux thing. SO new to this I don't know what t do!
 I will try to be around while you blokes are awake if I can!
Regards P

---

### Post by skymera on 2009-05-18
Boot the LiveCD and run GParted.

I think it's under System > Administrator. Called partiton manager or similar.

There you can resize your partitions.

---

### Post by Purd2 on 2009-05-18
OH my goodness! Thank you. I didn't expect it to be that simple. I will get back to let you know   Kind regards P

---

