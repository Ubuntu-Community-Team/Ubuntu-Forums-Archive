---
title: "Firewall?"
date: 2009-06-24
forum: New to Ubuntu
---

### Post by kazaril on 2009-06-24
Hi all, I just installed Ubuntu Jaunty Jackalope and was about to check my internet banking but became concerned because I saw no mention of a firewall throughout the installation. I know Linux is much more secure then Windows but I hesitate because I would like not to have my money stolen. Is there a particular program I should install or is everything just automatically protected.

Thanks heaps

---

### Post by balachandarlinks on 2009-06-24
Hi,
  Firewall is defaultly installed.If you need a GUI to monitor your firewall then go to synaptic and search for "firewall".programs like Firestarter and gufw are available.
                           cheers.......

---

### Post by SunnyRabbiera on 2009-06-24
Ubuntu has a lot of good security built in and indeed a firewall is a part of the system by default.
But if you feel paranoid firestarter is a good suggestion.

---

### Post by lovinglinux on 2009-06-24
I strongly recommend reading the [Ubuntu Security](http://ubuntuforums.org/showthread.php?t=765421) tutorial.

Ubuntu comes with a firewall, called iptables, but it allows all traffic by default. Additionally, Ubuntu comes with no listening services, so there isn't any program that could accept remote connections. Without a service running, any unwanted connection reaching your machine will be ignored. This basically means you don't need to create any firewall rules, unless you install a service. But then you would probably want to allow people to connect to that service, making the use of a firewall useless, unless you want to limit which IPs can connect to it.

If you want to activate the firewall you need to know iptables commands or install a firewall manager. The recommended one is [gufw](apt:gufw), which is graphical interface for ufw (uncomplicated firewall) which is the program that will create the iptables rules for you. It sounds complicated, but it isn't. Just install [gufw](apt:gufw) [apt-get] then go to "System >> Administration >> Firewall Configuration" and create your firewall rules.

In regard to Internet banking a firewall wouldn't protect you, because your computer is the one requesting connections when you access a web site. So you need to allow the connection to go out and once it is established, the data transfer between your machine and the web site will all be allowed. What you need to worry about is [phishing](http://en.wikipedia.org/wiki/phishing) [wikipedia.org] and password security. Only use strong passwords, those virtual keyboards provided by the bank web site and [hardware tokens](http://en.wikipedia.org/wiki/Security_token), if provided. Also make sure the connection with the site is encrypted.

I'm not a security expert, but I guess Ubuntu could be infected with keyloggers and other stuff that could redirect your browser to a fake site. I'm not sure tho. What I know is that there isn't any virus for Linux in the wild. The best way to avoid malware is to download applications only from repositories or trusted sources. Unlike Windows, you don't need to hunt applications on the web. The Ubuntu repositories contain a vast amount of applications that can e installed with a simple command or through the Add/Remove manager or through Synaptic package manager. If you need very specific applications you might need to download a deb file from the developer web site, which is basically like a Windows exe installation file. Nevertheless, try to avoid downloading stuff from web sites if you can.

Additionally, you might want to use [NoScript ](https://addons.mozilla.org/en-US/firefox/addon/722)extension, to protect Firefox from running scripts from untrusted web sites.

---

### Post by Herman on 2009-06-24
> I'm not a security expert, but I guess Ubuntu could be infected with keyloggers and other stuff that could redirect your browser to a fake site. I'm not sure tho. What I know is that there isn't any virus for Linux in the wild. The best way to avoid malware is to download applications only from repositories or trusted sources. Unlike Windows, you don't need to hunt applications on the web. The Ubuntu repositories contain a vast amount of applications that can e installed with a simple command or through the Add/Remove manager or through Synaptic package manager. If you need very specific applications you might need to download a deb file from the developer web site, which is basically like a Windows exe installation file. Nevertheless, try to avoid downloading stuff from web sites if you can.+1  I couldn't agree more. 

If you stick to the same repositories everyone else is using, all the software you will be installing is safe.
The programs we use in Ubuntu are 'open source', so other programmers can read the programs and see that they don't contain malicious code.
The programmers who are allowed to upload to the repositories use special keys called gpg keys, so only trusted programmers can upload software, read about secure apt here: [Secure Apt]("http://wiki.debian.org/SecureApt") - Debian Wiki

You are way, way safer with Ubuntu without any firewall than with closed source software and even the best firewall.

I got a phone call to go to a (Windows user) friend's house just last weekend because they couldn't download an urgent email they needed for work they had to have done by Monday morning. When I arrived I soon found the problem, it was simple. Their email program was blocked at the firewall, and not allowed access to the internet.
An update had caused some programs to need new permissions to access the internet and the user had not been able to recognize what the programs were so denied access.
Most Windows users can't tell what 'xyz.exe' is or if they should trust it or not.
Most Windows users do the opposite of what my friend did, they allow almost any program access to the internet. It would be a pretty big job to check every program that asks for internet access and most Windows users don't have time. Besides, if you have a nice game and it won't work properly because you denied it internet access, you're going to allow it access aren't you? (Sooner or later).

That's the problem with Windows. Even the best firewall in the world can't protect a Windows user, because almost all Windows users will choose to allow just about all programs access to the internet anyway, or their programs won't work as well as they should. Since the programs are closed source, nobody knows for sure if the programs are safe or not, nobody can read the program's source code to check. The programs are judged by their reputation only. How does any Windows user know what information their computer is sharing with the rest of the world or what their programs are really doing? I have even know people to install programs they actually paid for, as 'security programs', which were actually the viruses themselves, (like wolves in sheep's clothing).
And yet, most Windows users are brainwashed into believing that if they keep on paying for a reputable firewall and antivirus program they're 'safe'. (LOL).

Having said that, Windows would be perfectly secure if people didn't install software (games in particular) from sites on the internet. (If Windows provided repositories where people could download free software or even purchase software that they know they can trust).
And conversely, Ubuntu can be just as insecure as Windows if bad software is installed, from some unknown site on the internet.

You don't need any firewall in Ubuntu unless you open ports by installing 'services' (networking or file sharing programs).

---

### Post by coffeecat on 2009-06-24
Are you using a modem-router with either cable or adsl? If so, so long as it is configured properly, the firewall there will do an effective job of keeping intruders out. Just make sure that it doesn't respond to pings (some modem-routers do on a default configuration) and you'll be invisible on the big bad net. If you need to check this out, test your system with ShieldsUP at:

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

### Post by kazaril on 2009-06-25
Thanks folks, you've been a great help.:D

---

### Post by paul_be on 2009-06-25
> **coffeecat said:**
> Are you using a modem-router with either cable or adsl? If so, so long as it is configured properly, the firewall there will do an effective job of keeping intruders out. Just make sure that it doesn't respond to pings (some modem-routers do on a default configuration) and you'll be invisible on the big bad net. If you need to check this out, test your system with ShieldsUP at:

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

+1

A NAT router will be sufficient for incoming attacks(using linux doesnt hurt either:))

---

### Post by lisati on 2009-06-25
> **lovinglinux said:**
> 
I'm not a security expert, but I guess Ubuntu could be infected with keyloggers and other stuff that could redirect your browser to a fake site. I'm not sure tho. What I know is that there isn't any virus for Linux in the wild. The best way to avoid malware is to download applications only from repositories or trusted sources. Unlike Windows, you don't need to hunt applications on the web. The Ubuntu repositories contain a vast amount of applications that can e installed with a simple command or through the Add/Remove manager or through Synaptic package manager. If you need very specific applications you might need to download a deb file from the developer web site, which is basically like a Windows exe installation file. Nevertheless, try to avoid downloading stuff from web sites if you can.


Good ways of avoiding being caught out by a fake site is to pay attention to (a) what's in the address bar, (b) the link that gets highlighted in the status bar at the bottom of the screen when you hover your mouse over a URL, and (c) be wise to what personal information you'd normally be asked for when logging in to a real site. I recently received a phishing email supposedly from a bank I do online banking with. It had a link but what would normally be something like [http://mybank.co.nz](http://mybank.co.nz) was actually directed to something like [http://bovine.excrement/mybank.co.nz](http://bovine.excrement/mybank.co.nz)

---

### Post by kansasnoob on 2009-06-25
I don't remember if gufw is installed by default or not, just go to System > Administration > Firewall Configuration and tick on "enable".

[ATTACH]118876[/ATTACH]

If it's not there you can either install it from Synaptic Package Manager or go to Terminal and run:

```
sudo apt-get install gufw
```

More here:

[http://gufw.tuxfamily.org/index.html](http://gufw.tuxfamily.org/index.html)

---

