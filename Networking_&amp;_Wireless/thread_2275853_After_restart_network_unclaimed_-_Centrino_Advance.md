---
title: "After restart network unclaimed - Centrino Advanced-N"
date: 2015-04-28
forum: Networking &amp; Wireless
---

### Post by grayrace on 2015-04-28
At wits end... tried reading a few other forms but can't figure it out. 

It appears my computer is no longer recognizing my network cards driver. I'm on 14.04. Here is some of the diags I've done. 

```
r@FUBAR-XPS:~# lshw -C network  *-network UNCLAIMED     
       description: Network controller
       product: Centrino Advanced-N 6235
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 24
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d0400000-d0401fff




lspci  -nn | grep 0280
01:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6235 [8086:088e] (rev 24)


r@FUBAR-XPS:~# modprobe -c | grep iwlw
remove iwlwifi (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) && /sbin/modprobe -r mac80211


# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211



```

Looked up the drivers and dropped them in /lib/firmware  but don't think it's a problem with the files being there. It seems like something caused them to stop loading. 

Where I got drivers: 
[https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi#download](https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi#download)

---

### Post by michi1983 on 2015-04-29
Hey there,

please provide the output of the script described here:
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

