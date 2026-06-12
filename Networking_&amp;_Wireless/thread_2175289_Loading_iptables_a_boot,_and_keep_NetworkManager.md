---
title: "Loading iptables a boot, and keep NetworkManager"
date: 2013-09-18
forum: Networking &amp; Wireless
---

### Post by Frozen Forest on 2013-09-18
Until recently did I use* /etc/network/{if-post-down.d, if-pre-up.d}* to store and load iptables, but this does not work anymore. I tried the solution in the wiki¹, it works with option "*Solution #1 - /etc/network/interfaces*" but now the network manager don't work, get "*Unit not handled*" (translation). "Configuration on Startup for NetworkManager" have an other solution but found the following in the file "*/etc/NetworkManager/dispatcher.d/01firewall*"

[PHP]
# pre-up/pre-down not implemented. See
# https://bugzilla.gnome.org/show_bug.cgi?id=387832
#    pre-up)
#       export MODE="start"
#       export PHASE="pre-up"
#       exec run-parts /etc/network/if-pre-up.d
#       ;;
#    pre-down)
#       export MODE="stop"
#       export PHASE="pre-down"
#       exec run-parts /etc/network/if-down.d
#       ;;
[/PHP]

[PHP]
$ cat /etc/network/if-post-down.d/iptablessave 
#!/bin/sh
/bin/bash -c "/sbin/iptables-save -c > /etc/iptables.rules"
exit 0
[/PHP]

[PHP]
$ cat /etc/network/if-pre-up.d/iptablesload 
#!/bin/sh
if [ -f /etc/iptables.rules ]; then
    /sbin/iptables-restore -c < /etc/iptables.rules
fi
exit 0
[/PHP]

¹ [https://help.ubuntu.com/community/IptablesHowTo#Saving_iptables](https://help.ubuntu.com/community/IptablesHowTo#Saving_iptables)

---

