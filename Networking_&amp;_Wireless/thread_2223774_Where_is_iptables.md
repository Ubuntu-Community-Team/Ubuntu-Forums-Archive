---
title: "Where is iptables?"
date: 2014-05-12
forum: Networking &amp; Wireless
---

### Post by ruwan2 on 2014-05-12
Hi,

I am using Ubuntu 12.04 on a project connecting with an embedded linux target. I am setting up an NFS server on host Ubuntu 12.04 PC. It looks like NFS has problems and I am checking it step by step. In the following procedures on the web, I cannot find iptables under folder /etc/init.d. 





For Ubuntu NFS setting, please check [this page]("https://help.ubuntu.com/community/SettingUpNFSHowTo") 
  Verify that the server firewall is turned off:  **host $** /etc/init.d/iptables status  If the firewall is running, disable it:  **host $** /etc/init.d/iptables stop  **host $** exit 




It can run iptable with -h option in a console, but cannot with status option.

lcdkl138@lcdkl138-XPS-8500:/etc/init.d$ iptables -h
iptables v1.4.12

Usage: iptables -[ACD] chain rule-specification [options]
       iptables -I chain [rulenum] rule-specification [options]
       iptables -R chain rulenum rule-specification [options]
       iptables -D chain rulenum [options]
       iptables -[LS] [chain [rulenum]] [options]
       iptables -[FZ] [chain] [options]
       iptables -[NX] chain
       iptables -E old-chain-name new-chain-name
       iptables -P chain target [options]
       iptables -h (print this help information)

Commands:
Either long or short options are allowed.
  --append  -A chain        Append to chain
  --check   -C chain        Check for the existence of a rule
  --delete  -D chain        Delete matching rule from chain
  --delete  -D chain rulenum
                Delete rule rulenum (1 = first) from chain
  --insert  -I chain [rulenum]
                Insert in chain as rulenum (default 1=first)
  --replace -R chain rulenum
                Replace rule rulenum (1 = first) in chain
  --list    -L [chain [rulenum]]
                List the rules in a chain or all chains
  --list-rules -S [chain [rulenum]]
                Print the rules in a chain or all chains
  --flush   -F [chain]        Delete all rules in  chain or all chains
  --zero    -Z [chain [rulenum]]
                Zero counters in chain or all chains
  --new     -N chain        Create a new user-defined chain
  --delete-chain
            -X [chain]        Delete a user-defined chain
  --policy  -P chain target
                Change policy on chain to target
  --rename-chain
            -E old-chain new-chain
                Change chain name, (moving any references)
Options:
    --ipv4    -4        Nothing (line is ignored by ip6tables-restore)
    --ipv6    -6        Error (line is ignored by iptables-restore)
[!] --proto    -p proto    protocol: by number or name, eg. `tcp'
[!] --source    -s address[/mask][...]
                source specification
[!] --destination -d address[/mask][...]
                destination specification
[!] --in-interface -i input name[+]
                network interface name ([+] for wildcard)
 --jump    -j target
                target for rule (may load target extension)
  --goto      -g chain
                              jump to chain with no return
  --match    -m match
                extended match (may load extension)
  --numeric    -n        numeric output of addresses and ports
[!] --out-interface -o output name[+]
                network interface name ([+] for wildcard)
  --table    -t table    table to manipulate (default: `filter')
  --verbose    -v        verbose mode
  --line-numbers        print line numbers when listing
  --exact    -x        expand numbers (display exact values)
[!] --fragment    -f        match second or further fragments only
  --modprobe=<command>        try to insert modules using this command
  --set-counters PKTS BYTES    set the counter during insert/append
[!] --version    -V        print package version.
lcdkl138@lcdkl138-XPS-8500:/etc/init.d$ 

lcdkl138@lcdkl138-XPS-8500:/etc/init.d$ iptables status
Bad argument `status'
Try `iptables -h' or 'iptables --help' for more information.
lcdkl138@lcdkl138-XPS-8500:/etc/init.d$ 


What is wrong? Could you explain it to me?

Thanks,

---

### Post by TheFu on 2014-05-12
TL; DR
[B]
which iptables[/B] will tell you where the binary is located, if it is in your PATH.  init.d/ is where startup scripts are located, so if there isn't any startup script, then it won't be there.

Run **sudo iptables -L** to see if it has any rules. If you didn't enable any, then it doesn't.

---

### Post by spynappels on 2014-05-13
You can get a more verbose list of the rules defined (if any) by running
```
sudo iptables -v -L
```
However, as The Fu said, if you didn't enable it, by default it will be set to allow all on all chains.

How Ubuntu handles iptables is sometimes frustrating, in that by default the rules will not survive a reboot, unlike CentOS/RHEL. This is important to keep in mind, as a carefully crafted set of iptables rules can disappear without trace if the box is rebooted, unless you take some extra steps.

The way I keep my iptables rules persistent is to use iptables-save and iptables-restore

When I am happy with my rule set, I will save the rules as follows

```
sudo iptables-save > /path/to/savefile
```

I then add a post-up section in /etc/network/interfaces for the main interface and run

```
iptables-restore < /path/to/savefile
```

from this post-up section, so the rules are applied every time the interfaces come up.

It has the added benefit of being able to edit the /path/to/savefile file to make changes to the iptables rules, which can then be applied by simply running the iptables-restore command above using sudo.

For lots of information on iptables, have a look at the stickies in the Security forum, they are very helpful.

---

### Post by TheFu on 2014-05-13
Ubuntu (and perhaps debian) have a package to save firewall changes between boots. It is easily found in the repos - the name begins with iptables-. I think not saving them this is a safety thing, since the average user is likely to lock themselves out and a reboot is the only solution. Positive action to save them is necessary should a gun be pointed at a foot.

I've had issues with other tools like fail2ban mixing rules with my firewall rules.  Manually applying those (via rc.local) at reboot the easiest answer - blocking many thousands of subnets - mainly from countries where we don't do business. I would prefer to never block anyone, but after awhile, all the spam and wasted resources just isn't worth it. DROP is the only answer.

For most end-users, something like gufw is the best interface to iptables.

---

