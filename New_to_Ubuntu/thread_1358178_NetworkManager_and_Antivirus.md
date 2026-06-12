---
title: "NetworkManager and Antivirus?"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by Level1orc on 2009-12-18
Hi all, just installed Ubuntu alongside Vista, I'm looking forward to becoming involved in the community.

I attempted to connect to my wireless network, but NetworkManager was not showing up in the system notification bar.  Could someone please tell me where it might be?  This is probably a pretty simple question, but I've never used Ubuntu before, and I'd appreciate someone telling me how to bring it up.

Also, I'd like to migrate my antivirus software to Ubuntu.  Is there any easy way to do that?

Thanks everyone.  Again, nice to meet you all.

---

### Post by jamieleshaw on 2009-12-18
Network Connections can be found at System -> Preferences -> Network Connections.

Also it is unlikely you will need an anti-virus but there is a few including [http://free.avg.com/ww-en/download?prd=afl](http://free.avg.com/ww-en/download?prd=afl)
and Clam AV and more
;)

---

### Post by bkmfs on 2009-12-18
Anti-virus?  ...um, that would be a microsoft thing.  A lot of people move to Linux so that they don't need anti-virus software.   

Wireless cards.  Tell us what kind of computer you're on and/or the type of wireless card if you would.

p.s. welcome to Linux and don't let anybody tell you "Google it".  This ain't no treasure hunt.

;)

---

### Post by 3rdalbum on 2009-12-18
If you don't see the Network Manager, there could be one of two things wrong. Either:

1. nm-applet is not running - press Alt-F2 and type "nm-applet" and run it.

or

2. You don't have a Notification Area on your panel. Right-click the panel and choose Add To Panel... and then select Notification Area.

As for anti-virus, you've already had two good answers... anti-virus programs on Linux will only detect Windows viruses. Because there are no Linux viruses, and not likely to be any, any time soon. Of course, because Linux is a completely different operating system to Windows, it won't run Windows programs - so it neither runs your existing Windows anti-virus program, nor does it run Windows viruses anyway.

---

### Post by hovzio on 2009-12-19
Well I must disagree to a certain point. You can write viri for linux! (It hasnt proven profitable..)  There are rootkits floating around and to say there are no virus for linux is for the most part inaccurate. It boils down to the user; there are bad programs out there and if the user is smart enough to install it...(or tricked into it) Linux users tend to be more aware, this does not mean its not impossible to write a virus for linux.. The next thing is web applications, java, flash and co.. If firefox has a glitch in their code this could be a threat.. I do believe linux systems tend to be quite a bit safer (package manager, repos etc..) than windows but its important to realize that security is always an issue. check out rkhunter - searches for linux specific rootkits etc- lets you know when the md5sums of binaries have changed, keeping that in mind, its a cool program. This definatley takes place, 2007 the redhat repos had been infiltrated and their version of openssh-server had been manipulated...one could call that a virus..

If you are running a server of any kind it is important to be aware.. A server must be properly secured.. to say that linux has no viri is probably not the way to go...

---

### Post by 3rdalbum on 2009-12-19
There aren't any Linux viruses today. There are a couple of trojans and some rootkits, but I highly doubt that any Linux-based "anti-virus" software will pick up any of them.

Isolated cracker attacks are not viruses. If they are very good, they might be rootkits - but nothing that an "anti-virus" program will pick up.

The OP does not appear to be running a server, so advice about rootkits and securing services are irrelevant to this thread.

---

### Post by bkmfs on 2009-12-19
Surely there must be Linux viruses out there somewhere but you definitely would not catch one the same way a Vista would catch one through a 'WinSneeze'.  Programs like tripwire (

sudo apt get tripwire

) help protect against certain trojans but when you install tripwire, I believe you have to register it or something (you're gonna want to research this).  

I don't think you can get a virus just by opening grandma's email or logging on a 'questionable' site with your Linux machine though.  If someone can post why it is so easy to get a virus in windows in this way, that would be great.  That is something that just baffles the "F" out of me.

---

### Post by sliketymo on 2009-12-19
> **bkmfs said:**
> Surely there must be Linux viruses out there somewhere but you definitely would not catch one the same way a Vista would catch one through a 'WinSneeze'.  Programs like tripwire (

sudo apt get tripwire

) help protect against certain trojans but when you install tripwire, I believe you have to register it or something (you're gonna want to research this).  

I don't think you can get a virus just by opening grandma's email or logging on a 'questionable' site with your Linux machine though.  If someone can post why it is so easy to get a virus in windows in this way, that would be great.  That is something that just baffles the "F" out of me.


exe. , .dll ,active-x.

---

### Post by earthpigg on 2009-12-19
> If someone can post why it is so easy to get a virus in windows in this way, that would be great. That is something that just baffles the "F" out of me.

-once a security patch for FF/IE/Safari/etc comes out, that announces to the world exactly what the vulnerability is. it isn't hard from there to infer how to apply it. people that don't immediately update/upgrade/apply-patch are then even more vulnerable - FF/IE/Safari themselves ***announced*** the vulnerability to the bad guys! so, if you want to know how to exploit users, you need only read the official announcements made by the various web browser's developers... and assume 9X% of users will not update/upgrade in the near future. consider how many folks out there have the same IE 6 install from 5 years ago, with no updates. often these vulnerabilities are centered around the stuff that makes web sites pretty and snazzy. the same stuff that makes facebook and youtube snazzy can also let bad guys in, if your browser isn't patched.

-also consider that folks not wishing to deal with "Microsoft Genuine Advantage" malware will not be receiving security patches to IE.

-porn and 'warez' and other stuff that relies on social engineering. user clicks to play a video. and then: "Do you want to run flashinstaller.exe?" or "do you want to download hotgirltakesit.exe?" --- why, yes, of course the user does. his judgement is impared because of what his left hand is doing while his right hand is on the mouse.

-not every website that lets advertisers put up flashy advertisements throughly vettes the ads. using an unpatched and out of date web browser, you can indeed get malware and crap just by signing onto facebook (via the ads and clicking on the 'special offers').

-if you want to use the modern internet and be safe, you need to be using modern software. 

-you shouldn't look at porn using out-of-date software any more than you should have a one night stand using out-of-date birth control methods such as the "pull out method". noscript. adblock plus. ***worth*** the hassle.

-Linux is ***nearly*** as vulnerable to browser-based attacks as any other... a bit more secure because, at some point, the user will need to be engineered into giving the malware root privileges (only required if the malware is to propagate itself throughout the system). many ways of doing this - easy example would be to have the malware change a menu item in system->administration (this can be done as user, does not require root) to run the malware ***in addition*** to running the intended program... you ***expect*** to be asked for your password when you run gparted, so you won't notice that a new daemon starts running in the background as root shortly after you start gparted. I would not consider any computer running unsupported releases of Ubuntu as secure. ie: Firefox in Ubuntu 6.06 LTS... just as vulnerable as IE6. (if anyone has bothered writing malware targeting that platform is another question entirely)

---

### Post by bkmfs on 2009-12-19
I don't know.  It just seems that if you download a .pdf file with a '_non-updated_' Linux machine, you still wont have any problems.  If you download a .pdf file with an unprotected XP machine, you can catch 'WinHepatitis'.  Why is that?

By the way Level1orc, how's that NetworkManager coming along?

---

### Post by earthpigg on 2009-12-19
> Why is that?

are the windows machines ***still*** vulnerable if they are using the latest version of Adobe Acrobat Reader on a still-supported-by-security-releases version of MS Windows, or [a different .pdf reader]("http://en.wikipedia.org/wiki/Sumatra_PDF") on that same windows install? its an honest question, i honestly have no idea. Adobe Acrobat (and other .pdf viewers) vulnerabilities need to be seperated from any vulnerabilities inherent in the international and open .pdf standard.


also - has anyone even ***tried*** spreading malware to gnu/linux via .pdf? 

its [a huge pain]("http://searchwindowsserver.techtarget.com/tip/0,289483,sid68_gci1251819,00.html") in the rear to even do basic file management in windows with something similar to our beloved 'sudo' model of limited, temporary, and program specific priveladge escelation. there is an outstanding article somewhere out there (cant find it now) that explains how to set up xp or vista with a security model similar to the ubuntu one.


and yeah, you still with us Level1orc? i know we went off on a tangent -- but that just means more people will be paying attention if you post back :D

---

### Post by 3rdalbum on 2009-12-19
> **bkmfs said:**
> I don't know.  It just seems that if you download a .pdf file with a '_non-updated_' Linux machine, you still wont have any problems.  If you download a .pdf file with an unprotected XP machine, you can catch 'WinHepatitis'.  Why is that?



Linux programs are written with more of a focus on security, Ubuntu randomises the location of libraries into memory and won't execute data that is marked as 'data only' (hardens system against buffer overflow attack) and Ubuntu also restricts what Evince can do through AppArmour.

---

