---
title: "How can I change my DNS servers?"
date: 2021-01-29
forum: Networking &amp; Wireless
---

### Post by modeverything2 on 2021-01-29
I feel like this should be, and used to be such a simple thing to do, but I cannot figure out how to change my DNS servers.

I am running Ubuntu 20.04 LTS.

I first went to /etc/resolv.conf and it tells me that this file is managed by systemd-resolved.  I then check my /etc/systemd/resolved.conf file and I see no DNS servers are currently configured here, so it must be getting the configuration from somewhere else.  I run the command **resolvectl status** and I now see my DNS entries.

I'm not familiar with this was of setting DNS.  Where is it getting these values from?  Where can I change it?
I feel like this is harder than it should be, or I'm just making it too difficult on myself and overlooking something obvious.

Thanks for any help!

EDIT: Forgot to mention that this server is CLI only, no GUI.

---

### Post by thinkpad770x on 2021-01-29
The quickest way to do this is by changing the connection settings in the network manager gui

---

### Post by modeverything2 on 2021-01-29
I'm sorry, I forgot to say that this is a CLI only server.  Is there a way for me to do it in the command line?

---

### Post by thinkpad770x on 2021-01-29
I just checked the official 20.04 manual. It says the new file is located here

/ etc / r e s o l v . conf &#8722;> . . / run/systemd/ r e s o l v e /stub&#8722;r e s o l v . conf

---

### Post by sjreilly on 2021-01-29
Hi,
You should use the new netplan config.

Here is an example of my NIC with a static IP config pointing to the 1.1.1.1 DNS

```
network:
     version: 2
     renderer: networkd
     ethernets:
          enp2s0:
               dhcp4: no
               addresses: [192.168.0.100/24]
               gateway4: 192.168.0.1
               nameservers:
                    addresses: [1.1.1.1]
```

---

### Post by TheFu on 2021-01-29
If you use dhcp, change the settings in the dhcp server.

For other documentation, visit help.ubuntu.com  The network sections covers this.

---

### Post by modeverything2 on 2021-01-29
I appreciate the feedback and help.

I did first try looking in  the official Ubuntu 20.04 manual and I couldn't find it, that's why I  asked here.  The manual links took me to this page, which seems to only  instruct for a GUI interface;  [https://help.ubuntu.com/lts/ubuntu-help/net-manual.html.en](https://help.ubuntu.com/lts/ubuntu-help/net-manual.html.en).  I'm sure  there is a CLI part of the manual somewhere, but that's what I'm saying,  I haven't been able to find it yet.

I didn't mention this  before, but this is a production server, so it does have a static IP, so  unfortunately I can't change it with DHCP.

Trying to edit the new stub-resolv.conf file failed.  I get the following error:
"/run/systemd/resolve/resolv.conf"
"/run/systemd/resolve/resolv.conf" E212: Can't open file for writing
Press ENTER or type command to continue

I'll take a look at the netplan config option, however, I don't want to change too much since this a production server.

---

### Post by TheFu on 2021-01-29
Uh ... that's the desktop help.  Backup to the top level and select "Server".  help.ubuntu.com

If you post your netplan file, we can make suggestions.  Be certain to use 'code tags' or the indentation will be lost and useless here. See post #5 above for a bad example.  [https://ubuntuforums.org/misc.php?do=bbcode#code](https://ubuntuforums.org/misc.php?do=bbcode#code) explains how to use code tags here. If you don't post that way with the requested information, I won't help.  It is too hard.

There are lots and lots of examples of valid netplan files all over the place. After updating that, force a re-generation and apply:
```
sudo netplan generate
sudo netplan apply --debug
```

I don't recall, but you may need to reload/restart networking.

---

### Post by SeijiSensei on 2021-01-30
On systems like 20.04 that use systemd-resolved, you can specify the nameservers to use in /etc/systemd/resolved.conf. Add the primary to the DNS line, and any secondaries to the FallbackDNS line. Then run
```
sudo systemctl restart systemd-resolved
```
to use the new settings.

---

### Post by sjreilly on 2021-01-30
Hi @TheFu
Can I ask why #5 is a "bad" example? I tried to copy direct from my netplan file and the tabs got lost during the paste to this forum.

---

### Post by TheFu on 2021-01-30
> **sjreilly said:**
> Hi @TheFu
Can I ask why #5 is a "bad" example? I tried to copy direct from my netplan file and the tabs got lost during the paste to this forum.

see post #8.

---

### Post by sjreilly on 2021-02-01
Thanks. Sorted

---

### Post by modeverything2 on 2021-02-01
I just wanted to reply real quick to say I got it changed properly.  Once I was pointed in the correct direction of the "Server" documentation instead of the Desktop, I found the information regarding Netplan.  I then modified my Netplan and everything is working fine.

I appreciate the help on this.  This Netplan is new to me, I had not seen it before.

---

