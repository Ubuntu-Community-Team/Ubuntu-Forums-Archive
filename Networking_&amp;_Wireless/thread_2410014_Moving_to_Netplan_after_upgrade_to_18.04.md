---
title: "Moving to Netplan after upgrade to 18.04"
date: 2019-01-09
forum: Networking &amp; Wireless
---

### Post by jabiru2 on 2019-01-09
Hello,

I recently upgraded to 18.04 and simply want to change the old dns to a new IP.  All networking is currently working fine, static ip - not using netplan.

I checked the /etc/netplan and there are no files there? Netplan is installed.

sudo dpkg -s netplan.io | grep Status
Status: install ok installed

A couple of Questions:
Can i perform the change using a remote terminal without loosing connection?

If I now create a netplan and apply it will it just work? Or are there some gotchas I need to be aware of?

We dont use Ipv6 do I still need to add this to the netplan config file?

---

### Post by jabiru2 on 2019-01-13
I have completed this and all is working as it should. The only thing is netplan apply doesn't actually apply the settings, I needed to reboot the server which sucked.

---

