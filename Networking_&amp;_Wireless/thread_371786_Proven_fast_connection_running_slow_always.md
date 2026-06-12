---
title: "Proven fast connection running slow always"
date: 2007-02-27
forum: Networking &amp; Wireless
---

### Post by robacarp on 2007-02-27
Hello!

I have a computer that dual boots XP and Ubuntu Edgy connected to the internet through a Cable Modem.  I have run Ubuntu for a while now and started to notice that when I browse the web from ubuntu  my speed is slow slow.  I can immediatly reboot into windows and find that the speed of the internet is lightning fast.

I know that there are some more advanced settings in windows TCP/IP networking and such that can be used to take advantage of all that a high speed connection can offer --  I didn't do these -- but is there something similar that I can do to my Ubuntu installation?

I also have not installed anything on windows designed to speed up an internet experience (google has some of this software called accelerator I think....it usually uses a local proxy server).

Lastly I am using OpenDNS on both OS's for consistency.

---

### Post by EtniesBMX on 2007-02-27
I am having the exact same experience. Anyone else?

---

### Post by robacarp on 2007-02-27
Yay! I'm not crazy!

---

### Post by HarmonicaGoldfish on 2007-02-27
I am having the same issue. I hope someone can shed some light on this for us!

---

### Post by mitype2 on 2007-02-28
I have 10 meg service with Charter and my internet connection has slowed down big time since I made the switch over to Linux. It's like 384 kbps dsl again. When I had windows my internet flew but with Ubuntu my speed is terrible. Any help out there?

Sorry I jumped your thread Robacarp mybad.

---

### Post by HarmonicaGoldfish on 2007-03-01
I have sped up my slow internet with the instructions on this page:

[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4)

I followed the instructions for the mozilla web browser, restarted the browser, and had immediate results. 

I hope this works for you.

---

### Post by robacarp on 2007-03-03
thanks....its faster now...not all the way, but faster.  I'm going to disable the entire ipv6 ability and reboot.

---

### Post by slimdog360 on 2007-03-03
yep, the ipv6 thing does it, Ive also found that using opera makes loading pages faster again.

---

### Post by TwistesdTexan on 2007-03-03
Thanks. I had a recent update of Firefox and my configuration was changed and ipv6 was enabled. I went to about:config and filtered to ipv6 and made the sure it was disabled. This didn't disable all of the ipv6 functions seen when you type "ip a | grep inet6". So i went to edit my blacklist by typing at a terminal " sudo gedit /etc/modprobe.d/blacklist". I added the following lines to the end of the list without the quotes.
"# speeds up internet connection"
"blacklist ipv6"
The first line is to remind me of the reason for the second line. The second line is to blacklist the ipv6 feature. Now when I type "ip a | grep inet6" the return is nothing but a new line. I thought this might help someone else.

---

### Post by EtniesBMX on 2007-03-04
Doing this sovled my problem too. Thanks!:-D

---

