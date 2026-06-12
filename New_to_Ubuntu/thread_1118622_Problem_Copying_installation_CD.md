---
title: "Problem Copying installation CD"
date: 2009-04-07
forum: New to Ubuntu
---

### Post by rbulalakaw on 2009-04-07
I've been using Ubuntu 8.10 for more than four months. I enjoyed it. I even copied it once successfully so that I could share it with my friend.

Right now, however, I have problem copying the installation CD. I use the Copy CD from the right-click menu. The copy process completes and there is no detected problem, however, for some reason, when I try the new installation CD, for example--I try it live--Windows says "Invalid CD Detected."

Also, when I try to use it from the CD (from a reboot), it goes to the menu, but it cannot go past the menu. It says something about Error in CD.

I tried it with two CDs, both to no avail.

What am I doing wrong? I just used the "Copy CD" from the Ubuntu interface, which I did (and has generated the CD I am copying from).

I have an Acer 4730Z laptop with dual-boot (the other OS is WIndows XP, but that it was the same setup I had to reproduce the CD I am using now). My optical drive is a CD/DVD-RW with 52X speed (?).

I wanna share Ubuntu to my superiors (faculty members), but I am having difficulty because of this.

---

### Post by kpkeerthi on 2009-04-07
You should burn your CD at 4x or less. Use Brasero or K3B to burn the disk.

---

### Post by rbulalakaw on 2009-04-07
> **kpkeerthi said:**
> You should burn your CD at 4x or less. Use Brasero or K3B to burn the disk.

Thank you for the quick response. I tried doing so, but when I opened Brasero and used the Copy 1:1 function, the only options for Burning speed are: Max Speed, 10X and 16X.

I noticed the "simulate before burning" is not checked. Would it help if I check it? and which speed should I use?

---

### Post by kpkeerthi on 2009-04-07
Not sure why 4x doesn't show up in Brasero. What version of Brasero do you have? 10x (the lowest you have) would still be faster and may result in a bad copy. 

I suggest you give K3B a try.

---

### Post by rbulalakaw on 2009-04-07
> **kpkeerthi said:**
> Not sure why 4x doesn't show up in Brasero. What version of Brasero do you have? 10x (the lowest you have) would still be faster and may result in a bad copy. 

I suggest you give K3B a try.

I checked the "Help" and the version is "Brasero 0.8.2"

How do I access K3B? I have practically no knowledge of the command line.....

---

### Post by MrWES on 2009-04-07
> **rbulalakaw said:**
> I checked the "Help" and the version is "Brasero 0.8.2"

How do I access K3B? I have practically no knowledge of the command line.....

From a terminal; Applications | Accessories | Terminal

Type:

```
sudo apt-get install k3b
```

Bill

---

### Post by rbulalakaw on 2009-04-07
> **MrWES said:**
> From a terminal; Applications | Accessories | Terminal

Type:

```
sudo apt-get install k3b
```

Bill

Thanks, Bill. I tried this, but I get "Couldn't find package 3kb"

I don't understand why this is happening when I have the evidence that copying an installation CD is easy....

---

### Post by kpkeerthi on 2009-04-07
1. Create an ISO (ubuntu-image.iso) out of the Install CD you already have. Brasero can do this.

2. Generate MD5sum of the iso you just created
```
 md5sum ubuntu-image.iso
```

3. Compare the MD5sum with this [http://mirror.anl.gov/pub/ubuntu-iso/CDs/8.10/MD5SUMS](http://mirror.anl.gov/pub/ubuntu-iso/CDs/8.10/MD5SUMS) to make sure you have a proper install CD.

If the MD5Sums do not match, your install CD is corrupt. I suggest you download the ISO from the download server again. Otherwise proceed to Step 4.

4. Burn the ISO to a new blank CD
```
     cdrecord -v -pad speed=4 dev=0,0,0 ubuntu-image.iso  
```
If cdrecord complains about speed, change **speed=4** to **speed=0**. cdrecord will then attempt to use the lowest (safest) possible speed.

---

### Post by kpkeerthi on 2009-04-07
> **rbulalakaw said:**
> Thanks, Bill. I tried this, but I get "Couldn't find package 3kb"

I don't understand why this is happening when I have the evidence that copying an installation CD is easy....

It is k3b. Not 3kb.

---

### Post by rbulalakaw on 2009-04-07
Thanks! I will try this tomorrow.

---

### Post by MrWES on 2009-04-07
> **kpkeerthi said:**
> It is k3b. Not 3kb.

Heh...yah :)

---

