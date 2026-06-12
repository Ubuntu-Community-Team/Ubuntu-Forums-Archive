---
title: "Having fun with computers."
date: 2009-05-04
forum: New to Ubuntu
---

### Post by furialis on 2009-05-04
I have a unique situation and would like to exploit it. In my home I have a LAN setup with two STB's. My roommate also has a cable modem in the house. That means I have access to two machines in my house that are networked through the Internet. I have a spare computer that I can load anything I want onto. Currently it has XP SP3 on it. My main computer runs Jaunty. 

I'm just starting to learn about computers and networking and having a lab in my house helps. What I need are suggestions on how to learn about how computers interact with each other over the internet, how they share files, how web pages are stored and accessed, just about anything! I'd like to learn about SSH for example.

Hit me with suggestions, thanks!

---

### Post by jerrrys on 2009-05-04
call me confused...

LAN is local area network and internet is not required. if your plugging into the internet modem using ethernet [http://en.wikipedia.org/wiki/Ethernet](http://en.wikipedia.org/wiki/Ethernet) then your running LAN. if you are using the internet to access second system that would be remote access.

heres a starting point.

[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba)

samba is used to tie windows/linux together on LAN.  i you find that too heavy, try this..

[http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu:en-US:unofficial&hs=Zrg&num=50&ei=IRr_SYCYFpP2MIqxyawE&sa=X&oi=spell&resnum=1&ct=result&cd=1&q=ethernet+for+beginners&spell=1&cts=1241455166103](http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu:en-US:unofficial&hs=Zrg&num=50&ei=IRr_SYCYFpP2MIqxyawE&sa=X&oi=spell&resnum=1&ct=result&cd=1&q=ethernet+for+beginners&spell=1&cts=1241455166103)

---

### Post by furialis on 2009-05-04
I'm sorry for the ambiguity.

I have my own internet account, my own computer (with Jaunty on it) a router and some Linux based [STBs.]("http://en.wikipedia.org/wiki/Dreambox") This is my LAN with internet access in my room. I aslo have a spare computer that I can load anything onto and play with on my LAN. In the room next to me, my roomate also has his own internet account. I can test either with LAN or WAN.

Maybe I'm missing something, but I would think few people have access to WAN in their homes. I thought I had a unique opportunity to test WAN having a 15 sec walk between computers. 

I'm just looking to learn about how the net works. I have all my Music on my computer - could I access it through the WAN on my other computer? I'm pretty sure I can as I've set up a Samba share on my LAN. Isn't SSH a way to run commands remotely and securely? 

Ubuntu has opened my eyes to the world of computers and I'd like to know more. Thanks.

---

### Post by xhaan on 2009-05-04
I did the same thing before, installed FreeBSD on one of my old boxes and turned it into a stripped down headless ftp/http server with oustide access from the internet, and had turned another machine into a gateway/firewall and hooked them all together.

It's quite fun, really... but yeah, there's a lot you could do both LAN and WAN side, make a web server, a game server, or whatever. You can also practice LAN side networking which is not transparent or blocked to the WAN side (LAN only servers, NAT, port forwarding, etc)

---

### Post by furialis on 2009-05-04
> I did the same thing before, installed FreeBSD on one of my old boxes and turned it into a stripped down headless ftp/http server with oustide access from the internet, and had turned another machine into a gateway/firewall and hooked them all together.

It's quite fun, really... but yeah, there's a lot you could do both LAN and WAN side, make a web server, a game server, or whatever. You can also practice LAN side networking which is not transparent or blocked to the WAN side (LAN only servers, NAT, port forwarding, etc)

Those are the types of things I'm talking about. The only problem is, where do I start? Something simple for me to start with. Links to howto's would be much appreciated. Also, I'd like to hear anecdotes from as many people as possible about how they got started.

---

### Post by LowSky on 2009-05-04
First I think you really need to read up on how internet connections work, and the difference between a cable modem and a router, and WAN and LAN. Use google its your friend, try googling *linux network server*.  Looking up you own information can be even more rewarding than asking people on a forum to give you suggestions.

Second, may I suggest baby steps, first learn to crawl before you walk. Learn the ins and outs of Linux before moving onto other ambitions.

For instance as of right now, do you know how to use the terminal in Ubuntu, if asked could you use the command to show all currently open programs, could you type the correct phrase to view a file without using nautilus. Could you figure out how to install an application without  the help of a GUI? If you cant do these things as of right now, then you should learn and be comfortable doing them beofre moing onto other projects

BTW google has an option to do Linux related searches
[http://www.google.com/linux](http://www.google.com/linux)

how to install source files
[http://www.tuxfiles.org/linuxhelp/softinstall.html](http://www.tuxfiles.org/linuxhelp/softinstall.html)
[http://laptoplogic.com/resources/a-beginners-guide-on-how-to-install-linux-software](http://laptoplogic.com/resources/a-beginners-guide-on-how-to-install-linux-software)


linux command list
[http://www.oreillynet.com/linux/cmd/](http://www.oreillynet.com/linux/cmd/)

some great things to know

[http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)

---

### Post by furialis on 2009-05-04
Again, I apologize for the ambiguity.

LowSky, Thank you for the suggestions. The problem is I've reached a bit of a plateau in my quest for computer knowledge. I have no training at all in computers. Like I mentioned above, I've already set up a samba share on my LAN, which while very basic, is still quite a bit above the average Windows users. I'm long out of school and school provides you with a structured learning system of projects. I don't mind reading (and reading some more), I'd just like some projects to become a system admin, for example. What are the responsibilities, etc. What about setting up a simple web page on my server? I'm assuming the people who regularly answer questions on this site have gone through school for it. Should I just look up a college CS semester class list? Where should I start?

I'm pretty comfortable with the command line, and actually I never thought I would say it, but I would miss doing things that way if I were to go back to XP. It's so much easier. FTP, local networking, subnets - I'm getting there, I just need projects to tie it all together

Thanks for the help, I need to learn to be more clear.

Edit: My other [project]("http://ubuntuforums.org/showthread.php?t=1145049") didn't get any responses, nor could I find an answer googling. I'm trying something different.

---

### Post by xhaan on 2009-05-04
Hmm. It's kind of hard for me personally to advise you, since I'm **really** forgetful on how things work (I have to reference man pages all the time even for the most simple commands that I forget)... Plus I'm not a very good instructor, but I kind of started out the way you did, with a machine that I could do anything I wanted with, and the cool part about that was I didn't have to worry about breaking it, so I just dove in, read manuals and got my hands dirty.

One thing I do recommend with learning networking stuff in the beginning, is to start out LAN side only, or even loopback access only (probably the safest way to go). You really don't want to go 'live' on the internet with servers until you know quite a bit about security, because allowing outside access to your machines is always risky.

---

### Post by snova on 2009-05-04
> **furialis said:**
> I'd like to learn about SSH for example.

That one's easy. :)

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

> **furialis said:**
> I'm assuming the people who regularly answer questions on this site have gone through school for it. Should I just look up a college CS semester class list? Where should I start?

Not necessarily.

---

### Post by Iowan on 2009-05-04
help.ubuntu.com has several good help pages.  You will also find a good one on  [LAMP]("https://help.ubuntu.com/community/ApacheMySQLPHP").

---

