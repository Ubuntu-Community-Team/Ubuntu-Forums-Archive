---
title: "installing/configuring apps: ubuntu or Windows"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by ppb7 on 2009-09-27
Here's another little snag i've come across that plays against Linux.
I wanted to install an antivirus, so installed ClamAV which is included in the distro. but how should i go about configuring it?
Then I thought I'd try to work the web server. But, how should I go about it? Yes, I agree that overall ubuntu is my presferred OS, but it would be very difficult to convince other people to start using it instead of Windows which they think (rightly?) is much more (novice) user-friendly.

Enough of my abstract remarks. more concretely, with ClamAV, so far I haven't been able to check if anything has been set to my satisfaction. Is there a graphical interface? If not, that would deter lots of users from adopting it. I am a newbie but interested in anything computer-related. However, I will never be able to convince the other members of my family to set aside XP or Vista as a secondary OS if I can't show them that I can with confidence perform all the tasks that I can with Windows. More crucially than anything else, OpenOffice is not, as far as I can see, compatible enough with Office.
And even for myself there are problems. As I said, I like a bit of a challenge and I would like, for development purposes, to have access to a web server. However, sometimes I simply haven't got the time to search out everything by myself on the net. With XP I could sort of figure out  a few things by playing around with files. But here, there's nothing to get me started as most files are either incredibly long to read or incredibly complicated to understand.
Well, that means that, although ubuntu is probably 5 times as fast as XP as far as performance is concerned, to do some web development I will have to go back to using IIS. Unless you can suggest an alternative...:confused:

---

### Post by mikeyphi on 2009-09-27
Read more about ClamAV here:
[https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)

---

### Post by peculiar penguin on 2009-09-27
> I wanted to install an antivirus, so installed ClamAV which is included in the distro. but how should i go about configuring it?Synaptic lists a "clamav-docs" package which I would expect to contain documentation on things like that.

> Then I thought I'd try to work the web server. But, how should I go about it?Uh, which one?
But here's a general hint: It probably isn't completely undocumented.

> Enough of my abstract remarks. more concretely, with ClamAV, so far I haven't been able to check if anything has been set to my satisfaction. Is there a graphical interface?A glance at Synaptic shows ClamTk, klamAV,... don't know if these are any good, sorry.

> More crucially than anything else, OpenOffice is not, as far as I can see, compatible enough with Office.This may be true for complex documents, but isn't really a Linux issue since OOo's windows version has the same issues.

> Yes, I agree that overall ubuntu is my presferred OS, but it would be very difficult to convince other people to start using it instead of Windows which they think (rightly?) is much more (novice) user-friendly.> If not, that would deter lots of users from adopting it. I am a newbie but interested in anything computer-related. However, I will never be able to convince the other members of my family to set aside XP or Vista as a secondary OS if I can't show them that I can with confidence perform all the tasks that I can with Windows.May I ask why you are so concerned with "converting" other people when it doesn't sound like you've done your homework on this whole Linux thing yet?

> And even for myself there are problems. As I said, I like a bit of a challenge and I would like, for development purposes, to have access to a web server. However, sometimes I simply haven't got the time to search out everything by myself on the net. With XP I could sort of figure out a few things by playing around with files. But here, there's nothing to get me started as most files are either incredibly long to read or incredibly complicated to understand.There usually is  documentation (be it man pages, text or html in /usr/share/doc, websites,...), the internet is clogged with "How-to"s and guides and what-not, so I'm not sure what to tell you here. If you expect to figure out things entirely by clicking around in a GUI, Linux may not be ready for you yet.

---

### Post by bacardiandwatermelon on 2009-09-27
Rather than Clamav you could try kaspersky? I think this is the link... [http://www.kaspersky.co.uk/productupdates?chapter=146274389](http://www.kaspersky.co.uk/productupdates?chapter=146274389)

---

### Post by credobyte on 2009-09-27
Forget about Clam - get Avast ( CLI & GUI ).

---

### Post by mcduck on 2009-09-27
First, you don't really need any antivirus application in Ubuntu. ClamAV is mainly targeted for people who run mail servers and such, and all it does it scans for Windows viruses to help protect Windows systems on larger networks. So it definitely isn't targeted for home users.

For the web server, just install Ubuntu's own LAMP stack and you'll be fine. You can do that by opening Synaptic Package Manager (System/Administration/Synaptic Package Manager) and selecting Edit/Mark Packages by Task. Then mark the "LAMP server", and click "Apply" to install it.

Alternatively you can just open a terminal and run "sudo tasksel install lamp-server".

You can read more about managing Ubuntu's LAMP server here: [https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

What comes to user friendliness, you are clearly forgetting that once you were a novice with Windows as well. You had to learn what you need to run, where to click, how to download programs from the Internet etc.. That's not easy either, actually it requires quite a lot more knowledge than just opening Applications->Add/Remove and installing whatever you want.. :D

(I also must add that complaining about Ubuntu not being user friendly and threatening to move back to Windows isn't really the best way to get help in these forums.. ;) Also finding info about web server on Ubuntu takes less than two seconds, simple google search for "ubuntu web server" and opening the first link would have done the job.)

---

### Post by Pbethe on 2009-09-27
> **ppb7 said:**
> I wanted to install an antivirus, so installed ClamAV which is included in the distro. but how should i go about configuring it?
Then I thought I'd try to work the web server. But, how should I go about it? Yes, I agree that overall ubuntu is my presferred OS, but it would be very difficult to convince other people to start using it instead of Windows which they think (rightly?) is much more (novice) user-friendly.

Enough of my abstract remarks. more concretely, with ClamAV, so far I haven't been able to check if anything has been set to my satisfaction. Is there a graphical interface? If not, that would deter lots of users from adopting it. I am a newbie but interested in anything computer-related. However, I will never be able to convince the other members of my family to set aside XP or Vista as a secondary OS if I can't show them that I can with confidence perform all the tasks that I can with Windows. More crucially than anything else, OpenOffice is not, as far as I can see, compatible enough with Office.
And even for myself there are problems. As I said, I like a bit of a challenge and I would like, for development purposes, to have access to a web server. However, sometimes I simply haven't got the time to search out everything by myself on the net. With XP I could sort of figure out  a few things by playing around with files. But here, there's nothing to get me started as most files are either incredibly long to read or incredibly complicated to understand.
Well, that means that, although ubuntu is probably 5 times as fast as XP as far as performance is concerned, to do some web development I will have to go back to using IIS. Unless you can suggest an alternative...:confused:

ppb, to convince your family to get rid of Windows, you can tell them that linux users hardy ever see a virus that affects them. If one does start circulating, I am sure that clam will add it to its signature file. 
What sorts of problems are you having with OpenOffice?  If you end up dual booting because of them, you can still scan your Windows partitions for virus while running linux.  That way, you can catch viruses that hide themselves from virus scanners.

---

### Post by ppb7 on 2009-10-01
Right, the other day when i posted the thread was an off-day for me. So what I am going to do, as things have turned slightly for the better, is answer most of your questions while keeping in mind the issues that i raised
ABOUT CLAMAV
[quote=mikeyphi]Read more about ClamAV here:
[https://help.ubuntu.com/community/ClamAV](https://help.ubuntu.com/community/ClamAV)[/quote]
Thanks to mikeyphi for pointing me to that page. this should indeed allow me to get started.
[quote=mcduck]First, you don't really need any antivirus application in Ubuntu[/quote]yes you do, and for the very reason that there are so many Windows users + a move towards linux, hence a greater interest in making things difficult for linux users.

OTHER QUESTIONS
[quote=peculiar penguin]
There usually is documentation[/quote] which is correct but just at the moment, i haven't got time to go through docs, so thought i'd take advantage of your huge collective knowledge so you could guide me more quickly
[quote=peculiar penguin] May I ask why you are so concerned with "converting" other people when it doesn't sound like you've done your homework on this whole Linux thing yet?[/quote]
On top of that we've got an old computer with a pathetically slow version of XP (i think service pack 2 was wrongly installed), which explains why i'm so keen on exploring all compatibility avenues. people can then see how much faster jaunty is AND that it does at least as much as XP. At the moment refuses to move away from XP because there is not total compatibility between MS Office and OpenOffice.
[quote=mcduck](I also must add that complaining about Ubuntu not being user friendly and threatening to move back to Windows isn't really the best way to get help in these forums[/quote]i am really sorry if i gave that impression. I believe ubuntu is fantastic and i merely wish to make sure as many potential problems as possible are ironed out so i can introduce it as THE alternative to MS

[quote=pbethe]If you end up dual booting because of them, you can still scan your Windows partitions for virus while running linux. That way, you can catch viruses that hide themselves from virus scanners.[/quote]Thanks for the tip:!:

WEB SERVER
[quote=mcduck]You can read more about managing Ubuntu's LAMP server here: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)[/quote] Thanks for that! BTW i read that Hiawatha got a good review in linux magazine as an alternative to apache. What's your opicion?

OPENOFFICE
I will start a new thread elsewhere once i 've got my act together and tested exactly what i need to show.

---

### Post by ppb7 on 2009-10-02
As was said, I am still new at learning how to use linux, so i decided to go for avast antivirus since it's got a GUI and. lo and behold, the scan that's taking place at this very minute has already found 3 infected files from the software that runs an IE-like browser (I hate IE but have to use it for my job). So an anti-virus is necessary, especially if dual-booting still enables you to access data from the Windows partition.

---

### Post by Paqman on 2009-10-02
> **ppb7 said:**
> 
yes you do, and for the very reason that there are so many Windows users + a move towards linux, hence a greater interest in making things difficult for linux users.


Actually, no you don't. ClamAV et al don't protect you from Linux malware, they protect you from Windows malware. Since that isn't likely to be a threat on your Linux system you aren't any better protected while running ClamAV than if you weren't.

Linux malware threats to a desktop system aren't unheard of, but all known threats are patched, so there isn't anything that can hurt you.

If Linux gains more traction on the desktop that may change, as you mention, but for now we're still in a very good security position. You can install antivirus software if it gives you peace of mind, but it isn't necessary.

Have a read of [this thread]("http://ubuntuforums.org/showthread.php?t=510812") for an interesting discussion of desktop Linux security.

---

### Post by t0p on 2009-10-02
> **ppb7 said:**
> As was said, I am still new at learning how to use linux, so i decided to go for avast antivirus since it's got a GUI and. lo and behold, the scan that's taking place at this very minute has already found 3 infected files from the software that runs an IE-like browser (I hate IE but have to use it for my job). So an anti-virus is necessary, especially if dual-booting still enables you to access data from the Windows partition.

Windows viruses cannot affect  your Ubuntu OS.  Period.  And there are virtually no Linux viruses "in the wild". So a Linux web browser cannot get "infected".

What is this "IE-like" browser anyway?

---

### Post by 3rdalbum on 2009-10-02
ClamAV classes some fairly innocent Javascripts (that ship with Dreamweaver!) as malware, so be careful with what you delete.

---

### Post by Paddy Landau on 2009-10-02
> **ppb7 said:**
> At the moment refuses to move away from XP because there is not total compatibility between MS Office and OpenOffice.
Well, yes, of course they're not fully compatible. However, MS has agreed (reluctantly) to go with the open standards, and so compatibility should improve over the next few years, with luck.

I frequently receive Word documents, and thus far I've had no problem opening them with OpenOffice. Likewise, I send documents and spreadsheets to Windows users; I save them to .doc and .xls, and they have no problems reading them.

But, if your user absolutely requires Windows Office to do his work, I believe that Office works great under Linux (using Wine). I receive occasional Publisher files. I got fed up with the excessively slow response times under Windows, so I uninstalled it from Windows and reinstalled it in Wine on Ubuntu. It works ten times as fast and doesn't crash as often.

It's worth a try.

BTW, if you do end up using Wine, I strongly recommend [PlayOnLinux]("http://www.playonlinux.com/"), which makes using Wine a doddle.

---

### Post by Paqman on 2009-10-02
> **3rdalbum said:**
> ClamAV classes some fairly innocent Javascripts (that ship with Dreamweaver!) as malware, so be careful with what you delete.

From what i've seen it's also a pretty poor performer at spotting real malware. If you need to scan for Windows nasties on a Linux box you'd be far better off with something like Avast or Kaspersky.

---

### Post by ppb7 on 2009-10-02
> **t0p said:**
> What is this "IE-like" browser anyway?
go to [http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)
------------------------------------------
> **3rdalbum]ClamAV classes some fairly innocent Javascripts (that ship with Dreamweaver!) as malware, so be careful with what you delete.[/QUOTE]
The files have just been quarantined fo the time being. This is what Avast said the files were infected with: HTML:iframe-inf (two files) said:**
> . Do you know about these?
-------------------------------------------
[QUOTE=Paddy Landau]But, if your user absolutely requires Windows Office to do his work, I believe that Office works great under Linux (using Wine).
Where can I learn more about that
------------------------------------------
[QUOTE=Paddy Landau]I got fed up with the excessively slow response times under Windows, so I uninstalled it from Windows and reinstalled it in Wine on Ubuntu[/QUOTE]
Is uninstalling the software from the Windows partition necessary, or can you keep it and run Office under wine as well. And are we talking about all versions or just 2007?

---

### Post by [S|G] on 2009-10-02
> **ppb7 said:**
> 
The files have just been quarantined fo the time being. This is what Avast said the files were infected with: HTML:iframe-inf (two files); HTML:RedirME-inf [Trj]. Do you know about these?

Hi there!

While there are a few viruses that target linux they're not nearly as dangerous as windows viruses - they're more like proof-of-concept and they usually show that linux is a lot more secure than Windows. In order to avoid extending this discussion, you might want to read this (and you'd probably should):

[http://librenix.com/?inode=21](http://librenix.com/?inode=21)

Cheers!

---

### Post by Paddy Landau on 2009-10-02
> **ppb7 said:**
> Where can I learn more about that
[Wine]("http://wiki.winehq.org/") is a program that allows you to run Windows programs on Linux. It is far from perfect; some programs run perfectly, some run with minor annoyances, and others don't run at all.

Using Wine is a bit tricky, which is why I use [PlayOnLinux]("http://www.playonlinux.com/"). PlayOnLinux is a front-end that handles all the tricky bits of Wine for you. It takes a little getting used to (what program doesn't?), but once you get the hang of it, it's dead easy to install and uninstall Windows programs.

PlayOnLinux also isolates the installed Windows programs from each other, so if one screws up, you just uninstall and install it again. No problem.

You'll also find that the speed with which it installs and, especially, uninstalls, surprising after coming from a Windows environment.

Install Wine, if not already installed, from the repositories (System > Administration > Synaptic Package Manager).

To install PlayOnLinux, go to its download page, choose Ubuntu, and follow the instructions carefully.

> **ppb7 said:**
> Is uninstalling the software from the Windows partition necessary, or can you keep it and run Office under wine as well.
That depends on your license. Mine allows me to install it in only one place (as I understand it), which is why I uninstalled from Windows first.

> **ppb7 said:**
> And are we talking about all versions or just 2007?
Sorry, I don't know. There are databases of what runs, but you'll have to Google for them. There are also third-party applications instead of Wine that claim to work better (e.g. [CodeWeavers]("http://www.codeweavers.com/products/cxlinux/") claims to run 2007), but you'll have to pay for them; check their databases, too.

Your other alternatives are to dual-boot Windows (a pain, I know, as Windows takes so long to boot), or to load Windows in a virtual machine (provided that your machine is powerful enough).

---

### Post by Paqman on 2009-10-03
> **ppb7 said:**
> go to [http://www.tatanka.com.br/ies4linux/page/Main_Page](http://www.tatanka.com.br/ies4linux/page/Main_Page)


IEs4Linux is pretty much just for web designers who need to do browser checks. There's no way i'd use it to surf the net, it's based on obsolete versions of IE and therefore just not secure.

> 
The files have just been quarantined fo the time being. This is what Avast said the files were infected with: HTML:iframe-inf (two files); HTML:RedirME-inf [Trj]. Do you know about these?

It's a Windows trojan that popped up a few months ago. Only Avast and Avira have it in their databases (which might just mean that others list it under a different name). Highly unlikely to represent any threat to a Linux system.

---

