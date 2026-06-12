---
title: "scp and rsync stall when transferring from Ubuntu hardy heron 8.04"
date: 2008-08-16
forum: Networking &amp; Wireless
---

### Post by Vermind on 2008-08-16
Hi,
After I upgraded to Hardy, it seems that scp and rsync no longer transfer files properly. Scp stalls somewhere after 2000KB, and rsync stalls after a few files, I haven't determined the limit. The issue could be fixed from my workplace's environment by a reduced --bwlimit with rsync, but from another location I cannot transfer files reliably either to, or from, my Hardy desktop, when the other end is also a Hardy computer.

I am seeing this:
```
$ scp gdm-themes.tar.gz drache:dev/.
gdm-themes.tar.gz                              28% 2112KB   1.7MB/s   00:03 ETA
gdm-themes.tar.gz                              33% 2448KB   0.0KB/s - stalled -

```

I read about a workaround by setting a lower MTU on the interface in question, but it did not help.
I also tried playing around with the MTU values using:
sudo ping -f -v -c 10 -s somenumber target.host.name
and it appeared I get packet loss (20-30%) on all mtu values, except values exceeding 3000 (which does not make sense since I can't set that on my wireless interface, 2200 seems to be the maximum).

Further research into this has yielded no positive results. I went and downloaded the newest [OpenSSH 5.1]("http://www.openssh.com/portable.html"), compiled and installed it, to no avail; transfers from this computer still stall. I am fairly certain it is not the ssh. This occurs on both of my Ubuntu 8.04 machines: My 64-bit desktop, which is using the 8139too network module for an RTL network card, and my laptop, which uses atheros-based wireless.

My desktop had wondershaper installed. I removed it to see if that was causing the problem, but the problem remains.

Has anyone else run into this? any other workarounds?
Thanks.

---

### Post by steve c on 2008-09-23
I am seeing this as well, at least with scp. I haven't tried rsync. Unfortunately, I have no work around.

---

### Post by willca on 2008-09-23
I had similar transfer problems with my wifi. Try adding this at the end of your /etc/sysclt.conf and then reload it via sysclt -p

net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1

---

### Post by Vermind on 2008-09-23
Hello,
thank You very much, willca!
This fixes it. No stalls with scp, at least on the local network. I am getting stuff at 1.6MB per second, and successfully transferred a 300MB file. Wider testing to take place later.

Thanks again!

---

### Post by steve c on 2008-09-27
> **willca said:**
> I had similar transfer problems with my wifi. Try adding this at the end of your /etc/sysclt.conf and then reload it via sysclt -p
This didn't change anything for me. My transfers still fail at 2064 kB.

---

### Post by Vermind on 2008-09-27
steve c, I just noticed the same. A transfer uploaded from my server still stalled. This was after a reboot from the original fix, so, I said sysctl -p, and tried again. It did not stall. Seems that my sysctl is not being loaded properly at startup. How about you? Does this help?

---

### Post by steve c on 2008-09-27
> **Vermind said:**
> steve c, I just noticed the same. A transfer uploaded from my server still stalled. This was after a reboot from the original fix, so, I said sysctl -p, and tried again. It did not stall. Seems that my sysctl is not being loaded properly at startup. How about you? Does this help?
I'm afraid not. I didn't reboot. I can't imagine why /etc/sysctl.conf wouldn't be read at boot though. You sure that running sysctl -p after boot actually changed something?

Maybe try restarting and running
```
sysctl -a > pre
sysctl -p
sysctl -a > post
diff -u pre post
```
and see if the settings are actually different.

---

### Post by Vermind on 2008-09-27
Transfers do not stall on my machine. They are much faster at times as well. Sysctl gets loaded on bootup, but BEFORE the net module, and that is why the sysctl net settings "went to waste". So I added net to /etc/modules, and everything is perfect now.

I am marking this thread unsolved since steve c still has the same issue.

Steve c, which other fixes/workarounds have you tried? Changing default ssh config (GSSAPI auth and some other things), changing interface MTU, others?
I found that setting a bandwidth limit on scp did the trick when my transfers were stalling. I had approx a 200KB upload rate, so I set the scp limit to 1600. Are You having a problem getting files through at all, or through conveniently? is the "From" machine the one whose sysctl settings you were adjusting?

---

### Post by steve c on 2008-09-27
> **Vermind said:**
> Transfers do not stall on my machine. They are much faster at times as well. Sysctl gets loaded on bootup, but BEFORE the net module, and that is why the sysctl net settings "went to waste". So I added net to /etc/modules, and everything is perfect now.
Ah, okay. I wasn't aware that it would be affected by ordering like that.

> Steve c, which other fixes/workarounds have you tried? Changing default ssh config (GSSAPI auth and some other things), changing interface MTU, others?
I tried changing the MTU on some other advice that I read. I tried 1490, it had no impact. I haven't tried changing the ssh configuration since it isn't limited to ssh for me. HTTP transfers seem to be equally stalled. Downloading updates via the update manager also stalled. I started some update yesterday and went away for 6 hours. It still wasn't finished when I got back. (Admittedly not a solid data point since I don't happen to recall how large the files were.)

> I found that setting a bandwidth limit on scp did the trick when my transfers were stalling. I had approx a 200KB upload rate, so I set the scp limit to 1600.
I just tried that. The result was that it went much slower up to 2064 kB and then stalled.

> Are You having a problem getting files through at all, or through conveniently? is the "From" machine the one whose sysctl settings you were adjusting?
What happens is when I transfer to my ubuntu machine, it stalls at 2064 kB. After a while, it will resume extremely slowly before stalling again. This continues until the file is eventually transferred.

Transferring from the ubuntu machine seems to work much better. It still stalls, but at different points and it seems to recover more quickly and transfer more before stalling again.

This doesn't happen between my other computers on the same network, just the one running ubuntu. This didn't use to happen either. Unfortunately, since I don't typically transfer large files to or from the machine apart from system updates, I can't say exactly when this started happening, but certainly some point after I installed Hardy. (I wonder if it could be a new kernel I installed at some point.)

Thanks for all of your help.

---

### Post by steve c on 2008-09-27
Oops, I didn't answer one of your questions. I was changing the sysctl settings on the ubuntu machine.

---

### Post by Vermind on 2008-09-28
steve c, yours seems to be a different issue. Mine occurred only on transfers originating from the Ubuntu host, and only when SSL was used with the transfers. tla versioning system commits (large ones), rsync transfers, and scp transfers were stalled. If I put files in my HTTP share folder, they could be downloaded by others without problems. If I transferred files using netcat, they could be transferred as well. Transfers using Skype and msn also succeeded. There never was a problem with update downloading.

---

### Post by steve c on 2008-09-28
Perhaps so. I've never seen scp stall before so I assumed it was the same as your issue.

---

### Post by Ubuntu Warrior on 2008-09-30
At the risk of sounding very pessimistic here, the fact that rsync doesn't work properly on Ubuntu is a MAJOR issue. We currently use rsync to back up our Zimbra files hosted on an Ubuntu 6.10 server but it seems to arbitrarily leave out some files. Permissions are correct and doing a tar on the files works fine.

We tried to use scp but this also had problems in reliably transferring files across systems.

Suppose I don't need to highlight that the reliable transfer of business information is critical to an enterprise solution.

At this stage we have been forced back onto a Sun Solaris box until we can sort this issue.

Any ideas? :confused:

---

### Post by vhex on 2008-09-30
> **willca said:**
> I had similar transfer problems with my wifi. Try adding this at the end of your /etc/sysclt.conf and then reload it via sysclt -p

Thank you SO MUCH!

---

### Post by Vermind on 2008-10-08
Hello,
It appears stalls are occurring again when I transfer to the University Linux server. When I first tried the suggested net modifications, transfers there did not stall. Something is wrong...

---

### Post by steve c on 2008-10-09
Well, you can chalk my problems up to my switch dying. Apparently the few different ports I tried in my tests had all failed while the others were working so it seemed like not a switch problem.

When different symptoms appeared on my other machines (not running ubuntu), I noticed that setting my speeds from 1000baseT to 100baseT caused a significant speed up, but it was still slow. Wireshark showed a large number of duplicate tcp packets being sent. I pulled the switch out of the network and replaced it with a slower router and now my network issues have disappeared.

Thanks for all of the help and my apologies for wasting your time.

---

### Post by MartijnNL on 2008-12-17
One thing: if you're using Firestarter (firewall), that might cause the problem.

There's something about that problem here:

[https://help.ubuntu.com/community/Firestarter#Stalled%20connections](https://help.ubuntu.com/community/Firestarter#Stalled%20connections)

The solution in that article didn't solve the problem for me. Uninstalling firestarter did. Just switching firestarter off is not enough. I'll go try ufw.

---

### Post by detroit/zero on 2009-05-22
> **willca said:**
> I had similar transfer problems with my wifi. Try adding this at the end of your /etc/sysclt.conf and then reload it via sysclt -p

net.core.rmem_default = 524288
net.core.rmem_max = 524288
net.core.wmem_default = 524288
net.core.wmem_max = 524288
net.ipv4.tcp_wmem = 4096 87380 524288
net.ipv4.tcp_rmem = 4096 87380 524288
net.ipv4.tcp_mem = 524288 524288 524288
net.ipv4.tcp_rfc1337 = 1
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.tcp_sack = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_ecn = 0
net.ipv4.route.flush = 1
Worked for me.. Thanks!

I have two computers on a home network and am constantly moving files between them. I upgraded one to Jaunty not so long ago, and have been having problems with scp transfers ever since. I also noticed that ssh sessions from one to the other would periodically freeze.

It's a little early to be certain, but I just added those lines to the end of sysctl on both systems and now everything seems to be going OK.

Thanks again!

---

### Post by Vermind on 2009-05-22
For me, this was fixed in Jaunty.

---

### Post by caue.rego on 2009-05-25
for me, the MTU thing from 1500 to 1490 fixed the issue in Jaunty.

---

### Post by dennisn on 2010-06-04
I wish someone could tell us what "Jaunty" did to "fix" this problem. I don't use Ubuntu, but I probably have this problem? It's REALLY annoying.

For me, I seem to have gotten it working by changing those aforementioned sysctl's AND changing my network device MTU's to 2200 (nothing lower seemed to work; (ifconfig wlan0 mtu 2200))

But I still don't feel satisfied -- not only don't I know what the problem was, but the "solution" seems like a hack :\.

---

### Post by dennisn on 2010-06-04
My dissatisfaction was proven correct. After rebooting my client, (and possibly restarting the network interface on the server too), I can't get it to work, even following the same steps as before, which did seem to work. Aaaarrrrgggghhhh.

Here are some clips of an earlier tcpdump I took during the stall, maybe someone can see something informative:
[http://dennisn.dyndns.org/guest/pubstuff/scp-stalls/](http://dennisn.dyndns.org/guest/pubstuff/scp-stalls/)

---

### Post by michelino80 on 2012-10-21
Hi all, this thread is pretty old, but the problem may still be around, as, at least for me, it is not caused by ubuntu itself.

Basically, every "hop" between you and the server will open and re-incapsulate the packets and with the incorrect mtu settings, they will never reach the destination.

The list of MTUs between you and the destination (ie: your MTU, the MTU of your access point, the MTU of your modem, the MTU of all the exchange routers until the destination, ..) should be a monotonic increasing function, for the packet to arrive at your destination.

Put in other words, this is a sequence of MTU settings that will work:
1) your network card MTU: 1492
2) your access point MTU: 1492 or 1500
3) your modem MTU: 1500

This is a sequence of MTU that will NOT work:
1) your card MTU: 1500
2) your access point MTU: 1492
3) your modem MTU: 1500

as all the packets will be discarded between 1 and 2. I had X on my operating system, 1500 on my access point and 1492 on my modem, and speedtest.net was not working in upload. I changed my access point to have a 1492 MTU and now everything works fine.

I hope this may help someone.

cheers
mic

---

### Post by dennisn on 2012-10-21
> **michelino80 said:**
> 
as all the packets will be discarded between 1 and 2. I had X on my operating system, 1500 on my access point and 1492 on my modem, and speedtest.net was not working in upload. I changed my access point to have a 1492 MTU and now everything works fine.

I think that's a different problem. With this bug, transfers do begin, but stall. It's been a long time since I last saw it (perhaps it's already been fixed in the kernel or something), but it only happened on my LAN with fast ethernet transfers.

---

