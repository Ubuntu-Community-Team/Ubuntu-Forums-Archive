---
title: "Downloading Tor"
date: 2010-09-20
forum: New to Ubuntu
---

### Post by lizandeen on 2010-09-20
I'm on 9.04 and try as I might I cannot download or install Tor!I've checked, pasted and copied instructions from numerous websites and forums but keep getting told "Package tor is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package tor has no installation candidate"
Any ideas or solutions? Thanks to all in advance, Deen

---

### Post by jtarin on 2010-09-20
[Lookie,Lookie]("http://www.torproject.org/docs/debian.html.en"). Option two.

---

### Post by perspectoff on 2010-09-20
Also, the instructions noted in the previous post require a keyserver. Keyservers usually require port 11371 to be open in your firewall.

My old (possibly now outdated) Tor instructions are at 

[http://kubuntuguide.org/Lucid#Tor_.28Network_privacy.29](http://kubuntuguide.org/Lucid#Tor_.28Network_privacy.29)

and

[http://ubuntuguide.org/wiki/Ubuntu:Lucid#Tor_.28Network_privacy.29](http://ubuntuguide.org/wiki/Ubuntu:Lucid#Tor_.28Network_privacy.29)

To use Tor effectively, you must open a large number of ports in your firewall.

Since I am paranoid about keeping a large number of ports open, I dedicate one Ubuntu installation to Tor alone. (That installation can be on its own partition, which is what I do, or in its own virtual machine).

This allows me to keep Tor quarantined, in addition.

It has been a while since I have read all the limitations of Tor, but there are some. Don't forget, Tor was initially developed with the assistance of the US government, so I would not be surprised if there are some backdoors built in somewhere.

I am also very afraid of (spoof-like) redirection from an intermediate node.

Tor should therefore always be used with high-grade encryption if you are using it for anything sensitive!

Lastly, Tor is very slow. It is a very useful tool, but I hate those people who use it to anonymously trade files, which brings the system to a standstill. Please don't use it for that! 

My own 2 cents.

---

### Post by t0p on 2010-09-20
There are Firefox add-ons that make using tor as simple as clicking a button in your browser.  If you look under **Tools > Add-ons** and do a search for "tor" I'm sure you'll find what you need.

---

### Post by perspectoff on 2010-09-20
> **t0p said:**
> There are Firefox add-ons that make using tor as simple as clicking a button in your browser.  If you look under **Tools > Add-ons** and do a search for "tor" I'm sure you'll find what you need.

Not true. You are thinking about Torbutton, which toggles whether Firefox will use Tor as a proxy or not. But Tor must be installed and properly configured as a proxy before Torbutton will work.

---

### Post by lizandeen on 2010-09-20
I've tried updating my repository/sources list by following the instructions in method 2 on the Tor site in order to download it but when the computer tries to update them I get these messages in 2 separate warning boxes

E: Malformed line 62 in source list /etc/apt/sources.list (dist parse)
E: Unable to lock the list directory


E: Malformed line 62 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

Any thoughts?

---

