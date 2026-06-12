---
title: "DNS Flush in Maverick"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by mlnease on 2010-10-21
Hello,

I've been having a baffling problem in Maverick (which has otherwise performed flawlessly, thanks, Devs!)

I connect fine to everything on the Internet--except to my account at my ISP.  I can connect to my email account neither via Thunderbird nor via Firefox.

I have Lucid installed on another partition and it connects normally via both Thunderbird and Firefox.

I've troubleshot this extensively with a tech at my ISP.  At one point he suggested DNS flushing.  So I installed nscd and followed with 'sudo /etc/init.d/nscd restart'.  No luck.  Then I restarted Maverick and, hey presto! I could connect.

When I logged on today, I had the same problem, ran 'sudo /etc/init.d/nscd restart' again--no luck--restarted and I could connect again.

So it seems that every time I want to connect to my email, I have to run 'sudo /etc/init.d/nscd restart' and then restart the computer.

Any ideas?  I'd greatly appreciate any advice.

Thanks in Advance,

mike

---

### Post by spikoley on 2010-10-21
I am not sure what the solution is, but you could try switching your DNS.  Try [OpenDNS]("https://store.opendns.com/setup/device/ubuntu/") or [Google's DNS]("http://code.google.com/speed/public-dns/docs/using.html").

OpenDNS
> To avoid having your settings get revoked after reboots, or after periods of inactivity you may need to make the following changes via the command line:
$ sudo cp /etc/resolv.conf /etc/resolv.conf.auto
$ gksudo gedit /etc/dhcp3/dhclient.conf
# append the following line to the document
prepend domain-name-servers 208.67.222.222,208.67.220.220;
# save and exit
$ sudo ifdown eth0 && sudo ifup eth0
You may be required to change eth0 to your own network device's name if it uses a non-standard name.

For Google's DNS use the directions above, but with these IP addresses: 8.8.8.8 & 8.8.4.4

If that doesn't solve it then post the results of a ping to the site and the IP address.

---

### Post by mlnease on 2010-10-21
Spikoley, Dude!

> **spikoley said:**
> I am not sure what the solution is, but you could try switching your DNS.  Try [OpenDNS]("https://store.opendns.com/setup/device/ubuntu/") or [Google's DNS]("http://code.google.com/speed/public-dns/docs/using.html").

Been using Open DNS for years--I'll try the code and post the results.

OpenDNS


For Google's DNS use the directions above, but with these IP addresses: 8.8.8.8 & 8.8.4.4

If that doesn't solve it then post the results of a ping to the site and the IP address.

Thanks!

---

### Post by mlnease on 2010-10-21
> **spikoley said:**
> I am not sure what the solution is, but you could try switching your DNS.  Try [OpenDNS]("https://store.opendns.com/setup/device/ubuntu/") or [Google's DNS]("http://code.google.com/speed/public-dns/docs/using.html").

OpenDNS


For Google's DNS use the directions above, but with these IP addresses: 8.8.8.8 & 8.8.4.4

If that doesn't solve it then post the results of a ping to the site and the IP address.
[SOLVED]
Hey presto--thanks again!

---

### Post by spikoley on 2010-10-21
I am glad to hear it worked.  To mark it solved go to Thread Tools and click Solved.

---

