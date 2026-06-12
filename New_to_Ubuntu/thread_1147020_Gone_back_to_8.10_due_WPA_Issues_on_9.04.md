---
title: "Gone back to 8.10 due WPA Issues on 9.04"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by siforest65 on 2009-05-03
As of last week I had never heard of Ubuntu and knew very little about Linux. We have an oldish desktop (which the kids mainly use for internet and homework) and Windows finally gave up the ghost on Sunday, with us having no discs to try and re-load.

After a bit of research we decided to give Ubuntu a go and downloaded 8.10. Must say after getting to grips with Ndiswrapper to get wireless working I was very impressed with the speed and cleanliness of the OS. Also its nice to see that the computer world is not just about Microsoft and Apple.

Anyway, after a couple of days we were offered to upgrade to 9.04 which we did. Sadly we never managed to get online with WPA security enabled, even after loading WICD. Therefore yesterday I threw the towel in and reloaded 8.10.

I must stress that I am a typical windows user, so am used to pressing a button to get things done and using the terminal on Ubuntu does scare me quite a bit.

---

### Post by Sef on 2009-05-03
You should use what ever works for you.   8.10, Intrepid Ibex will have support for about 1 more year.

---

### Post by coffeeaddict22 on 2009-05-03
Welcome to Ubuntu!
Consider the terminal not so much a place of "deep voodoo magic", as a slightly different way of doing things.  It's not too different from trying to sift through statistics; a graph puts it in a picture, and is great for the overall viewpoint; for precision, you can't beat a number.  The beauty of the terminal is the ability to be explicit about what you want to do, and get a definitive answer back.  Graphical interaction is fine for an overall view, but it isn't very precise at times.

A couple of good safety rules, though.  If you don't understand, ```
man xxxx
``` where xxxx is the command you're wanting to know more about will give you more information.  if you aren't sure of the command, try ```
apropos xxxx
``` which gives you a list of the commands you're interested in.

Second, Linux was designed to keep Uni students from trashing the computer, so there's some very effective safety nets in place.  Most importantly, each user has a "space" they're allowed to play in; only a superuser can mess with the system.  Superusers, also known as root, are what another OS tried to mimic with Administrative priviledges; however, the degree of security in linux is a step or two higher.

 Ubuntu is designed for people not familiar with Linux, and appreciating our desire not to bork the system too often, in a terminal you pretty much can't trash anything without entering superuser mode;  that's done with the "sudo" command prefixed to whatever comes after it (and by definition, you are only superuser for that single command).  So any command prefixed with sudo is worth getting a little understanding of before you jump in.

Having said that, if you take the opportunity to play you'll get a much better understanding of the system- if you're into that.

---

### Post by siforest65 on 2009-05-04
Thanks for the replies.

I must admit from a user point of view both my kids are finding Ubuntu 8.10 excellent. The internet connection is solid, unlike when we had Windows XP on the computer when it kept dropping the wireless conection (I think there were IP conflicts).

At the moment, Ubuntu has brought new life to a fairly old machine. It doesn't appear to be too resource hungry so is running very quick.

When I get time, I think I'll have a bit of a play and may even try and get 9.04 working.

---

### Post by Mortus Pryde on 2009-05-04
I to found I had to revert back to Intrepid on my T42 Laptop, though my issue was the requirement for 3D excelerated graphics needed to make a few of my programs usable. Jaunty only supporting the new 9.4 Catalyst which nolonger supports my graphics, and the open source drivers falling well short.

Over all though as a transitioning Windows user I am finding Ubuntu to be quite exceptional. Even installing my network printer was a breaze, and a pleasent surprise.

---

### Post by swoody on 2009-05-04
Hi siforest, and Welcome to Ubuntu and The Fourms!! ):P

It's always great to see people convert from Windows to Ubuntu and enjoy the experience! I'm glad you kids are liking it as well! 

Now, as the others have said, if you're up and working in 8.10 there's really no need to upgrade to 9.04 just yet. If you're still interested in getting WPA to work in 9.04, you may want to try using the 'wicd' network manager instead of the network manager that comes default with Ubuntu. I have used it for several wireless problems I've had over the years (WPA encryption being one of them) and wicd has seemed very stable since then. If you want to try it out you can either use the command line to install it - by going to "Applications">"Accessories">"Terminal" and typing in:
```
sudo apt-get install wicd
```
or by using the Synaptic Package Manager by going to "System">"Administration">"Synaptic Package Manager" and searching for 'wicd' and selecting to install it. After selecting the package, you just click apply and let it do it's thing.

Again, this is *only* if you want to try and get WPA working for you in 9.04. 8.10 is very stable, and will be great if you just want to stick with what you have working already. So it's basically just your preference!

Also, as I'd recommend to anyone new to Ubuntu, there are a couple great links in my signature, if you'd like to look them over. The Ubuntu Beginner's Guide is a GREAT resource to have on hand to better learn about Ubuntu, and to hopefully guide you through any issues you may have. On top of that, don't be shy to ask any questions you may have in the forums, as there are always a bunch of very helpful and knowledable people on here :D

Again welcome to Ubuntu and the forums, and I hope your family enjoys the new 'improved' ;) computer!

---

