---
title: "Cannot load certain web sites"
date: 2007-01-11
forum: Networking &amp; Wireless
---

### Post by Asix on 2007-01-11
I have two computers networked one with another over a standard 100 mbit/s LAN cable. One computer is running Windows XP Pro SP2 and the other one (which I'm using) is running Kubuntu Edgy.
The computer running Win has a direct connection to the Internet over an ISDN line, and it shares its connection with the other computer running Edgy through Internet Connection Sharing (ICS). When I've installed Kubuntu on my computer, the network was configured automatically and I didn't have to make any adjustments to the network configuration because the computer was able to connect to the Internet without problems.
But after some time I've realized that I cannot load certain web sites. When I run Firefox and type the address of a web site, it will say "Waiting for http://www.somesite.com" and no progress will be made at that point. But when I log back to Windows XP I load that site almost instantly.
The fact is that it doesn't matter which application is used for browsing the Internet. I've tried to load the same web site in Firefox and in Konqueror, and both are having problems, so the problem  is system - wide.
Is there a workaround for this? I suspect it's my network configuration, but I don't know exactly what to do. Any clues on this? Thanks in advance.

---

### Post by recon69 on 2007-01-11
Need more information. like the name of the web site, maybe it's a problem with the web site and it will only work in EI. have you tried to ping the web site. what version of firefox you using, do you have popups blocked . is flash installed ect. but try ping the website first. 

this info would help people guess what might be causing your issue. without the details people will not have a chance of helping you 

regards

---

### Post by Asix on 2007-01-11
The version of Firefox is 2.0 (I'll upgrade it to 2.0.1 in a few days, but I don't think that will solve the problem), the Flash version is 7.0, and there are no popups blocked or anything.
I've pinged certain web sites, and got interesting results. For example, I cannot load web site [www.tickle.com](www.tickle.com), but I can ping it. 
So if I type ```
ping -c 4 www.tickle.com
``` I get the following output:
```

PING www.tickle.com (130.94.250.48) 56(84) bytes of data.
64 bytes from www.tickle.com (130.94.250.48): icmp_seq=1 ttl=238 time=244 ms
64 bytes from www.tickle.com (130.94.250.48): icmp_seq=2 ttl=238 time=243 ms
64 bytes from www.tickle.com (130.94.250.48): icmp_seq=3 ttl=238 time=245 ms
64 bytes from www.tickle.com (130.94.250.48): icmp_seq=4 ttl=239 time=242 ms

--- www.tickle.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3015ms
rtt min/avg/max/mdev = 242.484/243.727/245.053/1.135 ms

```
But I also cannot load [www.microsoft.com](www.microsoft.com) (yeah, I know, but that's just an example, though), so if I type ```
ping -c 4 www.microsoft.com
``` I get the following:
```

PING lb1.www.ms.akadns.net (207.46.20.60) 56(84) bytes of data.

--- lb1.www.ms.akadns.net ping statistics ---
4 packets transmitted, 0 received, 100% packet loss, time 3007ms

```
Hope that this helps.

---

### Post by RaZoR-x11 on 2007-01-11
Hey,

Quick one do you have java engine installed?

RaZoR

---

### Post by RaZoR-x11 on 2007-01-11
Just had a though do you have a firewall setup, or and proxy's some proxy wont support some site's.

---

### Post by Asix on 2007-01-11
The ICS computer is not behind any proxy or anything, and I'm sure that firewall is set up not to block any web sites (port 80 is opened in both directions, as well as other standard ports).
Though, I am not sure about Java, how can I check if I have it installed?

---

### Post by RaZoR-x11 on 2007-01-11
Quick one if it the page's are not displaying anything at all? or only on a few
page that wont load for you?

---

### Post by Asix on 2007-01-11
No, there's nothing displaying on the page, there's just white background and nothing except that.

---

### Post by recon69 on 2007-01-12
> But I also cannot load [www.microsoft.com](www.microsoft.com) (yeah, I know, but that's just an example, though), so if I type

Code:

ping -c 4 [www.microsoft.com](www.microsoft.com)



this is not suprising as microsoft blocks ICMP packets due to the high number of DOS attacks their servers receive. 

you could try using 

wget --spider [http://www.tickle.com](http://www.tickle.com)

then try without the --spider and see what happens, 

I loaded the page and it worked fine, I got flash 9 installed and java as well (Firefox 1.5.09) . I would check that you have java at least. have a look and see what you browser is saying, I'v seen web pages hang while trying to DL plugins and the like before. 

regards

---

### Post by Asix on 2007-01-12
I don't know if I have Java installed on my system, how can I check that? I only know that I have installed java-common package, but I'm not sure that's enough...

---

### Post by chili555 on 2007-01-12
To see if the Java plugin is installed in your browser, type about: plugins in the address bar. You should see something like this: Java(TM) Plug-in 1.5.0_08-b03

If it is not, the easiest way to get it is Automatix2. [http://getautomatix.com/wiki/index.php?title=Installation](http://getautomatix.com/wiki/index.php?title=Installation)

---

### Post by Asix on 2007-01-12
I don't want to install Automatix2 right now for some reasons, but when I type ```
sudo apt-get install sun-java5-jre sun-java5-plugin
``` it says this
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package sun-java5-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java5-jre has no installation candidate
```
But I think I've enabled all repositories and updated repository cache, I don't have a clue why it won't install it.

---

### Post by chili555 on 2007-01-14
[http://packages.ubuntu.com/edgy/libs/sun-java5-jre](http://packages.ubuntu.com/edgy/libs/sun-java5-jre)

Try this.

---

### Post by drax on 2007-01-16
Can i add my 2 cents worth in here....

I am also having a similiar (maybe same problem) sites like google work fine, but tickle.com, daphne-emu.com don't. Cannot even ping those that dont

I have 2 computers set up on the same line a windows box with no problems.. The linux running kubuntu edgy..

There is no proxy set up. I have the DNS manually configured as well as other gateway and internet ip's.

---

### Post by RaZoR-x11 on 2007-01-16
Hey there,

This thread is still here:-k.

Only joking, well have you configered your firewall etc?

Plus what browser are you running etc.

---

### Post by drax on 2007-01-17
for me... no firewall installed only the default ip tables.... That didn't work so added default settings using kmyfirewall and tried again without success..

Used both default KDE browser Konquerer and my perferred Firefox. Both fail in same instance


Edit: Figured it out.. the DNS i was using is dodgy.. works for windows, not for linux.. Not sure why, i'll tackle that another day. I added dyndns.org dns and everything is good..

---

### Post by tiggerrwit on 2008-02-09
I am having similar problems I am running a PC & laptop both running Windows Vista Basic, networking via Netear modem router computer connected wired & wireless I am connected by DSL ISP Optus, I have web pages that work most of the time then at times they will not load, emptying temp & caches don't help, sometimes reboot does & one time resetting the browser did, but don't want to have to keep doing that as I lose everything. some of the pages that load sometimes and not other times are google.com & com.au, ebay.com.au some links in ebay don't load, lot of overseas sites as well. can anyone help? Windows & virus scanner fully up to date. My ISP is no help at all said as long as mail page loads and emails thats as far as their support goes.

---

### Post by Asix on 2008-02-10
Oh, this post is really old, but I thnik I should say something anyway...
I've solved my problem by reinstalling Windows XP on that Windows machine, and then set up ICS again and then it worked perfectly. I don't know what was the cause, but thing are fixed now. 
Try reinstalling Windows and then try again. I didn't touch DNS configuration, though...

---

