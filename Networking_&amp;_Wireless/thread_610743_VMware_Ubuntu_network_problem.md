---
title: "VMware Ubuntu network problem"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by KDB9000 on 2007-11-12
To start off it was all working before I did a cloning of it. It will not bring up eth0. It says it that it isn't there. lspci shows it there and everything else seem to be correct. I have noticed on start up that it reports smbus (I think) host controller doesn't start and in lspci there is an unknown pci bridge. Not sure if this has anything to do with my problem but it might. 

I did a cloning of the OS to another hard drive (to increase the size of the hard drive... long story) and everything is working except the NIC. Any thoughts?

---

### Post by KDB9000 on 2007-11-13
Bump.

Anyone? I can see the NIC in Linux with commands I ran (lspci & dmesg) and I have removed the mod and put it back it, but Linux still says there is no eth0.

---

### Post by jfsylvain on 2007-11-13
It might be a mac address mismatch.

Make sure the mac address configured by Ubuntu,[INDENT] in Feisty: /etc/iftab
in Gutsy:  /etc/udev/rules.d/70-persistent-net.rules[/INDENT]
matches the mac address in the virtual machine's vmx file.

---

### Post by KDB9000 on 2007-11-13
It was, I tried in on my one install and it didn't work so I did a recopy and did something like that and it is working now. Here is the link to the page that helped me.

[http://communities.vmware.com/thread/46069](http://communities.vmware.com/thread/46069)

---

