---
title: "Help installing tor on jaunty 9.04"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by stlsaint on 2009-04-25
i seem to be unable to install tor or tork onto my virutal machine running jaunty...please help i have attached the screenshot thru my attachment....
it keeps saying that there are some files missing in the config file...

---

### Post by obreiro on 2009-05-09
TOR IS NOT in the Jaunty repositories. There are few other apps as Vidalia, Tork, torbutton  (for Firefox), privoxy...
But Tor engine is not present. You must install it from other personal repositories for example [http://phyx.wordpress.com/2009/05/06/tor-en-ubuntu-904-instalacionconfiguracion/](http://phyx.wordpress.com/2009/05/06/tor-en-ubuntu-904-instalacionconfiguracion/) )

I recommend to install it from source code or packages downloaded from Author's website.

Why Ubuntu have not Tor ??? I don't know.

---

### Post by Artemis3 on 2009-05-12
[quote="http://www.avuc.nl/2009/05/04/tor-on-ubuntu-904/"]Add these lines to ‘/etc/apt/sources.list’ with your favorite text-editor.

deb     [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) jaunty main
deb-src [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) jaunty main

Next open the terminal and do the following to make sure the system sees the new repos as ‘trusted’.

gpg --keyserver subkeys.pgp.net --recv 94C09C7F
gpg --fingerprint 94C09C7F
gpg --export 94C09C7F | sudo apt-key add -

And update with ’sudo aptitude update’. Now install Tor with ’sudo aptitude install tor’.[/quote]

The Tor package has mysteriously disappeared from 9.04 repositories...

---

### Post by paraplegicpanda on 2009-05-14
```

Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com jaunty/main libevent1 1.3e-3 [44.7kB]
**Get:2 http://mirror.noreply.org jaunty/main tor 0.2.0.34-1~intrepid+1 [1218kB]**
Get:3 http://us.archive.ubuntu.com jaunty/universe tsocks 1.8beta5-9.1 [276kB]
Get:4 http://us.archive.ubuntu.com jaunty/universe socat 1.6.0.1-1 [315kB]
**Get:5 http://mirror.noreply.org jaunty/main tor-geoipdb 0.2.0.34-1~intrepid+1 [714kB]**
```

Judging by the fact that the two bold lines above still say intrepid, I am assuming that Canonical is waiting for them to toss out a Jaunty specific release before they add it to the repos. Vidalia and Torbutton (both in the repos) are straight Deb packages so I don't believe they need the Jaunty releases... I may completely wrong on this, but it's what I am guessing.

Regardless, Tor needs to get back into the repos. Btw, the Intrepid release works fine on Jaunty.

---

### Post by braddock on 2009-06-19
The protesters in Iran are actively trying to use Tor to protect their safety.  

There are many calls for people outside Iran to run Tor proxies (known IPs get blocked by the government).

[http://iran.whyweprotest.net/showthread.php?t=802](http://iran.whyweprotest.net/showthread.php?t=802)

It would be a great time for someone to add Tor to the Jaunty 9.06 repos!

---

### Post by hypernihl on 2009-06-20
I have been a relay and a bridge for Iran for the last 48 hours, on a windows 7 machine. 

I cannot not get this working via vidalia in 9.04??? Any ideas???


I installed vidalia with apt, my network is setup fine, wtf, cannot connect to TOR with 9.04, please, help, ubuntu is my primary OS, and i'm stuck!!!

---

### Post by eruanne on 2009-06-21
I"m trying to set up Tor and a relay as well.  I set up Tor and Vidalia in about two seconds flat on my netbook which runs Windows 7.  Go figure!  My main computer, this one, is a dual boot with Ubuntu Jaunty and Windows Vista.  I tried the Tor-Vidalia combo on the Vista boot first, just because I was using that boot at the time.  No dice.  As usual, I cussed Vista (!) and went to the Ubuntu boot.  More cussing until I found this blog [http://www.avuc.nl/2009/05/04/tor-on-ubuntu-904/](http://www.avuc.nl/2009/05/04/tor-on-ubuntu-904/) which helped me get Tor.  It doesn't seem to be agreeing too well with FoxyProxy though, which I will consult with the original blogger about.  Anyway, I then went to Add/Remove applications (the built-in GUI) and found Vidalia.  Great!  I thought, since I knew it already.   Well, not so great.  It downloads and installs, then almost immediately quits.  It says it cannot connect properly, and when I check the log it says this is an experimental software and unsafe.  Well, I'm not doing it for my security but to provide more space on the Tor network for Iranian activists. I figure even a relay helps with that.  If it's not that secure, I just won't set up a Tor bridge for the Iranians, but the relay should still help right?
Could part of the problem be that I'm running the netbook as a relay on the same router?  Will it only connect using one Tor port per router?  I was thinking that could explain why I can connect one computer and not the other - although I did try disconnecting the netbook and connecting this big kahuna, and still no luck.  I guess I should try that again.

---

### Post by sam0vi on 2009-06-24
I did what the instructins say and tried "deb [http://mirror.noreply.org/pub/tor](http://mirror.noreply.org/pub/tor) <DISTRIBUTION> main" but bash tells me "deb: command not found". Is this happening to any of you? thanx

---

### Post by braddock on 2009-06-28
Why Tor fell out of Jaunty.  

[https://bugs.launchpad.net/ubuntu/+source/tor/+bug/328442](https://bugs.launchpad.net/ubuntu/+source/tor/+bug/328442)

From what I read, Tor provided debs for Jaunty many months ago.  The Ubuntu team rejected the debs because they did not have a committed Ubuntu maintainer.

So Tor fell out of Jaunty.  

If you want the Tor debs that were offered to Jaunty, install them from:

[https://wiki.torproject.org/noreply/TheOnionRouter/TorOnDebian](https://wiki.torproject.org/noreply/TheOnionRouter/TorOnDebian)

---

