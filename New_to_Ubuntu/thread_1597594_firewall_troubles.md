---
title: "firewall troubles"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by ten_dot_ten on 2010-10-15
Hello,

I'm a Windows and Mac user who is interested in switching to Linux. Last weekend I installed Ubuntu 10.10 (dual boot) on my Windows laptop, with the goal of getting it all set up the way I want and getting familiar with the OS before installing at as (hopefully) my primary OS on my MacBook.

While the install itself was a piece of cake, and I can generally-speaking find my way around OK, I didn't find an included firewall, so installed Firestarter. As soon as I did this, I lost my internet connection. I found a user guide for Firestarter, but find the instructions a bit above my head.

I need to know if Ubuntu has a built-in firewall I missed, and if so, some basic instructions on how to activate it and set it up to block all incoming traffic and have all outgoing traffic ask for permission (like ZoneAlarm works in Windows). I know little to nothing about ports and IP lists.

If there isn't a built-in firewall, can somebody help me to properly configure Firestarter?

---

### Post by Calash on 2010-10-15
Despite it being the first thing you find in the Software Center when you search, Firestarter is not very well supported and you will likely get a ton of advice to remove it.

On the subject of Firewalls in general you will get a variety of opinions.  By default the install will have no open ports, making a Firewall useless.  Ubuntu has one built in but it ether requires some command line knowledge or the installation of a GUI to manage it.

Please look at the following thread as it is a great document on the various security methods, what you really need, and how to make use of them

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by perspectoff on 2010-10-15
Yeah, Firestarter has been stable for a long time so there hasn't been much change to it lately. It does have an extensive documentation, though, and I don't think it is that difficult to understand.

If you think Firestarter is difficult, wait until you dive into ufw, the default firewall for Ubuntu. OMG. It is rather similar to Cisco firewalls in structure and very powerful, but that does not make it easy.

There is no substitute for reading the full documentation for either program, though. 

Most people from the Windows world don't actually use their firewalls very effectively (and they are a bit of a waste of time if you don't learn how to use them properly).

I use Firestarter continually because it is very quick and easy to turn off and on in real-time using the one-click GUI (which I can't say about ufw).

The trickiest thing about Firestarter is realising that they refer to the entire LAN in the format 192.168.0.1/24 instead of 192.168.0.1 - 192.168.0.255.

Learning that nomenclature was the hardest part of learning Firestarter for me. 

I have had ufw for about a year now and still can't get the hang of it. Besides, the GUI for ufw (gufw) doesn't allow me to change the things I need to in ufw in real-time.

But you will hear all kinds of opinions on this. YMMV.

Also, there is an awful lot of hair-splitting terminology used when referring to ports.

All traffic is allowed in and out in Ubuntu by default. A firewall selectively blocks some of that traffic (and nothing is blocked by default in Ubuntu).

However, unless an app is actually sending or receiving traffic (i.e. "ports open"), nothing is going through the ports ("ports closed"). Unless you are an expert, though, you will be unaware when traffic is actually going in and out of your computer ("ports open"). 

The idea of a firewall is to control whether certain ports will be allowed to "open" up (or not) just because an app wants to send traffic through it.

Now, Firestarter is indeed less powerful than other paradigms for Firewall control. 

It is indeed port based and not app-based (as is ZoneAlarm and PCTools Firewall). This is problematic, because some apps like to use multiple ports at random. It is impossible for an individual user to know which ports are to be used for every application.

Unfortunately, this is a limitation with iptables in general.

How do you allow only one program to be able to open and close ports but not any other program? How do you ensure that only traffic from that program goes through the ports that have then been opened up and there is no piggyback traffic (as happens in the Windows world with several types of malware)?

Can ufw provide this type of control?

> **Calash said:**
> 

Please look at the following thread as it is a great document on the various security methods, what you really need, and how to make use of them

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

Yeah, that page is pretty cool, if a bit advanced for new users and full of suggestions that aren't yet finished. There is also a good bit of misinformation. It asserts there are no viruses in the wild for Linux, whereas Wikipedia cites 863 known malware programs in Linux (see [http://en.wikipedia.org/wiki/Linux_malware](http://en.wikipedia.org/wiki/Linux_malware)).

---

