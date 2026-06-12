---
title: "want to know if linux can help me out on a small project"
date: 2009-12-11
forum: New to Ubuntu
---

### Post by pcgeek10 on 2009-12-11
hi, i am very new to linux, i have used the UI of Ubuntu 8/9 on an old laptop and being a PC Geek, the expirence hasn't been too good. I know a little about linux and of couasre i know linux for power users which i am (in pc) but i got a small question i would like help on.
 
I am setting up my room as a growing network with Smoothwall 3.x and my main computer (windows 7 (RC still :( no money yet but server 08 rs i got free)) and a old laptop back in 2003-06. I want to convert files that i cna't do in windows due to no free programs, all bunch of trials. One file (a friend worked on) had to install PearPc jsut to convert .caf files (a bunch of them) What i want to do (possible for furture use or recommend for power user friends) 
 
**here is the question** (in local network, no internet)
I want a Linux distro that is like a server but i want to connect to it via CMD to convert files. in other words i want to install programs and use them via netowrk in CMd to convert files or just work with them. I understnad that the program must support netowrk use via CMD but simply want ot know if this is possible.
 
You can find all over the net with online converters but I want to own my own online converters. Linux seems like the best choice for me. Simply becasue its free and programs are mostly free. I may need something like this for a furture use.
 
Any advice? Somewhat willing to learn a bit more of linux (maybe alot learning needed :P)

---

### Post by earthpigg on 2009-12-11
im assuming by the windows term "CMD" you mean the command line? 

and that you are then willing to learn the linux command line in order to also be productive in that environment?

ok, so what you want to do is install any version of any distro (that has active repos) onto whatever computer you want to be your server, configure [sshd]("http://en.wikipedia.org/wiki/OpenSSH") on the server, and access it using [PuTTY]("http://en.wikipedia.org/wiki/PuTTY") on the client windows machine.

an ssh session lets you directly access the command line of the server machine. once it is all set up and configured, there is no reason to even keep a keyboard and monitor attached to the server computer... as long as the ethernet cable stays plugged in, of course.

if all you want is basic functionality and strong reliability, i suggest either Debian Stable or Ubuntu 8.04 LTS. Server edition of ubuntu if you wish, but it really will make little/no difference in this case.

you seem like a do-it-yourself-er kind of guy, so you can probably do some googling on your own to get it up and running with just the basic concept and the names of the tools you want to look at - which i provided.

if you need help setting up ssh or accessing the server, let us know and we can help.

as for the actual conversion of files? well, you will need to be more specific :D

---

### Post by earthpigg on 2009-12-11
> power users which i am (in pc) 

one thing that just occured to me.

self-proclaimed 'power users' and people that think "Microsoft Windows = PC" would generally (but not always) be best served by reading this prior to even looking at a Linux LiveCD: [Linux is Not Windows.]("http://linux.oneandoneis2.org/LNW.htm")

if you find me pointing out that web page to you to be offensive, i am sorry. someone pointed it out to me years ago, and it benefited me greatly.

some of the section headings may seem a bit obvious at first, but i ask that you bear with me and give it a read. at least bookmark it for later. it will help you become more adaptable, versatile, understand the difference between "windows knowledge" and "***computer*** knowledge". both are valuable, without a doubt, but they aren't the same thing... no more than "CMD" and [bash]("http://en.wikipedia.org/wiki/Bash") and the general term "[command line]("http://en.wikipedia.org/wiki/Command_line")" are all the same thing. 

and, what geek doesn't want to be able work with the operating system that runs over 85% of the world's supercomputers? :D

---

### Post by lisati on 2009-12-11
> **earthpigg said:**
> one thing that just occured to me.

self-proclaimed 'power users' and people that think "Microsoft Windows = PC" would generally (but not always) be best served by reading this prior to even looking at a Linux LiveCD: [Linux is Not Windows.]("http://linux.oneandoneis2.org/LNW.htm")

if you find me pointing out that web page to you to be offensive, i am sorry. someone pointed it out to me years ago, and it benefited me greatly.

some of the section headings may seem a bit obvious at first, but i ask that you bear with me and give it a read. at least bookmark it for later. it will help you become more adaptable, versatile, understand the difference between "windows knowledge" and "***computer*** knowledge". both are valuable, without a doubt, but they aren't the same thing... no more than "CMD" and [bash]("http://en.wikipedia.org/wiki/Bash") and the general term "[command line]("http://en.wikipedia.org/wiki/Command_line")" are all the same thing. 

and, what geek doesn't want to be able work with the operating system that runs over 85% of the world's supercomputers? :D

Nicely said. 
There have also been discussions in the forums which touch on how a MAC is a [PC]("http://en.wikipedia.org/wiki/PC").

---

### Post by pcgeek10 on 2009-12-11
yeah by CMD i mean Windwos term (command line term) and by files i maen like convertering a .caf (mac audio file, which is hard to find a free program for windows but there for linux i foudn them easier) and i am kind the do-it-yourself type of guy but i like help and advice on where to go and direct me so not to go to a dead end. 
 
I am willing to learn linux where i can do things over the network (local) to get things done that i can't do in windows (but i don't want to switch to linux just use on a need to use basics) and what i have done in linux i want a Debain Base OS that i can connect to (programs in the linux OS) and isntall programs for network use.  I am not a big on networking either. I'm more a pc user/pc tech but networking not my strong suit.
 
 
in a way is what i want in a bit more detail:
 
open CMD (Doc Promt in windows) and connect to a debain base OS and use a program that has networking support and convert a audio/video/linux file (tar, etc.) file or/and simply be a file server. not jsut for one computerto use but multi computer in a network that needs to do somthing that not free in windows, also in short be lazy later on in life so no need ot use a linux Os in person jsut open a cmd laying on a couch/chair and do something without moving to another computer in a network. (any distro okay, but I use Ubuntu Desktop before to see how it is and get the feel of it so i thought about thier Server Edition may or may not work for me, but not sure and not sure on programs supportting this feature i want)
 
On the net there file converter and no need ot install anything cept upload and redownload but not good if got a huge file on a low bandwidth.
 
(hope this answer a bit more of what i'm asking)

---

### Post by pcgeek10 on 2009-12-11
i understand that Linux isn't Windows, but "power user" and not all the CLI "windows term"  isn't the same as it is in Linux and Macs. But, I'm mainly stated as being a power user in Windows not in computer gernaly, if anybody ask me to work on Linux, I would have to say no and if they came back to me saying I'm pose to be the computer geek, but I'm not a computer geek, I'm a PC (Windows and hardware) geek:D:D. And I would liek to work with Microsoft to help make the next Windwos, but not goign ot junk down Lionux too fast, want to knwo what i could be junking on, but Linux okay for me, but, not knowing linux well makes it hard for me but i understand it nto the same, but jsut a few mintues ago, i wish smoothwall had "Diskpart" for a file transfer (mod)
 
 
 
 
How can Linux even act as Windows if I can't even do a simple file transfer the same way i would if it was a PC?? :P
(just ran into a problem like that, but think i got it now with a forum help in Smoothwall forums)

---

### Post by lisati on 2009-12-11
> **pcgeek10 said:**
> 
open CMD (DO**S** Prom**p**t in windows) 

fixed for you :D

---

### Post by pcgeek10 on 2009-12-11
> **lisati said:**
> fixed for you :D
 
thanks, where i am its cold and hands are harding and my spelling not good either.
 
I can install windows, troubleshoot windows (kernal, memory dumps, etc.), custom built PCs (if money is present), setup Remote Services in WinServer 08 R2 for Remote app, and other big things in windows that normal people don't know but... I can't spell good :P :P :P

---

### Post by earthpigg on 2009-12-12
well, i explained to you how to talk to your server from a windows client:

PuTTY.

you enter some basic information about the computer you want to talk to:
[IMG]http://www.wifi.com.ar/english/doc/network/putty/putty-session.gif[/IMG]

and thats it. you are now looking at the command line of that *nix box... just as if you where behind the keyboard at the physical computer.
[IMG]http://raymond.cc/images/putty.gif[/IMG]
[IMG]http://www.cae.tntech.edu/help/remote-access/windows-putty/putty-logged-in.png[/IMG]

as for converting different multimedia formats: i myself haven't really done much of it, so i won't recommend any of the google results i see over any other ones.

look around at what solutions provided by google look promising to you. when you see one that you think looks promising, post a link to it here and we will let you know if it looks like a reasonable solution (as opposed to some random crud that doesnt work that some random person put up on the net somewhere.)

---

