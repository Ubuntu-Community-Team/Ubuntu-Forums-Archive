---
title: "Kubuntu 2x NIC tagged VLAN not connecting to Windows network"
date: 2024-03-02
forum: Networking &amp; Wireless
---

### Post by naraidoo on 2024-03-02
[B][I]Configuration

[/I][/B]
[LIST=1]
[*]Windows Server 2022 Datacenter Edition running Hyper-V
[*]Physical Ubiquiti Layer 2 Switch
[*]Virtual Switch (name = VMSwitch) configured as External based on physical Intel quad port X550 NIC (port #2)
[*]Server port #2 connects to Layer 2 port #2
[*]Layer 2 port #2 is untagged VLAN 300 and tagged VLAN 50
[*]Kubuntu 23.10 virtual machine (name = KuDev01) with KDE Plasma 5.27.8 Kernel 6.5.0-21 64-bit
[*]In Hyper-V KuDev01 given 2x virtual network adapters:
[LIST]
[*]vSwitch.300 is untagged - it should connect via VMSwitch and physical Intel NIC port #2 to a physical Layer 2 switch port #2 and exchange untagged traffic on VLAN 300
[*]vSwitch.50 is tagged - It should connect via VMSwitch and physical physical Intel NIC port #2 to a physical Layer 2 switch port #2 and exchange tagged traffic on VLAN 50
[/LIST]

[*]To configure for VLANS in KuDev01 I followed this article [https://wiki.ubuntu.com/vlan](https://wiki.ubuntu.com/vlan)
[*]In Terminal ifconfig shows:
[LIST]
[*]eth0 (associated with vSwitch.300) receives DHCP IP lease from DHCP server 10.10.300.1/24. It correctly gets 10.10.300.11/24 showing traffic via VLAN 300 is flowing correctly
[*]eth1 (associated with vSwitch.50) does not receive DHCP IP lease from DHCP server 10.10.50.1/24. It does not get the reserved IP address associated with the MAC.
[*]eth1.50 (associated with vSwitch.50) cannot use the static IP address assigned to it in step (8) and cannot connect to tagged VLAN 50.
[/LIST]
[/LIST]

[B][I]Problem Statement
[/I][/B]
The Kubuntu virtual machine cannot connect to the devices on tagged VLAN 50. 
(Additional problem) When the VM is rebooted, the configuration for eth1.50 needs to be reapplied manually (despite following the instructions in [https://wiki.ubuntu.com/vlan](https://wiki.ubuntu.com/vlan)).

[B][I]Troubleshooting So Far
[/I][/B]
[LIST=1]
[*]I have a Windows 11 VM configured with exactly the same settings as set out in steps (7) and (9) above, and VLAN 300 and VLAN 50 traffic properly reaches devices on those VLANs.
[*]Conclusion - Problem is not with Hyper-V virtual switch configuration.
[*]Conclusion - Problem is not with Layer 2 Switch  port and traffic configuration.
[*]Conclusion - Problem is with networking in Kubuntu VM.
[/LIST]

[B][I]Question
[/I][/B]How do I troubleshoot and fix this please?

---

