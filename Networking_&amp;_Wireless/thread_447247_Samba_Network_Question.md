---
title: "Samba Network Question"
date: 2007-05-17
forum: Networking &amp; Wireless
---

### Post by kdfuller on 2007-05-17
I have a home network that contains two Ubuntu computers and two Windows XP computers. I have configured  Samba and can see all computers on the network and can move files freely to and from the Windows computers from both Ubuntu computers. But for some reason I cannot move files between the two Ubuntu computers. It give me an error and says it is unable to access the file I try to move. Do I have something set up wrong or is this a known problem? I really would like to get it to work.

---

### Post by jimrz on 2007-05-17
> **kdfuller said:**
> I have a home network that contains two Ubuntu computers and two Windows XP computers. I have configured  Samba and can see all computers on the network and can move files freely to and from the Windows computers from both Ubuntu computers. But for some reason I cannot move files between the two Ubuntu computers. It give me an error and says it is unable to access the file I try to move. Do I have something set up wrong or is this a known problem? I really would like to get it to work.

not sure, may be due to rescent updates to samba. i installed the updates yesterday and am having similar issues between 3 ubuntu machines. just searched for posts in the last 1 day for "samba" and did not see a lot with this issue. ???

in the meantime, ssh is working just fine and will provide the functionality you need until we can figure out what's up with samba. you will need to have openssh-server (the client pkg is included in the default install)from synaptic installed on each ubuntu machine for this to work efficiently

if you figure out the samba prob, please post and I will do the same

---

