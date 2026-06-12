---
title: "sudo: unable to resolve host ZB: Temporary failure in name resolution"
date: 2024-04-16
forum: Networking &amp; Wireless
---

### Post by dieter-erich on 2024-04-16
Hi,
   my ubuntu-22.04 box (named "ZB") got stuck probably because of various parallel VPN connections. As I could not run it down correctly I power cycled it. Now everything is fine again but domain name resolution does not work. I even get the above message on trying to become sudo. When running "nmcli device show wlp0s20f3" everything seems fine with two addresses of relevant DNS servers. I also tried "sudo systemctl restart NetworkManager" but again get "sudo: unable to .... resolution" as in the Title. Nevertheless, after a quite long time, it asked for the root PW that I entered but nothing changed. 
Thank you for help! I am completely stuck......

---

### Post by TheFu on 2024-04-16
There's no such thing as a "root" password on Ubuntu systems.  Perhaps you are confused.  Ubuntu uses sudo and sudo is network aware, to it needs to compare the current hostname with whatever is inside any of the sudoers files.

The only solution for a bad sudoers setup that I know, and it will only work if full drive encryption isn't being used, is to get into rescue mode or boot from alternate boot media, then fix the issue inside the sudoer's.

BTW, hostnames are case insensitive, but some old scripts may not be written to deal with it, so a hostname really needs to be all lower-case. Same for usernames (all lowercase, numbers ok, if not the first character, no special characters at all).  
You can use the same ISO you used to install any desktop Ubuntu version in "Try Ubuntu" mode to edit the sudoers on the storage device inside the computer. You'll need to mount it and traverse down that mount into the /mnt/etc/sudoers file or sudoers.d/ directory to make the fixes.

In general, the first user added to an Ubuntu system gets placed into the **sudo** group and that is normally sufficient to gain sudoer access. For example, 
```
$ egrep sudo /etc/group
sudo:x:27:thefu
```

Obviously, the username on hour system will be different than mine.

Part of being a good admin is avoiding issues before they happen.  That's mostly what this post is about. There are lots of things that _should_, but need special processing for them to work.  Best to avoid those situations.

---

### Post by dieter-erich on 2024-04-17
Thank you! Sorry for the confusion: Sure, I used "sudo" and not "root"! It is not an issue of root or sudo access, it is rather a problem with the domain name resolution. For some reason the DNS does not work any more. For example, I can perfectly well ping a number, e.g. ping 131.130.1.11 but not a name, e.g. ping webmail.univie.ac.at. In the latter case I get an error message similar to the above (without sudo of course) . So, how to fix it?

---

### Post by TheFu on 2024-04-17
There are lots of possible answers for name resolution problems.  Systemd-resolved is the default resolver for the last 4 yrs under Ubuntu.  It often has problems, I'm sorry to say.  There is a config file for it.  I don't use Systemd-resolved, but I think the name is resolved.conf somewhere below /etc.  You can search for it. /etc/systemd/resolved.conf seems like a good guess.

Anyway, ensure that file has both primary and backup DNS set.  I prefer 1.1.1.1 and 1.0.0.1 for a number of reasons.  

Speed and their commitment to show everything, unfiltered, without tracking.  DNS can be used to track where you ask to visit on the internet. I wouldn't trust most other public DNS services to behave that way.  They often use DNS to capture personal data about us.

Anyway, set the 
```
DNS=
FallbackDNS=
```
values, _restart systemd-resolved_ service and see if that doesn't fix it forever.  In theory, your DHCP server should be providing correct DNS information to all clients. It works for almost all other systems, but not always for systemd-resolved.

If you have problems in the future, you can purge systemd-resolved from your system and handle DNS the way we did for 40 yrs before the Linux people decided to make it 1000x more complex than needed with resolvconf and systemd-resolved.

BTW, if you also run your own DNS server on your LAN, say to filter advertising and tracking domains ( [https://pi-hole.net/](https://pi-hole.net/) ), then you don't need any local caching DNS on every device on your LAN. It is a waste of resources and added complexity.  But if you use a laptop, allowing the DHCP server to provide the current DNS to be used could be important - i.e. hardcoding it may not be the best answer, especially if the laptop gets put onto work networks where companies have their own DNS almost always.

Anyway, that should get you working.

---

### Post by dieter-erich on 2024-04-17
I found the problem with sudo and solved it via correcting an inconsistency of hosts and hostname. [B]

However, the problem with Temporary failure in name resolution persists.[/B] When pinging e.g. webmail.univie.ac.at I get (after a long time): "temporary failure in name resolution"
1) in /etc/resolv.conf are the IPs of various name servers with lines such as "nameserver 8.8.8.8"
2) I did as described here: [https://www.tecmint.com/resolve-temporary-failure-in-name-resolution/](https://www.tecmint.com/resolve-temporary-failure-in-name-resolution/) and everything seemed OK but ping google.com gives the same error as above
3) I checked that the relevant ports are open and saw that the firewall is not active anyhow
4) I run "sudo systemd-resolve --flush-caches" but received the message "command not found" was this file somehow lost or is not present in Ubuntu Mate 22.04?
5) I changed the permissions as explained here: [https://www.linuxjournal.com/content/troubleshooting-temporary-failure-name-resolution-error-linux](https://www.linuxjournal.com/content/troubleshooting-temporary-failure-name-resolution-error-linux)
6) I checked the time and found that it was automatically synchronized and did not take into account the daylight saving time. I turned it off and set the correct time and rebooted. 
7) I tried this (also described in the above post): 
$ apt install netplan.io
$ systemctl unmask systemd-networkd.service
$ systemctl unmask systemd-resolved.service
$ ENABLE_TEST_COMMANDS=1 netplan migrate
$ netplan try

But with ENABLE........ I received an error and could not continue

How should I proceed?

---

### Post by dieter-erich on 2024-04-17
We must have posted at about the same time! TheFu had a very simple solution. I out commented all nameservers in /etc/systemd/resolved.conf and just put: 
nameserver 1.1.1.1
nameserver 1.0.0.1
rebooted and that was it!
Thanks so much, you saved me several more hours or days!

---

### Post by TheFu on 2024-04-17
Be very careful adding netplan to a desktop install.  If it were me, and I didn't PREFER to use server-style network configurations, I'd undo everything you did in post #5 above.  Nothing good will come from it and something bad could.

Netplan configuration and tools are a replacement for network-manager.  Do you really want to remove network-manager and not have any GUI for network stuff?  That's what using netplan in the server-way is meant to accomplish.  Probably not desirable, unless you are a server admin.

If you modified /etc/resolv.conf, those changes will be short-lived.  A number of "helpers" will overwrite that file periodically, regardless of whether they actually are helping.

All changes made to /etc/resolv.conf are immediate, BTW. No need to restart anything, unless the point to a localhost address ... er ... like a local caching server from systemd-resolved.

---

### Post by dieter-erich on 2024-04-18
Thanks for the warning! I shall try undoing what I did until post #5!  BTW: /etc/resolv.conf was already overwritten but still contains 1.1.1.1. and 1.0.0.1 and everything continues to work fine!
Thanks again!

---

