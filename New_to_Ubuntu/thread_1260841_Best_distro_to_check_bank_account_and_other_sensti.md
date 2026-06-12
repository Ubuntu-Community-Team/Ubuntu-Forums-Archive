---
title: "Best distro to check bank account and other senstive info"
date: 2009-09-08
forum: New to Ubuntu
---

### Post by GiantSpider on 2009-09-08
Hey I'm trying out ubuntu 9.04 but I'm still curious about other distros of Linux. I was thinking about having one of my family members use Ubuntu or another derivative. I will set up the computer for the user. The user has limited computer knowledge but doesn't use the computer for much other than surfing the net. The user is using windows xp right now. 

What the user does now:
1. Surfs net via Firefox 
   a. downloads utube videos and pictures.
   b. Checks bank account and email

2. Uses open Office and notepad. 

I also have the computer networked and use the hard drive as a backup for more important files some of which are senstive. 

 What I want from the distro is an easy to use, safe and secure enviorment, fast, and looks like and feels windows xp or windows 98. 
     What I want computer to do in order of importance:
  1. Easy to use, if the user doesn't use it she will revert to windows xp
  2. Familiar - looks like xp or win 98
  3. Secure, no hackers stealing bank account
  4. Speed
  5. Free (mandatory)

---

### Post by Paqman on 2009-09-08
> **GiantSpider said:**
> 
  1. Easy to use, if the user doesn't use it she will revert to windows xp


That depends on your user. I'd say Ubuntu is very easy to use, especially if you're looking at a user that spends 99% of their time in the browser. Once you've installed and got it set up with Flash, automated security updates, etc, then the system itself is point-and-click simple.

There's considerably less maintenance required for a Linux desktop than a Windows one, so there's no reason why you couldn't just set the machine up and leave them to it.

> 
  2. Familiar - looks like xp or win 98

There are themes available for this, the distro doesn't matter. Check out [gnome-look.org]("http://www.gnome-look.org/") or [KDE-look.org]("http://www.kde-look.org/") for plenty of free XP themes.

>   3. Secure, no hackers stealing bank account

Since you'd be using the browser to access it, this is less about the OS than it is about the browser. Use whatever has an up-to-date version of a browser with good security (eg:Firefox). If you use Ubuntu, wait till Karmic comes out next month to get the latest version of Firefox.

>   4. Speed

This is always a trade-off against features. The full-fat version of any modern distro (eg: Ubuntu, Fedora, Mandriva) will run plenty fast on any hardware from the last few years. If you're using older hardware you could use a lighter desktop environment such as XFCE or Openbox, but you will lose some functionality (they're probably about equivalent to a Win XP/2000 environment, roughly speaking)

> 
  5. Free (mandatory)

You're spoilt for choice there.

---

### Post by mapes12 on 2009-09-08
> **GiantSpider said:**
> Hey I'm trying out ubuntu 9.04 but I'm still curious about other distros of Linux. I was thinking about having one of my family members use Ubuntu or another derivative. I will set up the computer for the user. The user has limited computer knowledge but doesn't use the computer for much other than surfing the net. The user is using windows xp right now. 

What the user does now:
1. Surfs net via Firefox 
   a. downloads utube videos and pictures.
   b. Checks bank account and email

2. Uses open Office and notepad. 

I also have the computer networked and use the hard drive as a backup for more important files some of which are senstive. 

 What I want from the distro is an easy to use, safe and secure enviorment, fast, and looks like and feels windows xp or windows 98. 
     What I want computer to do in order of importance:
  1. Easy to use, if the user doesn't use it she will revert to windows xp
  2. Familiar - looks like xp or win 98
  3. Secure, no hackers stealing bank account
  4. Speed
  5. Free (mandatory)I would install Ubu 9.04 then tweak with MS themes like this one: [http://www.gnome-look.org/content/show.php/XPLuna?content=83797](http://www.gnome-look.org/content/show.php/XPLuna?content=83797)

I use Ubu without any tweaks and have no security issues for online banking / shopping etc. 

With regard to sensitive data you can use encryption (right click folder or file) [http://blogs.tech-recipes.com/incursor/2008/05/04/simple-encryption-in-ubuntu-804/](http://blogs.tech-recipes.com/incursor/2008/05/04/simple-encryption-in-ubuntu-804/) and / or set permissions (right click>Properties>Permissions tab)to keep you data safe.

---

### Post by Bucky Ball on 2009-09-08
If they can use firefox, that is exactly the same no matter what distro you're using.

---

### Post by MelDJ on 2009-09-08
this might be long but helpful
[http://en.wikipedia.org/wiki/List_of_Linux_distributions](http://en.wikipedia.org/wiki/List_of_Linux_distributions)

---

### Post by GiantSpider on 2009-09-08
hmmmm ok didn't realize the browser mattered so much. So will Ubuntu be safer than xp? In xp the user uses a free anti-virus, anti-spyware and firewall. The other thing is the user uses the latest version of firefox 2. Firefox 2 is used because it supports looks familiar to look like internet explorer 6.

---

### Post by piperdown10 on 2009-09-08
The great thing about Ubuntu, or any distro for that matter, is the safety. To my knowledge, there are no known viruses that effect Linux. However, Linux can still be a carrier for Microsoft targeting malware. There is an anti-virus available for Ubuntu and it also comes with a firewall application pre-installed, you'd just need to configure it.

---

### Post by MelDJ on 2009-09-08
> **GiantSpider said:**
> hmmmm ok didn't realize the browser mattered so much. So will Ubuntu be safer than xp? In xp the user uses a free anti-virus, anti-spyware and firewall. The other thing is the user uses the latest version of firefox 2. Firefox 2 is used because it supports looks familiar to look like internet explorer 6.

ubuntu does not have many viruses. and almost all of them are lab experiments to prove it is possible to exploit linux. They are already patched so no need to worry. just use a good password and you are safe

---

### Post by GiantSpider on 2009-09-08
Ok cool, what about if I dual boot? Should I transfer all the data from the xp partition to the Ubuntu partition and than put the files in an encrypted folder? In other words will the xp part of my system be a vunerablity if the user is using Ubuntu?

---

### Post by MelDJ on 2009-09-08
no. it wont be vulnerable unless you open a file containing a virus in it

---

### Post by egalvan on 2009-09-08
> **GiantSpider said:**
> 
  3. Secure, no hackers stealing bank account

Others have given some good advice on the other points...

but I want to add that most "hackers stealing bank accounts" 
usually do so by cracking the bank's servers, 
or they use "social cracking", 
which consists of tricking folks into either revealing their sensitive information (passwords, for example) 
or tricked into installing or running malware.
(as happened to a friend of mine)

Notice that these are totally INDEPENDENT of what software or Operating System YOU are running...

The first you have no control over (other than complaining loudly when your account is hacked).

The second is dependent on your surfing habits, and on being careful with sensitive information.


Still, *nix has a better security model than XP, and FAR better than W98.

And IE6 and Firefox 2 have security 'issues' that suggest STRONGLY updating to a more capable version.

And keeping your software up-to-date with security patches is VERY important...
 and this is easy to do with most *nix distros.

---

### Post by Paqman on 2009-09-08
> **egalvan said:**
> 
Notice that these are totally INDEPENDENT of what software or Operating System YOU are running...


+1

The biggest risk in online banking is undoubtedly phishing. Linux users are just as vulnerable to this as Windows users.

However, we are much less likely to fall prey to some of the other threats, such as keyloggers stealing our passwords. On balance we do enjoy a much better security situation.

---

### Post by Bucky Ball on 2009-09-08
[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

That should just about cover it. If you are using Windows to do your banking already I don't think you should be worried about Ubuntu, you should be worried about banking in Windows and make the change immediately!

Here is some more info:

[http://www.desktoplinux.com/articles/AT5785842995.html](http://www.desktoplinux.com/articles/AT5785842995.html)

[http://ubuntuforums.org/showthread.php?p=7911326](http://ubuntuforums.org/showthread.php?p=7911326)

Lots of servers in big organisations run Unix which is where Linux springs from and thus Ubuntu. I have had systems admin friends tell me the only insecure thing about a Unix server is the Windows boxes hanging off it!

MelDJ: Find me a file with a Linux virus I can download.

I am by no means saying Linux is impenetrable but there's been plenty try; even for money. I'll look for the article later.

---

### Post by MelDJ on 2009-09-08
just being right on this and not saying that linux does not have viruses:lolflag:

---

### Post by Bucky Ball on 2009-09-08
> **MelDJ said:**
> just being right on this and not saying that linux does not have viruses:lolflag:

Agreed. But extremely tricky to get in if you have your machine set up right (and it pretty much is by default in Ubuntu). Here's some more info.

[http://librenix.com/?inode=21](http://librenix.com/?inode=21)

---

### Post by winotree on 2009-09-08
[Answer removed --not relevant to OP question-topic]

---

### Post by GiantSpider on 2009-09-08
I was checking out some of the threads with a focus on spyware since that is what bothers my windows machines most. At least two said to use Safe History but that is only for firefox 2. I'm using firefox 3 on this computer and eventually will upgrade to firefox 3 on the xp computer as soon as I can make it look like ie6. How important is safe history for firefox 3 and is there a similar add-on that works in firefox 3?

---

### Post by Bucky Ball on 2009-09-09
Spyware? Never been an issue for me in Linux. I never hit the 'ok' button when a dodgy window comes up and tells me the machine could be infected though (if you do maybe don't!). If I did hit that button I can 99.9999% guarantee you it would be a Windows bug I would be letting in which Linux would not recognise anyway. If I were on a network with a Windows machine and passed the file over to it on the other hand ...

As I said before, if you are using Windows, the last thing you should be worried about in Ubuntu is security. It is bulletproof in comparison. (But again, not impenetrable if someone was cluey enough and could be bothered ... there's bigger brats to fry than the Linux community).

---

### Post by Lampi on 2009-09-09
German IT magazine C'T (Computer Technology) assembled a live cd for e-banking purposes - I didn't find the article in English - sorry for that, 

It is ubuntu based but the kernel is altered to enhance security.

[http://www.heise.de/ct/Sicheres-Online-Banking-mit-Bankix--/projekte/132668](http://www.heise.de/ct/Sicheres-Online-Banking-mit-Bankix--/projekte/132668)

---

### Post by shae on 2009-09-09
I have two comments to make.

One: You should NOT make the system seem like XP or 2000 because Linux is not Windows.  If you make it just sortof look like it, it is doomed to fail.  Let her see the new interface because it is very similar, if not better to Windows' interface.  It is definitely just as intuitive. If you just make it look like XP or 2000, it will just frustrate the user when she finds inconsistencies or is not able to do things the "old way".

Two: Phishing is going to be the main problem.  The best solution is to make sure the user understands Phishing and is on the lookout for it, to use a plugin such as SiteAdvisor or WebOfTrust and make sure the user understands how to use it, and to configure the computer to use OpenDNS which tries to block Phishing sites.

Ultimately the safety of online banking will be up to the user, just Linux is less vulnerable to Keyloggers, Trojans, Viruses, Spyware, etc.

---

