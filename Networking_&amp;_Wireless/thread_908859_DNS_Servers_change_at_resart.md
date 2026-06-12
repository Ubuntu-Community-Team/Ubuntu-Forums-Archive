---
title: "DNS Servers change at resart"
date: 2008-09-02
forum: Networking &amp; Wireless
---

### Post by HarrisonBP on 2008-09-02
For some reason, my DNS server IPs revert to their original values on restart.  Sometimes they even revert while my computer is on.  I have to use OpenDNS servers because otherwise I cannot get google.com or mail.google.com to load (strange, I can get google.cn, google.de and others to load just fine).  

It's been like this since I installed (1st time linux user).  It's not that hard to change them back, so I haven't tried to figure this out yet.

Thanks in advance.

---

### Post by HarrisonBP on 2008-09-07
Really now, 4 days, 25 views and no replies? You guys have helped me with tougher things, I know someone can figure this out.

---

### Post by HarrisonBP on 2008-09-07
.

---

### Post by fwre01 on 2008-09-07
"my DNS server IPs revert to their original values on restart"

Could you elaborate?

---

### Post by HarrisonBP on 2008-09-07
> **fwre01 said:**
> "my DNS server IPs revert to their original values on restart"

Could you elaborate?

Sure.  By default my DNS address was lets say: 

333.333.1.1  

For functionality purposes, I had to change this number to ones I got from OpenDNS.com, example:

333.22.333.331
333.22.333.332

Every time I reboot, these values are changed back to the default address, and I must again go into the DNS tab in my network settings and change them.

---

### Post by jwaiwit on 2008-09-07
Hmmm, from opendns.com they suggest to prepend dns to your old DNS. And DNS may changed by DHCP. :)

Hope this help?

---

### Post by fwre01 on 2008-09-07
its sounds astho its probably your DHCP server handing out different DNS addresses to your computer. Whats ur DHCP server?

---

### Post by HarrisonBP on 2008-09-07
how do I find my DHCP server?

---

### Post by darco on 2008-09-08
I had this issue myself..
First of all, make sure your router is also pointed to the OpenDns address...
Open this file... /etc/dhcp3/dhclient.conf
Scroll down to line 18 or so.

Add this line here:

prepend domain-name-servers 208.67.222.222,208.67.220.220;

thats it...

good luck 
darco

---

### Post by HarrisonBP on 2008-09-09
When I try this I get the message:

"Cannot save file /etc/dhcp3/dhclient.conf.
You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again."

What do I do?

---

### Post by darco on 2008-09-09
You need to be SU...try

```
 sudo nano /etc/dhcp3/dhclient.conf
```

darco

---

### Post by HarrisonBP on 2008-09-10
Okay, so this is what I get, what do I do from here?


 

 GNU nano 2.0.7         File: /etc/dhcp3/dhclient.conf               Modified  

# Configuration file for /sbin/dhclient, which is included in Debian's
#       dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#       man page for more information about the syntax of this file
#       and a more comprehensive list of the parameters understood by
#       dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#       not leave anything out (like the domain name, for example), then
#       few changes must be made to this file, if any.
#

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,

---

### Post by fwre01 on 2008-09-10
are you sure this is your DHCP server? are you using an adsl router?

---

### Post by darco on 2008-09-11
> **fwre01 said:**
> are you sure this is your DHCP server? are you using an adsl router?

dude, hes talking about changing his dns address in network manager and that every time he reboots it reverts back to the default dns address. Been there,done that.
So by following those  steps and adding that line, he will change the default dns to his choosing. He just needs to make sure his router is pointing to the same dns address.
If there are other ways, then explain the steps....

Harrison- see my previous post on your question "what do I do from here?"

good luck

darco

---

### Post by fwre01 on 2008-09-11
yes...i understand that

so, it sounds to me like its being over written every time his dhcp lease renews. so why not just change the lease to give him the correct information? instead of changing both. the point is, we dont know where the PC is receiving its leases from

---

### Post by lkjkhjsadfh on 2008-09-20
I'm not sure if the problem you are having is similar to what I was trying to correct on my own system but it seemed no matter what I (re)configured it would never use the OpenDNS ips but rather the DHCP-supplied DNS ips.

On a whim I removed the line 'usepeerdns' in /etc/ppp/peers/wvdial and restarted my connection and the OpenDNS servers are now being utilized.
Unsure if this will work for you as I don't know what connection type you are using.

---

### Post by sarahbearah on 2008-10-29
I had the same problem as HarrisonBP, and the prepend line in dhclient.conf fixed it.  (Thanks, jwaiwit and darco).  Harrison, I'm not sure from your posts if you got it to work, but for anyone else trying, there is already a line in the default /etc/dhcp3/dhclient.conf that says

#prepend domain-name-servers 127.0.0.1;

To make it work, erase the # symbol and replace 127.0.0.1 with your nameservers.  So it should look like

prepend domain-name-servers 333.22.333.331,333.22.333.332;

when you're done.  (comma separating them and a semi-colon at the end.)  Then save and quit, and things should work the next time you start networking.

---

