---
title: "when reboot the ubuntu 12.04 dsn server save problem"
date: 2014-02-26
forum: Networking &amp; Wireless
---

### Post by niraj2 on 2014-02-26
Hi

  I have ubuntu 12.04 I am adding the dns in resolv.conf . Once rebooted that entry get erase from the resolv.conf. 
And again I have to add the same everytime. Please guide how to solve this issue.

---

### Post by IvoGuerreiro on 2014-02-26
Hello, well,
If you want to stop the resolv.conf file from being overwritten enter:

```

sudo chattr +i /etc/resolv.conf

```
This makes your files immutable which means that even root will not be able to change or delete the file. 
To revert: 
```

sudo chattr -i /etc/resolv.conf

```
Anyway just wait to see if someone more experienced can confirmed.

---

### Post by SeijiSensei on 2014-02-26
If your machine uses DHCP to get its network configuration, you have two choices.

1) Edit the DHCP server configuration and specify the DNS servers you want to use there.  Then they will be sent to the client workstations during the DHCP negotiation.

2) Instead, you can add the lines
```

nameserver 1.2.3.4
nameserver 5.6.7.8

```
with the correct nameserver addresses to the file /etc/resolvconf/resolv.conf.d/head.  You need to use sudo for this.  That file is used to re-construct /etc/resolv.conf each time you boot.

If you use [static addressing]("https://help.ubuntu.com/12.04/serverguide/network-configuration.html#name-resolution"), add a line to the bottom of the eth0 stanza in /etc/network/interfaces like this:
```
dns-nameservers 1.2.3.4 5.6.7.8
```
The "s" at the end of "nameservers" is required and easy to forget.

I was one of the people who suggested the chattr approach when 12.04 first came out.  That release incorporated these changes to the way DNS resolution is handled with almost no prior warning and caused a lot of confusion.  Now I recommend playing "inside the lines" and using these official methods.

Oh, and since /etc/resolv.conf is simply a symbolic link to /run/resolvconf/resolv.conf, you would need to first delete the symbolic link, then create a new /etc/resolv.conf with an editor.  Then you can mark that file immutable if you want to go that route.

---

