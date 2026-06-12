---
title: "Viruses in Ubuntu?"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by ovroniil on 2009-08-16
I've heard earlier that there is no chance of infecting viruses in Ubuntu or any other linux distro. But I got a [wikipedia link]("http://en.wikipedia.org/wiki/List_of_proprietary_software_for_Linux#Antivirus") where several antiviruses are listed for linux!

So is linux really fully protected from viruses?

---

### Post by llamabr on 2009-08-16
The only way to completely protect your system is to disconnect it from the web.

That said, linux file system,  and system of permissions make it much more difficult for a user to infect the system.  Additionally, since 90% of desktops run windows, people who write viruses don't write them for linux.

Additionally, a few of those listed there are actually linux apps to remove viruses on windows.

So, be vigalent, don't install anything you don't recognize, don't run commands you don't understand, have a firewall, and you shouldn't have to worry overmuch.

---

### Post by SuperSonic4 on 2009-08-16
I should point out that this is common to GNU/Linux as a whole rather than Ubuntu

I believe they exist but have long been fixed or not even released into the wild.

As long as you're not an idiot you don't need an antivirus and if you were one would not save you

---

### Post by berthiggins on 2009-08-16
Although there are no known effective viruses for linux virus scanners are provided mainly to avoid passing viruses on to windows users for instance by e-mails etc.
For this reason they are more common on servers .

---

### Post by jrothwell97 on 2009-08-16
Linux, and therefore, by extension, Ubuntu, is virtually virus-free at present. Linux anti-virus software is usually designed to search for Windows viruses, to ensure that any Windows viruses on your Ubuntu machine don't become a risk to any other Windows machines.

---

### Post by mcduck on 2009-08-16
There are no Linux viruses in the wild, and the few that even exist are mostly just proof-of-concepts that wouldn't survive in real world. Then there are couple of viruses that could be considered as real one,  but depend on users having highly outdated versions of certain software (like Slapper).

There are two reasons for anti-virus apps being available for Linux:

1. May of them are for scanning for Windows viruses, for example to be used on a mail server to help protect Windows machines.

2. Profit. Anti-virus companies make money by selling their software, and would of course like to expand their market to contain Linux users as well. Many companies are telling us that while there are no viruses now, there might be in future and therefore we should buy their program. Of course the program will still only scan for Windows viruses since there's not much else to scan for.

Some people like to run antivirus on their Linux machines to protect their Windows systems, for example to avoid situations when they might move infected file from Linux to Windows. However, in my opinion, this is redundant as the Windows machine will have to run antivirus software anyway and thus should be able to protect itself.

The best protection for your Linux system is to simply install security updates when they are released. If you run an server applications that are open to the network you should configure a firewall as well, but for normal desktop use even that's optional.

---

### Post by Bachstelze on 2009-08-16
More info here:

[https://help.ubuntu.com/community/Antivirus](https://help.ubuntu.com/community/Antivirus)

Also, thread title edited so as to not spread FUD.

---

### Post by colau on 2009-08-16
> **ovroniil said:**
> I've heard earlier that there is no chance of infecting viruses in Ubuntu or any other linux distro. But I got a [wikipedia link]("http://en.wikipedia.org/wiki/List_of_proprietary_software_for_Linux#Antivirus") where several antiviruses are listed for linux!

So is linux really fully protected from viruses?
I think, there is no virus in Linux.

---

### Post by halitech on 2009-08-16
> **colau said:**
> I think, there is no virus in Linux.

we wish that were true

[http://en.wikipedia.org/wiki/Linux_Virus](http://en.wikipedia.org/wiki/Linux_Virus)

the do exist, just not really in the wild and are very limited what they can do if you did become infected

---

### Post by ovroniil on 2009-08-16
[quote=halitech]we wish that were true

[http://en.wikipedia.org/wiki/Linux_Virus](http://en.wikipedia.org/wiki/Linux_Virus)

the do exist, just not really in the wild and are very limited what they can do if you did become infected[/quote]

And I thought there is none!

---

### Post by mcduck on 2009-08-16
> **ovroniil said:**
> And I thought there is none!

If you check the actual descriptions for those viruses you'll understand why people say there are no viruses for Linux.. ;)

---

### Post by halitech on 2009-08-16
unfortunately they do exist but most are more proof of concept to show they could but Linux gets patched pretty quickly so unless you are running an old version without updates, you should be safe. Even if you do get one (by inadvertently running it) unless you run it as root (Sudo) then the most it could do is remove/damage your home folder which is fairly easy to fix (just create a new user and home folder)

---

### Post by lukjad on 2009-08-16
> **ovroniil said:**
> I've heard earlier that there is no chance of infecting viruses in Ubuntu or any other linux distro. But I got a [wikipedia link]("http://en.wikipedia.org/wiki/List_of_proprietary_software_for_Linux#Antivirus") where several antiviruses are listed for linux!

So is linux really fully protected from viruses?

Hey Ron ;)

Getting a virus in Linux is like getting hit by a meteoroid. It CAN happen, it HAS happened, but it's so unlikely, and the usual damage it causes is so minor that it's barely worth mentioning. 

A lady once was hit on the thigh by a meteor, and got a bruise. Likewise, there were some viruses designed for Linux, but like meteoroids, they usually burn up on entry, and usually didn't hit anyone, and when it does, it only affects that one person.

In time, perhaps there will be more viruses, just as one day there could be larger meteorites that hit the Earth. But for now we don't need to worry too much about it. 

Now, that's not to say that Linux has no vulnerabilities. There are always ways in. Saying that because Linux is immune to malware because viruses are rare and hard to produce is like saying that humans are immune to rock slides because they don't get hit much by meteoroids. 

The best was to remain secure is to only install software from trusted sources (such as the repositories). When you install software, you are basically giving the program the keys to your computer and telling it to do whatever it wants. Also, know what you are typing. If someone tells you to type a certain command and you don't understand what it is, look it up first. It's better to be safe and slow than to be fast and sorry. :)

EDIT: Also, keep your computer updated. The security updates close any newly discovered security holes.

---

### Post by HermanAB on 2009-08-16
Howdy,

Just relax and enjoy your new system!

However, always use proper passwords for all user accounts, since bad passwords is the main attack vector on Linux.

---

### Post by Paqman on 2009-08-16
> **ovroniil said:**
> And I thought there is none!

If you're running a patched-up-to-date Linux system there are none that are a threat to you. Which is the same thing as none, in a way.

The biggest attack vector that we have to worry about is through social engineering. We're just as vulnerable to that as any other OS. Only our relative obscurity protects us from this at the moment, and education about safe practices is the best defence.

---

### Post by AlanR8 on 2009-08-16
Coming up for three years for me and Linux and I've NEVER used anti virus software. 

In that time I've had to rebuild XP machines more than once due to various infections.

---

### Post by colau on 2009-08-16
> **AlanR8 said:**
> Coming up for three years for me and Linux and I've NEVER used anti virus software. 

In that time I've had to rebuild XP machines more than once due to various infections.
I also did not use any anti-virus in linux.

---

### Post by mrbiggbrain on 2009-08-16
> **ovroniil said:**
> And I thought there is none!

Near all the linux viruses where made in labs as proof of concepts, and are fixed rather quickly in the programs and kernel issues they exsploit. plus unless you really are asking for it the programs cant do too much damage.

---

### Post by ovroniil on 2009-08-17
Well... may be Linux will be affected by virus when it will gain popularity as well as more users like Windows. I think the tiny amount Linux users are not the matter of interests for the Virus Creators!

---

### Post by Nburnes on 2009-08-17
> **ovroniil said:**
> Well... may be Linux will be affected by virus when it will gain popularity as well as more users like Windows. I think the tiny amount Linux users are not the matter of interests for the Virus Creators!
They very well could, but lets not think like that :)

---

### Post by Crunchy the Headcrab on 2009-08-17
I think the most important thing is to not become complacent.  Linux is a relatively safe operating system at this time, but that has more to do with it's design and the vigilance of it's users than the lack of interest of malware creators imo.  Just because Linux isn't big in the desktop market don't think that there will never be attempts to break it.  It's huge for servers and I think that it is only going to become more popular in that regard.

---

### Post by ovroniil on 2009-08-17
Can anyone please tell me in nutshell, for which features are responsible for lower virus rate in Linux? Is it only the usage of ROOT (password protected installation of any software) or are there more??

by the way thank you all for the nice discussion...:)

---

### Post by halitech on 2009-08-17
> **ovroniil said:**
> Can anyone please tell me in nutshell, for which features are responsible for lower virus rate in Linux? Is it only the usage of ROOT (password protected installation of any software) or are there more??

by the way thank you all for the nice discussion...:)

the basic system was designed from the ground up to be a multi-user network system so basically each layer provides protection from the other layers. There are ways of installing software that doesn't require root (or sudo) access but they are installed to your home folder so the most that could happen if you do install something (or it runs without your knowledge) is that your home folder gets wiped out. If that happens, you simply use recovery mode, add a new user and you are back in operation.

---

### Post by ovroniil on 2009-08-18
Thanks halitech, for the nice but quick and brief explanation!!

---

### Post by ovroniil on 2009-11-10
Sorry for resurrecting this post. 

Any body has any idea, is there any chance of getting infected by Windows viruses in Ubuntu through Wine? I mean Wine may run windows viruses in Ubuntu. Can it be a threat for Ubuntu? Can my files/folder get affected from that virus?

---

### Post by lukjad on 2009-11-10
Running a virus in wine would bother whatever wine can access, nothing more.

---

### Post by Zoot7 on 2009-11-10
Here's a read about running some of the more heard about viruses and malware in wine, a little old though.
[http://www.linux.com/archive/feature/42031](http://www.linux.com/archive/feature/42031)

---

### Post by kio_http on 2009-11-10
I think the way linux is built, it can't be attacked as easily as Windows. This is assuming people do not login and use root as a normal user.

Even a virusses come they won't be as numerous as they are in Windows now.

---

### Post by Sir Jasper on 2009-11-10
[SIZE="3"][FONT="Comic Sans MS"][COLOR="Blue"]Hi,

Security is a vitally wider issue than susceptibility to infections. 

[COLOR="Red"]Phishing fraud is increasing and it destroys many unwitting lives.[/COLOR]

Firefox 3.5 now avails armour against phishing as does OpenDNS.

[COLOR="Red"]Intrinsically, Linux has no better phishing protection than Windows?[/COLOR]

My regards

Perhaps some of our Forum experts will assist with their comments?
[/FONT][/COLOR][/SIZE]

---

### Post by Zoot7 on 2009-11-10
> **Sir Jasper said:**
> [SIZE="3"][FONT="Comic Sans MS"][COLOR="Red"]Phishing fraud is increasing and it destroys many unwitting lives.[/COLOR]

Firefox 3.5 now avails armour against phishing as does OpenDNS.

[COLOR="Red"]Intrinsically, Linux has no better phishing protection than Windows?
[/FONT][/COLOR][/SIZE]
Well your protection is as good as firefox's protection really which is the same as in Windows, so no you don't get better protection in Linux from phishing. I think phishing is a hard thing protect against, but it's easy to prevent if you know what to look for; such as always keep an eye on the domain name in your browser and be wary of links disguised with urls like tinyurl etc.

---

### Post by BT1 on 2009-11-10
Sound advice I have been given, if you need to download a program to do something, download from the official repositories as these are tested through and through. If you stick with the official repository, you're pretty much immune to everything out there.

When you stray, so does your protection.

---

