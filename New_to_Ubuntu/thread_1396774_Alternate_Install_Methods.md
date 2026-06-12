---
title: "Alternate Install Methods?"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by Madonnas BoyToy on 2010-02-02
Okay, so I've been trying for days to install 9.04 to an old Gateway desktop (from the late '90s) that my friend has.  
I don't have a CD or Floppy drive on my computer so I can't make a disk that way.  I made a USB boot disk, but the target computer's BIOS doesn't support booting from USB.  
I tried to install using UNetbootin, but every UNetbootin method that I've tried doesn't work.
I want to remove Windows completely from the target PC, so Wubi isn't really an option for me...(Unless it is?)
For some reason the internet on the target PC stopped working (It was a fluke that it worked in the first place).  I had tried to do a net install, but it didn't recognize any of the computer's network hardware so I couldn't proceed.

So I'm wondering if I'm doing something wrong?  Or maybe there's something that I could do to get Ubuntu installed that I haven't tried yet?  
Perhaps I should just wait til I get a CD made?

My computer:
HP Mini 1000
OS - Jaunty

Target:  
Gateway 2000 Essential
OS - Windows 98 SE

---

### Post by philinux on 2010-02-02
> **Madonnas BoyToy said:**
> Okay, so I've been trying for days to install 9.04 to an old Gateway desktop (from the late '90s) that my friend has.  
I don't have a CD or Floppy drive on my computer so I can't make a disk that way.  I made a USB boot disk, but the target computer's BIOS doesn't support booting from USB.  
I tried to install using UNetbootin, but every UNetbootin method that I've tried doesn't work.
I want to remove Windows completely from the target PC, so Wubi isn't really an option for me...(Unless it is?)
For some reason the internet on the target PC stopped working (It was a fluke that it worked in the first place).  I had tried to do a net install, but it didn't recognize any of the computer's network hardware so I couldn't proceed.

So I'm wondering if I'm doing something wrong?  Or maybe there's something that I could do to get Ubuntu installed that I haven't tried yet?  
Perhaps I should just wait til I get a CD made?

My computer:
HP Mini 1000
OS - Jaunty

Target:  
Gateway 2000 Essential
OS - Windows 98 SE

How much memory has the gateway.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by Madonnas BoyToy on 2010-02-02
> **philinux said:**
> How much memory has the gateway.

[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)
It has 128 MB RAM, and I don't know how big the hard drive is, but I know that there's at least 20G free, currently.

---

### Post by philinux on 2010-02-02
> **Madonnas BoyToy said:**
> It has 128 MB RAM, and I don't know how big the hard drive is, but I know that there's at least 20G free, currently.

Thats not enough ram for ubuntu or even xubuntu I think. I'd give crunchbang a go.

[http://crunchbanglinux.org/](http://crunchbanglinux.org/)

Others that are lightweight are puppy and dsl.

---

### Post by Madonnas BoyToy on 2010-02-02
I've given Puppy and DSL a look, but have never heard of CrunchBang.  I'll look into it and see how it goes.
Would you recommend that I transfer the file to the target computer and then try using UNetbootin to install it?

---

### Post by Kixtosh on 2010-02-02
Perhaps it might be worth his while getting extra RAM, if the Gateway will support it, so that he can use regular Ubuntu or Xubuntu? I'd bet it's damn cheap to purchase by now, if it can be found.

For comparison, I have just installed Karmic Koala (Ubuntu 9.10) on two laptops dating from 1999 and 2000. Both have a maximum RAM capacity of 256MB and 400MHz/700MHz PII/PIII processors respectively (they're listed in my signature). I have to say that regular Ubuntu works very well so far (although I'm struggling with audio issues on the Dell, and can't get the external monitor to work properly with the Toshiba). Otherwise, with long term support being terminated for W2K later this year, I'd say they both work as well as they ever have done, and faster than they have been for a long long time. My eventual plan is to use Xubuntu so that the graphics aren't too demanding on the limited resources (as pointed out on that "Minimum System Requirements" page).

It sounds as though this Gateway might have very similar specifications. Booting from a Live CD, if it can be done, is an easy, but rather tedious way to do this (both of mine will boot from a CD, but they both use dedicated drives that are not connected by USB). It went flawlessly for me, including detection of the Netgear wireless cards, so internet was up and running within 60 seconds of the completed installation.

---

### Post by philinux on 2010-02-02
> **Madonnas BoyToy said:**
> I've given Puppy and DSL a look, but have never heard of CrunchBang.  I'll look into it and see how it goes.
Would you recommend that I transfer the file to the target computer and then try using UNetbootin to install it?

Never used unetbootin. It seems your options are limited on the gateway.

If you can get a livecd it wold be easier. Shame there's no net on the target though. I guess you're using it for office type stuff.

---

### Post by Madonnas BoyToy on 2010-02-02
Okay, well I got the internet to work again on the target PC, but I haven't made any headway in the installation department.

Whenever I use one of the UNetbootin options, it starts to boot, and then tries accessing the floppy drive and then fails. 

@Kixtosh - RAM upgrades are available at Walmart (I actually saw them the other day, on accident) and you're right, they are pretty cheap.  It's not my computer nor my money being spent on it, but I'll suggest it to my friend.

I'll continue researching to see if I can find any more information to help my cause.
Thanks so far, guys.  :)

---

### Post by Madonnas BoyToy on 2010-02-02
Well, after I got the internet working, I was able to run UNetbootin and install Debian over the internet.  It's working great so far.  Much faster than before.  Memory upgrades still probably wouldn't hurt though.

Anyway, thanks agian.

---

### Post by Kixtosh on 2010-02-03
> **Madonnas BoyToy said:**
> ... RAM upgrades are available at Walmart (I actually saw them the other day, on accident) and you're right, they are pretty cheap.  It's not my computer nor my money being spent on it, but I'll suggest it to my friend. ...Such an old laptop will have limits to how much you can use AFIK. Both of mine do, and it is 256MB in both cases (I think this is a BIOS related issue). 

Try the Kingston website for information on this, with the exact model number available. They're very good at letting you know what you can, or cannot, add. In fact, in the case of my Toshiba, the official Toshiba Direct sales outlet has an error, but the Kingston website has the correct information!

By checking the Kingston website, you'll know exactly what RAM specifications you should be looking for, and then you can shop where you like (Walmart, amazon.com, kingston.com) ... otherwise, you risk wasting your time buying something that will not be compatible IMO. Actually, once you've correctly identified the module(s) you need, amazon.com is a great place to check what the best pricing might be.

I'm glad to see you've made progress, and yes: so far, if everything is working, I would agree that some flavor of Linux is a great choice for older machines. I'm going to actually be able to use mine properly now. They don't function as though they were on crutches any more. They are totally viable machines after the switch from W2K, and like your friend, I won't have to worry about security issues with the end of W2K extended support later this year.

---

