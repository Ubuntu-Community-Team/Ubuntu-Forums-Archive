---
title: "Shields Up says some ports are being used by Trojans -  HELP!!"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by Noo 2 Ubuntoo on 2009-06-18
Hi,
    I decided to do a port security probe using the "Shields Up" web site. The result was that all ports were stealthed.

Then I hovered the cursor over the the first few ports on the "grid scan" diagram on the web page and what I found scared me into checking each of the first 1056 ports scanned with the following exception results: 

Port
28				/ - (Used by “Amanda” Trojan) 
30				/ - (Used by “Agent 40421” Trojan) 
285			/ - (Used by “WCTrojan” Trojan) 
334			/ - (Used by “Backage” Trojan) 
785			/ - (Used by “Network Terrorist” Trojan) 
808			/ - (Used by “WinHole” Trojan) 
831			/ - (Used by “Neurotic Kat” Trojan) 
1005			/ - (Used by “Theef” Trojan) 
1008			/ - (Used by “Lion”  & “AutoSpy” Trojan) 
1020			/ - (Used by “Doly” Trojan) 
1035			/ - (Used by “Multidropper” Trojan) 
1042			/ - (Used by “BLA” Trojan) 
  
I have now scanned my Ubuntu partition with ClamTK/AV and Avast home edition (for Linux) and my Windows partition with just Avast home edition(for Windows). 

They say no viruses found, although Avast had "permission denied/invalid argument" comments on a number of Ubuntu files (which I suspect is something to do with root permissions which I don't understand). 

Does anyone know why "Shields Up" is saying I have all these Trojans on these stealthed ports, but the anti viruses used have failed to detect any of them?

Please help!!   :(

---

### Post by Amilo1718 on 2009-06-18
> **Noo 2 Ubuntoo said:**
> Does anyone know why "Shields Up" is saying I have all these Trojans on these stealthed ports, but the anti viruses used have failed to detect any of them?
shields up said those ports could be used by trojans... not that they actually are there...
relax... chill...
:popcorn:

---

### Post by bodhi.zazen on 2009-06-18
IMO shields up is not the best source of information.

---

### Post by H2SO_four on 2009-06-18
Never heard of the site.  I'll go have a look :)

---

### Post by Noo 2 Ubuntoo on 2009-06-18
Thanks Amilo1718.  
> 
Posted by **Bodhi.Zazen** IMO shields up is not the best source of information. 

Where should I be going?

---

### Post by bodhi.zazen on 2009-06-18
What information do you want ?

I have an (ugly I know, sorry) web page here :

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

---

### Post by Locutus_of_Borg on 2009-06-18
```
nmap localhost
```
is always good

---

### Post by bodhi.zazen on 2009-06-18
> **Locutus_of_Borg said:**
> ```
nmap localhost
```is always good

IMHO, better to port scan from a remote location, another computer on your LAN for example, if you are looking for open ports.

---

### Post by Locutus_of_Borg on 2009-06-18
it is?

what is the reason for that?

---

### Post by bodhi.zazen on 2009-06-18
Because there are ports open to localhost via the lo interface. Those ports are not necessarily open to remote clients.

mysql and cups for example (assuming you have mysql installed). Same may be true if you have apache listening only on 127.0.0.1 .

So if you scan from localhost you get "false positives". So long as you recognize and understand them as such it is not a problem.

But that is why I prefer to scan from a remote host, your mileage may vary.

---

### Post by gbold on 2009-06-18
Try grc.com and look for the shields up! page.
Greg

---

### Post by Noo 2 Ubuntoo on 2009-06-18
> **bodhi.zazen said:**
> What information do you want ?

I have an (ugly I know, sorry) web page here :

[http://bodhizazen.net/Tutorials/iptables/](http://bodhizazen.net/Tutorials/iptables/)

Thanks for the link, which I've had a quick look at and established that I've got to do a lot more reading. Amilo1718 has allayed my fears by explaining I mis - interpreted the Shields Up results. 

However, when you said "not the best source of information" do you mean it may be providing inaccurate results re stealth testing? If yes where should I go,or are you talking on a deeper level? For the moment I am happy if my ports are stealthed.

Long term, I would love to see the developers make a Linux firewall like Zone alarm - preventing any program executing and transmitting to the internet which the user has  not initiated. 

A warning could be displayed about the program attempting to execute  with a request that the user allows or denies. The freedom should exist with such an application for the user to switch the warning function off, allowing programs to transmit automatically and proceed at his/her own risk.  

I am aware that it is almost impossible for a program to bypass root and start using the Linux OS to execute but sooner or later, especially with Linux being Open Source, a cracker will find a way and then start introducing spyware/malware etc. 

As for the present I'll start reading up on iptables. I read your other security page when I first started with Ubuntu but it was too much for a noobie like me who has only ever been a user.

---

### Post by Amilo1718 on 2009-06-18
> **Noo 2 Ubuntoo said:**
> Long term, I would love to see the developers make a Linux firewall like Zone alarm - preventing any program executing and transmitting to the internet which the user has  not initiated.
you're dual booting right? ;)
if fully on a *nix system the ports can be left open due to the different style of executing programs...
so if you want to be completely sure of not having your system sumbitted to malware/viruses/..., remove your MS OS :p

---

### Post by Sef on 2009-06-18
> I am aware that it is almost impossible for a program to bypass root and start using the Linux OS to execute but sooner or later, especially with Linux being Open Source, a cracker will find a way and then start introducing spyware/malware etc. 


Will never get much traction as long as people use common sense.   That Mac trojan that was in the news recently only could be installed if certain pirated software was being used.  If they had paid for a legitimate copy, then there would have not been a problem.

---

### Post by bodhi.zazen on 2009-06-18
You have a fine start, keep going.

Shields up is problematic, IMO, in a few ways.

1. It scans your router , not your computer. This leads to confusion as people wonder why if they closed a port ShieldsUp still shows it as open.

2. ShieldsUp uses the term "Stealth". While that sounds cool, that is not really standard terminology for firewalls. The issue is the difference between DROP and CLOSED, again not explained on ShieldsUP.

IMO CLOSED is as secure as DROP, certainly nothing to worry about for new users.

It is this lack of information / education that IMO is problematic as it more often panics new users w/o education.

As far as I know the results they return are accurate, so long as you understand you are canning your router and that "Stealth" = DROP.

In terms of application level security, it is there in Linux. Take a look at apparmor and selinux.

I would caution you that closed source has not been shown to be more secure then open source ;)

I would also caution you that those software restrictions you speak of in Vista (allow ... allow ... allow ...) are , IMO, skin deep. They are distracting and rapidly either ignored or disabled.

It is a simple matter to circumvent those apps as well (I will not disclose the crack here :lolflag: ) but I certainly would not rely on them (having seen how easy it is to crack them) or put as much trust in them as you seem to.

It is not so easy to crack apparmor or selinux.

selinux is enabled by default on Fedora. Apparmor is installed by default on Ubuntu, although there are insufficient profiles (IMO).

---

### Post by Noo 2 Ubuntoo on 2009-06-18
> **Amilo1718 said:**
> you're dual booting right? ;)
if fully on a *nix system the ports can be left open due to the different style of executing programs...
so if you want to be completely sure of not having your system sumbitted to malware/viruses/..., remove your MS OS :p

Apologies for my ignorance, but what is a "*nix system"?

---

### Post by bodhi.zazen on 2009-06-18
> **Noo 2 Ubuntoo said:**
> Apologies for my ignorance, but what is a "*nix system"?

Linux or Unix (Solaris, BSD, etc).

---

### Post by Noo 2 Ubuntoo on 2009-06-18
OK thanks everyone, I really appreciate your patience and help. 

My understanding has moved further forward tonight. I'm off to start researching the subjects Bodhi.Zazen has raised, signing off now.

Once again, Thanks very much.

---

### Post by LewRockwell on 2009-06-18
> **bodhi.zazen said:**
> You have a fine start, keep going.

Shields up is problematic, IMO, in a few ways.

1. It scans your router , not your computer. This leads to confusion as people wonder why if they closed a port ShieldsUp still shows it as open.



not everyone is behind a decent router

(for those who are currently connected directly to a modem with no firewall, you really should get behind a decent router asap)

your mileage may vary

---

### Post by freeman2000 on 2009-06-18
> **bodhi.zazen said:**
> IMO shields up is not the best source of information.

Shields Up and Steve Gibson are the standard-bearers in this area of security.  They are held in the highest regards by all in the computer security arena.  What did the site tell you after the test?  It always has some sort of description of what the problem may be.  And it will accurately tell you what version of linux you are using, and on what web browser.  Go back and rerun the tests.  Take your time, and pay attention to the answers/results that it gives you.  Good luck.

---

### Post by bodhi.zazen on 2009-06-18
> **freeman2000 said:**
> Shields Up and Steve Gibson are the standard-bearers in this area of security.  They are held in the highest regards by all in the computer security arena.  What did the site tell you after the test?  It always has some sort of description of what the problem may be.  And it will accurately tell you what version of linux you are using, and on what web browser.  Go back and rerun the tests.  Take your time, and pay attention to the answers/results that it gives you.  Good luck.

They may be but that does not mean I have to like their web site :)

In terms of information, IMO, there are many better resources.

What does ShildsUp teach about iptables ? I missed that page, linky ? 

and I still do not like the term "stealth" , it is IMO, misleading.

:lolflag:

Take a look at this page :

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables)

---

