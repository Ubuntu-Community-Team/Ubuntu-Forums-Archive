---
title: "Trouble with WiFi on Ubuntu Server 20.04"
date: 2020-04-27
forum: Networking &amp; Wireless
---

### Post by zogthegreat on 2020-04-27
Hi everyone!

So I installed Ubuntu Server on a laptop that I want to use for NextCloud. When I try to configure the WiFi, I lose all networking. I've tried configuring the default 00-installer-config.yaml and creating a file called 50-cloud-init.yaml. Here is the information that I'm inserting into the .yaml's:

network:
  ethernets:
    enp1s0:
      dhcp4: true
  version: 2
  wifis:
    wlp2s0:
      addresses: [192.168.100/24]
      gateway4: 192.168.1
      nameservers:
        addresses: [192.168.1, 8.8.4.4, 8.8.8.8]
      access-points:
        "*******":
          password: "****************"

I've tried to .yaml validators and they say that I have the right spacing for my .yaml.

Does anyone have any suggestion as to where I'm messing up?

Thanks!

zog

---

### Post by chili555 on 2020-04-27
I suspect that the trouble is this:

wifis:
wlp2s0:
addresses: [192.168.[COLOR="#FF0000"]1[/COLOR].100/24]
gateway4: 192.168.1[COLOR="#FF0000"].1[/COLOR]
nameservers:
addresses: [192.168.1[COLOR="#FF0000"].1[/COLOR], 8.8.4.4, 8.8.8.8]
access-points:
"*******":
password: "****************"

Please correct and try again.

---

### Post by zogthegreat on 2020-04-27
@chili555

Thanks for pointing that out chili555. Syntax, syntax, syntax! Unfortunately, fixing the IP address didn't fix the problem. I'm following the directions found here:

[https://askubuntu.com/questions/1152159/how-to-enable-wifi-on-ubuntu-server-18-04-without-existing-connection](https://askubuntu.com/questions/1152159/how-to-enable-wifi-on-ubuntu-server-18-04-without-existing-connection)

Everything seems to be good, but I don't get WiFi. I'm going to try using DHCP and see if I can at least get connected.

---

### Post by chili555 on 2020-04-27
Did you omit renderer: networkd?

---

