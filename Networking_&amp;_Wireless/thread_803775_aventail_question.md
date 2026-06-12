---
title: "aventail question"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by sw1995 on 2008-05-22
Hello,

So, I just found out that my company will let me work from home one day a week considering I face a nearly 1.5 hour commute to and fro each day. The stipulation is, however, that I need to install a program called aventail so I can remotely connect to my work computer to work from home. Does anyone know if this will work with Ubuntu? I do not have a windows computer at home. Any thoughts are greatly appreciated as I am excited and figured I would get a response quicker here than if I contacted my company's computer folk.

---

### Post by Third Thoughts on 2008-07-23
See this thread
[http://ubuntuforums.org/showthread.php?t=552216&highlight=aventail](http://ubuntuforums.org/showthread.php?t=552216&highlight=aventail)

---

### Post by Almumin on 2008-10-08
Hey Bart,

I don't have the entire tutorial that was sent to me. However, just real quick. You want to make sure that the latest Sun Java RTE is installed. Not OpenJDK. For some strange reason, it hiccups on OpenJDK (probably something app related to Aventail). Once you have Java installed. Download/install the Aventail client to /opt/aventail (mkdir aventail) or wherever you choose. Install it as root. I have seen many people that used sudo. For some crappy reason, I have always had issues with using sudo during the install. I mean, you can gksudo the launcher once you are done with the installation. /opt/aventail/ then bash ./install sh and you should be ok. (Remember in Ubuntu, Bash is not the default shell). As long as you have the Sun Java RTE (should be 6 now) and then install in terminal from root, you shouldn't have a problem. 

Let's post this back in the forum so someone else can benefit. 

Shea


[INDENT]He there,

I saw your message in a forum.  Is it possible to send me also some information
of how i can get my aventail up and running within ubuntu.

Many Thanks.
[COLOR=#888888]Bart De Wachter
[/COLOR][/INDENT]

---

