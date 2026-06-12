---
title: "screen issue after fresh install."
date: 2011-07-16
forum: New to Ubuntu
---

### Post by hookitup on 2011-07-16
So i just install ubuntu server, in the beginning of the install it asked something about the screen and i didnt know what to chose so i just picked one, BAD IDEA, the hole set up process looked perfectly fine and worked well but when it finally came to the reboot part all went down hill, the grub window pops up perfectly fine then the screen goes white and it looks all jacked up with white letters and black highlight, ( cant even read what they say, completely distorted ) so im assuming i picked the wrong one,,  but it seems it is in the termal or something, is there a code i can enter this (blindly) to resolve this ? or should i go through the pain of re-imaging it ?

---

### Post by wildmanne39 on 2011-07-16
> **hookitup said:**
> So i just install ubuntu server, in the beginning of the install it asked something about the screen and i didnt know what to chose so i just picked one, BAD IDEA, the hole set up process looked perfectly fine and worked well but when it finally came to the reboot part all went down hill, the grub window pops up perfectly fine then the screen goes white and it looks all jacked up with white letters and black highlight, ( cant even read what they say, completely distorted ) so im assuming i picked the wrong one,,  but it seems it is in the termal or something, is there a code i can enter this (blindly) to resolve this ? or should i go through the pain of re-imaging it ?Hi, you can look at this link because it might be a video card driver issue that can be fixed after you can boot into ubuntu.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Wim Sturkenboom on 2011-07-16
I however don't see a problem doing a re-install and choosing something else from the list. Takes 15 minutes or so?

PS
Unless things have changed since I installed 6.06 server (and removed it again), there is no GUI with the server; so just a warning not to expect that.

---

### Post by hookitup on 2011-07-16
this may be a stupid question but is ubuntu server , terminal based ?

---

### Post by hookitup on 2011-07-16
lol my bad u just answered my question ,, but umm i have an old pc so its slow to install

---

### Post by amjjawad on 2011-07-16
> **hookitup said:**
> i have an old pc so its slow to install

Is this why you installed Ubuntu Server? how old is your PC?

---

### Post by hookitup on 2011-07-16
this things is very old . still has ps2 connections and only 1 usb, and its just super old ,,, chipset is intel i810 only has 255m ram, celeron 664.7mhz ,,,, lol shes old, i got the issue fix, with the screen, here is my thread i posed a couple minuets ago, about how to set it up 
[http://ubuntuforums.org/showthread.php?p=11054262#post11054262](http://ubuntuforums.org/showthread.php?p=11054262#post11054262)

---

### Post by amjjawad on 2011-07-16
> **hookitup said:**
> chipset is intel i810 only has 255m ram, celeron 664.7mhz

Then why don't you install Lubuntu 11.04? at least you'll have GUI.

---

### Post by wildmanne39 on 2011-07-17
+1 for Lubuntu.

---

### Post by amjjawad on 2011-07-17
The Thread is marked as SOLVED but the OP did not post back. I hope he/she managed to solve the issue successfully :)

---

### Post by wildmanne39 on 2011-07-17
Hi, me too, that was a strange problem since he had the server edition installed and was only getting terminal mode.

---

### Post by Wim Sturkenboom on 2011-07-18
> **amjjawad said:**
> The Thread is marked as SOLVED but the OP did not post back. I hope he/she managed to solve the issue successfully :)

See post #7. OP did post back ;)

---

### Post by amjjawad on 2011-07-18
> **Wim Sturkenboom said:**
> See post #7. OP did post back ;)

RIGHT! 
I guess I was viewing 10 threads at the same time, as usual :)

Thanks a lot :)

By the way, I like your signature ;)

---

### Post by hookitup on 2011-07-18
hi folks, my issue was solved by [wildmanne39]("http://ubuntuforums.org/member.php?u=508533") , it worked for me and i was able to see the screen correctly after, and little did i know server edition is only terminal from what other post have said, i installed the GUI scene i dont know enought to do much in the terminal other then install stuff and run stuff. please check this post and help me out setting up my server. id greatly appriciate it [http://ubuntuforums.org/showthread.php?t=1805717](http://ubuntuforums.org/showthread.php?t=1805717)



Thanks__

---

### Post by amjjawad on 2011-07-18
> **hookitup said:**
> hi folks, my issue was solved by [wildmanne39]("http://ubuntuforums.org/member.php?u=508533") , it worked for me and i was able to see the screen correctly after, and little did i know server edition is only terminal from what other post have said, i installed the GUI scene i dont know enought to do much in the terminal other then install stuff and run stuff. please check this post and help me out setting up my server. id greatly appriciate it [http://ubuntuforums.org/showthread.php?t=1805717](http://ubuntuforums.org/showthread.php?t=1805717)



Thanks

Glad to know that :)

If you're having some hard time with that, you could save some time and effort and go GUI by installing **[Lubuntu]("http://lubuntu.net/")**. It's unquestionably one of my favorites :)

If you still want to keep your current installation, I'll try to have a look at your other thread and see if I could help!

---

### Post by hookitup on 2011-07-18
> **amjjawad said:**
> Glad to know that :)

If you're having some hard time with that, you could save some time and effort and go GUI by installing **[Lubuntu]("http://lubuntu.net/")**. It's unquestionably one of my favorites :)

If you still want to keep your current installation, I'll try to have a look at your other thread and see if I could help!
 
i have lubuntu on disk and tryed it, i like it but didnt install it till i tryed the ubuntu server edition, is there a server edition for lubuntu ? or can pretty much any distro be used as a server with the right software ??

---

### Post by amjjawad on 2011-07-18
> **hookitup said:**
> i have lubuntu on disk and tryed it, i like it but didnt install it till i tryed the ubuntu server edition, is there a server edition for lubuntu ? or can pretty much any distro be used as a server with the right software ??

Lubuntu and Ubuntu have exactly the same core, it's just the GUI ([Desktop Environment]("http://en.wikipedia.org/wiki/Desktop_environment")) that is different.

It depends on what you really need from that server?!
For example, I have a PC where it receives the Wireless Signal from downstairs and with a LAN Cable, I'm able to be online from the other room. I know it's funny but it's a long story :)
Point is, no matter what Distro is installed, as long as there is Wireless Connection and LAN connection, I'm online. I don't need complicated stuff. Thus, Lubuntu and/or Ubuntu or even any other distro will do the job as long as everything is there and work.

By the way, a server with GUI is almost the same as Ubuntu or even Lubuntu. You still can use the same packages if you have Ubuntu Desktop Edition or Lubuntu. 

IMHO, to deal with Linux Servers, better have a good knowledge with CLI.

In your case and if I were you, I would go Desktop Edition and save my time but that's me :)

---

### Post by hookitup on 2011-07-18
> **amjjawad said:**
> Lubuntu and Ubuntu have exactly the same core, it's just the GUI ([Desktop Environment]("http://en.wikipedia.org/wiki/Desktop_environment")) that is different.

It depends on what you really need from that server?!
For example, I have a PC where it receives the Wireless Signal from downstairs and with a LAN Cable, I'm able to be online from the other room. I know it's funny but it's a long story :)
Point is, no matter what Distro is installed, as long as there is Wireless Connection and LAN connection, I'm online. I don't need complicated stuff. Thus, Lubuntu and/or Ubuntu or even any other distro will do the job as long as everything is there and work.

By the way, a server with GUI is almost the same as Ubuntu or even Lubuntu. You still can use the same packages if you have Ubuntu Desktop Edition or Lubuntu. 

IMHO, to deal with Linux Servers, better have a good knowledge with CLI.

In your case and if I were you, I would go Desktop Edition and save my time but that's me :)

heres the thing, when i run the desktop edition i get a error , cant recall what it was but i think it basically said my computer is to old to run ubuntu , but when i did the server one it work and pluss i want it to be a server so it made sence in my mind to do the server edition,   i just have no idea how to set it up,,,

 correct me if im wrong but i fell like the server edition is no different from desktop edition other then different default package installed. so techinaly speaking i could download desktop edition on a computer that will except it and download certain packages and BAM its got server capability RIGHT ??? just trying to get a clear understanding of what entitles it to be a server.

---

### Post by amjjawad on 2011-07-18
> **hookitup said:**
> heres the thing, when i run the desktop edition i get a error , cant recall what it was but i think it basically said my computer is to old to run ubuntu

I installed Linux Mint LXDE Edition on an antique broken laptop (Pentium II and 64MB RAM) and guess what? it worked without any error message except it's so slow.
On your machine, Lubuntu 11.04 should be fast. If you want Super Fast then SliTaz or antiX but keep in mind that you may find some hard time when it comes to the Wireless Drivers.

Just give Lubuntu a try, you won't lose anything ;)

> but when i did the server one it work and pluss i want it to be a server so it made sence in my mind to do the server edition,   i just have no idea how to set it up

Neither do I :)
I would read some guides and do some google search.

> correct me if im wrong but i fell like the server edition is no different from desktop edition other then different default package installed.


[https://help.ubuntu.com/community/ServerFaq](https://help.ubuntu.com/community/ServerFaq)

> so techinaly speaking i could download desktop edition on a computer that will except it and download certain packages and BAM its got server capability RIGHT ??? 

Yes, I think you can do that if you have some hard time lea

> just trying to get a clear understanding of what entitles it to be a server.

[http://en.wikipedia.org/wiki/Server_%28computing%29](http://en.wikipedia.org/wiki/Server_%28computing%29)

---

### Post by hookitup on 2011-07-18
WOW i just had an epiphany, lol so "server" is just software, not a type of OS,,, i fell like a ding ding now, i totally thought ubuntu server edition was a hole different OS, but its really just different software, damn that explains a lot.=D>

Thanks for all your help dude

---

### Post by amjjawad on 2011-07-18
> **hookitup said:**
> WOW i just had an epiphany, lol so "server" is just software, not a type of OS,,, i fell like a ding ding now, i totally thought ubuntu server edition was a hole different OS, but its really just different software, damn that explains a lot.=D>

Thanks for all your help dude

A simple google search could enlighten your way ;)

You're most welcome!

---

### Post by wildmanne39 on 2011-07-18
Hi, I am glad my suggestion worked for you, enjoy ubuntu.

---

### Post by hookitup on 2011-07-18
hey you should check my other post to see if u have any other good advice [http://ubuntuforums.org/showthread.php?t=1805717](http://ubuntuforums.org/showthread.php?t=1805717)

---

