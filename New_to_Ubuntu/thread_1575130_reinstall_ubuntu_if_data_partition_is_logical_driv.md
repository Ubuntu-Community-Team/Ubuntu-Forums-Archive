---
title: "reinstall ubuntu if data partition is logical drive together with ubuntu"
date: 2010-09-15
forum: New to Ubuntu
---

### Post by hanciong on 2010-09-15
halo

last year, I had laptop ACER with two hidden partitions, one partition for C (windows), and another partition for D (data). All of them are primary partitions.  I wanted to dual boot windows with ubuntu. because one physical drive can't have more than 4 primary partitions, I had to make my ubuntu and my data together inside one extended partition. So the situation was like this:

2 stupid hidden partitions, primary
1 primary partition for C
1 extended partition, consisting of: primary partition (ubuntu root), logical drive for data, and logical drive for swap.

everything was fine. after that, when the new ubuntu came out, I reinstalled ubuntu. However, in doing so, my data partition was lost!! it was just undetected. after some painful efforts, I could get my data back, and deleted those stupid hidden partitions.

now, I have another new stupid laptop with two hidden partitions, and I want to dual boot again. I DON'T want to lose my data again if I reinstall ubuntu. what should I do? Is it enough if I mount my data partition into /data when installing ubuntu? in other words, is it enough if I do this:

extended partition: 1 primary (mount to ubuntu root), 1 logical drive (mount to /data), 1 logical drive for swap

if not mount to /data, then maybe mount to /home.

thx for the answer.

---

### Post by Mark Phelps on 2010-09-15
Referring to partitions as "stupid" ... is just plain stupid in itself.  Partitions are just partitions; they're neither smart nor stupid.

As to your situation, to see what you have, open a terminal and run "sudo fdisk -lu" (that's a lowercase L, not a one) -- and post the results back here.

There may be a valid (as in NOT stupid) reason for the partitions to be hidden.

---

### Post by Arla on 2010-09-15
Not sure why your data partition would have been lost, perhaps you accidentally selected the "format" option?

I've reinstalled with that same format (pretty much) many times, and never had an issue. I DO however have all my data backed up before trying it.

---

### Post by hanciong on 2010-09-16
I said that the hidden partitions are stupid because there are too many of them. other laptop (like HP or VAIO) only have one. and too much hidden partitions make dual booting with ubuntu more difficult (the problem with logical drive and so on). my friend has other stupid laptop (toshiba) with three hidden partitions! now he has to make his C and D in one extended partition. just imagine the mess if he wants to dual boot with ubuntu. and about your suggestion (sud fdisk -lu), I will try to do it, thx :p

> **Mark Phelps said:**
> Referring to partitions as "stupid" ... is just plain stupid in itself.  Partitions are just partitions; they're neither smart nor stupid.

As to your situation, to see what you have, open a terminal and run "sudo fdisk -lu" (that's a lowercase L, not a one) -- and post the results back here.

There may be a valid (as in NOT stupid) reason for the partitions to be hidden.

---

### Post by hanciong on 2010-09-16
do you have your data in the same extended partition with ubuntu root? because if not, then I don't have problem too. I only have problem when my data partition is in the same extended partition with ubuntu root.

> **Arla said:**
> Not sure why your data partition would have been lost, perhaps you accidentally selected the "format" option?

I've reinstalled with that same format (pretty much) many times, and never had an issue. I DO however have all my data backed up before trying it.

---

