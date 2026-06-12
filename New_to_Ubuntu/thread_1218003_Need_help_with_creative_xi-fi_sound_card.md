---
title: "Need help with creative xi-fi sound card"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by zebedeeboss on 2009-07-20
Hi guys and gurls... finally got Ubuntu installed on my machine and all seems ok   except...

Why is everything so damned hard to do  lol   having been a die hard windows fan for years I was pleased to finally get it installed only to fall over at the next hurdle.

I got my sound card drivers downloaded... clawed... climbed and worked my way around the terminal window only to be told  I can't make install as permissions don't allow installer to create a directory where it needs too

Any help greatly appreciated...  I really do want to put the "Linux simply don't work" behind me

"Complete Newbie"  Zeb

btw  its a creative xi-fi sound card... and having read some of the forums.... it seems to be a tricky problem ?

---

### Post by masux594 on 2009-07-20
what is the operation that u want to do?[the command that doesen't run..]

Sysc, A

---

### Post by hetx on 2009-07-20
You use the "sudo" command to get root permission. As in:

sudo apt-get install firefox

I assume your sound didn't work from the start? That's unlucky, never had that problem.

---

### Post by ~sHyLoCk~ on 2009-07-20
Yes, Linux is not easy. What can we do about it? Try and learn maybe? Or just quit and go back to windows, it all depends on your personal preference. Besides, distros like Ubuntu, Mandriva, Suse, have made Linux easier for newbies. The best way to find quick replies for your queries is through google, and I mean it the most caring way. 
To answer your permission question, try using "sudo" before a command, everytime it says Permission Denied.

---

### Post by zebedeeboss on 2009-07-20
Wow those replies were quick.... thank you I will try sudo   and see what happens and let you know  :D

---

### Post by Alias1407 on 2009-07-20
sudo means 'Super User Do', it temporarily borrows Administrator/Root privelages to do a task such as copy binaries or create config files in folders that you don't have privelages in.

If you have not set a root password yet, do this by...
```
sudo passwd
```

Then try...
```
sudo make install
```

---

### Post by masux594 on 2009-07-20
ubuntu has a VEEEEERY BIG community.. a sort of "Underground community" that only a ubuntu user know =)

Sysc, A

---

### Post by zebedeeboss on 2009-07-20
Hey... we have lift off... Thank you very much... now I have the basics working  I can slowly come to grips with Ubuntu

and ~sHyLoCk~  yes I will go running back to windows if I need to do something quickly as it is a familiar friendly face that I feel comfortable with. but now I have a basic install that actually works.... I WILL persevere

ps  once I understood what sudo was   all I had to do was a  "make"  then a "make install"  reboot  and I have sound :)

Thank You all once again... cya round the block

pps you will get tired of my newbie questions :):):) Zeb

---

### Post by ~sHyLoCk~ on 2009-07-20
> **zebedeeboss said:**
> Hey... we have lift off... Thank you very much... now I have the basics working  I can slowly come to grips with Ubuntu

and ~sHyLoCk~  yes I will go running back to windows if I need to do something quickly as it is a familiar friendly face that I feel comfortable with. but now I have a basic install that actually works.... I WILL persevere

ps  once I understood what sudo was   all I had to do was a  "make"  then a "make install"  reboot  and I have sound :)

Thank You all once again... cya round the block

pps you will get tired of my newbie questions :):):) Zeb

Don't be afraid/embarassed to ask questions, since this forum is meant for helping out people,specially the new ones. Just don't quit and keep on learning. ;)

Good luck

PS- Don't play around with sudo much, it gives you root privilige and might damage your system if you do something carelessly. eg-> Suppose you want to delete a file in home folder named abc.txt and you put a space after /home/$USER and instead you typed sudo rm ~/ abc.txt
 
It will damage your system! It will clean your home folder nicely. :)

---

### Post by yeats on 2009-07-20
> Hey... we have lift off... Thank you very much... now I have the basics working I can slowly come to grips with Ubuntu

and ~sHyLoCk~ yes I will go running back to windows if I need to do something quickly as it is a familiar friendly face that I feel comfortable with. but now I have a basic install that actually works.... I WILL persevere


That's the spirit.  Soon enough Ubuntu will be the "familiar friendly face" and Windows will be... well, Windows :-)

---

### Post by /usr/sbin on 2009-07-20
> **chrissharp123 said:**
> That's the spirit.  Soon enough Ubuntu will be the "familiar friendly face" and Windows will be... well, Windows :-)

The community is amzing here, you get such a quick reply. Anyway ontopic again, be careful using the sudo command.

---

### Post by willmsbrt1 on 2009-07-20
I am also new to ubuntu but with the help of this fine group of people I am not going back to windows and have now started to replace the pcs in our workplace ( as I can ) with operating ubuntu systems , 

Wish me luck as our workforce is some 20.000 ( Yes 20 thousand ) strong , 

I am over the 100 mark and my coworkers love the switch and with in house repositories the updating of the same pcs is easy , quick and efficent , 

Only need to test on one machine and the rest are good to go :) so newbie or not , in it for the long haul , 

p.s. the one thing my coworkers like the most of this arrangment is they have the ability to change settings to there preferance unlike windows administrative rights , cant defrag or change the system time , wahts up with that ? , the windows machines slow down very quickly if no maintenance done in a timely manner

---

### Post by /usr/sbin on 2009-07-20
^^^ Congratulations, keep up the good work. XP's and Vistas start up times are well known for very quickly getting longer :)

---

### Post by 3rdalbum on 2009-07-20
Linux is easy-peasy if you have fully-compatible hardware. The situation with Creative X-Fi is pathetic - Creative told the Linux community that there would be an official Linux driver for X-Fi, so the community didn't start reverse-engineering one. Finally, Creative released a driver that was buggy, only worked using an obsolete sound system, completely closed-source, and only worked on 64-bit Linux. Recently, after a year of not maintaining the driver, Creative released the source code and only now is it starting to improve.

Unfortunately since you have X-Fi you've been thrown in the deep end with having to compile a driver from source. That itself isn't hard, but if you don't know what you need to install on your system to compile kernel modules, and if you don't know how to elevate to root so you can install things to system-wide places, it can be very difficult indeed.

I make sure that all computers I build will work out-of-the-box with Ubuntu, so everything's ready to go literally after installing Ubuntu.

---

### Post by Little Bit on 2009-07-20
**I'm a brand new Linux girl**, and my first experience with Linux was easy and fast! I borrowed a friend's laptop and used it effortlessly for several different tasks, and when I returned it I remarked about how fast and how easy it was. That's when he sprung it: "It's Linux!" I was stunned. I had used Linux and it wasn't hard??! 

When the time was right (after Vista "updated" again and all kinds of troubles multiplied afterwards), I asked Robin about Linux and he introduced me to Ubuntu. Today is only my second day using it, but here is what I have already learned:

**These forums are awesome!** Just reading them (without even posing a question) is very informative. I have a bunch of stuff written down.

**The command line is a secret weapon** that I never would have dared use in Vista. I'm told that in Ubuntu I may never have to use it, but it is an awesome, powerful tool. It makes very short work of big tasks. And even a non-geeky little girl like me can use it!

**Ubuntu is more customizable** and configurable than Windows ever was! It's fun to play with and make it look just the way I want and do just what I need it to do.

**Even if you "break it," fixing Linux is easy!** Alot easier than I ever would have thought. It's so hard to get over this prejudice I've been taught, that Linux is just for geeks. I don't think it's as geeky as Windows is because I spent so much time in Windows installing programs one by one, installing, updating, and regularly scanning antivirus, anti spyware, registry cleaner and optimizers to make Vista behave like - well, like Ubuntu does without all that work! Who's the geeky girl now?

Love,
Amy

---

### Post by hetx on 2009-07-20
Now all we have to do is populate the world with Amys.

---

### Post by p0cky84 on 2009-07-20
Yes, linux is not easy. But it's worth it.

---

### Post by martini1179 on 2009-07-20
> **~sHyLoCk~ said:**
>  PS- Don't play around with sudo much, it gives you root privilige and might damage your system if you do something carelessly. eg-> Suppose you want to delete a file in home folder named abc.txt and you put a space after /home/$USER and instead you typed sudo rm ~/ abc.txt
 
It will damage your system! It will clean your home folder nicely. :)

 I would also say that probably 90% of what a new user needs to go can be done in Nautilus (the file manager), Add/Remove, and Synaptic. New users should get familiar with those before they start using sudo.

---

