---
title: "Cannot Connect to a Specific Domain"
date: 2008-03-19
forum: Networking &amp; Wireless
---

### Post by munkymac on 2008-03-19
Recently my office switched to a new webhost to our server. For some reason, I'm now (as of Monday) unable to connect to anything on our domain- [www.roadtripnation.com](www.roadtripnation.com). Can't get on the homepage in Firefox or check webmail, and Thunderbird continually times out when trying to connect to our incoming mail server.

I'm dual-booting XP and Gutsy on my HP Pavilion ze2000. When I boot in XP, I can connect fine. When I am at home running through my ISP, I can connect fine whether I am using XP or Ubuntu.

For some reason, at the office, while booting in Ubuntu (which is my default) I've connected once each morning--email works fine, i can load the website. But after that initial connection, I'm pretty much screwed--nothing for the rest of the day until i go home. I've tried power cycling the router to flush *its* DNS cache to no avail.

I've run the following commands, and can provide the output on each:
route
ifconfig
dig [www.roadtripnation.com](www.roadtripnation.com)
ping [www.roadtripnation.com](www.roadtripnation.com) - the ip address i got back was verified as the correct one by our web guy

I've run sudo /etc/init.d/networking restart
I've also checked my etc/hosts file
I'm set to OpenDNS

The problem is the same whether I'm wired or wireless

I've been running Ubuntu for 6 months, and haven't experience this problem until this past Monday morning. I'm the only person running Linux in my office. I connect with WICD

beyond that, i don't know what other info i should provide. Any help would be appreciated. Thanks in advance!

---

### Post by dmizer on 2008-03-19
1) does this domain point to the same ip you use to connect to the internet?
2) please post the contents of your /etc/hosts file.
3) make sure /etc/host.conf has "hosts" listed before "bind" like so:
```
order hosts,bind
```

---

### Post by munkymac on 2008-03-20
Here's the contents of my /etc/host.conf file:
```
order hosts,bind
multi on
```

And here's my etc/host file:
```
127.0.0.1 localhost
127.0.1.1 aaron-laptop

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

> 1) does this domain point to the same ip you use to connect to the internet?
It looks to me like (after looking at [www.showmyip.com](www.showmyip.com)) the IP address I'm connecting through is 216.237.52.158 (I could be wrong about this. The extent of my computer knowledge is knowing where to look for answers when i have a problem, and then following those directions)

The IP address i get when i ping roadtripnation.com is 72.167.92.22

---

### Post by dmizer on 2008-03-20
try going here: [http://www.opendns.com/support/cache/](http://www.opendns.com/support/cache/)

check the cache for the roadtripnation address, and then click the "Refresh the cache" button.

do you have an opendns account with white/black lists?

---

### Post by munkymac on 2008-03-21
For some weird reason, the Open DNS website doesn't want to play nicely with me. I've been using it without an account (only since this problem began), but it won't let me get past the captcha, and if i try to register for an account, it doesn't process it. I'm stuck.

--------
EDIT: Scratch that, something got messed up with my cookies. It's working now. The address for each instance is the same, and post cache refresh i still can't connect. 

I'm assuming it is something having to do with how Ubuntu is playing with my office network or ISP, since i can connect from home without problems, and at work I can connect with XP without problems, too.

---

### Post by dmizer on 2008-03-21
it could also be related to your office DNS, and open DNS ... have you tried disabling open DNS at work to see if that corrects your problem?

---

### Post by munkymac on 2008-03-23
Yeah, I only started using Open DNS in hopes of fixing this problem. I've tried without Open DNS (after enabling it) but the result is the same. 

I just find it weird that it seems to ONLY be the roadtripnation.com domain and all its variants.

---

### Post by dmizer on 2008-03-23
i really don't know why you would be having the problem, but here's a possible workaround.

edit /etc/hosts as root
```
gksudo gedit /etc/hosts
```

and add a line at the top for roadtripnation.com so your hosts file will look something like this:
```
127.0.0.1 localhost
127.0.1.1 aaron-laptop
[COLOR="Red"]72.167.92.22 roadtripnation.com[/COLOR]

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

---

### Post by munkymac on 2008-03-24
Dangit, that still doesn't work. I'm freaking stumped

But Dmizer, thanks for all your help thus far, I really do appreciate it.

---

### Post by dmizer on 2008-03-24
no problem at all, just sorry that we haven't made any progress.  do you use firefox in windows as well?  have you tried another browser in linux, like opera?

can you ping roadtripnation.com from the commandline?

---

### Post by munkymac on 2008-05-03
On my dual boot, I was able to connect using firefox in XP. I can ping roadtripnation.com from the command line in Linux, as well.

I've switched over to a fresh install of Xubuntu now (my computer is a little old and slow) and I'm still unable to connect at the office. It's nutty.

---

### Post by dmizer on 2008-05-18
don't know if you are still experiencing this or not.  i really don't know why it's not working for you but here's a possible fix: [http://articles.techrepublic.com.com/5100-10878_11-6174075.html](http://articles.techrepublic.com.com/5100-10878_11-6174075.html)

found here: [http://ubuntuforums.org/showthread.php?t=418144](http://ubuntuforums.org/showthread.php?t=418144)

double check to make sure ipv6 is in your /etc/modprobe.d/blacklist with the following command:
```
cat /etc/modprobe.d/blacklist | grep ipv6
```

the output should look like this:
```
blacklist ipv6
```

---

