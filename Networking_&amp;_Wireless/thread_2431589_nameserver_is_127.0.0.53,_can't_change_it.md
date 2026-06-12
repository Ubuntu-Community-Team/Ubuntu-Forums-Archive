---
title: "nameserver is 127.0.0.53, can't change it"
date: 2019-11-18
forum: Networking &amp; Wireless
---

### Post by RogerDavis on 2019-11-18
Nameserver always comes up 127.0.0.53, and will not change, even though it is changed in system network settings.

How do I fix this ?!?

---

### Post by Skaperen on 2019-11-18
what are you doing to make that address come up?  i would need to know that to get an idea where that information comes from.  are you typing a command at the command line?

---

### Post by RogerDavis on 2019-11-18
roger@roger-desktop:~$ nslookup google.com 
Server:		127.0.0.53
Address:	127.0.0.53#53

Non-authoritative answer:
Name:	google.com
Address: 172.217.5.206
Name:	google.com
Address: 2607:f8b0:4007:802::200e

---

### Post by Skaperen on 2019-11-18
what does the file [COLOR=#0000cd][FONT=courier new]**/etc/resolv.conf**[/FONT][/COLOR] have in it?

---

### Post by RogerDavis on 2019-11-19
Can't find /etc/resolv.conf .

I don't think it exists, or is VERY well hidden.

There is a folder called /etc/resolvconf, containing resolv.conf.d, which contains base, head, tail.

---

### Post by Skaperen on 2019-11-19
can you show a listing of all those files and directories?  i want to see ownership and dates.  also, output the contents of all the files with the head command to show a maximum of 10 lines each.

it's probably OK that the address is 127.0.0.53.  Linux cross-matches all the addresses configured on the "lo" interface (usually 127.0.0.0/8) so anything listening on one address gets all the traffic destined for any other.  what it's doing is just adding a way to filter DNS queries and answers by means that might be limited to just addresses.  i've done that myself in the past and it looks like systemd is doing it, at least on my system.

---

### Post by Skaperen on 2019-11-19
is anything not working for you that you believe is caused by this?  do you have a reason you understand for changing this?

---

### Post by uRock on 2019-11-19
I found the following input at [this link]("https://askubuntu.com/questions/1012641/dns-set-to-systemds-127-0-0-53-how-to-change-permanently").
> You can install a package resolvconf, which will modify the way /etc/resolv.conf is built up at system boot.

sudo apt install resolvconf
You can then create or modify a file /etc/resolvconf/resolv.conf.d/tail. If you put in this file a line nameserver 8.8.8.8, this line will be added at the end of /run/resolvconf/resolv.conf at boot. /etc/resolv.conf will now be a symbolic link to this file.

---

### Post by chili555 on 2019-11-19
You are not supposed to change it.

That indicates that dnsmasq is running on your system: [https://help.ubuntu.com/community/Dnsmasq](https://help.ubuntu.com/community/Dnsmasq) Dnsmasq will first look in its local cache for the numbers associates with a name, in your case, Google. If it finds it, it uses it. If and only if no listing is found in the local cache, does the system then use any DNS namerservers set by DHCP from the router or other internet appliance, or set by you in Network Manager, such as 8.8.8.8.

Please don't "fix" it because it isn't broken. It appears to be working perfectly.

---

### Post by SeijiSensei on 2019-11-19
We really need to know what version of Ubuntu you're running. DNS resolution has been handled in three different ways over the past few years - using dnsmasq, using resolvconf, and now using systemd-resolved, which is the default method starting with 18.04.

For both resolvconf and systemd-resolved, the file /etc/resolv.conf should contain just 127.0.0.53. The helper software compiles a list of nameservers during boot that are referenced using 127.0.0.53.  If you're on 18.04 or later, run the command "man systemd-resolved" to see how it works.  Check to make sure it is running using

```
sudo systemctl restart systemd-resolved
```

---

### Post by SeijiSensei on 2019-11-19
We really need to know what version of Ubuntu you're running. DNS resolution has been handled in three different ways over the past few years - using dnsmasq, using resolvconf, and now using systemd-resolved, which is the default method starting with 18.04.

For both resolvconf and systemd-resolved, the file /etc/resolv.conf should contain just 127.0.0.53. The helper software compiles a list of nameservers during boot that are referenced using 127.0.0.53.  If you're on 18.04 or later, run the command "man systemd-resolved" to see how it works.  Check to make sure it is running using

```
sudo systemctl restart systemd-resolved
```

Usually systemd-resolved will pick up the list of nameservers provided by your router during the DHCP handshake. If you want to specify nameservers manually, you can add them to the "DNS=" directive in the file /etc/systemd/resolved.conf.  See "man resolved.conf" for details.

---

### Post by RogerDavis on 2019-11-22
Version = Ubuntu 18.04.3 LTS

roger@roger-desktop:~$ sudo systemctl restart systemd-resolved
[sudo] password for roger: 
roger@roger-desktop:~$ 

/etc/systemd/resolved.conf.  apparently does not exist - I cannot find it.

In fact, none of the files you mention exist that I can find.

By way of background, what I'm trying to do it select DNS by advice of Namebench DNS check.

---

### Post by RogerDavis on 2019-11-22
By way of background, what I'm trying to do it select DNS by advice of Namebench DNS check.

---

