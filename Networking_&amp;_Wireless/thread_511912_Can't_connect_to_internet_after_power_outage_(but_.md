---
title: "Can't connect to internet after power outage (but Windows still can)"
date: 2007-07-28
forum: Networking &amp; Wireless
---

### Post by Chuckanut on 2007-07-28
This is an odd one and my lack of Linux experience has me lost.

The setup:
2 identical computers, one with Ubuntu Edgy and one with Win 2k
Both wired to a NetGear router
The NetGear is wired to an Actiontec DSL modem

Everything was working fine until 2 days ago, when our power went out for a minute.  Both computers are on a UPS and neither shut down, although the router and modem may have.  Now Ubuntu can't connect to websites, but Windows can.  Here's where it gets weird: Ubuntu can connect to the Win 2k system and swap files, Ubuntu is seen by the router and modem, and Ubuntu can successfully ping outside IP addresses.  But when I try to connect to anything on the net (browser, email, finances) it just hangs and eventually times out.

In Firefox, when I try to connect I can see the status bar show 'Looking up...', the status indicator goes to about half way, it shows 'Connecting to....' and it just hangs there.  I get the same results even if I enter the address as a valid IP address.  This should bypass any DNS issues, and it's obviously getting onto the web, so WTF???

I've tried disabling the DHCP and re-enabling it, both with and without rebooting, but that's about all I know how to do in Linux.  My Windows PC is still working just fine, so it can't be anything too complex.  Any thoughts/ideas/suggestions??

Thanks
Tom

---

### Post by noob12 on 2007-07-28
OK.  It sounds vaguely like the NAT state of the router is hosed in a way that the TCP masquerading is failing but your ICMP pings are going through.  I would suggest **power cycling the router**, then once that is up and ready ```
/etc/init.d/networking restart
``` on the Ubuntu box.

---

### Post by noob12 on 2007-07-28
Additional thing to check if the prior suggestions don't work.  Do you have a proxy configured in Firefox?
In Firefox goto **Edit  | Preferences | Advanced | Network | Connection | Settings ...  **
Make sure Direct Connection is selected (assuming you aren't trying to use a proxy).

---

### Post by Chuckanut on 2007-07-28
Noob,
Thanks for the suggestions, but it didn't work.  And there's no proxy set up.

I should elaborate on what I've done so far:
Power cycled both the router and DSL modem
With Administration | Networking, I've set manual IP, Gateway, etc., enabled/disabled/reenabled DHCP
I've directly accessed both the router and DSL modem and verified all the IP settings and that they both see Ubuntu.  (they do)

This is nuts, it's weird I can ping the outside world, I just can't connect to it.  Getting frustrating, too!

Tom

---

### Post by noob12 on 2007-07-29
A few additional things could help diagnose issues.
Please post the output to the following two

> 
ifconfig -a


> 
route -n


And also try a command-line web client like wget:

> 
sudo aptitude install wget


and then, **preferably in a new empty directory**

> 
wget [http://www.yahoo.com](http://www.yahoo.com)


---

### Post by noob12 on 2007-07-29
Let me add one more
```

cat /etc/nsswitch.conf

```

---

### Post by Chuckanut on 2007-07-30
Noob,
Sorry to take so long, lots of family stuff to do this weekend.

I have no idea what happened, but now it works fine.  I made no changes, just left it running the last few days.  I love random problems, they make life so much more interesting!

Thanks for your help, hopefully this was one time issue.

Tom

---

