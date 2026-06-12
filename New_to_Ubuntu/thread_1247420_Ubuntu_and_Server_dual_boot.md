---
title: "Ubuntu and Server dual boot"
date: 2009-08-22
forum: New to Ubuntu
---

### Post by ConfederateColonel on 2009-08-22
I see plenty of posts about dual booting with Windows, but that's not what I'm looking for. I want to learn PHP on a LAMP system (Linux / Apache / MySQL / PHP). I also want to use the same computer for regular Ubuntu.

A little background:

1) I don't need a Windows partition (I write Windows software for a living and we've already got plenty of Windows PCs here in the office).

2) I have been using Ubuntu on a Dell Mini-9 for a pretty good while, so I have some familiarity with the OS.

3) A couple years ago, I thought that I could simply install the Linux server along with Ubuntu (bad move), and my own dumb mistake soured me on Linux until I got so disgusted with Windows that I came back to Ubuntu.

4) My objective is to have a desktop dual-booted to either Linux server OR Ubuntu desktop.

Am I understanding the basic concepts correctly? Thank you!

---

### Post by staf0048 on 2009-08-22
I might not be understanding your question properly, but the Ubuntu Server edition also functions as a desktop - however you can easily turn the standard desktop into a server as well, just install Apache2, php5, and MySQL from synaptic.  

My current desktop (the one I'm writing from) currently operates as a server as well.

On the other hand, if you want to keep them on totally different partitions for security or personal preference, you should easily be able to install the server edition Ubuntu (or other OS) without problems - though admittedly I have not tested it.

---

### Post by wojox on 2009-08-22
How comfortable are you with the terminal? If you install Ubuntu Server there's no GUI. Now the server runs great because it's light weight with less packages and a more optimized kernel.

If however you need a GUI then you're better of running Ubuntu-Dektop with Apache, PHP, and MySQL installed.

---

### Post by ConfederateColonel on 2009-08-23
1) Security was not an issue. I was just following the instructions that I was given in the PHP tutorial. It specified the server edition and made no mention of the ability to do this using the desktop edition, so I assumed that I *had* to use the server edition.

2) Although I have spent plenty of time using terminal mode (my first programming class in college was in 1972 and I sat at a big keypunch machine with a stack of Hollerith cards, so I've been through the "pre-GUI" terminal phase), for normal use, I much prefer a GUI system.

3) My question has been fully answered - I will simply install Apache, MySQL,and PHP onto the desktop edition of Ubuntu.

As a side note, the whole purpose of diving into PHP (and maybe Python also) is to finally dump Windows for all personal use, and we will only have 4 Windows systems remaining for business use that requires Windows. I have become a real fan of Linux (specifically Ubuntu) and sorely disappointed in Microshaft. We will be moving the business programming toward Linux and away from Windows - or at least that is the plan.

Thank you very much for your assistance!

---

### Post by trogfish on 2009-08-25
I don't disagree with any of the above RE: installing LAMP on a desktop machine.  BUT, as cheap as hardware is these days, you may seriously consider provisioning any old machine you can find and turn it into a 'server';  This way, you can go all crazy learning the "in's and out's" of PHP without any risk to your desktop machine.  I mean seriously, any 499.99 desktop could become your practice server....  Or something recycled from home.  Or a friend's garaged laptop...
  The advantage is you get to learn how PHP interacts with everything else... Apache, security, mysql, firewalls, etc in a 'real' server (separate machine) network environment.  Again, without risk to your daily desktop.  Sometimes how things work on your local machine is different from how it appears when served from afar....
  Just food for thought, good luck.

---

### Post by ConfederateColonel on 2009-08-25
Thanks, Trogfish!  It would definitely be nice to have that kind of setup. At this point, the problem is where to physically locate another computer. Having to maintain a Windows system (at the ready for tech support calls and that sort of thing), plus the Ubuntu system, I don't have enough room at the desk to fit another one without things getting too cluttered. I could set it up at another desk in the office, but I know that wouldn't work for very long. Based on your post though, I will put more emphasis on getting a separate system set up after I have spent some time learning the basics on the desktop system.

Again, thanks for the info.

---

