---
title: "Wired network connection drops every 5min for 30secs"
date: 2007-12-07
forum: Networking &amp; Wireless
---

### Post by pgroves on 2007-12-07
Here's some background:

 1) This is a brand new desktop machine with Gutsy recently installed. 
 2) The integrated nic identifies itself is an Intel 82562v-2
 3) The connection is always wired.
 4) For various reasons concerning compatibility with the debian machines on the lan,
    I'm trying to configure the network *solely* through /etc/network/interfaces.
    4.a) I have set a static ip address in /etc/network/interfaces by copy and pasting
          the interfaces file from a debian-stable(etch) machine on the same network that
          uses the same approach, and has worked for years. (and changed the ip 
          address, of course)
    4.b) I've tried to obliterate network-manager and dhcdbd while trying to fix this 
           problem, they are removed via dpkg but I also removed:
           /etc/dbus-1/event.d/25NetworkManager
           /etc/dbus-1/event.d/26NetworkManagerDispatcher
 5) Another "fix" that didn't work was disabling ipv6. I did this both through
     /etc/modprobe.d/aliases and /etc/modprobe.d/blacklist

So basically what happens is that every 5 minutes, starting 5 minutes after I boot, the network stops responding but no error messages show up anywhere. Maybe 30 seconds later (sometimes less, sometimes more) everything starts working again. This includes web, aim, and ssh sessions to other machines on my local network. I connect to these machines by ssh NAME where NAME is mapped directly to the other machine's static ip address in /etc/hosts. I mention this because this makes me fairly certain it is not a DNS issue of any kind.

I have checked just about every log in /var/log and none of them list anything happening at the times of the interuptions.

I have been approaching this under the assumption that something is running that tries to "update" the network connection every 5 minutes, but if it's not network-manager, I don't know what it is. However, since learning that uninstalling network-manager does not actually get rid of it since it leaves behind executable python scripts (I found some in /etc/dbus-1/, maybe there are more), I can't be sure it's dead.

Since it is a very new network interface (the only reason I'm using ubuntu is that debian does not recognize it at all), I may soon try to put in a old nic card with old and stable drivers, but I don't have high hopes for that fixing it.

Any thoughts on diagnosing or know of a fix?

Also, can I turn off Avahi with no ill effects? (It's not clear to me if this is crucial or not)

---

### Post by pgroves on 2007-12-09
It turns out this wasn't Ubuntu or my machine. I had set the static IP of this new Ubuntu machine to an ip address in use by my VOIP router. Every 5 minutes the VOIP router was "calling home" to make sure it could still access the phone company servers. I didn't figure this out until weird things started happening when that phone rang.

So I guess the moral of the story is to "really" keep track of what static ip's are in use.

I'm sorry for the horrible things I thought about Network-Manager and Ubuntu's hardware support in general. I'm glad I didn't post them. :-)

-peter

---

### Post by freshinstall on 2007-12-14
Ive had a very similar problem although I dont have it timed down to 5:30 seconds.
Im using an earlier (not v2) version of the chipset with the e100 driver.

Nothing has worked.  My IP is not in use and I have tried other IPs which I know are not in use and I have the same problem when using DHCP.

---

