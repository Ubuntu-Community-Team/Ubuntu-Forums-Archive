---
title: "Virus in an XP VM?"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by jotto! on 2009-11-12
One of the reasons for swapping to ubuntu was the lack, or so it seems, of virus attacks and the security of linux based machines.

2 questions, how secure is a standard out of the box install of ubuntu and does it need any virus and internet security?

And, is a VM running XP as a guest vulnerable to virus attacks like a normal PC or because its virtual, is it not affected?

TIA.

---

### Post by theozzlives on 2009-11-12
> **jotto! said:**
> One of the reasons for swapping to ubuntu was the lack, or so it seems, of virus attacks and the security of linux based machines.

2 questions, how secure is a standard out of the box install of ubuntu and does it need any virus and internet security?

And, is a VM running XP as a guest vulnerable to virus attacks like a normal PC or because its virtual, is it not affected?

TIA.

A virus can attack a Windows VM, but it's contained in the virtual HD. You still need to play the Anti-Malware charade with Windows. I make a copy of my HD file and update it often. That way if my Windows 7 gets hosed, I got by backup file to fall back on. I just delete the messed up one.

---

### Post by kio_http on 2009-11-12
> **jotto! said:**
> One of the reasons for swapping to ubuntu was the lack, or so it seems, of virus attacks and the security of linux based machines.

2 questions, how secure is a standard out of the box install of ubuntu and does it need any virus and internet security?

And, is a VM running XP as a guest vulnerable to virus attacks like a normal PC or because its virtual, is it not affected?

TIA.
1.
No virus protection software needed. Although you may like a firewall for securing against remote attacks (not PC crash)

2.
No only the XP system in the VM would fail not Ubuntu. The VM works like a separate computer.

---

### Post by Bunnybugs on 2009-11-12
Well, Ubuntu isn't fragile with virus, but XP in a VM can be catched by them, it won't damage your Ubuntu system, but it can damage your VMachine...

Trojans for example can't really hurt you, and the VM uses a virtual motherboard to run that system... I wish you luck with it... it's pretty safe!

---

### Post by HarrisonNapper on 2009-11-12
> **jotto! said:**
> One of the reasons for swapping to ubuntu was the lack, or so it seems, of virus attacks and the security of linux based machines.

2 questions, how secure is a standard out of the box install of ubuntu and does it need any virus and internet security?

And, is a VM running XP as a guest vulnerable to virus attacks like a normal PC or because its virtual, is it not affected?

TIA.

I should add something to what others have said. Make sure you are accessing websites with sensitive personal information through Ubuntu, if you can. Security in Firefox and in Ubuntu are better than IE on Windows. Really, I try and do as little as possible on my VM; it's there in case I really need Windows for something. Apart from netflix, I've not found anything that really requires Windows.

---

### Post by jotto! on 2009-11-12
Thanks for the replies. With Windows Im used to having to run many different programs to help protect the system but as with all stuff, its only good after a new attack has been protected against. 

Im just trying a VM to see if I can run some windows applications that I have although I know there are many equivalents!

With regards to a firewall, to most companies offer a linux based one? What do you guys use or recommend?

---

### Post by Bunnybugs on 2009-11-12
> **HarrisonNapper said:**
> I should add something to what others have said. Make sure you are accessing websites with sensitive personal information through Ubuntu, if you can. Security in Firefox and in Ubuntu are better than IE on Windows. Really, I try and do as little as possible on my VM; it's there in case I really need Windows for something. Apart from netflix, I've not found anything that really requires Windows.
Only using the ubuntu to run a VM is just stupid:S

Or is it just me that draws that kind of conclusion?:D

---

### Post by HarrisonNapper on 2009-11-13
> **Bunnybugs said:**
> Only using the ubuntu to run a VM is just stupid:S

Or is it just me that draws that kind of conclusion?:D

You misunderstood me. I use the VM only when necessary. I use Ubuntu for basically everything but netflix. I was stressing that one should avoid using a VM particularly when accessing sensitive information online.

Jotto, there are lots of firewalls available in linux. Though it wouldn't be quite as accurate to say "which company" because of the unique market relationships in FOSS.

Probably a more common firewall is Firestarter, but you can search Synaptic for "firewall" and see what comes up :D

---

### Post by J-Buntu on 2009-11-13
I use VirtualBox to run XP, as previous posts have already answered the question about the vulnerability of windows, i will just suggest an anti-virus that i use on XP in Virtualbox - Avast Home Edition. It's free and as lightweight as they come for a highly secure AV. If you really wanted to install a firewall too, i would recommend Comodo, it's compatible with Avast. The windows software will protect you if you are surfing online in windows and anything will be contained inside the VM anyway. Both can be found free on cnet downloads BTW.

---

### Post by bodhi.zazen on 2009-11-13
> **jotto! said:**
> One of the reasons for swapping to ubuntu was the lack, or so it seems, of virus attacks and the security of linux based machines.

2 questions, how secure is a standard out of the box install of ubuntu and does it need any virus and internet security?

I suggest you start with : [Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

> And, is a VM running XP as a guest vulnerable to virus attacks like a normal PC or because its virtual, is it not affected?

TIA.A Windows installation running as a VM is just as vulnerable as a Physical machine running windows. So you will need all the same tools you use to secure windows , makes no difference if it is running in a VM.

FYI: You can run Firefox in Windows and, IMO, Firefox is more secure then IE.

---

### Post by bodhi.zazen on 2009-11-13
> **J-Buntu said:**
> I use VirtualBox to run XP, as previous posts have already answered the question about the vulnerability of windows, i will just suggest an anti-virus that i use on XP in Virtualbox - Avast Home Edition. It's free and as lightweight as they come for a highly secure AV. If you really wanted to install a firewall too, i would recommend Comodo, it's compatible with Avast. The windows software will protect you if you are surfing online in windows and anything will be contained inside the VM anyway. Both can be found free on cnet downloads BTW.

Install windows in a VM. During the installation keep it isolated from the internet.

Then run it as a snapshot and discard changes. This way your install is always optimized, fast, and secure (any viruses downloaded are gone when you shut down the VM).

---

### Post by HarrisonNapper on 2009-11-13
> **bodhi.zazen said:**
> Install windows in a VM. During the installation keep it isolated from the internet.

Then run it as a snapshot and discard changes. This way your install is always optimized, fast, and secure (any viruses downloaded are gone when you shut down the VM).

This is a glorious idea. I assume this would mean I'd have to re-download firefox every time? Honestly, I probably won't do it just because it's honestly no skin off my back if I get a virus in my VM. They can watch instant netflix to their heart's content, hehe. I'll check VBox documentation and read more about the snapshot feature; thanks for the tip!

---

### Post by Bunnybugs on 2009-11-13
> **bodhi.zazen said:**
> I suggest you start with : [Ubuntu Security - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=510812") 

A Windows installation running as a VM is just as vulnerable as a Physical machine running windows. So you will need all the same tools you use to secure windows , makes no difference if it is running in a VM.

FYI: You can run Firefox in Windows and, IMO, Firefox is more secure then IE.

Well, the difference is that the virus can't leave the virtual HDD that your v-Widdows uses;)

So, No problems I guess??

At least, when your run a VM in microshizzle, it can't leave the virtual drive;)

Specially because this is a file, and not a physical HDD...

It's less work to secure a VM, at least... that's my opinion... I'm not aloud to call myself a Ubuntu guru, but I know pretty much about MS

---

### Post by bodhi.zazen on 2009-11-13
no, no, install windows and all software you need (you can transfer the firefox installation file without internet access if you are *that* paranoid), then take a snapshot.

Save any data you need to a network share.

---

### Post by HarrisonNapper on 2009-11-13
Coolio. That information has been added to my brain repository.

---

### Post by bodhi.zazen on 2009-11-13
> **Bunnybugs said:**
> Well, the difference is that the virus can't leave the virtual HDD that your v-Widdows uses;)

So, No problems I guess??

At least, when your run a VM in microshizzle, it can't leave the virtual drive;)

Specially because this is a file, and not a physical HDD...

It's less work to secure a VM, at least... that's my opinion... I'm not aloud to call myself a Ubuntu guru, but I know pretty much about MS

Well, that makes no sense. A virus does not leave your physical hard drive either.

A virus is as much a problem to a VM as it is to a PM.

Worse, a compromised machine on your LAN, virtual or physical, it bad news and can be used to leverage attacks on other machines on your LAN.

---

### Post by J-Buntu on 2009-11-13
> **bodhi.zazen said:**
> Install windows in a VM. During the installation keep it isolated from the internet.

Then run it as a snapshot and discard changes. This way your install is always optimized, fast, and secure (any viruses downloaded are gone when you shut down the VM).
______________________

Okay, i'll try that because i haven't got around to re-installing XP on the VM since i upgraded to Karmic. Thanks for the advise.

---

### Post by Bunnybugs on 2009-11-13
> **bodhi.zazen said:**
> Well, that makes no sense. A virus does not leave your physical hard drive either.

A virus is as much a problem to a VM as it is to a PM.

Worse, a compromised machine on your LAN, virtual or physical, it bad news and can be used to leverage attacks on other machines on your LAN.

Well, that's why they build Gateways, routers, servers, hubs with firewalls these days;)

I know that the regular VM hosts have a firewall between the physical and the virtual connection;) so it can't leave your VM... a crashed VM ain't a really big poblem I guess;)

---

### Post by Bunnybugs on 2009-11-14
Well, that's an awkward silence....

Didn't mean to hurt feelings... But it just didn't make sense to me... did some research today, and it all tells me that I were right...

Some of them even have their own virus scanners, so that it's impossible to execute/download a virus in the VM... it updates as much as possible trough the internet connection....

Just ask me if you have more questions

---

### Post by undecim on 2009-11-14
You really don't have to worry about security in Ubuntu. It's default setup is secure as long as you practice the same good security that you should on any computer, which basically boils down to:

1: Avoid suspicious websites.

2: Don't install software from any source that you wouldn't give administrative access to your computer.

3: Have a descent password.

When running a Windows VM, the Windows VM can still get viruses, but they won't infect your Ubuntu install. The virus/hacker can still access anything that can be accessed from the VM (for example, shared folders)

Though if you are using a NAT connection in VirtualBox (the default), Virtualbox acts like a hardware firewall (router) for your VM, which protects you from worms that are infecting other machines on the same network. However, if you download a worm and it infects your VM, the VM can spread the worm to other windows computers on your network.

---

