---
title: "TrueCrypt"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by ludwigr on 2010-05-09
Hey guys. 

Earlier when I used Windows I had the whole harddrive encrypted with Truecrypt, and I want to do the exactly same thing in Ubuntu. 

I've download TrueCrypt, installed it correctly but I can't find where I encrypt the whole harddrive. 
Any tips or directions on how I do that? 
And also I would like so that you have to write in a password before the machine boots up. 

Thanks.
With the kindest regards
ludwigr.

---

### Post by sandyd on 2010-05-09
trucrypt doesn't work with ubuntu.

however, you can encrypt your home directory, if thats what you want.

---

### Post by ludwigr on 2010-05-09
> **carlee said:**
> trucrypt doesn't work with ubuntu.

however, you can encrypt your home directory, if thats what you want.

It doesn't? Well, how do you explained I installed it successfully and can encrypt files and such? :) 

So if I encrypt my home directory, you must enter a password before you can get into the OS? 

Thanks.

---

### Post by sandyd on 2010-05-09
> **ludwigr said:**
> It doesn't? Well, how do you explained I installed it successfully and can encrypt files and such? :) 

So if I encrypt my home directory, you must enter a password before you can get into the OS? 

Thanks.
It doesn't work with encrypting the whole drive because the /boot directory needs to be exposed in order for the OS to boot.
and typically, if you have the /boot folder exposed, its not secure.

b) yes. you must manually mount the directory with the password before you can login.

hence, I refered to encfs, which will encrypt your home drive, then decrypt it when you type in the correct password when you login.

---

