---
title: "Network Tools"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by scottishbloke on 2010-10-10
Hi folk's, Just discovered that the ping function using the network tools does not seem to be doing anything?

---

### Post by sandyd on 2010-10-10
> **scottishbloke said:**
> Hi folk's, Just discovered that the ping function using the network tools does not seem to be doing anything?
it shows if a web address is reachable.

i.e.
```

sandy@sandyd-laptop ~ $ ping google.com
PING google.com (173.194.33.104) 56(84) bytes of data.
64 bytes from lga15s14-in-f104.1e100.net (173.194.33.104): icmp_req=3 ttl=54 time=682 ms
64 bytes from 173.194.33.104: icmp_req=4 ttl=54 time=578 ms
64 bytes from lga15s14-in-f104.1e100.net (173.194.33.104): icmp_req=5 ttl=54 time=494 ms
^C64 bytes from lga15s14-in-f104.1e100.net (173.194.33.104): icmp_req=6 ttl=54 time=631 ms

--- google.com ping statistics ---
6 packets transmitted, 4 received, 33% packet loss, time 14894ms
rtt min/avg/max/mdev = 494.954/596.718/682.070/69.169 ms

```

my internet is VERY slow atm because im uploading 12 GB of stuff through  VPN, but you get the idea...

---

### Post by jtarin on 2010-10-10
Try ping from the terminal.

---

### Post by spiky001 on 2010-10-10
can you ping from terminal ok

---

### Post by scottishbloke on 2010-10-10
Yeah I can ping from the terminal but just wondering why I cant using the network tools?

---

### Post by jtarin on 2010-10-10
Mine works fine....make sure your using it correctly.

---

### Post by SpockVulcan on 2010-10-10
He isnt alone I have that same issue... ping works fine in Terminal but not in Network Tools

---

### Post by scottishbloke on 2010-10-10
Yep Its a weird one, And I know how to use It, It worked fine In Linux mint 9, Anyone any ideas? I'm all ear's?

---

### Post by NerdWermz on 2011-01-13
I'm on 10.10 and I'm having the same problem. Cannot seem to find anything on it, and yes I'm using it correctly.

---

### Post by uRock on 2011-01-13
Has anyone filed a bug report on this?

**Update:** This is a known bug. Please go to this link and click that it affects you. [https://bugs.launchpad.net/ubuntu/+source/gnome-nettool/+bug/663014](https://bugs.launchpad.net/ubuntu/+source/gnome-nettool/+bug/663014)

---

### Post by NerdWermz on 2011-01-13
Thank you for that.

---

### Post by uRock on 2011-01-13
You're welcome. It appears that the Gnome devs are working on it, so hopefully it'll get fixed soon. I use that tool often and was surprised when I found this thread and found that the tool was broken on my machine as well.

For the time being the ping tool in the terminal will have to suffice.

---

### Post by patrik k on 2011-01-13
Install Zenmap from Synaptic Package Manager and run from terminal- sudo zenmap
Excellent tool.

---

### Post by uRock on 2011-01-13
> **patrik k said:**
> Install Zenmap from Synaptic Package Manager and run from terminal- sudo zenmap
Excellent tool.
Indeed. Zenmap is one of my favorite tools. I used zenmap to test my laptops' firewalls before using them on public networks. Of course I only use it to test my Windows machines, as I trust UFW to protect my Ubuntu installs.

---

### Post by endotherm on 2011-01-13
so why does it work for some but not others? based on #7 in your bug report, the issue is with an unexpected token in the output making the output  string unparsable. 

is it reasonable to assume that your maveric box might return 
"64 bytes from 127.0.0.1: icmp_seq=3 ttl=64 time=0.169 ms"

and mine might return 
"64 bytes from 127.0.0.1: icmp_req=3 ttl=64 time=0.169 ms" ?

---

### Post by NerdWermz on 2011-01-18
> **patrik k said:**
> Install Zenmap from Synaptic Package Manager and run from terminal- sudo zenmap
Excellent tool.
Very cool tool.  thanks.

---

### Post by NerdWermz on 2011-01-18
> **patrik k said:**
> Install Zenmap from Synaptic Package Manager and run from terminal- sudo zenmap
Excellent tool.
Very cool tool.  thanks.

---

### Post by NerdWermz on 2011-01-18
> **patrik k said:**
> Install Zenmap from Synaptic Package Manager and run from terminal- sudo zenmap
Excellent tool.

Very cool. thank you.

---

### Post by scottishbloke on 2011-04-10
Right I have found this thread at last, Now this bug Is still not fixed yet, Why Is that?

---

### Post by jtarin on 2011-04-10
> **scottishbloke said:**
> Right I have found this thread at last, Now this bug Is still not fixed yet, Why Is that?What version of Ubuntu are you running? It seems to be broke in my Lucid where it had worked before. I'm suspecting an update of some other package broke it.

---

### Post by scottishbloke on 2011-05-01
I'm using Linux mint 10 which Is the same pretty much as ubuntu. Not working In 11.04 either, Must not be top priority.

---

### Post by uRock on 2011-05-01
> **scottishbloke said:**
> I'm using Linux mint 10 which Is the same pretty much as ubuntu. Not working In 11.04 either, Must not be top priority.

IIRC, Network Tools is not maintained by Canonical.

---

### Post by scottishbloke on 2011-05-03
Well that would make sense I suppose as to why Its broken the last couple of releases, Back to windows for me, I really need tools that work.:cry::cry:

---

### Post by jtarin on 2011-05-03
> **scottishbloke said:**
> Well that would make sense I suppose as to why Its broken the last couple of releases, Back to windows for me, I really need tools that work.:cry::cry:
What's the problem? Move up to Zenmap. Network Tools and more :rolleyes:

---

### Post by uRock on 2011-05-03
> **jtarin said:**
> What's the problem? Move up to Zenmap. Network Tools and more :rolleyes:

Especially when ping is the only thing broken in the Network Tools app.

---

