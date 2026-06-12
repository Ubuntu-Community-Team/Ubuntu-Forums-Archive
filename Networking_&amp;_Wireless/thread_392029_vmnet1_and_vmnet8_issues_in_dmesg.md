---
title: "vmnet1 and vmnet8 issues in dmesg?"
date: 2007-03-24
forum: Networking &amp; Wireless
---

### Post by JohnPhys on 2007-03-24
Hey all,

I seem to have messages in dmesg that constantly show up involving the vmware networking devices vmnet1 and vmnet8,

```

[17214852.132000] Unknown OutputIN= OUT=vmnet1 SRC=172.16.22.1 DST=172.16.22.255 LEN=198 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=178
[17214852.132000] Unknown OutputIN= OUT=vmnet8 SRC=172.16.49.1 DST=172.16.49.255 LEN=198 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=178
[17214853.132000] Unknown OutputIN= OUT=vmnet1 SRC=172.16.22.1 DST=172.16.22.255 LEN=190 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=170
[17214853.132000] Unknown OutputIN= OUT=vmnet8 SRC=172.16.49.1 DST=172.16.49.255 LEN=190 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=170
[17214879.032000] Unknown OutputIN= OUT=vmnet1 SRC=172.16.22.1 DST=172.16.22.255 LEN=260 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=240
[17214879.032000] Unknown OutputIN= OUT=vmnet8 SRC=172.16.49.1 DST=172.16.49.255 LEN=260 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=138 DPT=138 LEN=240
[17214883.284000] Unknown OutputIN= OUT=vmnet1 SRC=172.16.22.1 DST=172.16.22.255 LEN=198 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=178
[17214883.284000] Unknown OutputIN= OUT=vmnet8 SRC=172.16.49.1 DST=172.16.49.255 LEN=198 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=178
[17214884.288000] Unknown OutputIN= OUT=vmnet1 SRC=172.16.22.1 DST=172.16.22.255 LEN=190 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=170
[17214884.288000] Unknown OutputIN= OUT=vmnet8 SRC=172.16.49.1 DST=172.16.49.255 LEN=190 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=631 DPT=631 LEN=170


```

...and on and on like that, another 2 lines being added every so often.  Can anyone help me understand what might be causing it?  Thanks!

---

### Post by ani5lin on 2007-04-01
I have the same issue. It has something to do with the firestarter, if i dissable firewall, I get no messages..., despite the messages, everything seems to be working well, (samba share, vmware...)

---

### Post by ani5lin on 2007-04-03
I've reconfigured vmware for NAT networking (without Host only option, so that i dont have another network device - vmnet1), enabled internet connection sharing in firestarter for vmnet8, and allowed samba services for the vmware IP range, now the messages are gone.

---

### Post by JohnPhys on 2007-04-04
Thanks for the replies, I'll have to try them when I get my VM up and running again!

---

### Post by JohnPhys on 2007-04-27
How did you reconfigure the vm for NAT?  I get the messages even when not running the vm.

---

### Post by ani5lin on 2007-05-06
The default installation of VM  configures it with NAT and Host-only networking. Try running vmware-config.pl and when it says: "Do you want to use Host-Only networking..." or something like that- I don't remember exactly... choose NO, keep hitting enter for all other options...

The reason why I configured it for one of the two networking types, and not both, is because firestarter only supports one interface for the local network configuration. You can choose vmnet8 and make the messages disappear for vmnet8, but you still have vmnet1...

Again, I had this issue when using firestarter, if firewall is disabled (in firestarter) the messages are gone. If you are using firestarter, this should help you, otherwise I dont know what the problem could be. And, yes, I had these messages also when VM was turned off, now they are gone

When VM is configured for one type of networking only, open preferences in firestarter, Enable connection sharing in Network settings, and choose device (in my case vmnet8 ), then figure out which IP is assigned to the device (vmnet8 ) in my case 192.168.187.X, then go to policy, add rule for allowed services, choose samba, and for the IP choose (replace with your IP) 192.168.187.1/24  - 24 is there, so that it  makes all IPs from 192.168.187.1 to 192.168.187.254 allowed. 

Hope it helps

---

### Post by spacedoubtman on 2007-12-29
Hi,

I just found its possible to disable logging in firestart by editing /etc/firestarter/configuration and changing the line
LOG_LEVEL=info
to be
LOG_LEVEL=none

Thanks,
Adam

---

### Post by JohnPhys on 2008-01-26
Thanks for the info.  Unfortunately, I want the logging to exist, I just want it to go to a separate file.  Thanks for the advice though!

---

