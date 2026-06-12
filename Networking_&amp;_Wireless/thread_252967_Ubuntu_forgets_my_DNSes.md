---
title: "Ubuntu forgets my DNSes"
date: 2006-09-07
forum: Networking &amp; Wireless
---

### Post by bastiegast on 2006-09-07
Hi, Ive set my DNS servers several times through System > Administration > Networking > DNS servers. But Ubuntu keeps forgetting them on next reboot or if I for example change my ethernet device or netwoking settings. :-s

---

### Post by skymt on 2006-09-07
Try configuring them in /etc/resolv.conf, like this:

* Run```
gksudo gedit /etc/resolv.conf
```

* For each DNS server, add a line with the format:```
nameserver a.b.c.d
```...where a.b.c.d is the IP of one of your nameservers.

---

### Post by bastiegast on 2006-09-07
Thanks :) Im im trying it out now.

UPDATE: Well, im a little dissappointed about gnomes networking config gui, since by editing this file my networking issues i had are gone \\:D/ However i had days of struggle trying to resolve them with the gnome gui. All those days internet was slow or randomly died because of DNS problems, all solved now so thank you again!

---

### Post by tbonius on 2006-09-07
If you are getting your IP address dynamically (DHCP) then the DNS server entries will be overwritten every time you reboot.  Try using the dhclient-enter-hooks to make sure you are adding your own entries into /etc/resolv.conf

T

---

### Post by bastiegast on 2006-09-07
> **tbonius said:**
> If you are getting your IP address dynamically (DHCP) then the DNS server entries will be overwritten every time you reboot.  Try using the dhclient-enter-hooks to make sure you are adding your own entries into /etc/resolv.conf

T

I see, so thats the reason, previous post i was a little over enthusiastic because my dns servers have been overwritten again. So what exactly is dhclient-enter-hooks, does it prevent your dns servers being overwritten?

---

### Post by skymt on 2006-09-07
dhclient-enter-hooks.d is a folder in /etc/dhcp3. Try running 'gksudo gedit /etc/dhcp3/dhclient-enter-hooks.d/dns' and copy and paste (untested, I don't use DHCP):```
#!/bin/bash
for server in "*list of DNS server IPs, seperated with spaces*" ; do
    if ! grep $server /etc/resolv.conf ; then
        echo "nameserver "${server} >> /etc/resolv.conf
    fi
done
```

---

### Post by handy on 2006-09-08
I have the same problem, I ended up running a script which overwrites my **/etc/resolv.conf** every time I boot-up:

[See post #15 off this thread?]("http://ubuntuforums.org/showthread.php?p=1435783#post1435783")

It works for me, until my ISP changes the DNS addresses, which they do do every so often... :rolleyes:  Then I have to edit my resolve.conf to make it accurate again.

---

### Post by handy on 2006-09-08
> **skymt said:**
> dhclient-enter-hooks.d is a folder in /etc/dhcp3. Try running 'gksudo gedit /etc/dhcp3/dhclient-enter-hooks.d/dns' and copy and paste (untested, I don't use DHCP):```
#!/bin/bash
for server in "*list of DNS server IPs, seperated with spaces*" ; do
    if ! grep $server /etc/resolv.conf ; then
        echo "nameserver "${server} >> /etc/resolv.conf
    fi
done
```

I have followed your advice, I'll test it out & feedback the results.  

Your method is far more elegant than my desperate measures (see previous post) :D

---

### Post by linuxusr50 on 2006-09-10
I had the same problem when I was running VPNC to establish a vpn connection with my work place.

I solved the problem by loading and running resolvconf.

You will need to put the nameservers you want to remain constant in the following directory:

/etc/resolvconf/resolv.conf.d/base

use the following format:

nameserver      x.x.x.x
nameserver      x.x.x.x
nameserver      x.x.x.x

---

### Post by Iowan on 2006-09-10
There's another thread around here somewhere that presented this information... 
If you are getting your IP address vis DHCP, check the /etc/dhcp3/dhclient.conf file.  ```
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name,[COLOR="Red"] domain-name-servers[/COLOR], host-name,
        netbios-name-servers, netbios-scope;

```
As I recall, the highlighted section requests a list of DNS servers from your ISP - overwriting your file.  If you delete the [COLOR="Red"] domain-name-servers[/COLOR], your settings *shouldn't* get overwritten.

[http://www.ubuntuforums.org/showthread.php?t=202053&highlight=dhclient.conf]("http://www.ubuntuforums.org/showthread.php?t=202053&highlight=dhclient.conf")
Or... this one might help.

---

### Post by handy on 2006-09-11
@**skymt**, it looks like the DNS addresses that I want now stay, but the router's address gets written in sometimes, & is read before the other 2, which renders them useless.

So, I am a little closer, but not quite there yet... :) 

@**linuxusr50**, Thanks for your reply, :) I will try it too, & feedback in  few days...

@**Iowan**, Thanks for your reply, :) I have made the script modification, checked out the supplied link, which looks good, I may have to do the **sudo chattr +i /etc/resolv.conf**?  I'm testing it without first, & in combination with **skymt's** fix, which nearly works... :) 

If I have to I'll try all 3 at once! :KS

---

### Post by handy on 2006-09-11
> **skymt said:**
> dhclient-enter-hooks.d is a folder in /etc/dhcp3. Try running 'gksudo gedit /etc/dhcp3/dhclient-enter-hooks.d/dns' and copy and paste (untested, I don't use DHCP):```
#!/bin/bash
for server in "*list of DNS server IPs, seperated with spaces*" ; do
    if ! grep $server /etc/resolv.conf ; then
        echo "nameserver "${server} >> /etc/resolv.conf
    fi
done
```

Hmm... I had a memory once, I just don't know where I left it!?

Thanks **Skymt**, I tested your solution solo, & I believe that it works perfectly.  

I have a vague recollection of leaving my router's address in the **/etc/resolv.conf** file. :rolleyes: 

After removing the router's IP address, & then testing with quite a few *cold* restarts, I have none other than the required address's.

So, it's looking **very** good, & it's so much easier than my **$ cp resolve.conf resolv.conf** method with all it's steps! :mrgreen:

---

### Post by handy on 2006-09-16
@ **Skymt**, unfortunately it was not my memory as previously posted... :( 

The router/modem's IP address has hi-jacked the **/etc/resolv.conf** by putting it's self in first place & thereby blocking the other 2 DNS addresses!

Bugger...

I just edited the **/etc/dhcp3/dhclient.conf** 

removing - **domain-name-servers**

Then making the **/etc/resolv.conf** immutable with the following line:

**sudo chattr +i /etc/resolv.conf**

I'll see how that goes into the future?

---

### Post by putte30 on 2006-09-26
Having same problems with the dns issue. sudo chattr +i /etc/resolv.conf doesnt work for me.. generating errors...

---

### Post by f00buntu on 2006-09-26
You can force your own dns servers when using dhcp by putting:

supersede domain-name-servers x.x.x.x;

in your /etc/dhcp3/dhclient.conf where x.x.x.x is your preferred dns server (you can enter multiple servers seperated by a space)

man dhclient.conf for more info

---

### Post by handy on 2006-09-26
> **f00buntu said:**
> You can force your own dns servers when using dhcp by putting:

supersede domain-name-servers x.x.x.x;

in your /etc/dhcp3/dhclient.conf where x.x.x.x is your preferred dns server (you can enter multiple servers seperated by a space)

man dhclient.conf for more info

Thanks for that!

I have undone all my changes (which were working) & have taken your advice.  After reading the man pages on dhclient.conf, I would think that at last I have found the correct way to solve this problem...

Thanks again! :KS

---

### Post by handy on 2006-09-27
I checked today & found that my modem/router's IP address has put itself at the top of the list, thus preventing me from accessing the repo's! :( :confused:

I'll try putting that IP address last list in the **dhclient.conf** & see what kind of result that gets?

---

