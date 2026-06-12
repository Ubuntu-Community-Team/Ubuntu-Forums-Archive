---
title: "CLI configure both static and DHCP wifi connections"
date: 2013-10-13
forum: Networking &amp; Wireless
---

### Post by chorlton2080 on 2013-10-13
Hi folks

I need to be able to set-up wifi for both home and office use using the CLI.

I can configure either the DHCP or the static, but I'm struggling getting both to co-exist.

My home router will accept a DHCP connection. My work router will only accept a pre-defined static IP.

My problem is how to have both as configuration parameters in /etc/network/interfaces (using wpa_supplicant as appropriate) and the OS chose the appropriate connection based on availability.

I can't use the GUI and Network Manager to sort this: I need to be able to configure using the console.

Many thanks in advance.

---

### Post by TheFu on 2013-10-13
If your work uses DHCP, then I'd setup DHCP reservations on your router at home. That way you can use DHCP at both places, but still have a "static" IP at home.

If your work uses static IPs, then I'd setup static IPs are home too. If they are on the same subnet, use the same IP. If they are on different subnets, read up on having multiple IPs on a single interface and write a post-up script for the /etc/network/interface file stanze to add/remove the route you want/do not want based on other network information.

Added DHCP reservation in case someone else is lurking.

---

### Post by chorlton2080 on 2013-10-13
Thanks for the reply and in retrospect I should have added more detail.

Yes, I have a static IP at work and it is of the same subnet.

Whilst your advice makes a lot of sense, unfortunately I have a further problem: the router at home is not reliable at static IP reservation using MAC, it forgets the setting at each power cycle.

---

### Post by ian-weisser on 2013-10-13
Do you have Network Manager installed? It can do that.
If so, have you tried the *nmcli* command?

---

### Post by chili555 on 2013-10-13
I'd suggest you set up /etc/network/interfaces like this:```
auto lo
iface lo inet loopback

mapping eth0
      script /home/<username>/net.sh
      map eth0 eth0-home
      map eth0 eth0-work

iface eth0-home inet dhcp
      
iface eth0-work inet static
      address #ipaddress for work
      netmask #netmask for work
      gateway #gateway for work
```Now create a file /home/<username>/net.sh with the following contents

```
#!/bin/sh
echo eth0

```
save and close the net.sh file.

You are all set now. You can use command ```
sudo ifup eth0=eth0-home
``` ...to start network with eth0-home settings and ```
sudo ifup eth0=eth0-work
``` ...to start with eth0-work settings.

---

### Post by TheFu on 2013-10-13
@chili555 - I didn't try what you suggest ... the connection between ~/net.sh and everything else is missing, right?

---

### Post by TheFu on 2013-10-13
> **chorlton2080 said:**
> Thanks for the reply and in retrospect I should have added more detail.

Yes, I have a static IP at work and it is of the same subnet.

Whilst your advice makes a lot of sense, unfortunately I have a further problem: the router at home is not reliable at static IP reservation using MAC, it forgets the setting at each power cycle.

Not at all - adding too much data in the initial post wouldn't get multiple people engaged.
A non-reliable router probably shouldn't be trusted at all. $20 can solve that with a cheapo dd-wrt compatible router.

---

### Post by chili555 on 2013-10-13
> **TheFu said:**
> @chili555 - I didn't try what you suggest ... the connection between ~/net.sh and everything else is missing, right?I'm not sure I understand your question. The file /home/<username>/net.sh, once you write it, is called in /etc/network/interfaces. Why do you think the connection is missing? 

Did you read *man interfaces* in regard to mapping?

---

### Post by TheFu on 2013-10-13
> **chili555 said:**
> I'm not sure I understand your question. The file /home/<username>/net.sh, once you write it, is called in /etc/network/interfaces. Why do you think the connection is missing? 

Did you read *man interfaces* in regard to mapping?

Actually I didn't see the "script /home/<username>/net.sh"
line in your post. Must have been my mistake.

---

