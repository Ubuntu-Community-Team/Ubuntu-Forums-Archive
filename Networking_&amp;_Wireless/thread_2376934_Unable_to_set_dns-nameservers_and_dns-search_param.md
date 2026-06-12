---
title: "Unable to set dns-nameservers and dns-search parameters in Kickstart file"
date: 2017-11-07
forum: Networking &amp; Wireless
---

### Post by dave_f2 on 2017-11-07
Hi,

I'm using the following Kickstart command to specify my IP settings for a machine I'm trying to spin up:

network --device=ens160 --bootproto=static --ip=192.168.1.4 --netmask=255.255.255.0 --network=192.168.1.0 --gateway=192.168.1.1 --hostname=ubuntuhost'

Is there an option within the Kickstart file itself to set parameters for 'dns-nameservers' and 'dns-search'? I'm trying to avoid an echo command or something defined in the %post section. Right now, I do get prompted for a dns-nameserver during the Kickstart install.

Thanks!

---

### Post by oldos2er on 2017-11-07
Moved to Networking & Wireless. 

Which version of Ubuntu are you running?

---

### Post by dave_f2 on 2017-11-07
Ubuntu Xenial 16.04.3 64-bit

I'm not sure this matters as I'm looking for a way to define two parameters in an Ubuntu Kickstart file


Since there's no reply, can this get pushed up into a feature?

---

### Post by espressobeanie on 2018-05-17
*bump*

Would like to see this solved.

---

### Post by wildmanne39 on 2018-05-17
Hello espressobeanie , this is an old thread and another users, please only bump your own threads, if you need support please start a thread of your own.

Thanks

---

### Post by QIII on 2018-05-17
Hello!

If this is indeed a bug rather than a request for peer support, then it needs to be reported as such via launchpad/apport/ubuntu-bug.  This is a peer-to-peer user support forum and developers rarely come here except by accident.

Nobody here can fix bugs directly.  We can only report them like any other end-users.

---

