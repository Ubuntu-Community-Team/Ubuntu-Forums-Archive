---
title: "Recovery Disc?"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by R@inm@n on 2010-04-04
How to make a recovery disc in Karmic?

Today, as I was trying to re-size my Karmic partition using gparted I somehow mucked up my Karmic Koala install and ended up having to re-install the whole OS including all my apps.

I thought that while I was doing this re-install that it would be nice to have a repair or recovery disc in my collection so I could just insert this DVD into the DVD drive and repair my already installed Karmic, so I didn't have to re-install the whole thing over again.

Is this possible in Ubuntu Karmic ?   If so, how ?


R.

---

### Post by redbook4574 on 2010-04-04
> **R@inm@n said:**
> How to make a recovery disc in Karmic?

Today, as I was trying to re-size my Karmic partition using gparted I somehow mucked up my Karmic Koala install and ended up having to re-install the whole OS including all my apps.

I thought that while I was doing this re-install that it would be nice to have a repair or recovery disc in my collection so I could just insert this DVD into the DVD drive and repair my already installed Karmic, so I didn't have to re-install the whole thing over again.

Is this possible in Ubuntu Karmic ?   If so, how ?


R.
I think the nearest you are going to find would be remastersys, this allows you to make a bootable cd containing any changes you have made to ubuntu, but remember you would still need to back up any data and your home partition.

---

### Post by J V on 2010-04-04
I just wrote a shell script with a huge "sudo apt-get --force-yes install" command containing all my apps, make one of those, its easier...

---

### Post by bythebay on 2010-09-04
I just joined this group to ask this exact question.

In some amount of searching I have found "building base ubuntu factory ISO" at
<http://en.community.dell.com/support-forums/software-os/w/linux/building-base-ubuntu-factory-iso.aspx>    This sounds like it would make a recovery DVD with OS, Apps, personal configurations and user data included.  Problem is I do not understand the language well enough to actually try this.  The 'ask a question' links are really developer links and so far I have not received any guidance.

FYI,  I recently got a Dell NetBook 10n, found neither my wife or I liked 9.10 remix so I used the 'create recovery disk' utility.  I then loaded 9.10 and with a lot of help from friends got a very workable configuration which does the job.  When I went to "create recovery disk" the option had disappeared :-(

Can any one refer me to the proper forum to ask questions about the Dell tool ?

BillB

---

### Post by Sef on 2010-09-04
> Can any one refer me to the proper forum to ask questions about the Dell tool ?


Try the [Dell Ubuntu support subforum]("http://ubuntuforums.org/forumdisplay.php?f=342").

---

