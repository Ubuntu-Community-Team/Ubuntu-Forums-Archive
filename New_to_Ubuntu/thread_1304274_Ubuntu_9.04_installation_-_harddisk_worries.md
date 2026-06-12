---
title: "Ubuntu 9.04 installation - harddisk worries"
date: 2009-10-29
forum: New to Ubuntu
---

### Post by mcclunyboy on 2009-10-29
Hi,

I just installaed Ubuntu on a windows laptop which was about 4/5 years old...the specs are still OK and it should cope fine.  However the reason I did the install was due to Windows no longer booting, I was told a virus was at fault but after the install of Ubuntu I have noticed a few things...I am wondering if either you can clarify my prognosis or suggest some solutions.

Ubuntu installed correctly, downloaded flash player fine, started the updates for Ubuntu (never installed - it wouldnt let me
)- this is when things started to go wrong...I also downloaded Avast and Atunes...However  I kept getting random error messages concerning file permissions (wondering if it was this keycode thing initially)...then I couldn't open any of the synaptic package manager, update manager even when neither was open.  I downloaded the updates but it wouldnt install due to errors - did what I was told in terminal, it helped but asked for a reboot....

So I rebooted, it failed on startup and asked to do a "fsdk" i think which fixed some errors but not all...however this has happened a few times and it is very tedious and a relatively long process.

I installed Avast in the end after having errors during installtion, running a command it suggest through terminal fixed that one.

It says Atunes is installed correctly but at the minute it wont open, I have tried re-installing....Anyway It has now asked for the checkdisk a few times....

I think the hard disk has gone - my next move is to re-install ubuntu and go slower...I am beginner to Ubuntu.

---

### Post by gareththegeek on 2009-10-29
I'm no expert either but I'd agree it sounds like a faulty hard disk. You could try
```
man badblocks
```
to check out the disk

---

### Post by hal10000 on 2009-10-29
You should also look into the file /var/log/messages for Harddisk failures or similar things

---

### Post by philinux on 2009-10-29
> **mcclunyboy said:**
> Hi,

I just installaed Ubuntu on a windows laptop which was about 4/5 years old...the specs are still OK and it should cope fine.  However the reason I did the install was due to Windows no longer booting, I was told a virus was at fault but after the install of Ubuntu I have noticed a few things...I am wondering if either you can clarify my prognosis or suggest some solutions.

Ubuntu installed correctly, downloaded flash player fine, started the updates for Ubuntu (never installed - it wouldnt let me
)- this is when things started to go wrong...I also downloaded Avast and Atunes...However  I kept getting random error messages concerning file permissions (wondering if it was this keycode thing initially)...then I couldn't open any of the synaptic package manager, update manager even when neither was open.  I downloaded the updates but it wouldnt install due to errors - did what I was told in terminal, it helped but asked for a reboot....

So I rebooted, it failed on startup and asked to do a "fsdk" i think which fixed some errors but not all...however this has happened a few times and it is very tedious and a relatively long process.

I installed Avast in the end after having errors during installtion, running a command it suggest through terminal fixed that one.

It says Atunes is installed correctly but at the minute it wont open, I have tried re-installing....Anyway It has now asked for the checkdisk a few times....

I think the hard disk has gone - my next move is to re-install ubuntu and go slower...I am beginner to Ubuntu.

Open a terminal and run this.

```
cat /var/log/messages | grep "I/O error"
```

---

### Post by ibizatunes on 2009-10-29
Ubuntu 9.10 has a nice GUI to monitor hardrive stuff like I/O problems etc.....

You just need in the BIOS S.M.A.R.T enable on the hardrive and away you go, maybe update to the new version

---

### Post by karimruan on 2009-10-29
> **ibizatunes said:**
> Ubuntu 9.10 has a nice GUI to monitor hardrive stuff like I/O problems etc.....

You just need in the BIOS S.M.A.R.T enable on the hardrive and away you go, maybe update to the new version

I will be the next one to suggest using karmic koala, even if just because of the disk utility it has, I have heard alot about. I am upgrading today.

---

### Post by twright on 2009-10-29
Upgrading to Karmic is probably a good idea in any case.

Why are you installing Avast? - there is not much point on Linux as security is managed as a core component of the system, not as an afterthought.

You should be able to install ATunes quite easily in Karmic just by going to the Software Centre.

---

### Post by mcclunyboy on 2009-10-29
hi, i will try karmic koala tonight...if that fails i will put it down to the HD and get a new one ordered...

alex

---

### Post by mcclunyboy on 2009-10-30
I installed Karmic Koala and as soon as it logged on it said that hard  disk failure was imminent.

I will try and get a new HD " IDE 100GB" for the laptop - can anyone give me links to cheap new ones?!

I also installed this on another Dell laptop and it is working a treat - so far im very impressed, I haven't encountered any problems yet so it is very easy to use...im not looking forward to my first error though :P

---

