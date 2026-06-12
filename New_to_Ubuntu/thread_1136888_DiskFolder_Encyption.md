---
title: "Disk/Folder Encyption"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by Lazy-buntu on 2009-04-25
I was thinking about using some encryption on my laptop to protect my data, but I'm not really sure what method to go with.

I have used Truecrypt (on a Windows install) in the past to create an encrypted container, which has worked pretty well for what I wanted it for (it was only about 400MB in size).

I dual boot Windows Vista and Jaunty, so I am wondering if I go with the entire disk encryption is it going to mess up my bootloader? I use EasyBCD on Windows as my bootloader, so GRUB is installed just on my Jaunty partition (Windows bootloader hands it off to GRUB if I pick Jaunty when I boot up). I was thinking about just creating an encrypted partition (NTFS), which I could share between Ubuntu and Windows.

However, that would leave everything else unencrypted. So I guess if I want **everything** encrypted, I need to go with entire disk encryption. 

Anyway here's basically what I want to know:
1. If I use Truecrypt for entire disk encryption of both Vista and Jaunty, is there anything I need to really worry about (corrupted data, not being able to access my OSs, etc.)
2. What are some examples of why you would want entire disk encryption.

---

### Post by Lazy-buntu on 2009-04-25
I found this in the archives: [http://ubuntuforums.org/archive/index.php/t-696461.html](http://ubuntuforums.org/archive/index.php/t-696461.html)


So if I wanted to encrypt Ubuntu, I'd be better off just encrypting /swap /home and /tmp?


Still, what would be some reasons for using entire disk encryption for Windows? Do those people have 'secrets' hiding in their registry of certain programs, or what?

---

### Post by Lazy-buntu on 2009-04-26
bump :confused:

---

### Post by DGortze380 on 2009-04-26
> **Lazy-buntu said:**
> 
Anyway here's basically what I want to know:
1. If I use Truecrypt for entire disk encryption of both Vista and Jaunty, is there anything I need to really worry about (corrupted data, not being able to access my OSs, etc.)
2. What are some examples of why you would want entire disk encryption.

1) Yes. Lost Encryption Key, Abrupt Shutdown, Corrupted files will cause your entire disk to become a useless jumble of bits. No, it is not possible to recover the data. In addition, backups become more difficult.

2) There are very few reasons (I would argue there are none) that a typical home user would need whole disk encryption.

---

### Post by inobe on 2009-04-26
i just hide the folder i wish to be unseen by others.

right clicking the folder and rename it, here's an example, a folder named **data**

**.data**

that will hide the folder and you can view it by hitting show hidden folders.

or you can lock the folder, replace username with your actual user name and folder you wish to lock at the end of the path, this will even lock you out completely !

```
chmod -r /home/username/data
```

to unlock the folder change the - to + in the command.

example

```
chmod +r /home/username/data
```

not recommended for the faint of hearts though.

enjoy

---

### Post by DGortze380 on 2009-04-26
> **inobe said:**
> i just hide the folder i wish to be unseen by others.

right clicking the folder and rename it, here's an example, a folder named **data**

**.data**

that will hide the folder and you can view it by hitting show hidden folders.

or you can lock the folder, replace username with your actual user name and folder you wish to lock at the end of the path, this will even lock you out completely !

```
chmod -r /home/username/data
```

to unlock the folder change the - to + in the command.

example

```
chmod +r /home/username/data
```

not recommended for the faint of hearts though.

enjoy

None of those options really secure the data, at all...

---

### Post by Cresho on 2009-04-26
There is no such thing as an encrypted disk.  I get payed to take data out of encrypted disks.

---

### Post by PukingPenguin on 2009-04-26
You get paid to take data off of encrypted disks, which don't exist. 

Hmm.


I would suggest that YOU don't exist, at least not according to Sartre...


:lolflag:

---

### Post by HermanAB on 2009-04-26
On Linux, you only need to encrypt your /home and /swap directories and if you make a swap file residing on /home, then you only need to encrypt /home.

On Windows, the system is so messy that it is best to encrypt the whole disk, since you never know where data is stored.

Bear in mind though, that a small error on an encrypted hard disk can cause the whole disk to be lost.  So if you use encryption, then you have to be more vigilant with backups.

---

### Post by inobe on 2009-04-26
> **DGortze380 said:**
> None of those options really secure the data, at all...



it simply changes the permissions so that those who want to see it's contents cannot unless they know of chmod +r.

have a good day

---

### Post by diw on 2009-04-27
I have been using disk encryption on root, home and swap (but not boot)for over 12 months and have never had a problem.  It makes life a bit easier - not only is your data secure but it saves me from using a master password on firefox which I find a repetitive pain in the ***.  If you follow these instructions you won't go far wrong

[URL="http://kuparinen.org/martti/comp/ubuntu/en/cryptolvm.html"[/URL]

---

### Post by Lazy-buntu on 2009-04-28
I was reading an article not too long ago about people's laptops getting taken by border patrol or whoever without a warrant or probably cause.

Anyway, they were mentioning the only way to protect your privacy was encrypting your hard drive. They also said you might be required to enter a password by the officers, but if you had a key file (or something else I'm forgetting) then they can't require you to give them that.


Nothing I'm worried about, since I hardly travel. That would just infuriate me if they had the audacity to sit there and question me about my laptop. I'd probably ask them if they had anything better to do. But now I'm getting off topic.


I was also reading about how easy it is to get around passwords. Obviously, if you can boot from a CD you can pretty much access anything non-encrypted right away. If you can't boot from a CD, then there's probably other ways of doing it, which aren't time exhaustive.

Maybe I shouldn't be so paranoid. I don't even take my laptop outside my home, but the tin-foil-hat wearer inside of me says I need to be protected.

---

### Post by DGortze380 on 2009-04-28
> **Lazy-buntu said:**
> 
Maybe I shouldn't be so paranoid. 

That would certainly be my suggestion. Everyone I know with whole disk encryption ends up losing something at some point. Most of the time it's a lot of data because they got lazy with backups...

My Rule of Thumb, if you don't need it, don't use it.
If you want to play with it, set up a VM.

---

### Post by Lazy-buntu on 2009-04-28
:eyes dart back and forth:

But ***they*** are watching. Always watching...



Just kidding. Thanks for the advice. I guess when I look into encryption in the future, I'll look at folder encryption or encrypted containers.

Is there a risk of corruption when you only work with folders or containers?

---

### Post by DGortze380 on 2009-04-29
> **Lazy-buntu said:**
> :eyes dart back and forth:

But ***they*** are watching. Always watching...



Just kidding. Thanks for the advice. I guess when I look into encryption in the future, I'll look at folder encryption or encrypted containers.

Is there a risk of corruption when you only work with folders or containers?

yup, make sure you back up anything you save in them. Chance is slightly lower though.

---

### Post by Monotoko on 2009-04-29
and if you do it as root using sudo so root owns it, no-one can see it unless there in your admin group and can use sudo ;)

---

