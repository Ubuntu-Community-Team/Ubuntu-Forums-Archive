---
title: "Is it possible to just copy Ubuntu from one pc to another?"
date: 2009-06-20
forum: New to Ubuntu
---

### Post by kymco on 2009-06-20
Good day. I'm just a newbie in Ubuntu 9.04 and I'd like to ask for some help. I successfully installed Ubuntu 9.04 in my kid's notebook, an MSI Intel atom N270 with 2GB memory and 160GB harddrive, thru Wubi. I made a separate 20GB partition which I dedicated for Ubuntu. I tried to install Ubuntu 9.04 in my old laptop, an ACER AMD Turion 64ML with 1GB memory and 80GB harddrive, but it hanged and did not complete the installation. Since it took around 4hrs. to download the installation file, I'm afraid I'll just waste my time trying to download it again. Will it be possible if I will just copy all the files from my kid's notebook to my old laptop? If so, what other files, .dll or anything should I copy to my laptop? Please help.

---

### Post by TeoBigusGeekus on 2009-06-20
Why install it through wubi?
Download the Ubuntu cd and install it from there.
As for your question, I don't think it is possible to do that...

---

### Post by prvteprts on 2009-06-20
Regarding "copying files in order to install": Puppy Linux has a method of frugal installation. Try reading up on that. As far as Ubuntu goes, maybe there is a way, but it would be much more complicated than you described. Also, aside from copying the necessary, granted it is possible, you would also need to setup a boot loader.

What I could recommend to you would be, to download the ISO installation file. The LiveCD is probably the more convenient one to use to install, however since the installation hanged, you could also try the alternate CD. I'm assuming you deleted the ISO file you used to install on your kid's machine. Well, regardless of which ISO image you download, burn it (using software which could make a bootable disc from ISO) so you don't lose it again. You could also use that to boot and install from there, without using Windows. It will also setup the boot loader for you.

---

### Post by glennric on 2009-06-20
Yes, it is possible to copy files from one computer to another and get an operational system.  However, if you are not experienced with manipulating linux configuration files (fstab, menu.lst, etc.) I wouldn't recommend it.  You will probably end up spending more time trying to get the copied os to work on the new computer than the four hours of dloading and installing fresh.  

By the way, linux doesn't use dll files.  Those are Windows libraries.

---

### Post by futileissue on 2009-06-20
You will at least need a liveCD of Ubuntu or another distribution, but if you have that you might as well try the install again anyway.  Where did the Ubuntu installation hang, if I may ask?  It shouldn't take so long if your computer has a gig of RAM.

---

### Post by Thingymebob on 2009-06-20
I've never had a successful install with the livecd on Acers but the alternate cd has always worked flawlessly.

---

### Post by kymco on 2009-06-20
Thank you guys for the inputs. I guess it will be more complicated than downloading the file again. By the way, there is an Ubuntu ISO image (more or less 800MB) in my kid's notebook where Ubuntu resides, can I burn it and try to install it in my laptop? 

My laptop hanged for around 30 or 45mins. while installation was in progress after the needed file was already downloaded. 

Again thanks a lot.

---

### Post by theozzlives on 2009-06-20
I've swapped Hard Drives before, but never copied the files, neither is recommended.

---

### Post by Jazzy_Jeff on 2009-06-20
Your best bet is to download the alternate install cd and make sure you burn it slow. It is a text base install but easy to do. I also have problems using the live cd's. Also, it should only take around 20-30 minutes to install. If it goes over 40 there is something wrong.

---

### Post by ramjet_1953 on 2009-06-20
If both PC's are identical in every respect, you could clone the hard drive using CloneZilla.

However, if they are not identical, it is unlikely that it will work, because part of the install procedure for any OS is to identify hardware and install the correct drivers.

Regards,
Roger :D

---

