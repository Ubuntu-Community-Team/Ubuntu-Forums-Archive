---
title: "Introducing a Teenage User and Remote Login"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by beegary on 2010-01-28
[COLOR=black][FONT=Verdana][SIZE=3]Strange title I know![/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=3]I am a fairly new user to Ubuntu, and was hoping for some guidance:[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][SIZE=3]My 13 Year old cousin had a netbook given to her, an Acer eePc. It is quite old. It had XP installed but was Riddled with Adware, Viruses etc. It took her at least 10mins to access a wireless network and get IE loaded.[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][SIZE=3]I tried my LiveUSB of Ubuntu 9.10. It worked a treat.[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][SIZE=3]So I have removed XP, and installed 9.10. I didn&#8217;t want to give her NBR as I have no experience using it and am expecting that she is going to need some help.[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=3]I have also since realised that there are specific distros for the eePC range but 9.10 worked perfectly so I do not really see the need to go back. [/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=3]I have installed some games and the edubuntu package from the software centre.[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][SIZE=3]Anyway that&#8217;s the history; here are my questions before I hand it over to her:[/SIZE][/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana][SIZE=3]1. Is it possible to easily setup Remote login to her netbook from my 9.10 install? We will both be on a wireless network via a router to 2mb+ broadband. I do not really want to have to forward ports etc on her router as there is some distance between us.[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=3]2. Is it feasible to send some commands, particularly apt-get etc inside an executable shell script and have her just execute them? I can foresee file permission problems?[/SIZE][/FONT][/COLOR]
[COLOR=black][FONT=Verdana][SIZE=3]3. Do you have any recommendations for software to aid her in School Work?[/SIZE][/FONT][/COLOR]
 
 
[COLOR=black][FONT=Verdana][SIZE=3]I have always known I would enjoy using Linux as I have always been a bit of a geek, but I cannot believe how simple and easy it was to get Ubuntu up and running on her eePC[/SIZE][/FONT][/COLOR]

---

### Post by ICEB3AR on 2010-01-28
To the First: I don't know exactly, but i think it is not possible to connect to her without having open ports at the router, if you have to use the internet. 
2. You can write a shell scripts and she can easily execute that, if you send this to her. But to do this it has to be 'marked 'as executable in the file permissions: chmod u+x <path_to_file> for this you could write a little script which sets this e.g.
```

#!/bin/bash
if [ `whoami` == "root" ]; then
  chmod u+x <path_to_file>
  echo "File Permission Updated" 
else
  echo "You must be root"
fi
exit 0

```
3. Depends on what she does at school

---

### Post by nothingspecial on 2010-01-28
> **beegary said:**
> 
 
[COLOR=black][FONT=Verdana][SIZE=3]1. Is it possible to easily setup Remote login to her netbook from my 9.10 install? We will both be on a wireless network via a router to 2mb+ broadband. I do not really want to have to forward ports etc on her router as there is some distance between us.[/SIZE][/FONT][/COLOR]


Are you on the same wireless network? If so, this ridiculously easy. If not, still straightforward, but you will have to open ports, as far as I know.

Yes you can send her scripts to run, but if you have remote access you can run them yourself.

I suggest you have a look at [[COLOR="Magenta"]ssh[/COLOR]]("https://help.ubuntu.com/community/SSH")

---

### Post by sebastianabate on 2010-01-28
For remote control without port forwarding you can use Yuuguu ([http://www.yuuguu.com/home](http://www.yuuguu.com/home))
Its a multiprotocol messenger with desktop sharing capabilities, and multiplataform.
I tried it and worked like a charm.

---

### Post by beegary on 2010-01-28
> **nothingspecial said:**
> Are you on the same wireless network? If so, this ridiculously easy. If not, still straightforward, but you will have to open ports, as far as I know.

 
 
Im afraid not, Ill check out the Yugoo idea, sounds just what I need.
I have no idea what she does at school! Its been a while since I was 13!!!
 
Thanks allot everyone

---

### Post by Marvin666 on 2010-01-28
If you install all the open office pakages, some clipart, firefox, gimp, and a calcultor (I reccomend kcalc), that should cover any school-related needs.

---

### Post by J V on 2010-01-28
> **beegary said:**
> [COLOR=black][FONT=Verdana][SIZE=3][/SIZE][/FONT][/COLOR]
[SIZE=1][COLOR=black][FONT=Verdana]1. Is it possible to easily setup Remote login to her netbook from my 9.10 install? We will both be on a wireless network via a router to 2mb+ broadband. I do not really want to have to forward ports etc on her router as there is some distance between us.[/FONT][/COLOR][/SIZE][SIZE=1]
[/SIZE] [SIZE=1][COLOR=black][FONT=Verdana]2. Is it feasible to send some commands, particularly apt-get etc inside an executable shell script and have her just execute them? I can foresee file permission problems?[/FONT][/COLOR][/SIZE][SIZE=1]
[/SIZE] [COLOR=black][FONT=Verdana][SIZE=3][SIZE=1]3. Do you have any recommendations for software to aid her in School Work[/SIZE][/SIZE][/FONT][/COLOR]
Normal sized text plz...

1 You just go to preferences and click remote desktop: nice and easy GUI
2 I wrote a script for something like this, automatically downloads latest flash if ur on 64 bit etc, keyboard shortcuts and the like, all she needs to know is to rightclick > properties > allow running as program
3 Most of the apps that come with it are all she should need, and if she needs more, they are about 2 clicks away :P

---

### Post by beegary on 2010-01-28
> **J V said:**
> Normal sized text plz...
 
Sorry I pasted from MS Word on my works PC and everything went a bit haywire!
 
> **J V said:**
> 
1 You just go to preferences and click remote desktop: nice and easy GUI
2 I wrote a script for something like this, automatically downloads latest flash if ur on 64 bit etc, keyboard shortcuts and the like, all she needs to know is to rightclick > properties > allow running as program
3 Most of the apps that come with it are all she should need, and if she needs more, they are about 2 clicks away :P
 
1. And that works through Routers without Static I/P's and port forwarding?
2. Great!
3. Yes but she may need help finding them etc, hence 2.
 
thanks for your help

---

