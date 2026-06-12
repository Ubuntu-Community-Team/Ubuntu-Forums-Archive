---
title: "Can i get into Ubuntu on a Wubi installation"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by Peterfc on 2010-10-21
I tried to update to 10.10 after my home desktop and my laptop updated to 10.10 without any trouble. 

I have a Windows work machine that has Ubuntu installed via Wubi at present running 10.04. For a while i have had a problem when i get updates but i have lived with it. I tried to update yesterday via the update manager. During the update i got various error messages. I clicked Print screen in the hope i could use them later for help. Just in case i also used a camara to save the error i was getting. Now when i switch on i get as far as the Login but when i get to put my password in the system just goes back to the Login. The second image i have supplied is the message i get when i try on login. 

I am happy to install as a true dual boot if i can get into the present Wubi installation of Ubuntu to get at some data i need.

---

### Post by ArgusVision on 2010-10-21
Are you able to select a previous kernel in GRUB? One that may not have the config issues?

---

### Post by Peterfc on 2010-10-21
> **ArgusVision said:**
> Are you able to select a previous kernel in GRUB? One that may not have the config issues?

Hi Thanks for the reply

No i can't login to Ubuntu at all.

It's only a way to get into Ubuntu so i can get some data of and i will do a clean install and ditch the Wubi version.

---

### Post by bcbc on 2010-10-21
try ext2read.
Or boot a live cd and loop mount the root.disk as per the [wubi guide]("https://wiki.ubuntu.com/WubiGuide#How can I access my Wubi install and repair my install if it won't boot?").

---

