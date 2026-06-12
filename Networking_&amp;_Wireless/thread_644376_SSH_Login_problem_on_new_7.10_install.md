---
title: "SSH Login problem on new 7.10 install"
date: 2007-12-18
forum: Networking &amp; Wireless
---

### Post by tuproxy on 2007-12-18
I just did a re-install of 7.10, ran the updates and upgrades and then immediately installed openSSH-server


I am now trying to use PuTTY to SSH into my box and I get an error:
 "Unable to open connection - Host does not exist"

I am typing in the right host name, so what's the deal?  Do I have to do additional configuration of SSH?

Thanks in advance!

---

### Post by Dr Small on 2007-12-18
When using PuTTY, the host should be the IP Address of the machine with openssh-server.
Make sure port 22 is opened on your firewall in order to allow incoming connections, to the machine with openssh-server, also.

Dr Small

---

### Post by tuproxy on 2007-12-18
That worked. I was able to just type the hostname in in my 6.10 install and it would go right to the box.  Is there something that I need to do to enable this feature?  

I had Samba configured in the previous install and have not yet done so with this machine.

---

