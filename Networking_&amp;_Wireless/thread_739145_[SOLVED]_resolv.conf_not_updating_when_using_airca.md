---
title: "[SOLVED] resolv.conf not updating when using aircard"
date: 2008-03-29
forum: Networking &amp; Wireless
---

### Post by MikeyXX on 2008-03-29
When I use my wireless, the resolv.conf gets updated fine, when I switch to wired, it gets updated fine. However, when I don't use either but use my aircard, I can't get to the internet until I manually edit my resolv.conf to update the dns information that I get via my pppd information. 

Any ideas what would cause this?

---

### Post by superprash2003 on 2008-03-29
the resolv.conf works only when DHCP is enabled.. you might want to edit this file /etc/dhcp3/dhclient.conf

---

### Post by MikeyXX on 2008-03-31
Will do, what am I looking for?

---

### Post by stream303 on 2008-03-31
You may want to try putting your ISP's primary and backup dns server addresses in the router's setup page directly.  Or you can use another dns server, such as those from OpenDNS.com

Putting the dns server addresses into my router directly has solved more issues like this than I can count, especially on mixed-os environments living behind a router...

---

### Post by MikeyXX on 2008-04-01
Good points, but remember, I'm using an Aircard, not a wireless card. When I switch to wireless I get the DNS entries no problem. When I switch to Aircard the resolv.conf doesn't update with the 10.x.x.x dns entries that the wvdial results indicate is offered. If I manually put them in the resolv.conf I get DNS working fine. 

I even looked and the dhclient.conf does ask for the domain-name-server. So I don't know why it's not taking.

---

### Post by chilinski on 2008-04-03
> **MikeyXX said:**
> Good points, but remember, I'm using an Aircard, not a wireless card. When I switch to wireless I get the DNS entries no problem. When I switch to Aircard the resolv.conf doesn't update with the 10.x.x.x dns entries that the wvdial results indicate is offered. If I manually put them in the resolv.conf I get DNS working fine. 

I even looked and the dhclient.conf does ask for the domain-name-server. So I don't know why it's not taking.

The prepend line in dhclient.conf handles that.

---

### Post by MikeyXX on 2008-04-03
This is what my chclient.conf looks like. My prepend line is edited out.

```
send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope;
#require subnet-mask, domain-name-servers;
timeout 30;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}
```

I'm not sure how to read this. I see that it's requesting
- request subnet-mask, 
-broadcast-address, 
-time-offset, routers,
-domain-name, 
-domain-name-servers, 
-host-name,
-netbios-name-servers,
- netbios-scope;

---

### Post by MikeyXX on 2008-04-03
Ok, I edited the file and put two lines "prepend domain-name-server x.x.x.x" "prepend domain-name-server y.y.y.y"

And then I started the aircard and..... nothin. Still didn't change my resolv.conf. It only is listing my past dns listing from my wireless router (wireless is turned off).

---

### Post by stream303 on 2008-04-04
Here's a couple of things that got me when used to manually edit them - not sure if you are making the same mistake as me, but I'll toss it out just in case...

```

#prepend domain-name-servers 127.0.0.1;
```

What I used to blow all the time when editing, was to be sure I was using the plural of "servers", rather than "server".

In the case of multiple dns addresses, I just separated them with a comma, but often forgot to put a semicolon at the end.  Here's an example with fake dns addresses:

```
prepend domain-name-servers 123.45.678,345.67.890;
```

Thought I'd just check to see if any typos might be creeping in....

---

### Post by MikeyXX on 2008-04-16
Oh, I just did two prepend commands.


The drawback is that it's going to check the prepended DNS first, get denied and then go to whatever dhcp appended to the back end when on wired or wireless. But oh well, can't have it all.

---

### Post by chilinski on 2008-04-16
You can use the "append" command instead of "prepend" if you want the servers listed after the ones obtained from DHCP.

With either command, the addresses of the nameservers are separated by commas and the line ends with a semicolon. So if you had a bunch of DNS, it would read:

prepend domain-name-servers 209.70.98.11, 14.15.16.17, 121.244.155.11;

As an aside, I haven't resolved this one yet, but when I use my aircard, Pidgin never connects.

---

