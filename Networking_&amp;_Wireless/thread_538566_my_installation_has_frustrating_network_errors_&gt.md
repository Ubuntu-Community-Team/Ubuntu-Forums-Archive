---
title: "my installation has frustrating network errors &gt;.&lt;"
date: 2007-08-30
forum: Networking &amp; Wireless
---

### Post by CC_machine on 2007-08-30
**Ubuntu on my laptop has had some wierd networking problems lately. whenever i connect to any wifi network, I get no internet or networking. (this occasionally happens through a wired cat5 also). I tried running a bunch of commands, heres the output:**


ping google.com
unknown host: google.com

**so at this point I thought it was a DNS error, so i tried an ip:**

ping 192.168.1.1
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
ping: sendmsg: Operation not permitted
[keeps repeating forever...]

As you can probably guess, Firefox gives the usual "Server not found" if I try to use the web. >_>

In Windows, the network works flawlessly. So i put in my Ubuntu CD and low and behold, it also works great running live! The network in question at the moment is a WPA encrypted wifi network, but Windows and Ubuntu Live can both use a local linksys open network (no encryption), while my Ubuntu installation can connect, but the above errors :(

I tried right clicking on network-manager on my panel and going to "Connection Information", but Ubuntu Live and my installation show the exact same info! (note: the signal strength is shown to be well over 80% on both, so it should work :( )

Then when i went into my Ubuntu installation once, This dialog appears:
"Please contact your system administrator to resolve the following problem:
SIOCGIFFLAGS error: No such device". All i can do is click OK.:confused:

laptop specs:
Dell Inspiron 6400
Intel 3945 a/b/g wireless for core 2 duos
Core 2 Duo 1.73ghz
1GB ddr2 ram
Intel 950 graphics

thanks in advance if anyone can help, I really want to fix this :(

---

### Post by dmizer on 2007-08-30
did you install an iptables gui front end (firewall) like shorewall or firestarter?

post the output of:
```
sudo iptables -L INPUT
```

try stopping your firewall and retry your ping.  i'm betting that you've got an incorrectly configured iptables.

---

