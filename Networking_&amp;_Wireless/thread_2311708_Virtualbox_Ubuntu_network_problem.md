---
title: "Virtualbox Ubuntu network problem"
date: 2016-01-29
forum: Networking &amp; Wireless
---

### Post by luc9 on 2016-01-29
Hello, so today i tried to make my virtualbox ubuntu server able to be public to my home pc.

I dont get any network connection at all after inserting this:
Those are the right settings as far as i know haha

Is there any problem because my enp0s3 now also says inet addr: 192.168.2.100 instead of 10.0.2.15

I am using virtualbox, Can anyone help me with this? thanks!

[COLOR=#0000cd][B]iface lo inet loopback
[/B][FONT=inherit][B]iface enp0s3 inet static
        address 192.168.2.100
        netmask 255.255.255.0
        gateway 192.168.2.254
dns-nameservers 8.8.8.8 8.8.4.4[/B][/FONT][/COLOR][COLOR=yellow][FONT=inherit]
[/FONT][/COLOR]

---

### Post by newbie-user on 2016-01-31
It says 192.168.2.100 because you set it that way in your /etc/network/interfaces file. Check to make sure that you've bridged the VM's enp0s3 withj the host's LAN connection. That way, the VM can talk to your local network. You might currently have it NAT'ed, hence the 10.0.2.15 address.

---

