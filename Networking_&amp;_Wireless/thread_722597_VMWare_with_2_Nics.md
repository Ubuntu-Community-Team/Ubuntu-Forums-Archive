---
title: "VMWare with 2 Nics"
date: 2008-03-12
forum: Networking &amp; Wireless
---

### Post by MockY on 2008-03-12
Here is what am trying to accomplish:

I have Gutsy as host OS and Windows XP as guest. I have 2 nics installed and in working order. I want to use one of the NICs for the Ubuntu OS and the other NIC for the host, but both on the same network. However, there is no option for selecting what NIC I want to use in VMWare Workstation. I have this setup with VirtualPC but I have no clue how to do it in VMWare Workstation.

In other words, I want the host and the guest to act as 2 completely different machines in the network, without having to share the same IP address. 

I am a bit confused and would like some help.

---

### Post by supremedalek on 2008-04-15
I cannot say if this will work for vmware workstation, but I am running vmware server in an unbuntu 7.10 box with 5 nics. This is how I assigned a few of those to vmware:

```
raub@keg:~$ sudo vmware-config.pl
[sudo] password for raub:
Making sure services for VMware Server are stopped.

Stopping VMware services:
   Virtual machine monitor                                             done
   Bridged networking on /dev/vmnet0                                   done
   DHCP server on /dev/vmnet1                                          done
   Host-only networking on /dev/vmnet1                                 done
   DHCP server on /dev/vmnet8                                          done
   NAT service on /dev/vmnet8                                          done
   Host-only networking on /dev/vmnet8                                 done
   Virtual ethernet                                                    done

Configuring fallback GTK+ 2.4 libraries.                                        
[...]
You have already setup networking.

Would you like to skip networking setup and keep your old settings as they are?
(yes/no) [no]

Do you want networking for your virtual machines? (yes/no/help) [yes]

Would you prefer to modify your existing networking configuration using the
wizard or the editor? (wizard/editor/help) [editor]

The following virtual networks have been defined:

. vmnet0 is bridged to eth1
. vmnet1 is a host-only network on private subnet 192.168.215.0.
. vmnet8 is a NAT network on private subnet 192.168.209.0.

Do you wish to make any changes to the current virtual networks settings?
(yes/no) [no] y

Which virtual network do you wish to configure? (0-99) 2

What type of virtual network do you wish to set vmnet2?
(bridged,hostonly,nat,none) [none] b

Configuring a bridged network for vmnet2.

Your computer has multiple ethernet network interfaces available: eth0, eth2,
eth3, eth4, vmnet1, vmnet8, wlan0. Which one do you want to bridge to vmnet2?
[eth0] eth2

The following virtual networks have been defined:

. vmnet0 is bridged to eth1
. vmnet1 is a host-only network on private subnet 192.168.215.0.
. vmnet2 is bridged to eth2
. vmnet8 is a NAT network on private subnet 192.168.209.0.                      

Do you wish to make additional changes to the current virtual networks
settings? (yes/no) [yes] no

Extracting the sources of the vmnet module.                                     

```

Note I've already had eth1 being used; in a previous vmware-config.pl session I had told it not to use eth0 and then added eth1. This time I then also added eth2.

On the other hand, to even use one single nic without sharing the same ip, all you had to do is to go in bridged mode under vmware.

---

### Post by mesocal on 2008-07-08
supremedalek is right on the money with this.  I don't know if you have to run through the whole vmware-config.pl just to adjust the nic.  

as for me, i just bridged eth0 to vmnet0 and eth1 to vmnet1 during the vmware-config.pl setup wizard (since you can choose either wizard or text editor, it makes me think that you can just edit some config files instead of running the whole vmware-config.pl).

good luck.

---

