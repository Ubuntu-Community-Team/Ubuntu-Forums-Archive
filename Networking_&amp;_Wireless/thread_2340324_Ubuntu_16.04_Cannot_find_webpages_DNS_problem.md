---
title: "Ubuntu 16.04 Cannot find webpages DNS problem?"
date: 2016-10-17
forum: Networking &amp; Wireless
---

### Post by aqk on 2016-10-17
On a desktop that dual-boots Windows-10 and Ubuntu 16.04, the Ubuntu system cannot resolve any urls.
i.e. if I type   google.ca  into a browser address bar, I get
  "Server not found"  from Firefox.
  "This site cannot be reached"   from Chromium.

On my laptop (this one) connected to the same router, I have no problem with Ubuntu 16.04

Presumably somewhere the nameservers are messed up.
When I boot into Windows I have no problem. As well, I have no problem with Skype on Ubuntu, and pings work OK.

What is the best way to proceed here? I've searched for several solutions and tried a couple of things, but most of these solutions seem to refer to  Ubuntu 13.10 or earlier, or a caveat appears "The networking has changed since Ubuntu 14.04" or some such warning.

Is there a ***CLEAR AND SIMPLE  SET*** of sudo edits, commands and queries that I can type in on UBUNTU **16.04 **that will get my DNS working properly?
Thanx.

---

### Post by ajgreeny on 2016-10-17
When you say pings work OK do you mean pings using names or only if using IPs?

For example, first **ping 216.58.212.110**
Does that work?
Now try **ping google.com** which is the named version of that IP.
Does that also work?

---

### Post by aqk on 2016-10-17
um..  I mean pings specifying IPs (and Tracerts specifying IPs)  work.
But obviously  Ping google.com  does not.  I have a nameserver or DNS problem.

---

### Post by ajgreeny on 2016-10-18
OK. In your panel click on the network icon and go to Edit connections.
Highlight your connection being used, cliock Edit again and on the IPv4 tab try using **Automatic (DHCP) Addresses only ** and in the **DNS Servers** box add **8.8.8.8,8.8.4.4**

Make sure you get the numbers and punctuation correct, ie, note particularly the comma in the middle following the forth 8.
Those are google's public DNS name server IP addresses and are a good place to start; they will allow you to figure out if it is a problem locally or with your ISP's DNS server setup.

---

### Post by aqk on 2016-10-18
Already tried that.  I ALWAYS use Google's  8.8...   DNS servers.
Well, sometimes I use OpenDNS at 208.67.222.222 and 220... but they have a habit sometimes of arbitrarily blocking some sites for peculiar reasons.

No, I suspect the problem is inside the network machinations of Ubuntu 16.04 - some tables have become corrupted. 

I just thought of something! -
I am using Windows right now, but I can boot this laptop into Ubuntu 16.04! 
And it accesses the Internet quite well.
Then, all I have to do compare the network stuff on this machine with the network stuff on the badly-behaving Ubuntu 16.04
I can even place this laptop right beside the offending system.

ADDENDUM- both machines connect to the router **via Wi-Fi.**  

 I suspect there is stuff in /etc  that is wrong. That's where all problems seem to happen!  ;-)
  But where to look and for what?.....

---

### Post by macu on 2016-10-18
I have the same problem with Ubuntu Gnome 16.10  
It helps to add a new profile in a Network manager and then switch to new created profile.

Or today i tried
```
sudo killall dhclient
```

and it helped me too...just try that if it will work for you

edit: I tried to use firefox or chromium and you are right, in both browsers it doesn't work properly (for me http sites are ok, but https doesn't work). But if I use chrome all sites there works....
I maybe report this bug in this thread, i will do it to when i will have time for that. It seams it is a same problem (but for me without suspending, but after boot)
[http://https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1633912]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1633912")

---

### Post by aqk on 2016-10-20
Thanx for the suggestion re   killall dhclient.  Maybe I will read up on it first before trying it.  KILLALL sounds ominous.
But after reading several threads about DNS problems, I **still think my problem lies somewhere in  /etc**  and its various networking subfolders.

Again -
Is there a CLEAR AND SIMPLE SET of sudo edits, commands and queries that I can type in on UBUNTU 16.04 that will get my DNS working properly?

---

### Post by promet on 2016-10-25
Hey aqk,

killall is pretty straight forward <i><b>if</b></i> you select the right process... ;)

```
 &::> man killall
```

---

