---
title: "Firefox connection timeout"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by Normie26 on 2009-10-31
Just updated from Ubuntu 9.4 to 9.10 Karmic.  Everything appears to have gone OK except system appears to be much slower and I can't get on the internet with Firefox.  FF keeps telling me connection has time out.  Not used to trouble shooting Ubuntu issues as I've only just moved over to Linux.
Have uninstalled and reinstalled Firefox and also tried to downgrade from 3.5 to 3 but no luck.. Still can't access the net, keep getting "The connection has timed out". Would appreciate any help to resolve issue

---

### Post by aheckler on 2009-10-31
Open up a Terminal and see if you can ping anything:
```
ping -c 3 google.com
```

Can you paste the output here?

---

### Post by Normie26 on 2009-10-31
ping works Ok 3 packets sent , 3 packets received 0% packet loss time 2001ms

---

### Post by toppervergara on 2009-10-31
do you have a spare lan card it seems to be hardware trouble. try cleaning the contacts of the present card with an eraser then plug it back in.

---

### Post by aheckler on 2009-10-31
Can you paste the output of this as well:
```
cat /etc/hosts
```

---

### Post by aheckler on 2009-10-31
> **toppervergara said:**
> it seems to be hardware trouble

I doubt it. He can ping stuff just fine, so his connectivity is working.

---

### Post by HiImTye on 2009-10-31
try
```
firefox -safe-mode
```in a terminal (accessories>terminal) and see if you can connect to anything. may be a plugin/extension problem. if that doesn't time out when you connect to something then try disabling some of your extensions so you can narrow down where the problem is

if not post something here

---

### Post by Normie26 on 2009-10-31
Not sure what this means, but here is the response:

	 	 ASUS-SERVER:~$ cat /etc/hosts  
 127.0.0.1	localhost  
 127.0.1.1	ASUS-SERVER  
 

 # The following lines are desirable for IPv6 capable hosts  
 ::1     ip6-localhost ip6-loopback  
 fe00::0 ip6-localnet  
 ff00::0 ip6-mcastprefix  
 ff02::1 ip6-allnodes  
 ff02::2 ip6-allrouters  
 ff02::3 ip6-allhosts 



I have internet connectivity, but FF does not wan't to go to any URL

---

### Post by Normie26 on 2009-10-31
Getting the same results in FF safe mode.  Does not appear to be processing any URL
Have disable all browser  extensions

---

### Post by HiImTye on 2009-10-31
can you connect to the net with any other programs (evolution, for instance)

---

### Post by Normie26 on 2009-10-31
No I can't connect with Evolution. Can't upload or download any emails either. 
Getting same timeout response as Firefox

---

### Post by frank002 on 2009-10-31
I also had a very slow Firefox when I upgraded my wife's computer. I disabled IPV6 in Firefox and that fixed the problem.  This looks like a step backwards. This problem did not exist in 9.04.

---

### Post by Normie26 on 2009-10-31
I'm sure this was a ipv6 issue, I disabled IPv6 in firefox. (Typed 'about:config' in the firefox address bar. Then 'ipv6' in the filter - and in 'network.dns.disableIPv6'. Changed the 'false' value to 'true'. Closed down and restarted firefox and problem seems to be resolved and can now access net OK.  But still having issue with Evolution. Obviously a setting issue but where to start?
Is there a similar setting that can be changed in Evolution?

---

### Post by aheckler on 2009-10-31
Try following [these steps]("http://wwww.ubuntuforums.org/showpost.php?p=8203865&postcount=5") and see if it helps.

---

### Post by neofizz on 2009-10-31
That totally worked for me, thanks Normie26!:)

---

### Post by Normie26 on 2009-11-21
OK got rid of  IPV6 and can now access Internet with Firefox, but still can't get Evolution email to work or access the internet by other means i.e. check for software updates.  Its like a fiewall block or maybe a port being blocked.

---

### Post by jmlm-1970 on 2012-02-13
The solution for some URL return timeout error is in firewall settings.
 
 Just disable the following, in firewal preferences (menu edit/preferences/Advanced Options):
 
 block broadcasts from external network
 block broadcasts from internal network
 block traffic from reserved addresses on public interfaces
 
 Have fun,
 João Moreira.

---

### Post by winh8r on 2012-02-13
oops

---

