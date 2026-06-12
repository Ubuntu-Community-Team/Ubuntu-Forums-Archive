---
title: "Ubuntu assigns eno address to iDrac card on reboot.  Why, and how to prevent?"
date: 2022-01-21
forum: Networking &amp; Wireless
---

### Post by davidahillman on 2022-01-21
So this is a weird one that I've certainly never seen before.  Ubuntu on this Dell R720 that I have here consistently re-configures its network interfaces on reboot, and does so in a pathological manner.  The problem is Ubuntu specific -- to test, I installed both Manjaro and Rocky ( sequentially ) and neither of them exhibit this behavior.

Steps to Replicate:
[LIST=1]
[*]Plug in one cable to the motherboard quad-port, say, eno2 and one to the iDrac (7) card
[*]Power-on
[*]Install Ubuntu 20.04.3 LTS from known-good ISO -- I performed this step several times, both from a physical console and from a virtual console through the iDrac
[*]Confirm that the installation procedure has recognized the eno interface, and configured it for DHCP, and a valid address has been assigned
[*]In SystemSettings->Connections->IPv4, set that eno "Wired connection" to manual assignment, and specify the IP address -- say, 192.168.1.100 -- netmask, and gateway.  Click apply.
[*]sudo apt install net-tools
[*]In a shell, execute "ifconfig eno2 down", wait for confirmation, and follow with "ifconfig eno2 up"
[*]Run "ip a" or "ifconfig -a" and confirm that eno2 is now configured with 192.168.1.100 -- and none of the other addresses are.
[*]Ping some addresses or otherwise confirm network operation
[*]Reboot
[*]Repeat step 8.
[/LIST]

Expected Behavior:
Interface configuration should remain the same, specifically eno2 should be 192.168.1.100, enos 1,3,4 should be unconfigured, and the iDrac card should maintain its previous address

Observed Behavior:
iDrac card gets assigned 192.168.1.100 -- even though it's attached to a different subnet -- and none of the eno interfaces have an IP address assigned at all.  Network is dysfunctional as a result, obviously.

What could cause this, and how can it be corrected?


To clarify, all of the hardware involved is known-good.  Tests with other operating systems -- Rocky and Manjaro -- work exactly as expected.  Two different Ubuntu ISOs on two different USB sticks have been used to install on the R720, and the problem is repeated.  Same ISOs have been used to install on other machines without issue.  For the record, the R720 in question is pretty standard.  Dual Xeon E5-2640s, 192GB RAM, and 7 2.5" disks of varying type.  Nothing else is installed, specifically, no additional network cards or anything like that.

My first response was that I must have erred on step 5, and accidentally reconfigured the iDrac card -- but that's not it.  I've re-done the installation several times now, and triple-checked my work. Furthermore, if this were the cause, it would be revealed in steps 7 through 9, and it's not.

Something is altering the network configuration on reboot, well after the changes have been made in SystemSettings, and confirmed with other tools.  Who could that be?

Thanks.

---

