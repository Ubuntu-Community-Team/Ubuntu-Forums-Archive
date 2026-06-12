---
title: "unable to mount NEW VOLUME"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by Santooka on 2009-03-17
Dear all,

I am facing this problem that suddenly my PC in both operating systems (ubuntu & Vista) became really unstable, and after 2 days Vista crashed and i had to install it.

the days when they were unstabel i had a message appearing every now and then on ubuntu that it's unable to mount NEW VOLUME, but in the end it mounted it.

later on after the new installation of vista, i mean now, I can never mount this NEW VOLUME volume on ubuntu, it works fine on vista.

there r 2 messages that appear, the first one is attached as a pciture becuase i couldn't copy and paste it here.

the second one says:

> Unable to mount NEW VOLUME
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

so these are the messages that appear to me on ubuntu 8.10

do u have any ideas what to do about it?

thank u

---

### Post by BDNiner on 2009-03-17
Did you run chkdsk /f and reboot twice in Windows? There may be physical errors with you disk like some bad sectors.

---

### Post by Santooka on 2009-03-17
i did that and nothing changed.

---

### Post by BDNiner on 2009-03-17
How are you connecting the drive to your computer? Is it USB? Can you try the drive on a different USB port?

---

### Post by Santooka on 2009-03-17
no it's a sata hard disk , and it's only a prtition in it that cannot be mounted

---

### Post by BDNiner on 2009-03-17
I don't understand. Is it part of a RAID configuration? You can mount any physical disk unless I am misunderstanding what you are trying to say.

---

### Post by Santooka on 2009-03-17
ok i am not good at this at all so i am going to tell u this:

it's only hard drive 640GB, and it is partitioned into 3 partitions, c: d: e: in vista, the D: drive (/media/NEW VOLUME --> /dev/sda5)is unable to be mounted in ubuntu.

i don't know what's RAID in the first place, so i dunno what's the problem here.

---

### Post by Santooka on 2009-03-20
i figured out something that i had a terrible problem with my power supply and i changed it and my pc is incredibly better right now, but i still have the same problem with the same partition, any ideas?

---

