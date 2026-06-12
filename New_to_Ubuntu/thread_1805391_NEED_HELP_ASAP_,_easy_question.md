---
title: "NEED HELP ASAP , easy question"
date: 2011-07-16
forum: New to Ubuntu
---

### Post by hookitup on 2011-07-16
i am a noobie ,,, i am attempting setting up a server(ubuntu server), i finally got my bios in my old computer to be able to boot from usb now .... i am at the part where i pick a partitioning method,  i have five options 

1- resize scsi2 (0,0,0), partition #1 (sda) and use freed s
2- use entire disk
3- use entire disk and set up LVM
4- use entire disk and set up encrypted LVM
5- manual 



This is not going to be a dual boot and it will be serving files (if i get it to work) , which one should i pick, i dont really know what much of it means and i dont want to do it wrong ,, 

 some additional information on what all this means would be sweet as well if u have time :D

Thanks in advance

---

### Post by dFlyer on 2011-07-16
That all depends on how much work you want to do. The easiest way is to use the entire disk, but that just gives you / with all sub folders under it. What do you want to do?

---

### Post by wojox on 2011-07-16
If this computer is just used for serving files use option #2

This will use the entire hard-rive.

---

### Post by hookitup on 2011-07-16
> **dFlyer said:**
> That all depends on how much work you want to do. The easiest way is to use the entire disk, but that just gives you / with all sub folders under it. What do you want to do?

sorry a little hard to fallow what you mean ,, i want to use the whole disk but what is LVM and encrypted LVM ??

I cant seem to find a good explanation on the Internet of what they are

---

### Post by wildmanne39 on 2011-07-16
Hi, choose the entire disk option. Not the one with encryption. That is what I would do, I have seen a lot of people on here have problems after encrypting there drives and file systems, that is for security, but if something goes wrong then it is harder to fix. 
You do not need to worry about LVM either.

---

### Post by hookitup on 2011-07-16
so i decided to do option 2 , and i chose samba file server, will i be able to access this server when i am away from office ? and how do i go about setting this up , and making its secure.

---

### Post by wildmanne39 on 2011-07-16
> **hookitup said:**
> so i decided to do option 2 , and i chose samba file server, will i be able to access this server when i am away from office ? and how do i go about setting this up , and making its secure.Hi, when you are ready to set it up start a thread with a good title describing what you need so the right people will be able to find you.

---

### Post by hookitup on 2011-07-16
good idea 

Cheers :D

---

### Post by wildmanne39 on 2011-07-16
> **hookitup said:**
> good idea 

Cheers :DHi, your welcome, that is a little over my head I have never set one up if your question is resolved, would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

