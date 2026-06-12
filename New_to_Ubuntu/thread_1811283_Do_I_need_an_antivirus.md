---
title: "Do I need an antivirus?"
date: 2011-07-24
forum: New to Ubuntu
---

### Post by cfree on 2011-07-24
I have always heard from people that when someone switches from windows to a mac or linux OS that there is no need for an antivirus program is this true. Also would the same hold true for a firewall program? And if I do need one can what would be some good programs

---

### Post by cgroza on 2011-07-24
No, you don't. There is antivirus software for Linux, but they scan for Windows viruses only.

---

### Post by bezgoan on 2011-07-24
The linux flavours or in general Unix flavours do not require any antivirus for the reason that virus would infect if and only if there is an align in the kernel, else virus will not be able to control the hardware. To enter into kernel, one would always need root access, which will lead to chicken and egg situation and hence no virus are seen in Unix flavours. 

I am not an expert, but this is what I perceive it as from my knowledge.

---

### Post by amjjawad on 2011-07-24
> **cfree said:**
> I have always heard from people that when someone switches from windows to a mac or linux OS that there is no need for an antivirus program is this true. Also would the same hold true for a firewall program? And if I do need one can what would be some good programs

You don't need an AntiVirus Program when you're using Linux but it doesn't mean there is NOT any AntiVirus Programs, actually there is but usually to fix Windows Machines ;)

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

As for Firewalls, I recall there is one installed by default with Linux Mint but can't remember the name.

[https://help.ubuntu.com/community/Firewall](https://help.ubuntu.com/community/Firewall)

A quick and a simple Google Search will show you great things and will answer such Qs ;)

---

### Post by Rex Bouwense on 2011-07-24
Do you need an anti-virus program?  The short answer is no.  Do you need a firewall?  Again the short answer is no.  However, many people install an anti-virus system.  Here are a couple of sites for information:

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)
[https://help.ubuntu.com/community/Linuxvirus](https://help.ubuntu.com/community/Linuxvirus)

A firewall is installed by default and you can activate it if you so desire.
Again, here is a site for information:

[https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)

---

### Post by cfree on 2011-07-24
So the reason why we don't need an antivirus is because the virus would need root access to run itself? And would that mean you could have a virus sitting on your desktop and would be fine just as long as you didn't open it and give it root permissions?

---

### Post by Rex Bouwense on 2011-07-24
For anyone to make any changes to your system, that person or program must have root authority to do so.  You can get root authority for a short period of time to make changes, but a program cannot unless you (as root) tell it to.  I'm not sure if that is clear.

I was told a long tome ago that a Linux operating system was like a room with locked windows and locked doors.  Nothing can get in unless you let it in.

---

### Post by haqking on 2011-07-24
> **cfree said:**
> So the reason why we don't need an antivirus is because the virus would need root access to run itself? And would that mean you could have a virus sitting on your desktop and would be fine just as long as you didn't open it and give it root permissions?

The reason you dont need to worry about AV so much is that Linux does not have the market share of other operating systems and so virus developers dont spend as much time creating them for Linux machine as there are more windows users out there to infect.

on top of which, the security model is different in Linux and it is harder for a virus to infect a Linux machine and would need to do so in a different way to most other platforms due to the lack of .exe files and running with escalated privelege.

There have been some Viruses for linux as seen in the links already provided but they have been patched long since and though AV software is available viruses are really not an issue in a linux environment at the moment though things change everyday

for peace of mind feel free to install ClamAV or other Av software if you so desire.

also look at apparmor for more peace of mind for your machine and app security

---

### Post by amjjawad on 2011-07-24
Some extra links might be helpful too:

[http://en.wikipedia.org/wiki/Computer_virus](http://en.wikipedia.org/wiki/Computer_virus)

[http://www.google.ae/search?q=Linux+Virus&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.ae/search?q=Linux+Virus&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

---

### Post by texasboy2084 on 2011-07-24
I'm not all that Linux savvy, but from my understanding you don't need an anti-virus because a virus is made on Linux for Windows not for Linux.

---

### Post by cfree on 2011-07-24
Ok I have a better understanding of it now thanks for all the responses :)

---

### Post by amjjawad on 2011-07-24
> **cfree said:**
> Ok I have a better understanding of it now thanks for all the responses :)

Glad to know that :)

Is that all? or you have another Q? :)

---

### Post by haqking on 2011-07-24
> **texasboy2084 said:**
> I'm not all that Linux savvy, but from my understanding you don't need an anti-virus because a virus is made on Linux for Windows not for Linux.

not true.

however most viruses in the wild are for windows machines as i stated above.

the platform a virus is developed on is neither here nor there, most viruses are developed in a windows environment for a windows environment.

traditionally they were written in assembler, but nowadays you can get plenty of virus creation kits and lots are created in Visual basic.

in short it is about what the virus is supposed to do not what OS it was created on

---

### Post by oldsoundguy on 2011-07-24
To clarify a bit.  It takes real effort to install something in Linux that is OUTSIDE of the repositories.  Multiple steps. (the "Linux is not that much in use so not that much of a target" statement does not wash .. not with nearly 60% of ALL servers running Linux or Unix.)

Now your BROWSER is a different story.  So practicing safe hex .. er on line networking is still a damn good idea.

AND, IF you are in a network with a hub/router between you and the world, not much need for a firewall for single user.  An office situation with multiple users .. a firewall between computers may be called for. (and in that situation, an AV installed to check your eMail so you may forward CLEAN eMail to protect the Windows users is called for.)

---

### Post by IWantFroyo on 2011-07-24
No antivirus is really needed (unless you like to browse unsafe sites so much that viruses are cogging up your folders). And then its easier to just delete them.

As for a firewall, you could do it. It isn't necessary, however. UFW is a good start. It can be worth experimenting with networking on Linux. You can fool around with aircrack-ng just for fun/knowledge.

---

### Post by cfree on 2011-07-24
> **IWantFroyo said:**
> No antivirus is really needed (unless you like to browse unsafe sites so much that viruses are cogging up your folders). And then its easier to just delete them.

As for a firewall, you could do it. It isn't necessary, however. UFW is a good start. It can be worth experimenting with networking on Linux. You can fool around with aircrack-ng just for fun/knowledge.

What do you mean like your downloads folder from items that you have downloaded from different sites?

---

### Post by amjjawad on 2011-07-24
> **cfree said:**
> What do you mean like your downloads folder from items that you have downloaded from different sites?

Just make sure NOT to visit any suspicious website and download anything from there ;)

With Ubuntu for example when we use Synaptic, we don't have to visit any website to install any program, it's almost all there :)

---

### Post by IWantFroyo on 2011-07-24
> **cfree said:**
> What do you mean like your downloads folder from items that you have downloaded from different sites?

It will probably try to do something in C://*whatever* (Windows filesystem) and utterly fail, possibly giving you an error message (probably not).

If its a Mac virus, it'll probably have to ask for permissions, so you'll likely get something like:
/home/user/Downloads/virus is asking for superuser permissions. Grant? (obviously not)
If you put your password in, it probably still won't work (ever tried to install a Mac program in Linux? If that worked, Apple and their OS X would be screwed).

Bottom Line: Do not put your password anywhere lightly. If you don't know what program is asking for permissions, don't give it to them. If you know what the program is but you don't trust it, go research for reviews. All trusted programs have them.

---

### Post by cgroza on 2011-07-24
> **haqking said:**
> The reason you dont need to worry about AV so much is that Linux does not have the market share of other operating systems and so virus developers dont spend as much time creating them for Linux machine as there are more windows users out there to infect.

Hmmm, what should I infect? A meaningless desktop or a big server hosting 100+ websites... tough choice...

---

### Post by wildmanne39 on 2011-07-24
Hi, for a firewall you can use gufw, you can read about it in the security section of the forum.

---

### Post by lisati on 2011-07-24
+1 for the responses so far. The best anti-virus solution available includes a feature that is available to all systems: a healthy dose of good sense by the user. In other words, be smart about what you allow on your computer.

---

### Post by beew on 2011-07-24
There is but one reason that you may need an AV, that you are in communication  with some Windows users who don't know better to install or upgrade their Av so you don't want to pass on viruses which wouldn't harm you but may do damages to such Windows users (there are such people btw, like my dad, but since he mostly calls me and it is always he who sends me attachments and dubious links rather than the other way around so I don't need any AV even with him. :))

---

### Post by egalvan on 2011-07-24
> **cgroza said:**
> Hmmm, what should I infect? A meaningless desktop or a big server hosting 100+ websites... tough choice...

Boy, did you hit the nail on the head!! :guitar:

that "smaller market share" boogie-man is Microsoft FUD, pure and simple.

The Internet is **heavily** dependent on Linux/BSD/UNIX...

Apache, MySQL, DNS, BND, firewalls, routers, switches, etc.



ActiveX... a boon to Trojans everywhere.

---

### Post by egalvan on 2011-07-24
> **beew said:**
> There is but one reason that you may need an AV, that you are in communication ** with some Windows users who don't know better to install or upgrade their Av so you don't want to pass on viruses which wouldn't harm you but may do damages to such Windows users **

I agree with this 100%,
and its the reason I have AV on my main Linux box...
to safe-guard Microsoft machines... :P

---

### Post by UltraNEO* on 2011-07-24
> **cfree said:**
> I have always heard from people that when someone switches from windows to a mac or linux OS that there is no need for an antivirus program is this true. Also would the same hold true for a firewall program? And if I do need one can what would be some good programs

Depends on your circumstances. If you're in a corporate situation then both Mac and Linux systems will have anti-virus installed but they'll be there to filter/catch/kill Windows viruses only. As far as I know, Windows viruses can't affect a Mac.

---

