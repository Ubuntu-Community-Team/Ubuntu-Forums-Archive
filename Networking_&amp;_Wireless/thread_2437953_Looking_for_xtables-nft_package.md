---
title: "Looking for xtables-nft package"
date: 2020-03-03
forum: Networking &amp; Wireless
---

### Post by The Cog on 2020-03-03
On Xubuntu 19.10, I am looking to install package xtables-nft [http://manpages.ubuntu.com/manpages/eoan/en/man8/iptables-nft.8.html](http://manpages.ubuntu.com/manpages/eoan/en/man8/iptables-nft.8.html) but it doesn't seem to be there. Is it available on regular Ubuntu 18.10 or is it missing there too? If it's not there, then 1) why is it listed in the manpages, and 2) is it likely to be there in 20.04?

Any insights would be welcome. Thanks

---

### Post by Doug S on 2020-03-06
I have been trying to figure out a reply, and am not certain:

Isn't the xtables-nft stuff in the kernel already, at least as a module? In which case, you merely have to start using it, which should force the related module to load?

All I can do is list what I did to attempt to justify what I just wrote:
First, I looked at the Ubuntu kernel configuration (well, I did it for mainline PPA, which may or may not be the same as production kernels). I looked here:

```
CONFIG_NF_FLOW_TABLE=m
CONFIG_NETFILTER_XTABLES=m

#
# Xtables combined modules
#
CONFIG_NETFILTER_XT_MARK=m
CONFIG_NETFILTER_XT_CONNMARK=m
CONFIG_NETFILTER_XT_SET=m

#
# Xtables targets
#
CONFIG_NETFILTER_XT_TARGET_AUDIT=m
CONFIG_NETFILTER_XT_TARGET_CHECKSUM=m
...

```Then I just tried one of the commands:

```
doug@s15:~/temp-intel-git/lkp-tests$ iptables-nft
iptables v1.8.4 ([COLOR="#FF0000"]nf_tables[/COLOR]): no command specified
Try `iptables -h' or 'iptables --help' for more information.

```Verses:
```
doug@s15:~/temp-intel-git/lkp-tests$ iptables
iptables v1.8.4 ([COLOR="#FF0000"]legacy[/COLOR]): no command specified
Try `iptables -h' or 'iptables --help' for more information.
```

---

### Post by The Cog on 2020-03-07
Thanks for the reply, Doug S. I didn't go into compiling a kernel, I just looked at packages.

On my current machine, I have already installed package nftables. I have not removed iptables though. As a result, I can use both command sets. They appear to operate completely independently. iptables commands affect iptables-save output, and nft commands affect "nft list ruleset" output. I have avoided using iptables commands, relying in nftables. But kvm/virsh makes iptables entries when I load it.

xtables-nft appears to replace the iptables commands with compatible equivalents that make nft entries instead. This is what I would like to do, so that even virsh is making nft entries along with the rest of my config.
These pages suggests it should be possible: [https://wiki.nftables.org/wiki-nftables/index.php/Moving_from_iptables_to_nftables](https://wiki.nftables.org/wiki-nftables/index.php/Moving_from_iptables_to_nftables) and [https://wiki.nftables.org/wiki-nftables/index.php/Legacy_xtables_tools](https://wiki.nftables.org/wiki-nftables/index.php/Legacy_xtables_tools). And there is the Ubuntu page linked in my first post which describes the package. 

And this indicates that there is an alternatives scheme in place:
```
steve@StevesPC:~/ansible$ which iptables
/usr/sbin/iptables
steve@StevesPC:~/ansible$ ls -l /usr/sbin/iptables
lrwxrwxrwx 1 root root 26 Sep 28 13:28 /usr/sbin/iptables -> /etc/alternatives/iptables
steve@StevesPC:~/ansible$ ls -l /etc/alternatives/iptables
lrwxrwxrwx 1 root root 25 Sep 28 13:27 /etc/alternatives/iptables -> /usr/sbin/iptables-legacy
steve@StevesPC:~/ansible$ ls -l /usr/sbin/iptables-legacy
lrwxrwxrwx 1 root root 20 Sep 28 13:28 /usr/sbin/iptables-legacy -> xtables-legacy-multi
steve@StevesPC:~/ansible$ ls -l /usr/sbin/xtables-legacy-multi
-rwxr-xr-x 1 root root 99272 Sep 25 20:36 /usr/sbin/xtables-legacy-multi
```

So it seems that everything is in place. And I confirmed by renaming the /usr/sbin/iptables that virsh uses this (and crashes if it is missing) so I assume that it would use nft if the iptables-nft equivalent (probably xtables-nft-multi) was linked instead. 

And I have just discovered while writing this reply that xtables-nft-multi does exist on my system. I found this page: [https://wiki.debian.org/iptables](https://wiki.debian.org/iptables) which explains a lot. I wish I had found it earlier. I just tried the alternatives switch and it seems to work although I haven't rebooted or tried virsh yet. Manual iptables commands now make entries in the nft ruleset. Excellent!

```
steve@StevesPC:~/ansible$ ls -l /usr/sbin/iptables
lrwxrwxrwx 1 root root 26 Sep 28 13:28 /usr/sbin/iptables -> /etc/alternatives/iptables
steve@StevesPC:~/ansible$ ls -l /etc/alternatives/iptables
lrwxrwxrwx 1 root root 22 Mar  7 10:37 /etc/alternatives/iptables -> /usr/sbin/iptables-nft
steve@StevesPC:~/ansible$ ls -l /usr/sbin/iptables-nft
lrwxrwxrwx 1 root root 17 Sep 28 13:28 /usr/sbin/iptables-nft -> xtables-nft-multi
steve@StevesPC:~/ansible$ ls -l /usr/sbin/xtables-nft-multi
-rwxr-xr-x 1 root root 232880 Sep 25 20:36 /usr/sbin/xtables-nft-multi

```

Thanks again for your reply. It prompted me to search again to explain how far I had got, and this time I got lucky.

---

### Post by Doug S on 2020-07-28
> **The Cog said:**
> xtables-nft appears to replace the iptables commands with compatible equivalents that make nft entries instead. This is what I would like to do, so that even virsh is making nft entries along with the rest of my config.
...
I found this page: [https://wiki.debian.org/iptables](https://wiki.debian.org/iptables) which explains a lot. I wish I had found it earlier. I just tried the alternatives switch and it seems to work although I haven't rebooted or tried virsh yet. Manual iptables commands now make entries in the nft ruleset. Excellent!
...Just curious how you made out in the end. The latest mainline kernel seems to have switch to default to nftables, which caught me off guard. I am wanting to build a new 20.04 server based box for my main firewall/gateway/router and then retire my old 16.04 server based one. I am wondering if I should switch to nftables.

---

