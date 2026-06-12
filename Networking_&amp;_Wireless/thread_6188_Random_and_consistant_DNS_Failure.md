---
title: "Random and consistant DNS Failure"
date: 2004-11-25
forum: Networking &amp; Wireless
---

### Post by WildCode on 2004-11-25
Before I start, I did follow the dns failure howto listed when you search the forums for "dns".

I am having random but consistant dns failures with ubuntu 4.10.

I followed the install process (got it installed the 3rd time after the 1st and 2nd time failed) and allowed ubuntu to update itself. I also installed fglrx and the 2.6.8-k7 packages supplied by ubuntu's apt repository.

The issue I am having is that ubuntu is failing most time from boot to resolve hostnames. connection to the outside using IP addresses works fine.

The network setup as follows, windows and ubuntu machine connect to a hub which si then connected to an ADSL router/modem which handles dhcp, dns and nat for the network.

Windows machines have no problem with dns even at the same time ubuntu dns is failing.

I followed the dns failure howto and installed resolvconf pump and dnsmasq as stated in the howto (when dns mysteriously worked), and reset the networking, but to no avail. A few minutes after dns failed again. when it fails it rarely comes back up leaving me to reboot constantly till dns works again.

checking the md5sum of the working resolv.conf (when dns is working) to the resolv.conf when dns is failing shows no difference. There is absolutly nothing in the logs that shed any light on this problem.

This has been goingon for days now, and when dns has been working, I've done apt-get update and upgrade in the hope that some package upgrade will fix the problem, but it persists.

Can anyone please give me a solution to this problem.

Once again, before I get asked, windows machines dns  work without issue using the modem/router as the dns server when ubuntu is having issues repeatedly . So its not an issue with a failing dns.

---

### Post by Swab on 2004-11-26
Login to your modem/router and get the DNS server IP addresses from there.  Then add those servers to your DNS tab on the Ubuntu networking utility.  Might work!

---

### Post by bob k on 2004-11-26
[QUOTE=WildCode]Before I start, I did follow the dns failure howto listed when you search the forums for "dns".

I am having random but consistant dns failures with ubuntu 4.10.

I followed the install process (got it installed the 3rd time after the 1st and 2nd time failed) and allowed ubuntu to update itself. I also installed fglrx and the 2.6.8-k7 packages supplied by ubuntu's apt repository.

The issue I am having is that ubuntu is failing most time from boot to resolve hostnames. connection to the outside using IP addresses works fine.

The network setup as follows, windows and ubuntu machine connect to a hub which si then connected to an ADSL router/modem which handles dhcp, dns and nat for the network.

Windows machines have no problem with dns even at the same time ubuntu dns is failing.

I followed the dns failure howto and installed resolvconf pump and dnsmasq as stated in the howto (when dns mysteriously worked), and reset the networking, but to no avail. A few minutes after dns failed again. when it fails it rarely comes back up leaving me to reboot constantly till dns works again.

checking the md5sum of the working resolv.conf (when dns is working) to the resolv.conf when dns is failing shows no difference. There is absolutly nothing in the logs that shed any light on this problem.

This has been goingon for days now, and when dns has been working, I've done apt-get update and upgrade in the hope that some package upgrade will fix the problem, but it persists.

Can anyone please give me a solution to this problem.

Once again, before I get asked, windows machines dns  work without issue using the modem/router as the dns server when ubuntu is having issues repeatedly . So its not an issue with a failing dns.[/QUOTE]
 Does the hub have an IP address. (is it a smart hub or a pass thru)

---

### Post by mdr on 2004-11-26
as a wild guess I would suggest this is more the slow IPv6 issue rather than an actual dns issue.
i.e. firefox is very slow and stuck on resolving dns.

see this thread...
[http://ubuntuforums.org/showthread.php?t=3699&highlight=iPv6](http://ubuntuforums.org/showthread.php?t=3699&highlight=iPv6)

apply the about:config change to firefox - it then works a treat.
did for me behind my adsl router / modem.

---

### Post by WildCode on 2004-11-26
[QUOTE=bob k]Does the hub have an IP address. (is it a smart hub or a pass thru)[/QUOTE]

its a pass through hub. ie: the hub is invisable to the network.

---

### Post by WildCode on 2004-11-26
[QUOTE=mdr]as a wild guess I would suggest this is more the slow IPv6 issue rather than an actual dns issue.
i.e. firefox is very slow and stuck on resolving dns.
[/QUOTE]

This is not limited to firefox, applications effected are any that use dns, including, but not restricted to, apt-get, xchat, ntp-update, ping, traceroute, firefix, lynx, dig, ...

---

### Post by WildCode on 2004-11-26
[QUOTE=Swab]Login to your modem/router and get the DNS server IP addresses from there.  Then add those servers to your DNS tab on the Ubuntu networking utility.  Might work![/QUOTE]

nope, this just changes the resolv.conf, and changing anything in there doesn't work either.

---

### Post by arctic on 2004-11-26
install the following packages via apt-get (if necessary, open a new terminal and ping your repositories (e.g. "ping [www.blablabla.com](www.blablabla.com)):

resolvconf
pump
dnsmasq

in case of a laptop, install "laptop-net", too.

---

### Post by WildCode on 2004-11-26
[QUOTE=arctic]install the following packages via apt-get (if necessary, open a new terminal and ping your repositories (e.g. "ping [www.blablabla.com](www.blablabla.com)):

resolvconf
pump
dnsmasq

in case of a laptop, install "laptop-net", too.[/QUOTE]

If ya read my original message you'd know I've already done that, but the problem still persists.

---

### Post by arctic on 2004-11-27
ooops...
sorry, i gotta read more carefully :D
try the following:
type in a terminal:

sudo echo "net.ipv4.tcp_window_scaling=0">> /etc/sysctl.conf

---

### Post by WildCode on 2004-11-27
[QUOTE=arctic]ooops...
sorry, i gotta read more carefully :D
try the following:
type in a terminal:

sudo echo "net.ipv4.tcp_window_scaling=0">> /etc/sysctl.conf[/QUOTE]

hmm, sorry, didn't help.

I double checked and ifconfig shows the network card with the same ip (ipv4)address as the dhcp server gives it in windows, and ip (ipv4) addresses are accessable, but not hostnames. Hostnames definitly work in the lan with the windows machines, including the same machine as ubuntu when booted into windows.

There are no errors/warnings/entries in logs that could help.

---

### Post by arctic on 2004-11-27
have you tried disabling your network, setting new dns-entries to your /etc/resov.conf and reactivating your network after applying the above mentioned changes? try it once again... if that does not work, i dunno what can be done other than using a 2.4.20+ kernel...

---

### Post by WildCode on 2004-11-27
[QUOTE=arctic]have you tried disabling your network, setting new dns-entries to your /etc/resov.conf and reactivating your network after applying the above mentioned changes? try it once again... if that does not work, i dunno what can be done other than using a 2.4.20+ kernel...[/QUOTE]

:/ yeah I tried that ... looks like I'll be stuck with 2.4 :/

---

### Post by LongCat5e on 2005-11-02
I'm also having this problem.

Everything works, except for DNS - I even got apt-get to work by using a windows box to resolve the domain names and manually entering the IP addresses.

I've rechecked the configurations about 7 times - they all work on machines that aren't running Ubuntu 5.10

I can provide any information about the systems that you may need, as long as you can tell me how to find it. ;)

---

### Post by ahlandberg on 2007-03-26
> **Swab said:**
> Login to your modem/router and get the DNS server IP addresses from there.  Then add those servers to your DNS tab on the Ubuntu networking utility.  Might work!

Thank you so much for this posting!

It fixed my problem that caused me headaches!!

Cheerio, Anders

---

