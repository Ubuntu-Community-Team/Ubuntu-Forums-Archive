---
title: "Asterisk on Ubuntu Server Edition"
date: 2008-07-02
forum: Networking &amp; Wireless
---

### Post by suaderinvader on 2008-07-02
Ok so I am very new to Ubuntu Desktop Edition and Even newer to Server Edition. I am switching from Windows XP and Vista to Ubuntu so that kinda makes it harder. 

I am currently helping a friend with his data center help desk. I am working remotely using an SSH connection. My job is to get this Asterisk to work on Ubuntu Server Edition. I have just sent my friend a message on what version of Ubuntu Server Edition I am working on as it just now occurred to me I do not know which version it is though I do suspect it is the newest version which is 8.03 or something like that. 

There are several complications though, I was going to use the Zaptel hardware support but that will not be able to work in VMware ESX and will not be enough firepower for what we need. And we need a way to bring in voice traffic in that doesn't require custom hardware on the network. "Two ways that I can think of right now are (1) SIP trunks from an external provider or (2) using a router to convert a PRI call to IP for the Asterisk server to handle.  I have some experience with #2, but none with #1." Was what he sent me in a message. S:confused: But ok, he's going to take care of that most likely so thats less I have to lose sleep over now.

My second idea, as a fall back was to use Xorcom.com sources and FreePBX as it would get us the basic Asterisk+FreePBX install. He suggested that i check that apache2, php5, and mysql were already installed and that they should be since they are pretty much standard and if they aren't that they shouldn't be too difficult to install.

However I do not know how to verify that they are install and I do not know anything about directories on this as since I am a Windows XP user I am used to the C:/Program Files or C:/Documents    and Settings or something like that to explore for files and I don't know a single thing about navigating through directories on this OS much less doing it remotely. Although I did see a thread that did point me in the direction of getting a graphical interface (desktop) so thats a start at least right? Right.

So as you can see I am stuck. I don't know how to navigate in this OS, I don't know how to verify that certain files or programs are installed which is something that i desperately need to do, and if they aren't installed then I need to install them which is something that I also don't know how to do.

Although I think I am getting somewhere with finding the packages containing the supplies apache2, php5, and mysql by using:

sudo aptitude search (either apache 2, php5, mysql)

However when I do that I get an enormous list of packages and I do NOT know which ones I need and which ones I do not. But I have been able to make an EDUCATED guess at which ones I might need do not need by the description but am not 100% sure at the moment.

Also one question, how do I access websites using this Server edition (i.e how would I go to [HTTP://www.yahoo.com](HTTP://www.yahoo.com) or something else???)

If anything else comes up I'll try to add to the thread or something...I don't know, I'm new to the forum and in desperate need of help.

I bet this computer is enjoying my suffering :popcorn:

Stupid computer...

Thanks for the help in advance!

---

### Post by StooJ on 2008-07-06
Uhm, no offense or anything, but it might be an idea to learn to walk before you can run.

One of the first things I learned when I moved away from Windows to Linux was that I really didn't know anything about computers at all. I only knew about Windows, and hardware under windows. I had a lot of un-learning to do before I could get to grips with this completely different OS. I went from "expert" to complete novice in a single day. It is a painful awakening, but a very rewarding journey.

So, my advice would be to start a lot smaller. Try to get to grips with an ubuntu installation of your own before trying to set up something like a remote asterisk deployment elsewhere. Try a dual-boot Ubuntu desktop edition on your own machine, getting used to the way things are done. Since you're interested in servers, try getting comfortable with the command line.

However, to answer one of your questions, if you want to browse the web in a terminal, you could try lynx, which is a text-based browser and very clever too (in my opinion, anyway)

To install lynx
```
sudo apt-get update && sudo apt-get install lynx
```
apt-get update simply updates the list of packages you can install for your system. Always a good idea before you install anything new.
apt-get install lynx is pretty self explanatory.
You'll probably be asked for a password too.

To run lynx
```
lynx
```

---

### Post by emid on 2008-07-14
In my opinion, if this Ubuntu server is only running as an Asterisk box, you would be better off using a different distro altogether.  I would recommend that you guys install either [trixbox]("http://trixbox.org/") or [PBX in a Flash]("http://pbxinaflash.com/").  If you aren't that comfortable with linux in general, it will be SIGNIFICANTLY easier to get things up and running.  You'll end up with Asterisk and FreePBX all set up for you.

Setting up SIP trunks is really quite easy once you are in the FreePBX web UI.  There are also plenty of tutorials that will explain what you need to do step by step. Check out the trixbox forums, the freePBX forums, and nerdvittles.com (the guys behind PBX in a Flash).

You'll save yourself a lot of grief by going this route.  There really is no major benefit in setting up an Ubuntu box from scratch for this purpose.

---

