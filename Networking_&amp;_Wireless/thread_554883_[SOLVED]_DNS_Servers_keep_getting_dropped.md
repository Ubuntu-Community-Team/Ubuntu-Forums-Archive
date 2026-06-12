---
title: "[SOLVED] DNS Servers keep getting dropped"
date: 2007-09-19
forum: Networking &amp; Wireless
---

### Post by prophet665 on 2007-09-19
Every time I boot up 7.04 (and many times even mid-session), I need to re-input my DNS servers.  I have found the following thread from 2 years ago:

[http://ubuntuforums.org/showthread.php?t=84185](http://ubuntuforums.org/showthread.php?t=84185)

But, I can't believe this is still a problem.  I am having to manually input them through the Connection Manager that is in the top right hand of my screen.  The thread's answer is that I need to edit my dhclient.conf file.  

Is this still the case?  If so, why doesn't that file get updated when I change the DNS servers through the connection manager?

Needless to say, this is EXTREMELY annoying.

---

### Post by kevdog on 2007-09-19
See this thread --- it may help:

[http://ubuntuforums.org/showthread.php?t=543659](http://ubuntuforums.org/showthread.php?t=543659)

---

### Post by prophet665 on 2007-09-19
Thanks for answering my post, but unfortunately, it is not my ISP (Earthlink) DNS server that is flakey.  My Ubuntu installation keeps dropping the DNS server entries and reverts back to 127.0.0.0 as the only entry.  

To compound this problem, I tried editing the dhclient.conf file, but it tells me I do not have permission to do that.  This is strange because at this time I have not setup any other accounts other than the admin account that was established at the initial installation.

---

### Post by dreadlord_chris on 2007-09-19
> **prophet665 said:**
> Thanks for answering my post, but unfortunately, it is not my ISP (Earthlink) DNS server that is flakey.  My Ubuntu installation keeps dropping the DNS server entries and reverts back to 127.0.0.0 as the only entry.  

To compound this problem, I tried editing the dhclient.conf file, but it tells me I do not have permission to do that.  This is strange because at this time I have not setup any other accounts other than the admin account that was established at the initial installation.
so... how did you try to edit the file? bet you didn't **sudo** the command...
```

sudo nano /etc/dhcp3/dhclient.conf

```
and you're in....

---

### Post by prophet665 on 2007-09-19
That would be a winning bet!  I am still learning how to accomplish all the things I do in Windows without a second thought inside Linux.  

I will try that command, but I still wonder why it told me I did not have the permissions to edit that file when I am suppose to be running under an administrator account using gedit.

---

### Post by prophet665 on 2007-09-19
> **dreadlord_chris said:**
> so... how did you try to edit the file? bet you didn't **sudo** the command...
```

sudo nano /etc/dhcp3/dhclient.conf

```
and you're in....

Ok...edited the file using nano.  I rebooted, verified the file was changed, and checked my DNS servers.  No dice.  It is reverting to my router (192.168.1.1) as my DNS server .  I have posted my file below, and as you can see, the entry was saved.  

Should I change the "send host-name" line?
What is my next option to try?


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
option domain-name-servers 207.69.188.185, 207.69.188.186;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}

---

### Post by noob12 on 2007-09-19
Um.  The "#" marks indicate that the rest of the line is a comment and will be ignored.  For the lines you want to be active, you need to remove the leading "#" sign.

---

### Post by prophet665 on 2007-09-19
> **noob12 said:**
> Um.  The "#" marks indicate that the rest of the line is a comment and will be ignored.  For the lines you want to be active, you need to remove the leading "#" sign.

Yup...I know that (and I do not mean that in a snarky way!).  There are two lines in this file that are not commented out:

send host-name "<hostname>";
option domain-name-servers 207.69.188.185, 207.69.188.186;

I just realized that the lease {} lines that encapsulate the option line are commented out.  I will uncomment them and reboot and see what happens.

---

### Post by noob12 on 2007-09-19
If you want them to apply to all interfaces, keep them outside of any lease blocks.  The man page **man dhclient.conf** is actually pretty good.

---

### Post by dreadlord_chris on 2007-09-19
this is how I do it:
```

# OpenDNS  servers
# http://www.opendns.com/start/ubuntu.php
prepend domain-name-servers 208.67.222.222,208.67.220.220;

```
These are the last 3 lines in my dhclient.conf - what it does is inserts the 2 IPs listed at the beginning of my DNS list

---

### Post by prophet665 on 2007-09-20
> **dreadlord_chris said:**
> this is how I do it:
```

# OpenDNS  servers
# http://www.opendns.com/start/ubuntu.php
prepend domain-name-servers 208.67.222.222,208.67.220.220;

```
These are the last 3 lines in my dhclient.conf - what it does is inserts the 2 IPs listed at the beginning of my DNS list

Thank You, Chris!

I used the prepend command and now I have the correct DNS Servers listed even after a reboot.  It is weird that it keeps adding my router to the list, yet I can't find a file that tells it to do that action.

---

### Post by dreadlord_chris on 2007-09-20
it's pretty common when the router is the default gateway AND is serving DHCP to also forward DNS requests - thus being seen by connected clients AS the DNS...

Since this thread is solved, could you mark it so...

thanks....

---

