---
title: "Weird connect between vm and host (feisty)"
date: 2007-05-08
forum: Networking &amp; Wireless
---

### Post by seamuso on 2007-05-08
VMWare server (1.0.3) w/ win2k as virtual -  feisty (kubuntu) is host OS for the vmware install.

I am unable to make a connection from the win2k vm -> feisty via ftp and ssh. Less concerned about the ftp than I am ssh (I use winscp for file transfers).

I can correctly connect to other ssh servers and ftp servers on my lan from the vm and can correctly connect to ssh and ftp services running in feisty from other machines on my lan as well as from my feisty user login.

I can ping from the vm machine -> feisty
I can pull up webpages that are hosted on the feisty system from the 2k vm

When I ```
 sudo proftpd -n 
``` an try to make the connection from the 2k vm, I see the connection attempt .. ```
bluebuntu.bluefrogcs.com (192.168.1.111[192.168.1.111]) - FTP session opened.
``` and then it just hangs there until I stop the connection attempt (hang = up to at least 4 minutes without a server timeout).


Has anyone else run into this?  Is it an easy fix? My vmware is running in bridged mode only, so no nat to mess with.

**See final post for resolution**

---

### Post by agurk on 2007-05-08
In Feisty, have you opened the ftp and ssh ports using Firestarter?

---

### Post by seamuso on 2007-05-08
ports aren't blocked anywhere ...

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

Like I mentioned, I can get on any other machine and make the connections to the feisty machine. There just seems to be a block between vmware and feisty .. not the installed guest, between feisty and vmware itself. 

This is what I used for the install guide -

[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)


Nothing fancy or different than what I have done previously.

---

### Post by agurk on 2007-05-08
> Like I mentioned, I can get on any other machine and make the connections to the feisty machine. There just seems to be a block between vmware and feisty .. not the installed guest, between feisty and vmware itself.
Ah, sorry, I missed that. Weird. Well, I'm currently out of ideas. Might be worth disabling IPv6 though, but that's just a stab in the dark.

---

### Post by seamuso on 2007-05-08
> **agurk said:**
> Ah, sorry, I missed that. Weird. Well, I'm currently out of ideas. Might be worth disabling IPv6 though, but that's just a stab in the dark.

Heh .. ipv6 was disabled almost from the start

---

### Post by seamuso on 2007-05-08
Resolved -

Looks like the vmware modules in the repository are at fault. I uninstalled 1.0.3 completely, reinstalled 1.0.1, used vmware-any-any-update109.tar.gz to correct the known module compile errors, connected correctly to ssh/ftp guest -> host

Then ran (from here .. [https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server) )

```
sudo sed -i -e "s/\/sbin\/insmod -s -f \"\/lib\/modules\/\`uname -r\`\/misc\/\$1.o\"/modprobe -s -f \$1/" /etc/init.d/vmware
sudo sed -i -e "s/sub configure_module {/sub configure_module {\n return 'yes';/" /usr/bin/vmware-config.pl
sudo vmware-config.pl

sudo /etc/init.d/vmware restart
``` to use the feisty built modules .. ftp/ssh connection dead on test.

Uninstalled vmware completely, installed 1.0.3, used vmware-any-any-update109.tar.gz to correct known module build errors .. ftp/ssh working.


When I originally installed 1.0.3, I only used the sed commands for the fix and since it built fine, didn't give it another thought until I installed my ftp server last night.

oh well, live and learn .. hope this helps.

---

