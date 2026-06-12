---
title: "Lost internet connection. Can't connect"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by lukeinvancouver on 2010-09-27
I don't know what happened but all of a sudden I can't get access to the internet.

I've tried every thing I could think of:
Firefox working offline ... it seems to go there all the time
Enable networking
select auto etho

I've been running Jaunty Jackalope 9.04 - joyfully - for many months.

Update manager can't find a connection.
I tried to update (finally) to the most recent release. No dice.

Any help would be greatly appreciated. I love my Ubuntu but I'm typing this on a Windows Vista machine.

Good golly.

---

### Post by Sef on 2010-09-27
How are you connecting to the internet: wired, wireless, or both?

---

### Post by akelsall on 2010-09-27
Can you open a terminal window and enter the command below (and post the output):

ifconfig

---

### Post by lukeinvancouver on 2010-09-27
> **akelsall said:**
> Can you open a terminal window and enter the command below (and post the output):

ifconfig

Thank you for helping.

I did but since I am communicating with my Windows machine I can't copy and paste.

There are 7 lines "under" etho
There are 8 lines "under" lo

I can't make sense of it.

But maybe this line is of interest:

UP LOOPBACK RUNNING MTU:16436 Metric:1

Just a guess in the dark....

:)

---

### Post by lukeinvancouver on 2010-09-27
I found the problem: The cable had become partially dislodged but still sitting in the socket. (I have no idea how this happened. Perhaps when I unplugged the line in.)

I thank everybody who tried to help.

Unfortunately I don't know where to mark the thread "Resolved".

I just found out how and marked it resolved.

---

