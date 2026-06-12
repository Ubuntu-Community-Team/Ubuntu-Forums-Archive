---
title: "[SOLVED] Network interface keeps changing (eth0-&amp;gt;eth1-&amp;gt;eth2)"
date: 2008-04-04
forum: Networking &amp; Wireless
---

### Post by renli on 2008-04-04
Every time I reboot my laptop my network interface increases by one.  What I mean by this is that I had eth0.  Then I rebooted and it went to eth1.  Next reboot eth2 and so on.  I am now at eth20. Why is it doing this?  Is this going to cause problems eventually?

This is a new laptop, an HP6714ca.  I am running Gutsy.

Thank you

---

### Post by andguent on 2008-04-04
I don't know the answer to your question, but one way to search for text in files is this:
```
sudo find /etc|xargs grep eth20
```

Could you post the output of that here? It should list filenames:text, and should at least tell you what is recording previous settings. If I had to guess, I would say your /etc/iftab is full of wacky mac addresses, but then that would require your mac address to change every time you reboot. Doesn't make sense, but who knows.

---

### Post by renli on 2008-04-04
The output from the command "sudo find /etc|xargs grep eth20" is:

will@hermes:/etc/udev/rules.d$ sudo find /etc|xargs grep eth20
[sudo] password for will:
grep: /etc/shadow: Permission denied
grep: /etc/shadow-: Permission denied
grep: /etc/ssl/private: Permission denied
grep: /etc/ssl/private/ssl-cert-snakeoil.key: Permission denied
grep: /etc/at.deny: Permission denied
grep: /etc/fuse.conf: Permission denied
grep: /etc/passwd-: Permission denied
grep: /etc/mysql/debian.cnf: Permission denied
grep: /etc/security/opasswd: Permission denied
grep: /etc/X11/Xwrapper.config: Permission denied
grep: /etc/group-: Permission denied
grep: /etc/sudoers: Permission denied
grep: /etc/apt/secring.gpg: Permission denied
grep: /etc/apt/trustdb.gpg: Permission denied
grep: /etc/.pwd.lock: Permission denied
grep: /etc/ppp/pap-secrets: Permission denied
grep: /etc/ppp/chap-secrets: Permission denied
grep: /etc/cups/ssl: Permission denied
grep: /etc/cups/ssl/server.crt: Permission denied
grep: /etc/cups/ssl/server.key: Permission denied
/etc/udev/rules.d/70-persistent-net.rules:SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:6c:1e:5f", NAME="eth20"
grep: /etc/gshadow-: Permission denied
grep: /etc/gshadow: Permission denied

There is no /etc/iftab filebut to my understanding it has been replaced in gutsy with /etc/udev/rules.d/70-persistent-net.rules.

My 70-persistent-net.rules is as follows:

will@hermes:~$ cat /etc/udev/rules.d/70-persistent-net.rules 
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x10de:0x054c (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:51:03:e5", NAME="eth0"

# PCI device 0x10de:0x054c (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:ce:ed:c9", NAME="eth1"

# PCI device 0x10de:0x054c (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:a9:46:76", NAME="eth2"

# PCI device 0x10de:0x054c (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:1d:8f:ad", NAME="eth3"

# PCI device 0x10de:0x054c (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:bb:80:22", NAME="eth4"

# PCI device 0x168c:0x001c (ath_pci)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:1f:3a:13:66:be", ATTRS{type}=="1", NAME="ath0"

# PCI device 0x10de:0x054c (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:7d:71:f4", NAME="eth5"

# PCI device 0x10de:0x054c (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:27:05:a7", NAME="eth6"

# PCI device 0x10de:0x054c (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:9d:89:e3", NAME="eth7"

# PCI device 0x10de:0x054c (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:3a:cd:03", NAME="eth8"

# PCI device 0x10de:0x054c (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:58:0b:b4", NAME="eth9"

# PCI device 0x10de:0x054c (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:fd:f7:38", NAME="eth10"

# PCI device 0x10de:0x054c (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:43:d9:15", NAME="eth11"

# PCI device 0x10de:0x054c (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:70:83:a2", NAME="eth12"

# PCI device 0x10de:0x054c (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:e2:23:e5", NAME="eth13"

# PCI device 0x10de:0x054c (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:99:36:e6", NAME="eth14"

# PCI device 0x10de:0x054c (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:33:2d:a8", NAME="eth15"

# PCI device 0x10de:0x054c (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:cb:e9:b9", NAME="eth16"

# PCI device 0x10de:0x054c (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:a0:cc:8b", NAME="eth17"

# PCI device 0x168c:0x001c (ath_pci)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="06:1f:3a:13:66:be", ATTRS{type}=="1", NAME="ath1"

# PCI device 0x10de:0x054c (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:75:7b:7f", NAME="eth18"

# PCI device 0x10de:0x054c (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:65:b8:b6", NAME="eth19"

# PCI device 0x10de:0x054c (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:6c:1e:5f", NAME="eth20"

*****EOF****

Also my /etc/udev/rules.d/75.persistent-net-generator.rules is as follows:

will@hermes:~$ cat /etc/udev/rules.d/75-persistent-net-generator.rules 
# these rules generate rules for persistent network device naming

ACTION=="add", SUBSYSTEM=="net", KERNEL=="eth*|ath*|wlan*|ra*|sta*" \
        NAME!="?*", DRIVERS=="?*", GOTO="persistent_net_generator_do"

GOTO="persistent_net_generator_end"
LABEL="persistent_net_generator_do"

# build device description string to add a comment the generated rule
SUBSYSTEMS=="pci", ENV{COMMENT}="PCI device $attr{vendor}:$attr{device} ($attr{driver})"
SUBSYSTEMS=="usb", ENV{COMMENT}="USB device 0x$attr{idVendor}:0x$attr{idProduct} ($attr{driver})"
SUBSYSTEMS=="ieee1394", ENV{COMMENT}="Firewire device $attr{host_id})"
SUBSYSTEMS=="xen", ENV{COMMENT}="Xen virtual device"
ENV{COMMENT}=="", ENV{COMMENT}="$env{SUBSYSTEM} device ($attr{driver})"

IMPORT{program}="write_net_rules $attr{address}"
ENV{INTERFACE_NEW}=="?*", NAME="$env{INTERFACE_NEW}"

LABEL="persistent_net_generator_end"

******EOF*******

Thanks

---

### Post by andguent on 2008-04-04
> SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:6c:1e:5f", NAME="eth20"

You should only have one of these lines per physical piece of hardware. that "00:00:6c:6c:1e:5f" is supposed to be a serial number, unique to your hardware. That serial number isn't supposed to change, unless under some rare occurance that you tell it to.

You are very welcome to back up that udev file and then clear out everything below the eth0 line. It will bring the network device numbering back down.

Can you use ifconfig to confirm that every reboot, your HWaddr actually is different? What brand/model of network card is this? Very very weird.

---

### Post by renli on 2008-04-05
I deleted the extra lines in the 70-persitent-net.rules file and rebooted.  It came up with a rule for eth0.  Upon another reboot it then added a line for eth1 and my NIC was configured as eth1.  Second reboot, it's now eth2.

lspci gives this for my ethernet controller:

00:0a.0 Ethernet controller: nVidia Corporation Unknown device 054c (rev a2)


It's the same MAC address every time I reboot.
EDIT: I don't know what I was thinking when I wrote this.  It is a _different_ HWaddr every time I reboot.

Thanks

---

### Post by andguent on 2008-04-05
I just googled for 'udev detects wrong hwaddr' and got a few hits, including this:
[http://davehall.com.au/blog/dave/2008/02/10/flakey-bios-gigabyte-ga-m68sm-s2l-makes-mac-address-change-reboot](http://davehall.com.au/blog/dave/2008/02/10/flakey-bios-gigabyte-ga-m68sm-s2l-makes-mac-address-change-reboot)

It looks an absolutely exact fit to your problem. Let us know how it goes.

(Quoting from article for future reference in case the link breaks)
> One issue I did hit was the onboard NIC on my Gigabyte GA-M68SM-S2L motherboard despite what the specs say it is a "nVidia Corporation Unknown device 054c (rev a2)" which uses the forcedeth driver. Everytime I rebooted the box the NIC would increment its interface number - eth0, eth1 ... eth6 and so on. Changing the "Smart LAN" setting in the BIOS from auto to disabled just disables the NIC, not what I wanted.

After googling I discovered that others had experienced similar problems with ASUS boards with nVidia NICs, changing their MAC addresses. Looks like Gigabyte (and ASUS) have been shipping invalid MAC addresses on some of their boards, and forcedeth isn't happy about it, so it just generates a new (valid yet) random MAC address.

With a little help from sysfs I was able to hack my udev config so it all works now. My /etc/udev/rules.d/70-persistent-net.rules looks like

SUBSYSTEM=="net", DRIVERS=="forcedeth", ATTRS{vendor}=="0x10de",
&#10149; ATTRS{device}=="0x054c", NAME="eth0"

I grabbed the output of "cat /sys/class/net/ethX/device/{device,vendor}" to populate the relevant ATTRS entries above.

---

### Post by renli on 2008-04-05
That worked like a charm.  Thank you very much.

Also,just as a general FYI this problem does not seem to occur in the latest Hardy Heron Beta release.  At least, not on my machine.

Thanks again.

---

### Post by nutz on 2008-04-05
Same here, I had this problem on a Compaq F750us laptop with Gutsy but with Hardy the problem is gone.

---

### Post by andguent on 2008-04-05
Glad to know it helped. Chalk one more up for google. :) I was about to ask that you mark the thread solved, but you beat me to it.

---

### Post by Coollie on 2008-06-06
> **andguent said:**
> I just googled for 'udev detects wrong hwaddr' and got a few hits, including this:
[http://davehall.com.au/blog/dave/2008/02/10/flakey-bios-gigabyte-ga-m68sm-s2l-makes-mac-address-change-reboot](http://davehall.com.au/blog/dave/2008/02/10/flakey-bios-gigabyte-ga-m68sm-s2l-makes-mac-address-change-reboot)

It looks an absolutely exact fit to your problem. Let us know how it goes.

(Quoting from article for future reference in case the link breaks)

> **nutz said:**
> Same here, I had this problem on a Compaq F750us laptop with Gutsy but with Hardy the problem is gone.

I had the same problem with my ASUS mobo. My solution: BIOS upgrade. Problem solved!

Greetz!

---

