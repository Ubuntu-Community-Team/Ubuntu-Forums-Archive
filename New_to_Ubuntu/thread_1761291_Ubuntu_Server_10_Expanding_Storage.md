---
title: "Ubuntu Server 10 Expanding Storage"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by Elwha on 2011-05-18
Forgive me.. :) I'm a Microsoft Server guy!!  However I have a Ubuntu Server 10.04 installation running about 2TB of storage on a SATA RAID 5 drive set.  Its in a custom built tower server.    
 
My Ubuntu consultant indicates that we have to conduct a complete rebuild of the server because we cannot swap drives, have them rebuild, and then expand the storage.      
 
Can you give me, the Ubuntu novice some information on how best to:
 
1) Verify the information that was given to me by the consultant.  I have remote web access to Full Webmin, but that is all. 
2) Some options on a resolution without the rebuild.
3) A link to the very best documentation on Ubuntu Server installations.     
 
I should mention the rebuild location would require flight and travel to a rather nice destination at GREAT expense to our small company.
 
Thanks in advance for replies!

---

### Post by wlraider70 on 2011-05-18
1) I'm not a raid expert, but I thought that raid 5 was striped, and that it required using the same size drives.

So if you had three, 2TB drive and changed one to a 5TB it wouldn't work.

2) Assuming, I'm not mistaken... (and even if I am)

You could add a 2nd raid array leaving the original for OS and the new array for your increased needs.  

3) The problem I usually find with documentation is that its quickly outdated, or slightly varied, ie the default file path has changed. Nonetheless i like [https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

---

### Post by Hedgehog1 on 2011-05-18
The consultant is likely telling you the truth - but it depends on the hardware you are running.

Most 'based on a card' RAIDs do indeed need to be rebuilt when enlarged.

At a time like this, I would suggest changing to a new raid system and new drives, configuring the system, and then copying the data from the old raid to the new.  Based on the cost of down time, this is really cheaper.

If you go this route, please use a ready made system like this:
[Sans Digital TowerRAID 5-Bay USB 3.0/eSATA Hardware RAID]("http://www.amazon.com/Sans-Digital-TowerRAID-Hardware-TR5UT-BP/dp/B003YDZE0Q/ref=sr_1_10?s=electronics&ie=UTF8&qid=1305701774&sr=1-10")

There is an execption to this. Drobo's cost more, but they let you grow without having to rebuild:
[Drobo FS-8 bay Gigabit Ethernet Network Attached Storage DRDS3A21]("http://www.amazon.com/Gigabit-Ethernet-Network-Attached-DRDS3A21/dp/B00457X100/ref=sr_1_7?ie=UTF8&qid=1305701529&sr=8-7")

One way or another you pay to grow your array.  Drobos lets you pay up front.  Normal hardware RAID is a pay as you go.

Both methods work.  I lean toward normal hardware raid as drives wear out and need to be swapped over time anyway, but Drobo is nice, too.

**The Hedge**

:KS

---

