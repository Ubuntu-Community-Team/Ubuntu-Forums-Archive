---
title: "First time Ubuntu"
date: 2010-07-06
forum: New to Ubuntu
---

### Post by billyss on 2010-07-06
Hello! I am new in this forum, forgive me if I post in the wrong place. Recently I had some troubleshooting installing WIndows in my laptop, so I turned to linux Ubuntu. First time I ever use linux in a pc, altought I used to test around with it in a virutal machine some time ago. Now I am using it... And I like it! :D

By the way, my latop is kinda old and some times it becomes laggy when I have open more than 3 applications... I hope that I will eventually get used to it or find a way to make it better. I think turning from firefox to chrome did some help.

So guys, I just wanted to share my first Ubuntu experience with you, it's great... Looking forward to get more in the community!
:popcorn:

Oh, last but not least, a silly question: Now with Ubuntu, do I need an antivirus? Although I think not, I'd like to hear from someone that knows... Hehe.

---

### Post by J V on 2010-07-06
No you don't: Heres a prepost...

> **Viruses**
Linux has almost no viruses, not that it's not a popular target, google, yahoo, and several other multi-million dollar targets run on linux.

If there ever was a serious Linux virus out there, to get it to actually work, you would need to:


[LIST]
[*]Log onto your email
[*]Open your email
[*] Download the attachment
[*]Find the attachment
[*]Right-click and go to properties
[*]Go to the permissions tab
[*]Check the box marked execution
[*]Run the application (It can now infect the files in the same directory as it is in)
[*]Input your password (It can now infect files over the entire system)
[/LIST]

 On windows, all you have to do is to log onto your email, windows does the rest automatically, which leaves you open to viruses.

If you are still worried you will actually do this whole list without wondering if its a virus, the Ubuntu wiki has a nice list of [currently known Linux viruses]("https://help.ubuntu.com/community/Linuxvirus"), and their trivial (sometimes whimsical) natures.

You might still however, want to scan for windows viruses, so you don't infect your friends/colleagues with files from your computer (Which is equally unlikely as you would have to deliberately copy it over to them)

For this purpose you should install "[ClamTK]("apt://clamtk")" (Click to install) which is an interface for "ClamAV", which can scan incoming and outgoing email, or in your case, specific files.

---

### Post by mike555 on 2010-07-06
if your computer is older you might want to turn off things you don't use from ; System > Preferences > Startup apps. ..... like maybe bluetooth , Ubuntu one , Personal file sharing , etc.

---

### Post by jimrz on 2010-07-06
> **mike555 said:**
> if your computer is older you might want to turn off things you don't use from ; System > Preferences > Startup apps. ..... like maybe bluetooth , Ubuntu one , Personal file sharing , etc.

OR possibly use a lighter version of ubuntu like LUbuntu ... post the specs of your laptop (cpu, ram, etc) and people will likely give suggestions based on their experiences with similar equipment

---

### Post by nene7 on 2010-07-06
+1 to post before.
 May be it better a version lightweight like Lubuntu.

---

### Post by Zzl1xndd on 2010-07-06
If you could tell us about the specs on your system we might be able to make better recommendations. 

My first thought is you might just need a little more ram. 

Although if that is the case Lubuntu would fix you up without having to get more.

---

### Post by carlexpc on 2010-07-06
switch to a lightweight desktop since you are running ubuntu on an old pc. as others have recommended, try lubuntu.

---

### Post by billyss on 2010-07-07
Thanks everyone for replies! Well my pc specs are:

AMD Sempron 2800+ ~1.6GH
512MB RAM (448 used)
VIA S3G Unichrome pro igp Video card (64MB)
...and 15GB free space in first partition of HDD

Indeed, memory is not much...
Lubuntu sounds like a very nice idea thanks :) :) 

Also, how do I turn into a lightweight desktop? You mean to turn off windows effects or something like that?

---

### Post by donato roque on 2010-07-07
Welcome to the Ubuntu forums.
I recommend this [security page for new users]("http://ubuntuforums.org/showthread.php?t=510812").  It should answers most of your questions and it's helped me a lot with my questions too.

---

### Post by Zzl1xndd on 2010-07-07
> **billyss said:**
> 
AMD Sempron 2800+ ~1.6GH
512MB RAM (448 used)
VIA S3G Unichrome pro igp Video card (64MB)
...and 15GB free space in first partition of HDD


I would say ram is likely the root of your problem. Lubuntu uses a different and much more light weight desktop environment.

You can find it here 

[http://lubuntu.net/](http://lubuntu.net/)

---

### Post by kevinatkins on 2010-07-07
If you're using Ubuntu 10.04, easiest way to get lightweight Lubuntu desktop - open up a terminal and type -
```
sudo apt-get install lubuntu-desktop
```

You'll then have the option of using either Gnome or LXDE.. and Lubuntu really is very good indeed on older hardware.

Failing that, drop an extra 512MB RAM into your machine - should make a useful improvement.. the rest of your machine isn't too bad spec wise.

---

### Post by billyss on 2010-07-07
Thank you a lot friends ;)

---

