---
title: "How to dual boot an already dual booted cpu?"
date: 2010-07-18
forum: New to Ubuntu
---

### Post by aszxcv on 2010-07-18
Currently  I have windows vista and ubuntu 8.04 dual boot setup. I have the ubuntu 10.04 free cd . I   would like to install that and get rid of ubuntu 8.04. I have no clue how to do it. I tired fiddling around 10.04 cd and got nowhere. I am afraid that i might erase my windows vista. How do i get rid of ubuntu 8.04 so i can install 10.04? So basically i would like to do a fresh install of 10.04  in the process getting rid of 8.04.

---

### Post by new__buntu on 2010-07-18
If you want to play it perfectly safe you can just upgrade to 10.04 via update manager. It WILL take much longer though, as you have to go through multiple steps, and each takes around an hour+ to complete. Otherwise delete the partition with 8.04 on it manually and retask it to 10.04 (see the below post regarding manual partitioning - it's much more informative).

EDIT: the updates take an hour+, but most of the time the computer won't require input, so it won't necessarily take an hour+ of your time per update. Thought that could use some clarification.

---

### Post by qyot27 on 2010-07-18
Choose the Install option from the 10.04 setup, and when it gets to the Partitioning step, choose Manual Partitioning (or Advanced, I can't quite remember the terminology).  You'll get the actual layout of the partitions on the hard drive.

In here you can select 8.04's system partition and tell it to be overwritten and 10.04 installed there. It may also help if you had created a separate /home partition, but that depends on how 8.04 had been set up (if you want to create a separate /home now, it will take extra steps).

As long as you don't do anything to the NTFS partition Vista will be fine.

---

