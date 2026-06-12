---
title: "Anti-virus Software?"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by Sonofsurak on 2009-01-20
Do I need to use anti-virus software with Ubuntu?

---

### Post by schnauzer93 on 2009-01-20
No.

---

### Post by Dumbestcrayon on 2009-01-20
No. I'm not going to say there are "absolutely zero viruses for Ubuntu" but you don't need an anti-virus.

---

### Post by illurim on 2009-01-20
I don't believe so. One of the perks of using Linux is that "there are no viruses". While I'm sure in the strictest of technical senses this **isn't** 100% true, for your normal day-to-day operations, you won't need anti-virus software.

One of the more tech geeks will probably provide a bit better of an explanation (or correct me if I'm mistaken).

---

### Post by Sonofsurak on 2009-01-20
I didn't think so.  Thanks for the advice.

---

### Post by Piraja on 2009-01-20
Here's a quote from an [Ubuntu Community Document]("https://help.ubuntu.com/community/Antivirus") page:

> Why do I need anti-virus software? Isn't Linux virus-free?

For the most part, Linux is engineered in a fashion that makes it hard for viruses to run ([click here for more info]("http://librenix.com/?inode=21")). Also, because more PCs currently run Windows, it is more worthwhile writing viruses for the Windows platform. However, there are many reasons you might want a virus scanner on your Linux PC:

    * to scan a Windows drive in your PC
    * to scan Windows machines over a network
    * to scan files you are going to send to other people
    * to scan e-mail you are going to forward to other people
    * some Windows viruses can run with Wine.
    * Linux virus infections are theoretically possible 

So I think it is for you to decide whether to install anti-virus software or not. I suppose there are many of us, like me, who don't think they need that in Ubuntu Linux. But don't take my word for it.

---

### Post by donkyhotay on 2009-01-20
The only thing I've ever needed to use anti-virus on linux is for help identifying infected files from a windows box.

---

### Post by Bablefish on 2009-01-20
Both AVG and Avast have Anti Virus software for Linux

---

### Post by mayorpacmanjones on 2009-01-20
no but i heard clamwin is also available for linux

---

### Post by SunnyRabbiera on 2009-01-20
Currently there are 0 viruses for linux, or at least 0 that work.
You are safe :D

---

### Post by donkyhotay on 2009-01-20
> **mayorpacmanjones said:**
> no but i heard clamwin is also available for linux

Heh, more like the other way around. Clamwin is based off clamAV which is an open source virus scanner used primarily on *nix.

---

### Post by WatchingThePain on 2009-01-20
Hi, you don't need an anti-virus but a firewall is recommended. There are less viruses (or virii) that can affect Linux but they do still exist. I have heard of rootkits on Linux as well. 

You can find Firestarter in synaptic package manager, which is a front end that lets you configure the linux firewall quite easily.

---

### Post by donkyhotay on 2009-01-20
> **WatchingThePain said:**
> Hi, you don't need an anti-virus but a firewall is recommended. There are less viruses (or virii)that can affect Linux but they do still exist. I have heard of rootkits on Linux as well. 

You can find Firestarter in synaptic package manager, which is a front end that lets you configure the linux firewall quite easily.

Firestarter is not a true firewall, it's just a front-end for iptables which is automatically installed and running on your system already. The only thing you would need firestarter for is if you need to *change* your firewall settings. It's actually not recommended to keep firestarter running all the time as it requires root permissions and so is actually security *liability* if you just let it run in the background forever.

---

### Post by theozzlives on 2009-01-20
You know I "cleaned house" on a ladies computer a couple of weeks ago and forgot how much malware one Windows computer can have! Geese!

---

### Post by OllieGab on 2009-01-20
So is there any risk that, when booted in Linux, a (Windows) virus can "arrive", sit in waiting, and then cause problems whenever I boot up my Windows part of my harddrive?

Ollie

---

### Post by donkyhotay on 2009-01-20
Only if they are accessed by either you a program. So long as they are just 'sitting' there there is no problem but theoretically if you download instAllz_v1ruses.exe under linux and then try to run it under windows, the windows will be infected. Same is true though for any file that can give you a virus not just executables.

---

### Post by lukjad on 2009-01-21
> **Sonofsurak said:**
> Do I need to use anti-virus software with Ubuntu?

An anti-virus is a "logical" idea, if only just to make sure that you don't infect Windows computers. While I won't say that there are ***NO*** viruses for Linux, there are so few, and they are so ineffective that right now, they are not much of a threat. The problem is, however, if we grow complacent, and our market share continues to grow, eventually there may prove to be a form of malware that could be dangerous to Linux. There are some steps you can take to protect yourself.

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

Hope this helps! :D

---

### Post by hyper_ch on 2009-01-21
> **lukjad007 said:**
> The problem is, however, if we grow complacent, and our market share continues to grow, eventually there may prove to be a form of malware that could be dangerous to Linux. There are some steps you can take to protect yourself.

Malware != viruses

I have my doubts virsuses will ever have a great impact on linux... other types of malware could have... especially when socially engineered...

---

### Post by bruce89 on 2009-01-21
> **lukjad007 said:**
> The problem is, however, if we grow complacent, and our market share continues to grow, eventually there may prove to be a form of malware that could be dangerous to Linux. There are some steps you can take to protect yourself.

[LIST]
[*]There is still an utterly tiny market share
[*]There are a lot of different distros and hardware types, meaning executables may not work properly.
[*]Free Software is more easy to fix as anyone can do it
[/LIST]

---

### Post by hyper_ch on 2009-01-21
> **bruce89 said:**
> [LIST]
[*]There is still an utterly tiny market share
[/LIST]

actually, there are more linux devices out there than devices running windows...

---

### Post by ErsinG on 2009-01-21
well, i'm very tired of using various programs just to keep safe my computer and i switched to ubuntu.. so far no problems, no viruses, no trojans... 
so, i don't really think you need to use an antivirus program in ubuntu

---

### Post by boof1988 on 2009-01-21
> **donkyhotay said:**
> Firestarter is not a true firewall, it's just a front-end for iptables... 

Yes... True... But...

...> **donkyhotay said:**
> which is automatically installed and running on your system already.

It is my understanding that the firewall is not running/loaded on the default install.

```
user@host:~$sudo ufw status
Firewall not loaded
```

Try is on a fresh install and check the output.  Of course there may be some *nix varieties that may start the firewall on initial install...

So my understanding (if one is setting up the computer's firewall) is that one needs to start the firewall and set appropriate rules.  This can be done using many different methods (ufw, direct iptables mod, firestarter, gufw etc.)

---

### Post by bruce89 on 2009-01-21
> **hyper_ch said:**
> actually, there are more linux devices out there than devices running windows...

Depends if you include Windows Mobile I suspect.

---

### Post by lukjad on 2009-01-21
> **hyper_ch said:**
> Malware != viruses

I have my doubts virsuses will ever have a great impact on linux... other types of malware could have... especially when socially engineered...

I agree that malware is not viruses, but my point is that we cannot just sit back and ignore security. My post was there to point out the possible security concerns and measures that could be taken.

> **ErsinG said:**
> well, i'm very tired of using various programs just to keep safe my computer and i switched to ubuntu.. so far no problems, no viruses, no trojans... 
so, i don't really think you need to use an antivirus program in ubuntu

The point I'm trying to make is that security is still important, and we need to keep our guard up. If we don't, we will be in serious trouble some day.

---

### Post by WatchingThePain on 2009-01-21
Don't try this but I once copied some infected files from my windows on to Linux to see what would happen, nothing happened.
Say if someone dual boots though, usually grub or lilo go in the MBR so if windows gets wrecked and the  MBR gets wiped I suppose that means linux would not boot either.

---

### Post by Paqman on 2009-01-21
> **boof1988 said:**
> ... 
It is my understanding that the firewall is not running/loaded on the default install.


True.

> 
So my understanding (if one is setting up the computer's firewall) is that one needs to start the firewall and set appropriate rules.  This can be done using many different methods (ufw, direct iptables mod, firestarter, gufw etc.)

Not so. The firewall isn't switched on by default, but neither are there any services listening on ports. With nothing listening you are no more at risk with the firewall switched off than on.

---

### Post by boof1988 on 2009-01-21
> **Paqman said:**
> Not so. The firewall isn't switched on by default, but neither are there any services listening on ports.

It is so... because:

> **Paqman said:**
> ...The firewall isn't switched on by default...

All I said was that the firewall is not turned on by default.  Are the "firewall" and "port listening" different things/applications?  Does the firewall prevent applications from listening to ports?  I would like to know the difference, since I'm still learning.

> **Paqman said:**
> With nothing listening you are no more at risk with the firewall switched off than on.

I agree to this... No disputes at this with my current knowledge level.

---

### Post by WatchingThePain on 2009-01-21
What ports are open on a default install?.

---

### Post by Paqman on 2009-01-21
> **boof1988 said:**
> 
All I said was that the firewall is not turned on by default.  Are the "firewall" and "port listening" different things/applications?


Sort of. If there is no service listening on a port then it doesn't make any difference whether the firewall has closed that port or not. Any attacker trying to get into your box through that port can't succeed, because they've got nothing to connect to.

---

