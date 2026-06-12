---
title: "linux-headers-2.6.38-8"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by avnd on 2011-07-28
Hi there!

I wanted to install Amarok and remove Banshee (since I don't have much space). So I went ahead with the following command.

$sudo apt-get autoremove banshee (I like learning to do things in the terminal)

In the confirmation dialogues that followed, among the packages that were to be removed were the following two.

1. linux-headers-2.6.38-8
2. linux-headers-2.6.38-8-generic

These two looked a little important (not that I know what they do). What do these two packages do and is it okay to go ahead and remove them?

Thanks and Cheers!

---

### Post by Paqman on 2011-07-28
The command you want is:
```
sudo apt-get remove banshee
```

Which is different from:
```
sudo apt-get autoremove
```

The first command simply removes Banshee. The second one removes all the obsolete packages from your system (it will ignore the "banshee" after autoremove). What it won't do is remove Banshee. Don't worry though, autoremove is actually a good thing to run occasionally, as it only gets rids of things you aren't using. In your case it's saying it would like to get rid of an old kernel and it's headers.

---

### Post by Frogs Hair on 2011-07-28
Here is some information about the Linux kernel if interested . [http://en.wikipedia.org/wiki/Linux_kernel](http://en.wikipedia.org/wiki/Linux_kernel)

---

### Post by avnd on 2011-07-28
@Paqman, Major_Bloodnok & Frogs Hair: Thank you for your replies, fellas.

@Major_Blooknok: As soon as I read Paqman's reply I went ahead and removed them (including the linux header thingy). I rebooted and everything went fine except that Banshee was removed of course (duh!). I saw your comment after that and ran 
$uname -r
Interestingly, the current kernel I am running is the same. I don't know what to make out of it. Maybe I'll get a better view after reading Frogs Hairs' suggested link.

Thanks again, fellas!

Cheers!

---

### Post by avnd on 2011-07-28
> **Major_Bloodnok said:**
> ok then, install them back.
$ sudo apt-get update
$ sudo apt-get install linux-headers-2.6.38-8 linux-headers-2.6.38-8-generic

When I rebooted after removing them, things worked fine actually. Should I have to re-install them again? :)

---

### Post by 3602 on 2011-07-28
You are probably booting an older kernel.
But wait, if I'm right, the Linux kernel is made of linux-image, linux-headers and linux-headers-generic. So you still have the linux-image left...
Yeah, definitely install them back. Although you *should* be on 2.6.38-10 by now.

---

