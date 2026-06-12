---
title: "File system problems !!!"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by pnaditya on 2010-12-08
**I have installed ubuntu in my sony laptop but when i open the file system im unable to create the folder in it?**


It gives the following error : " You do not have the necessary permissions  ".

---

### Post by coffeecat on 2010-12-08
I think you are trying to create a folder in the root of your filesystem. Only root can do that and you should only do that in special circumstances. What are you trying to create a folder for? If it's for data storage, use your home folder, not the root of the filesystem.

---

### Post by kesman on 2010-12-08
As a normal user you only have permissions to make directories and write files in /home/username -directory aka "~" -directory.

If you really need to make a directory elsewhere, you need root permissions, which you can get by typing
```
gksudo nautilus
```
in terminal, but note that this really allows you to completely mess up your system and is not recommended for other than advanced users.

---

### Post by matt_symes on 2010-12-08
Hi

+1  coffeecat. The home folder is where you want to be creating your data folders. In there you can create as many folders as you want.

As a standard user you cannot create folders or add files anywhere else on the file system  unless you become root user. You will also notice you cannot delete any files or folders outside your home directory without root privileges, or even any other file operation such as renaming.

This is part is of the Linux security model and helps make it safer than other operating systems, as an  average  user or virus (etc) cannot place files where they should not be.

I notice you are new to the forums, so maybe this is all new to you. Rest assured, it is designed to keep you and your computer safe.

However having said that, here is some documentation on sudo. It will give you temporary root privilages.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Kind regards

---

### Post by pnaditya on 2010-12-08
@matt _symes:

I partitioned my hard drive into 2 parts one for ubuntu and another  drive is free .. I want to create folder there for organizing songs ,  videos etc ...

---

### Post by coffeecat on 2010-12-08
> **pnaditya said:**
> @matt _symes:

I partitioned my hard drive into 2 parts one for ubuntu and another  drive is free .. I want to create folder there for organizing songs ,  videos etc ...

OK. Your other partition (not "drive", that's a Windows misnomer) will be using a Linux filesystem and will at the moment be owned by root. Which is why you can't write to it. If you intend to use it for storing your personal files, you can easily change ownership to yourself, but we need some information first. Open a terminal and post the output of the following commands:

```
sudo fdisk -lu
cat /etc/fstab
ls -l /media
```Please enclose the output in code tags by using the # button in the toolbar above the message field.

---

### Post by matt_symes on 2010-12-08
Hi

My apologies pnaditya. When somebody posts here i can never be sure of their competence with Linux after one post, so if i explained something to you that you already knew then please understand why.

Follow coffeecat's instructions and you will be up and running in no time.

Kind regards

---

### Post by coffeecat on 2010-12-08
@matt_symes, what you posted was excellent and needed saying, even if not for the OP. My first post was a little too terse. I'm afflicted with a rotten seasonal virus atm, and I'm not firing an all cylinders, so please fell free to correct anything of mine that needs correcting. :)

---

### Post by Quackers on 2010-12-08
Cat flu? :-)

---

### Post by coffeecat on 2010-12-08
> **Quackers said:**
> Cat flu? :-)

No, bird flu. I blame the ducks! :p

---

### Post by coffeecat on 2010-12-09
@pnaditya, did you get your filesystem permissions sorted out?

---

