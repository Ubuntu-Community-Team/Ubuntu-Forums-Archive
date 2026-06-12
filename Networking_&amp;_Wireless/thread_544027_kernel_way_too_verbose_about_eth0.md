---
title: "kernel way too verbose about eth0"
date: 2007-09-05
forum: Networking &amp; Wireless
---

### Post by sumguy231 on 2007-09-05
Since yesterday, I noticed that about every several seconds or so this shows up in the dmesg output and /var/log/kern.log:
```

<snip>
Sep  5 20:07:58 formalwear kernel: [422055.557462] Unknown OutputIN= OUT=eth0 SRC=169.254.8.183 DST=169.254.255.255 LEN=176 TOS=0x00 PREC=0x0
0 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=156
Sep  5 20:08:11 formalwear kernel: [422068.455796] Unknown OutputIN= OUT=eth0 SRC=169.254.8.183 DST=169.254.255.255 LEN=185 TOS=0x00 PREC=0x0
0 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=165
Sep  5 20:08:29 formalwear kernel: [422086.428980] Unknown OutputIN= OUT=eth0 SRC=169.254.8.183 DST=169.254.255.255 LEN=176 TOS=0x00 PREC=0x0
0 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=156
Sep  5 20:08:42 formalwear kernel: [422099.430548] Unknown OutputIN= OUT=eth0 SRC=169.254.8.183 DST=169.254.255.255 LEN=185 TOS=0x00 PREC=0x0
0 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=165
<snip>

```
And so on for hundreds of entries. I have a wireless connection on ath0, and I've pretty much never used an ethernet connection with this computer. I guess it's not really hurting anything, but I'm worried about log filesize and the resource overhead of logging this so often.

What's causing it, and can I at least get it to shut up?

---

### Post by noob12 on 2007-09-05
This is from a logged iptables filter.  Check your iptables or firestarter configuration.

---

### Post by sumguy231 on 2007-09-05
Thanks, that's a good lead. I'm still working on it, Firestarter seems to ignore my change to /etc/firestarter/configuration. The log level was set to "info" but changing it to warning or error does nothing. Is there a better or more direct way to change that, like syslog.conf?

---

### Post by noob12 on 2007-09-06
As far as I can tell, Firestarter doesn't provide you a good way to turn this off.  I don't use firestarter.  I configure my firewall directly with iptables commands.

One option is to set  **LOG_LEVEL=debug** in **/etc/firestarter/configuration** and then disable all logging of **kern.debug** messages in **/etc/syslog.conf**.  But this also loses all other debug messages from the kernel that you might want to see.

If you don't change your firewall configuration much you can edit **/etc/firestarter/firewall**.  Find the section that says "Unsupported Traffic Catch-All".     In this section comment out (prepend with #) the lines the three lines commented below.  Leave the other ones uncommented (as shown).
```

$IPT -A INPUT -j LOG_FILTER
#$IPT -A INPUT -j LOG --log-level=$LOG_LEVEL --log-prefix "Unknown Input"
$IPT -A OUTPUT -j LOG_FILTER
#$IPT -A OUTPUT -j LOG --log-level=$LOG_LEVEL --log-prefix "Unknown Output"
$IPT -A FORWARD -j LOG_FILTER
#$IPT -A FORWARD -j LOG --log-level=$LOG_LEVEL --log-prefix "Unknown Forward"

```
I think you'd have to make this patch whenever you redefined the firewall rules.

---

### Post by sumguy231 on 2007-09-06
Alright, that works well enough. Thanks a lot. :)

---

