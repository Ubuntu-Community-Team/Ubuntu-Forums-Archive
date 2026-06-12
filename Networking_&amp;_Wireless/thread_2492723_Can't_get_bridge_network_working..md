---
title: "Can't get bridge network working."
date: 2023-11-21
forum: Networking &amp; Wireless
---

### Post by johantonissen on 2023-11-21
Hi there!


I have a intel nuc which runs a server with several docker container and several services running on bare metal. I would like to run django project i'm building on a docker container in a VM using Virtual Machine Manager. I'm however unable to get the bridge network going, NAT works like a charm but I want to be able to access the VM from outside my network.


Here's my system info:
```

cat /etc/os-release
PRETTY_NAME="Ubuntu 22.04.3 LTS"
NAME="Ubuntu"
VERSION_ID="22.04"
VERSION="22.04.3 LTS (Jammy Jellyfish)"
VERSION_CODENAME=jammy
ID=ubuntu
ID_LIKE=debian
HOME_URL="https://www.ubuntu.com/"
SUPPORT_URL="https://help.ubuntu.com/"
BUG_REPORT_URL="https://bugs.launchpad.net/ubuntu/"
PRIVACY_POLICY_URL="https://www.ubuntu.com/legal/terms-and-policies/privacy-policy"
UBUNTU_CODENAME=jammy

```


Here's my ethernet info, my server is connected over ethernet and my wifi is disabled:
```

lspci -nnk | grep net -A2
00:1f.6 Ethernet controller [0200]: Intel Corporation Ethernet Connection (6) I219-V [8086:15be] (rev 30)
	DeviceName:  LAN
	Subsystem: Intel Corporation Ethernet Connection (6) I219-V [8086:2074]
	Kernel driver in use: e1000e
	Kernel modules: e1000e

```


heres my ip info:
```

ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 1c:69:7a:62:9e:0b brd ff:ff:ff:ff:ff:ff
    altname enp0s31f6
    inet 192.168.2.250/24 brd 192.168.2.255 scope global noprefixroute eno1
       valid_lft forever preferred_lft forever
    inet6 fd9d:99c7:1326:1:e95d:7a14:4e27:eb2a/64 scope global temporary dynamic 
       valid_lft 1644sec preferred_lft 1644sec
    inet6 fd9d:99c7:1326:1:cd38:20de:c11c:3ad5/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 1644sec preferred_lft 1644sec
    inet6 fe80::876e:8ae4:88f1:c9c/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
3: wlp0s20f3: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 92:84:ea:34:ef:8c brd ff:ff:ff:ff:ff:ff permaddr d8:3b:bf:50:6c:d4
4: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 52:54:00:c5:7a:52 brd ff:ff:ff:ff:ff:ff
    inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0
       valid_lft forever preferred_lft forever
5: br-a4b4ab0978d7: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:46:33:4e:69 brd ff:ff:ff:ff:ff:ff
    inet 172.31.0.1/16 brd 172.31.255.255 scope global br-a4b4ab0978d7
       valid_lft forever preferred_lft forever
    inet6 fe80::42:46ff:fe33:4e69/64 scope link 
       valid_lft forever preferred_lft forever
6: br-d97364d42154: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether 02:42:7e:66:76:38 brd ff:ff:ff:ff:ff:ff
    inet 172.27.0.1/16 brd 172.27.255.255 scope global br-d97364d42154
       valid_lft forever preferred_lft forever
7: br-e98e97cb4545: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:fe:6a:a9:87 brd ff:ff:ff:ff:ff:ff
    inet 172.24.0.1/16 brd 172.24.255.255 scope global br-e98e97cb4545
       valid_lft forever preferred_lft forever
    inet6 fe80::42:feff:fe6a:a987/64 scope link 
       valid_lft forever preferred_lft forever
8: br-9824dd83e841: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether 02:42:4b:df:5e:a4 brd ff:ff:ff:ff:ff:ff
    inet 172.21.0.1/16 brd 172.21.255.255 scope global br-9824dd83e841
       valid_lft forever preferred_lft forever
9: docker0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:3c:61:fd:4f brd ff:ff:ff:ff:ff:ff
    inet 172.17.0.1/16 brd 172.17.255.255 scope global docker0
       valid_lft forever preferred_lft forever
    inet6 fe80::42:3cff:fe61:fd4f/64 scope link 
       valid_lft forever preferred_lft forever
10: br-58f17667ca98: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:3d:b5:38:d2 brd ff:ff:ff:ff:ff:ff
    inet 172.19.0.1/16 brd 172.19.255.255 scope global br-58f17667ca98
       valid_lft forever preferred_lft forever
    inet6 fe80::42:3dff:feb5:38d2/64 scope link 
       valid_lft forever preferred_lft forever
11: br-627d09ae2f5d: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether 02:42:8a:b5:2c:e9 brd ff:ff:ff:ff:ff:ff
    inet 172.26.0.1/16 brd 172.26.255.255 scope global br-627d09ae2f5d
       valid_lft forever preferred_lft forever
12: br-e4866286311b: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:06:71:51:8b brd ff:ff:ff:ff:ff:ff
    inet 192.168.16.1/20 brd 192.168.31.255 scope global br-e4866286311b
       valid_lft forever preferred_lft forever
    inet6 fe80::42:6ff:fe71:518b/64 scope link 
       valid_lft forever preferred_lft forever
13: br-fbdcacafda66: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether 02:42:e3:38:a8:c5 brd ff:ff:ff:ff:ff:ff
    inet 172.20.0.1/16 brd 172.20.255.255 scope global br-fbdcacafda66
       valid_lft forever preferred_lft forever
14: br-0cb6bbaa2dcb: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether 02:42:82:3c:c0:0e brd ff:ff:ff:ff:ff:ff
    inet 172.29.0.1/16 brd 172.29.255.255 scope global br-0cb6bbaa2dcb
       valid_lft forever preferred_lft forever
15: br-41995dedb449: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:38:0b:ae:aa brd ff:ff:ff:ff:ff:ff
    inet 192.168.32.1/20 brd 192.168.47.255 scope global br-41995dedb449
       valid_lft forever preferred_lft forever
    inet6 fe80::42:38ff:fe0b:aeaa/64 scope link 
       valid_lft forever preferred_lft forever
16: br-65577ea7f86d: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:41:84:5a:88 brd ff:ff:ff:ff:ff:ff
    inet 172.22.0.1/16 brd 172.22.255.255 scope global br-65577ea7f86d
       valid_lft forever preferred_lft forever
    inet6 fe80::42:41ff:fe84:5a88/64 scope link 
       valid_lft forever preferred_lft forever
17: br-b3a0915ddff3: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether 02:42:25:f1:dd:05 brd ff:ff:ff:ff:ff:ff
    inet 172.28.0.1/16 brd 172.28.255.255 scope global br-b3a0915ddff3
       valid_lft forever preferred_lft forever
18: br-1fa631a66ed2: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether 02:42:0b:f0:d9:97 brd ff:ff:ff:ff:ff:ff
    inet 172.25.0.1/16 brd 172.25.255.255 scope global br-1fa631a66ed2
       valid_lft forever preferred_lft forever
19: br-e50cee81d109: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:59:2f:ca:c0 brd ff:ff:ff:ff:ff:ff
    inet 172.23.0.1/16 brd 172.23.255.255 scope global br-e50cee81d109
       valid_lft forever preferred_lft forever
    inet6 fe80::42:59ff:fe2f:cac0/64 scope link 
       valid_lft forever preferred_lft forever
20: br-832c2ec7c010: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:6c:e5:c0:2a brd ff:ff:ff:ff:ff:ff
    inet 172.18.0.1/16 brd 172.18.255.255 scope global br-832c2ec7c010
       valid_lft forever preferred_lft forever
    inet6 fe80::42:6cff:fee5:c02a/64 scope link 
       valid_lft forever preferred_lft forever
22: veth4ac3d6b@if21: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-832c2ec7c010 state UP group default 
    link/ether 8e:e5:49:e3:4e:39 brd ff:ff:ff:ff:ff:ff link-netnsid 6
    inet6 fe80::8ce5:49ff:fee3:4e39/64 scope link 
       valid_lft forever preferred_lft forever
26: veth89151ca@if25: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-a4b4ab0978d7 state UP group default 
    link/ether 6a:1b:4a:fe:13:52 brd ff:ff:ff:ff:ff:ff link-netnsid 14
    inet6 fe80::681b:4aff:fefe:1352/64 scope link 
       valid_lft forever preferred_lft forever
28: vethfed031a@if27: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-e4866286311b state UP group default 
    link/ether be:ed:5e:c9:f2:35 brd ff:ff:ff:ff:ff:ff link-netnsid 10
    inet6 fe80::bced:5eff:fec9:f235/64 scope link 
       valid_lft forever preferred_lft forever
30: vethff29f54@if29: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-e98e97cb4545 state UP group default 
    link/ether f2:19:51:88:5b:81 brd ff:ff:ff:ff:ff:ff link-netnsid 0
    inet6 fe80::f019:51ff:fe88:5b81/64 scope link 
       valid_lft forever preferred_lft forever
32: veth29ff70c@if31: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-e50cee81d109 state UP group default 
    link/ether b2:8f:08:a6:2e:52 brd ff:ff:ff:ff:ff:ff link-netnsid 11
    inet6 fe80::b08f:8ff:fea6:2e52/64 scope link 
       valid_lft forever preferred_lft forever
36: veth317c60e@if35: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-41995dedb449 state UP group default 
    link/ether 9a:2c:87:36:ad:26 brd ff:ff:ff:ff:ff:ff link-netnsid 5
    inet6 fe80::982c:87ff:fe36:ad26/64 scope link 
       valid_lft forever preferred_lft forever
38: veth736fa80@if37: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-e50cee81d109 state UP group default 
    link/ether da:c8:5c:98:e0:5a brd ff:ff:ff:ff:ff:ff link-netnsid 12
    inet6 fe80::d8c8:5cff:fe98:e05a/64 scope link 
       valid_lft forever preferred_lft forever
40: vethe93905e@if39: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master docker0 state UP group default 
    link/ether c2:5d:a7:56:dc:5a brd ff:ff:ff:ff:ff:ff link-netnsid 3
    inet6 fe80::c05d:a7ff:fe56:dc5a/64 scope link 
       valid_lft forever preferred_lft forever
42: veth709add6@if41: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-a4b4ab0978d7 state UP group default 
    link/ether ce:69:98:ed:7d:03 brd ff:ff:ff:ff:ff:ff link-netnsid 8
    inet6 fe80::cc69:98ff:feed:7d03/64 scope link 
       valid_lft forever preferred_lft forever
44: vethc6f7fa1@if43: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-58f17667ca98 state UP group default 
    link/ether 32:6b:fc:b1:54:60 brd ff:ff:ff:ff:ff:ff link-netnsid 9
    inet6 fe80::306b:fcff:feb1:5460/64 scope link 
       valid_lft forever preferred_lft forever
46: veth0d17d2a@if45: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-e50cee81d109 state UP group default 
    link/ether ce:55:6f:26:3f:76 brd ff:ff:ff:ff:ff:ff link-netnsid 7
    inet6 fe80::cc55:6fff:fe26:3f76/64 scope link 
       valid_lft forever preferred_lft forever
48: vetha7f5de7@if47: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-a4b4ab0978d7 state UP group default 
    link/ether 4e:86:8d:38:58:5d brd ff:ff:ff:ff:ff:ff link-netnsid 13
    inet6 fe80::4c86:8dff:fe38:585d/64 scope link 
       valid_lft forever preferred_lft forever
52: vethafabf2c@if51: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-65577ea7f86d state UP group default 
    link/ether 7a:8b:14:0b:59:4c brd ff:ff:ff:ff:ff:ff link-netnsid 3
    inet6 fe80::788b:14ff:fe0b:594c/64 scope link 
       valid_lft forever preferred_lft forever
54: vethf05a12e@if53: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master docker0 state UP group default 
    link/ether 56:96:05:8c:76:e4 brd ff:ff:ff:ff:ff:ff link-netnsid 2
    inet6 fe80::5496:5ff:fe8c:76e4/64 scope link 
       valid_lft forever preferred_lft forever
56: veth2b4ab69@if55: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-41995dedb449 state UP group default 
    link/ether 4e:5c:97:64:7b:87 brd ff:ff:ff:ff:ff:ff link-netnsid 3
    inet6 fe80::4c5c:97ff:fe64:7b87/64 scope link 
       valid_lft forever preferred_lft forever
58: veth263bb73@if57: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master docker0 state UP group default 
    link/ether ea:62:43:ab:ee:38 brd ff:ff:ff:ff:ff:ff link-netnsid 15
    inet6 fe80::e862:43ff:feab:ee38/64 scope link 
       valid_lft forever preferred_lft forever
1142: cali9ef2ca550b7@if3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether ee:ee:ee:ee:ee:ee brd ff:ff:ff:ff:ff:ff link-netns cni-81847f82-1962-a353-2ac5-3f3ed0a967cf
    inet6 fe80::ecee:eeff:feee:eeee/64 scope link 
       valid_lft forever preferred_lft forever
1143: calidb89c5c550a@if3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether ee:ee:ee:ee:ee:ee brd ff:ff:ff:ff:ff:ff link-netns cni-f75b679a-10fe-32d3-352b-036b6b16a4ee
    inet6 fe80::ecee:eeff:feee:eeee/64 scope link 
       valid_lft forever preferred_lft forever
1144: caliad442cc56ba@if3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether ee:ee:ee:ee:ee:ee brd ff:ff:ff:ff:ff:ff link-netns cni-378d769a-15e0-effb-8c65-e8ca36015df6
    inet6 fe80::ecee:eeff:feee:eeee/64 scope link 
       valid_lft forever preferred_lft forever
1145: cali4e3f42ded4c@if3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether ee:ee:ee:ee:ee:ee brd ff:ff:ff:ff:ff:ff link-netns cni-a32b2f64-5a70-3abc-2b98-afaa7f0a0c56
    inet6 fe80::ecee:eeff:feee:eeee/64 scope link 
       valid_lft forever preferred_lft forever
1146: cali84be666b758@if3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether ee:ee:ee:ee:ee:ee brd ff:ff:ff:ff:ff:ff link-netns cni-47f8c6c8-8034-fa83-dd86-f974f9dcb7b9
    inet6 fe80::ecee:eeff:feee:eeee/64 scope link 
       valid_lft forever preferred_lft forever
1147: califee36422fdd@if3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether ee:ee:ee:ee:ee:ee brd ff:ff:ff:ff:ff:ff link-netns cni-6b48ae83-a3c6-2b2f-a0f4-831c979d82f8
    inet6 fe80::ecee:eeff:feee:eeee/64 scope link 
       valid_lft forever preferred_lft forever
1148: cali6d55d0fcd5b@if3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether ee:ee:ee:ee:ee:ee brd ff:ff:ff:ff:ff:ff link-netns cni-599871a6-9a3d-90fe-f6aa-27ec3ed77164
    inet6 fe80::ecee:eeff:feee:eeee/64 scope link 
       valid_lft forever preferred_lft forever
1149: cali0399de1aa1d@if3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether ee:ee:ee:ee:ee:ee brd ff:ff:ff:ff:ff:ff link-netns cni-43461439-e69e-8703-8a06-aa029ddf0491
    inet6 fe80::ecee:eeff:feee:eeee/64 scope link 
       valid_lft forever preferred_lft forever
1150: calic4f9df93190@if3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether ee:ee:ee:ee:ee:ee brd ff:ff:ff:ff:ff:ff link-netns cni-c3729389-f04c-062a-b336-82f37c6fd246
    inet6 fe80::ecee:eeff:feee:eeee/64 scope link 
       valid_lft forever preferred_lft forever
1151: caliba400f0ef55@if3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether ee:ee:ee:ee:ee:ee brd ff:ff:ff:ff:ff:ff link-netns cni-d563618a-f441-75d3-b3c0-d40dc5deea83
    inet6 fe80::ecee:eeff:feee:eeee/64 scope link 
       valid_lft forever preferred_lft forever
1152: caliab7bb467db7@if3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether ee:ee:ee:ee:ee:ee brd ff:ff:ff:ff:ff:ff link-netns cni-b63a5e1f-4b0b-ba60-204f-4dd1ef046aae
    inet6 fe80::ecee:eeff:feee:eeee/64 scope link 
       valid_lft forever preferred_lft forever
1153: cali3796c15a1a8@if3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether ee:ee:ee:ee:ee:ee brd ff:ff:ff:ff:ff:ff link-netns cni-77c5aab9-c940-2215-72b5-97761714cf90
    inet6 fe80::ecee:eeff:feee:eeee/64 scope link 
       valid_lft forever preferred_lft forever
1156: vxlan.calico: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1450 qdisc noqueue state UNKNOWN group default 
    link/ether 66:af:58:c7:03:8e brd ff:ff:ff:ff:ff:ff
    inet 10.1.178.0/32 scope global vxlan.calico
       valid_lft forever preferred_lft forever
    inet6 fe80::64af:58ff:fec7:38e/64 scope link 
       valid_lft forever preferred_lft forever
903: veth0e67c6e@if902: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master docker0 state UP group default 
    link/ether 56:92:3a:ca:70:3e brd ff:ff:ff:ff:ff:ff link-netnsid 1
    inet6 fe80::5492:3aff:feca:703e/64 scope link 
       valid_lft forever preferred_lft forever

```


Heres my network interfaces:
```

sudo nano /etc/network/interfaces
source /etc/network/interfaces.d/*


auto lo
iface lo inet loopback

```


I've tried multiple guides to get a bridge working but all failed. I've tried to build a bridge network and add ethernet connection as a slave using nmtui but then I got the error that I can't activate the bridged network. I've also tried to add the bridge using brctl but that also did not have any effect. The weird thing is that when I've created a a bridge it was set on as DOWN and I've tried to change the status to UP, but when I do that the status in 'ip a' does not change, even after restarting the network service.


My server has an IP of 192.168.2.250 and my router had the IP of 192.168.2.254. However the ip range of my VM always ended up being in the range 192.168.122.*.  The VM is running fedora 39 server and should have an ip of 192.168.2.251.


Does anyone have an idea what i'm doing wrong ?

---

### Post by TheFu on 2023-11-21
/etc/network/interfaces was deprecated around 2019.  Use netplan.  Documentation for it is here: [https://netplan.io/](https://netplan.io/)  There is an examples page which has a bridge example there.

I know nothing about docker. We use lxc containers here, but the network bridges are part of the network layer, not the containers beyond telling each container which bridge to use. Same for virtual machines. Bridges are outside the hypervisor management.

---

### Post by johantonissen on 2023-11-21
okay i've tried using netplan but getting some weird errors.
This is my netplan now:


```

network:
  version: 2
  renderer: networkd
  ethernets:
    eno1:
      addresses:
        - 192.168.2.250/24
      nameservers:
        addresses: [8.8.8.8, 8.8.4.4]
      routes:
        - to: default
          via: 192.168.2.254
  bridges:
    br0:
      interfaces:
        - eno1
      addresses:
        - 192.168.2.251/24
      nameservers:
        addresses: [8.8.8.8, 8.8.4.4]
      routes:
        - to: default
          via: 192.168.2.254

```


and this are my errors:


```

sudo netplan apply


** (generate:2273852): WARNING **: 20:03:32.844: Problem encountered while validating default route consistency.Please set up multiple routing tables and use `routing-policy` instead.
Error: Conflicting default route declarations for IPv4 (table: main, metric: default), first declared in br0 but also in eno1
WARNING:root:Cannot call Open vSwitch: ovsdb-server.service is not running.


** (process:2273850): WARNING **: 20:03:33.554: Problem encountered while validating default route consistency.Please set up multiple routing tables and use `routing-policy` instead.
Error: Conflicting default route declarations for IPv4 (table: main, metric: default), first declared in br0 but also in eno1


** (process:2273850): WARNING **: 20:03:35.183: Problem encountered while validating default route consistency.Please set up multiple routing tables and use `routing-policy` instead.
Error: Conflicting default route declarations for IPv4 (table: main, metric: default), first declared in br0 but also in eno1


** (process:2273850): WARNING **: 20:03:35.183: Problem encountered while validating default route consistency.Please set up multiple routing tables and use `routing-policy` instead.
Error: Conflicting default route declarations for IPv4 (table: main, metric: default), first declared in br0 but also in eno1



```


I'm trying to get these to understand and trying to look for routing-policy in [https://netplan.readthedocs.io/en/latest/netplan-yaml/](https://netplan.readthedocs.io/en/latest/netplan-yaml/) but i have troubles figuring it out. Can someone help me explain whats wrong?

---

### Post by ian-weisser on 2023-11-21
Here's an example of Netplan YAML that works without error:

```

# /etc/netplan/00-server-config.yaml

network:
  version: 2
  renderer: networkd
  ethernets:
    enp0s7:
      dhcp4: false
      dhcp6: false

  bridges:
    br0:
      interfaces: [enp0s7]
      dhcp4: true
      dhcp6: true

```

and here's the corresponding "ip a" output:

```

2: enp0s7: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel master br0 state UP group default qlen 1000
    link/ether 00:30:6d:3d:72:7c brd ff:ff:ff:ff:ff:ff
3: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether ea:6c:3c:63:5c:47 brd ff:ff:ff:ff:ff:ff
    inet 192.168.1.9/24 metric 100 brd 192.168.1.255 scope global dynamic br0
       valid_lft 499sec preferred_lft 499sec
    inet6 fe80::e86c:3cff:fe63:5c47/64 scope link 
       valid_lft forever preferred_lft forever

```

Note that the bridge gets the IP address, not the eth  interface.
To ssh to the server, use the bridge IP address.

Containers on this server get different IP addresses on the same subnet (of course, it's bridging) from the LAN hardware router.
To ssh to a container, use that container's IP address (not listed here).

In this case, static IP addresses are set on the router (MAC reservation for DHCP), not on each system. Hence the dhcp:true setting instead a specified IP address.

---

### Post by Doug S on 2023-11-21
I think, but am not certain, you need this:

```
network:
  version: 2
  renderer: networkd
  ethernets:
    eno1:
      dhcp4: no
  bridges:
    br0:
      interfaces:
        - eno1
      addresses:
        - 192.168.2.25[COLOR="#FF0000"]0[/COLOR]/24
      nameservers:
        addresses: [8.8.8.8, 8.8.4.4]
      routes:
        - to: default
          via: 192.168.2.254
```
And your VM needs to be set to use bridge networking and to have 192.168.2.251.

---

### Post by johantonissen on 2023-11-21
Thank you!

My question is, then, how do i make sure my server gets 192.168.2.250 and the vm running on that server gets 192.168.2.251 if i only am supplying 1 static ip address ?

---

### Post by johantonissen on 2023-11-21
okay i've changed the settings now and my physical server still has the ip i want it to have (192.168.2.250).

```

network:
  version: 2
  renderer: networkd
  ethernets:
    eno1:
      dhcp4: no
  bridges:
    br0:
      interfaces:
        - eno1
      addresses:
        - 192.168.2.25[COLOR=#FF0000]0[/COLOR]/24
      nameservers:
        addresses: [8.8.8.8, 8.8.4.4]
      routes:
        - to: default
          via: 192.168.2.254

```

However when i run netplan apply I get one error:
```

sudo netplan apply
[sudo] password for planet: 
WARNING:root:Cannot call Open vSwitch: ovsdb-server.service is not running.

```

Ive tried starting and enableing the service but it does not exist.

My ip is as follows, the br0 seems to be up with ip 192.168.2.250;
```

ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel master br0 state UP group default qlen 1000
    link/ether 1c:69:7a:62:9e:0b brd ff:ff:ff:ff:ff:ff
    altname enp0s31f6
3: wlp0s20f3: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether e6:3c:f3:6a:91:95 brd ff:ff:ff:ff:ff:ff permaddr d8:3b:bf:50:6c:d4
4: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 52:54:00:c5:7a:52 brd ff:ff:ff:ff:ff:ff
    inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0
       valid_lft forever preferred_lft forever
5: br-a4b4ab0978d7: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:46:33:4e:69 brd ff:ff:ff:ff:ff:ff
    inet 172.31.0.1/16 brd 172.31.255.255 scope global br-a4b4ab0978d7
       valid_lft forever preferred_lft forever
    inet6 fe80::42:46ff:fe33:4e69/64 scope link 
       valid_lft forever preferred_lft forever
6: br-d97364d42154: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether 02:42:7e:66:76:38 brd ff:ff:ff:ff:ff:ff
    inet 172.27.0.1/16 brd 172.27.255.255 scope global br-d97364d42154
       valid_lft forever preferred_lft forever
7: br-e98e97cb4545: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:fe:6a:a9:87 brd ff:ff:ff:ff:ff:ff
    inet 172.24.0.1/16 brd 172.24.255.255 scope global br-e98e97cb4545
       valid_lft forever preferred_lft forever
    inet6 fe80::42:feff:fe6a:a987/64 scope link 
       valid_lft forever preferred_lft forever
8: br-9824dd83e841: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether 02:42:4b:df:5e:a4 brd ff:ff:ff:ff:ff:ff
    inet 172.21.0.1/16 brd 172.21.255.255 scope global br-9824dd83e841
       valid_lft forever preferred_lft forever
9: docker0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:3c:61:fd:4f brd ff:ff:ff:ff:ff:ff
    inet 172.17.0.1/16 brd 172.17.255.255 scope global docker0
       valid_lft forever preferred_lft forever
    inet6 fe80::42:3cff:fe61:fd4f/64 scope link 
       valid_lft forever preferred_lft forever
10: br-58f17667ca98: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:3d:b5:38:d2 brd ff:ff:ff:ff:ff:ff
    inet 172.19.0.1/16 brd 172.19.255.255 scope global br-58f17667ca98
       valid_lft forever preferred_lft forever
    inet6 fe80::42:3dff:feb5:38d2/64 scope link 
       valid_lft forever preferred_lft forever
11: br-627d09ae2f5d: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether 02:42:8a:b5:2c:e9 brd ff:ff:ff:ff:ff:ff
    inet 172.26.0.1/16 brd 172.26.255.255 scope global br-627d09ae2f5d
       valid_lft forever preferred_lft forever
12: br-e4866286311b: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:06:71:51:8b brd ff:ff:ff:ff:ff:ff
    inet 192.168.16.1/20 brd 192.168.31.255 scope global br-e4866286311b
       valid_lft forever preferred_lft forever
    inet6 fe80::42:6ff:fe71:518b/64 scope link 
       valid_lft forever preferred_lft forever
13: br-fbdcacafda66: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether 02:42:e3:38:a8:c5 brd ff:ff:ff:ff:ff:ff
    inet 172.20.0.1/16 brd 172.20.255.255 scope global br-fbdcacafda66
       valid_lft forever preferred_lft forever
14: br-0cb6bbaa2dcb: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether 02:42:82:3c:c0:0e brd ff:ff:ff:ff:ff:ff
    inet 172.29.0.1/16 brd 172.29.255.255 scope global br-0cb6bbaa2dcb
       valid_lft forever preferred_lft forever
15: br-41995dedb449: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:38:0b:ae:aa brd ff:ff:ff:ff:ff:ff
    inet 192.168.32.1/20 brd 192.168.47.255 scope global br-41995dedb449
       valid_lft forever preferred_lft forever
    inet6 fe80::42:38ff:fe0b:aeaa/64 scope link 
       valid_lft forever preferred_lft forever
16: br-65577ea7f86d: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:41:84:5a:88 brd ff:ff:ff:ff:ff:ff
    inet 172.22.0.1/16 brd 172.22.255.255 scope global br-65577ea7f86d
       valid_lft forever preferred_lft forever
    inet6 fe80::42:41ff:fe84:5a88/64 scope link 
       valid_lft forever preferred_lft forever
17: br-b3a0915ddff3: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether 02:42:25:f1:dd:05 brd ff:ff:ff:ff:ff:ff
    inet 172.28.0.1/16 brd 172.28.255.255 scope global br-b3a0915ddff3
       valid_lft forever preferred_lft forever
18: br-1fa631a66ed2: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether 02:42:0b:f0:d9:97 brd ff:ff:ff:ff:ff:ff
    inet 172.25.0.1/16 brd 172.25.255.255 scope global br-1fa631a66ed2
       valid_lft forever preferred_lft forever
19: br-e50cee81d109: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:59:2f:ca:c0 brd ff:ff:ff:ff:ff:ff
    inet 172.23.0.1/16 brd 172.23.255.255 scope global br-e50cee81d109
       valid_lft forever preferred_lft forever
    inet6 fe80::42:59ff:fe2f:cac0/64 scope link 
       valid_lft forever preferred_lft forever
20: br-832c2ec7c010: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:6c:e5:c0:2a brd ff:ff:ff:ff:ff:ff
    inet 172.18.0.1/16 brd 172.18.255.255 scope global br-832c2ec7c010
       valid_lft forever preferred_lft forever
    inet6 fe80::42:6cff:fee5:c02a/64 scope link 
       valid_lft forever preferred_lft forever
22: veth4ac3d6b@if21: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-832c2ec7c010 state UP group default 
    link/ether 8e:e5:49:e3:4e:39 brd ff:ff:ff:ff:ff:ff link-netnsid 6
    inet6 fe80::8ce5:49ff:fee3:4e39/64 scope link 
       valid_lft forever preferred_lft forever
3098: bridge1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 46:fd:6b:dd:de:5e brd ff:ff:ff:ff:ff:ff
    inet 192.168.2.250/24 brd 192.168.2.255 scope global bridge1
       valid_lft forever preferred_lft forever
    inet6 fd9d:99c7:1326:1:44fd:6bff:fedd:de5e/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 1064sec preferred_lft 1064sec
    inet6 fe80::44fd:6bff:fedd:de5e/64 scope link 
       valid_lft forever preferred_lft forever
26: veth89151ca@if25: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-a4b4ab0978d7 state UP group default 
    link/ether 6a:1b:4a:fe:13:52 brd ff:ff:ff:ff:ff:ff link-netnsid 14
    inet6 fe80::681b:4aff:fefe:1352/64 scope link 
       valid_lft forever preferred_lft forever
3099: vxlan.calico: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1450 qdisc noqueue state UNKNOWN group default 
    link/ether 66:af:58:c7:03:8e brd ff:ff:ff:ff:ff:ff
    inet 10.1.178.0/32 scope global vxlan.calico
       valid_lft forever preferred_lft forever
    inet6 fe80::64af:58ff:fec7:38e/64 scope link 
       valid_lft forever preferred_lft forever
28: vethfed031a@if27: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-e4866286311b state UP group default 
    link/ether be:ed:5e:c9:f2:35 brd ff:ff:ff:ff:ff:ff link-netnsid 10
    inet6 fe80::bced:5eff:fec9:f235/64 scope link 
       valid_lft forever preferred_lft forever
30: vethff29f54@if29: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-e98e97cb4545 state UP group default 
    link/ether f2:19:51:88:5b:81 brd ff:ff:ff:ff:ff:ff link-netnsid 0
    inet6 fe80::f019:51ff:fe88:5b81/64 scope link 
       valid_lft forever preferred_lft forever
32: veth29ff70c@if31: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-e50cee81d109 state UP group default 
    link/ether b2:8f:08:a6:2e:52 brd ff:ff:ff:ff:ff:ff link-netnsid 11
    inet6 fe80::b08f:8ff:fea6:2e52/64 scope link 
       valid_lft forever preferred_lft forever
36: veth317c60e@if35: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-41995dedb449 state UP group default 
    link/ether 9a:2c:87:36:ad:26 brd ff:ff:ff:ff:ff:ff link-netnsid 5
    inet6 fe80::982c:87ff:fe36:ad26/64 scope link 
       valid_lft forever preferred_lft forever
38: veth736fa80@if37: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-e50cee81d109 state UP group default 
    link/ether da:c8:5c:98:e0:5a brd ff:ff:ff:ff:ff:ff link-netnsid 12
    inet6 fe80::d8c8:5cff:fe98:e05a/64 scope link 
       valid_lft forever preferred_lft forever
40: vethe93905e@if39: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master docker0 state UP group default 
    link/ether c2:5d:a7:56:dc:5a brd ff:ff:ff:ff:ff:ff link-netnsid 3
    inet6 fe80::c05d:a7ff:fe56:dc5a/64 scope link 
       valid_lft forever preferred_lft forever
42: veth709add6@if41: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-a4b4ab0978d7 state UP group default 
    link/ether ce:69:98:ed:7d:03 brd ff:ff:ff:ff:ff:ff link-netnsid 8
    inet6 fe80::cc69:98ff:feed:7d03/64 scope link 
       valid_lft forever preferred_lft forever
44: vethc6f7fa1@if43: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-58f17667ca98 state UP group default 
    link/ether 32:6b:fc:b1:54:60 brd ff:ff:ff:ff:ff:ff link-netnsid 9
    inet6 fe80::306b:fcff:feb1:5460/64 scope link 
       valid_lft forever preferred_lft forever
3118: cali84be666b758@if3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether ee:ee:ee:ee:ee:ee brd ff:ff:ff:ff:ff:ff link-netns cni-13b20215-b3d1-fcf8-a076-9e4ad4674acc
    inet6 fe80::ecee:eeff:feee:eeee/64 scope link 
       valid_lft forever preferred_lft forever
46: veth0d17d2a@if45: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-e50cee81d109 state UP group default 
    link/ether ce:55:6f:26:3f:76 brd ff:ff:ff:ff:ff:ff link-netnsid 7
    inet6 fe80::cc55:6fff:fe26:3f76/64 scope link 
       valid_lft forever preferred_lft forever
3119: cali6d55d0fcd5b@if3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether ee:ee:ee:ee:ee:ee brd ff:ff:ff:ff:ff:ff link-netns cni-071a3d9a-5bd2-9dc7-4d58-ca1e65ce8488
    inet6 fe80::ecee:eeff:feee:eeee/64 scope link 
       valid_lft forever preferred_lft forever
3120: cali4e3f42ded4c@if3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether ee:ee:ee:ee:ee:ee brd ff:ff:ff:ff:ff:ff link-netns cni-6618fdc6-6963-70e8-ca7c-06132b31c1e9
    inet6 fe80::ecee:eeff:feee:eeee/64 scope link 
       valid_lft forever preferred_lft forever
48: vetha7f5de7@if47: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-a4b4ab0978d7 state UP group default 
    link/ether 4e:86:8d:38:58:5d brd ff:ff:ff:ff:ff:ff link-netnsid 13
    inet6 fe80::4c86:8dff:fe38:585d/64 scope link 
       valid_lft forever preferred_lft forever
3121: calidb89c5c550a@if3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether ee:ee:ee:ee:ee:ee brd ff:ff:ff:ff:ff:ff link-netns cni-86d2ae35-a0f5-1824-754e-e4a25a74fef3
    inet6 fe80::ecee:eeff:feee:eeee/64 scope link 
       valid_lft forever preferred_lft forever
3122: caliba400f0ef55@if3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether ee:ee:ee:ee:ee:ee brd ff:ff:ff:ff:ff:ff link-netns cni-3f754995-e4fc-954a-c919-7a87e83cd607
    inet6 fe80::ecee:eeff:feee:eeee/64 scope link 
       valid_lft forever preferred_lft forever
3123: caliab7bb467db7@if3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether ee:ee:ee:ee:ee:ee brd ff:ff:ff:ff:ff:ff link-netns cni-0c40513b-7045-8cc7-c586-c147980fd8e5
    inet6 fe80::ecee:eeff:feee:eeee/64 scope link 
       valid_lft forever preferred_lft forever
3124: cali0399de1aa1d@if3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether ee:ee:ee:ee:ee:ee brd ff:ff:ff:ff:ff:ff link-netns cni-702f95ae-70e4-9638-77b1-c21b800e06b5
    inet6 fe80::ecee:eeff:feee:eeee/64 scope link 
       valid_lft forever preferred_lft forever
52: vethafabf2c@if51: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-65577ea7f86d state UP group default 
    link/ether 7a:8b:14:0b:59:4c brd ff:ff:ff:ff:ff:ff link-netnsid 3
    inet6 fe80::788b:14ff:fe0b:594c/64 scope link 
       valid_lft forever preferred_lft forever
3125: cali9ef2ca550b7@if3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether ee:ee:ee:ee:ee:ee brd ff:ff:ff:ff:ff:ff link-netns cni-bb134c08-ce9f-77c1-adec-1f87d0913fef
    inet6 fe80::ecee:eeff:feee:eeee/64 scope link 
       valid_lft forever preferred_lft forever
3126: caliad442cc56ba@if3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether ee:ee:ee:ee:ee:ee brd ff:ff:ff:ff:ff:ff link-netns cni-1922206d-dcff-e8c7-3930-5820e74483af
    inet6 fe80::ecee:eeff:feee:eeee/64 scope link 
       valid_lft forever preferred_lft forever
54: vethf05a12e@if53: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master docker0 state UP group default 
    link/ether 56:96:05:8c:76:e4 brd ff:ff:ff:ff:ff:ff link-netnsid 2
    inet6 fe80::5496:5ff:fe8c:76e4/64 scope link 
       valid_lft forever preferred_lft forever
3127: califee36422fdd@if3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether ee:ee:ee:ee:ee:ee brd ff:ff:ff:ff:ff:ff link-netns cni-81f908a9-0452-169e-72d4-80b25b4a4837
    inet6 fe80::ecee:eeff:feee:eeee/64 scope link 
       valid_lft forever preferred_lft forever
3128: calic4f9df93190@if3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether ee:ee:ee:ee:ee:ee brd ff:ff:ff:ff:ff:ff link-netns cni-4a8989df-bc78-776a-0de3-60356139fd9e
    inet6 fe80::ecee:eeff:feee:eeee/64 scope link 
       valid_lft forever preferred_lft forever
56: veth2b4ab69@if55: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-41995dedb449 state UP group default 
    link/ether 4e:5c:97:64:7b:87 brd ff:ff:ff:ff:ff:ff link-netnsid 3
    inet6 fe80::4c5c:97ff:fe64:7b87/64 scope link 
       valid_lft forever preferred_lft forever
58: veth263bb73@if57: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master docker0 state UP group default 
    link/ether ea:62:43:ab:ee:38 brd ff:ff:ff:ff:ff:ff link-netnsid 15
    inet6 fe80::e862:43ff:feab:ee38/64 scope link 
       valid_lft forever preferred_lft forever
3131: cali3796c15a1a8@if3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether ee:ee:ee:ee:ee:ee brd ff:ff:ff:ff:ff:ff link-netns cni-c37a7b50-f66e-ef5f-bbb8-7bea87243beb
    inet6 fe80::ecee:eeff:feee:eeee/64 scope link 
       valid_lft forever preferred_lft forever
2667: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 3e:52:f8:a4:ce:c2 brd ff:ff:ff:ff:ff:ff
    inet 192.168.2.250/24 brd 192.168.2.255 scope global br0
       valid_lft forever preferred_lft forever
    inet6 fd9d:99c7:1326:1:3c52:f8ff:fea4:cec2/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 1712sec preferred_lft 1712sec
    inet6 fe80::3c52:f8ff:fea4:cec2/64 scope link 
       valid_lft forever preferred_lft forever
903: veth0e67c6e@if902: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master docker0 state UP group default 
    link/ether 56:92:3a:ca:70:3e brd ff:ff:ff:ff:ff:ff link-netnsid 1
    inet6 fe80::5492:3aff:feca:703e/64 scope link 
       valid_lft forever preferred_lft forever


```

I've set my qemu VM to the follwing, i've also tried eno1 instead if br0 and e1000e instead of virtio but no luck.

```

<interface type="bridge">
  <mac address="52:54:00:04:49:b9"/>
  <source bridge="br0"/>
  <model type="virtio"/>
  <address type="pci" domain="0x0000" bus="0x01" slot="0x00" function="0x0"/>
</interface>

```

---

### Post by Doug S on 2023-11-21
Note: I am not an expert. After a saga, I got it to work and haven't thought about it since.

See if [this ]("https://ubuntuforums.org/showthread.php?t=2461631&p=14036896#post14036896")helps.

I also have this file in my configuration directory:

```
doug@s19:~/config/etc/libvirt/qemu/networks$ [COLOR="#FF0000"]cat README[/COLOR]
2021.11.19. Due to file permissions and other setups, this one is not so easy to backup.
See also: https://ubuntuforums.org/showthread.php?t=2461631&p=14036896#post14036896

doug@s19:~/config/etc/libvirt/qemu/networks$ ls -l /etc/libvirt/qemu/networks
total 24
drwxr-xr-x 2 root root 4096 Apr 30  2021 autostart
-rw------- 1 root root  367 Apr 30  2021 br0.xml.original   <<<< Obsolete
-rw-r--r-- 1 root root   96 Apr 18  2021 bridge.xml.original   <<< Obsolete
-rw------- 1 root root  576 Apr 23  2021 default.xml.original  <<< Saved, just in case we want to go back
-rw------- 1 root root  383 Apr 30  2021 host-bridge.xml       <<< Autogenerated via below commands
-rw-r--r-- 1 root root  104 Apr 30  2021 host-bridge.xml.original <<< Saved original file.


Commands:

doug@s19:/etc/libvirt/qemu/networks$ sudo cp bridge.xml.original host-bridge.xml
virsh net-define host-bridge.xml
virsh net-autostart host-bridge
virsh net-start host-bridge
virsh net-list --all
```

---

### Post by Doug S on 2023-11-21
> **johantonissen said:**
> Thank you!

My question is, then, how do i make sure my server gets 192.168.2.250 and the vm running on that server gets 192.168.2.251 if i only am supplying 1 static ip address ?

Your VM will set that address via its own netplan file.

---

### Post by TheFu on 2023-11-21
> **johantonissen said:**
> Thank you!

My question is, then, how do i make sure my server gets 192.168.2.250 and the vm running on that server gets 192.168.2.251 if i only am supplying 1 static ip address ?

Your docker container should grab the desired IP. That's how it works with LXC. It has a network config, using netplan, inside the container.  "Bridge" is the key term here, not 100% network manager for everything running on the physical host system.

If should also be obvious that static IPs should be used by all servers, not DHCP.  DHCP is fine if you want an end-user desktop, but not for servers.

openVswitch is an alternative to normal linux bridges.  Both require installation of a package.  In my testing, openVswitch added complexity and only provided better performance for 10Gbps physical connections or faster, so if your server isn't using a 10Gbps NIC, stick with the normal Linux bridge utils.  I've never seen that error, but I've always installed bridge-utils BEFORE attempting anything.

Also, if you are doing docker, ignore all the virsh commands. Those are for libvirt and KVM.  If you are doing docker and not trying to have libvirt manage it, it won't help.

---

### Post by johantonissen on 2023-11-23
okay thanx everyone for the great help up untill this point. I think I'm almost there. I however not seeing host-bridge pop up. my config is as follows :

```

/etc/libvirt/qemu/networks$ ls
autostart  default.xml  default.xml.old  host-bridge.xml
/etc/libvirt/qemu/networks$ sudo cat host*
<!--
WARNING: THIS IS AN AUTO-GENERATED FILE. CHANGES TO IT ARE LIKELY TO BE
OVERWRITTEN AND LOST. Changes to this xml configuration should be made using:
  virsh net-edit host-bridge
or other application using the libvirt API.
-->


<network>
  <name>host-bridge</name>
  <uuid>a57c20b8-dd04-4089-b713-71f883ac4828</uuid>
  <forward mode='bridge'/>
  <bridge name='br0'/>
</network>

```

and activated it:
```

virsh net-autostart host-bridge
virsh net-start host-bridge
virsh net-list --all




 Name          State    Autostart   Persistent
------------------------------------------------
 default       active   yes         yes
 host-bridge   active   yes         yes

```

my config in qemu looks like this:
```

<interface type="bridge">
  <mac address="52:54:00:04:49:b9"/>
  <source bridge="host-bridge"/>
  <model type="virtio"/>
  <address type="pci" domain="0x0000" bus="0x01" slot="0x00" function="0x0"/>
</interface>

```

but host-bridge does not show up under ip a now so when i try to boot i get an error that there is no such device as host-bridge....

it's also not found under ip a:
```

ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel master br0 state UP group default qlen 1000
    link/ether 1c:69:7a:62:9e:0b brd ff:ff:ff:ff:ff:ff
    altname enp0s31f6
3: wlp0s20f3: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether c2:48:2f:93:f8:34 brd ff:ff:ff:ff:ff:ff permaddr d8:3b:bf:50:6c:d4
4: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 3e:52:f8:a4:ce:c2 brd ff:ff:ff:ff:ff:ff
    inet 192.168.2.250/24 brd 192.168.2.255 scope global br0
       valid_lft forever preferred_lft forever
    inet6 fd9d:99c7:1326:1:3c52:f8ff:fea4:cec2/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 1787sec preferred_lft 1787sec
    inet6 fe80::3c52:f8ff:fea4:cec2/64 scope link 
       valid_lft forever preferred_lft forever
5: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 52:54:00:c5:7a:52 brd ff:ff:ff:ff:ff:ff
    inet 192.168.122.1/24 brd 192.168.122.255 scope global virbr0
       valid_lft forever preferred_lft forever
6: docker0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:84:8e:a8:a4 brd ff:ff:ff:ff:ff:ff
    inet 172.17.0.1/16 brd 172.17.255.255 scope global docker0
       valid_lft forever preferred_lft forever
    inet6 fe80::42:84ff:fe8e:a8a4/64 scope link 
       valid_lft forever preferred_lft forever
7: br-58f17667ca98: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:d9:da:ab:ba brd ff:ff:ff:ff:ff:ff
    inet 172.19.0.1/16 brd 172.19.255.255 scope global br-58f17667ca98
       valid_lft forever preferred_lft forever
    inet6 fe80::42:d9ff:feda:abba/64 scope link 
       valid_lft forever preferred_lft forever
8: br-627d09ae2f5d: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether 02:42:5a:5d:d4:b0 brd ff:ff:ff:ff:ff:ff
    inet 172.26.0.1/16 brd 172.26.255.255 scope global br-627d09ae2f5d
       valid_lft forever preferred_lft forever
9: br-65577ea7f86d: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:fa:0b:de:b4 brd ff:ff:ff:ff:ff:ff
    inet 172.22.0.1/16 brd 172.22.255.255 scope global br-65577ea7f86d
       valid_lft forever preferred_lft forever
    inet6 fe80::42:faff:fe0b:deb4/64 scope link 
       valid_lft forever preferred_lft forever
10: br-d97364d42154: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether 02:42:41:9b:99:b5 brd ff:ff:ff:ff:ff:ff
    inet 172.27.0.1/16 brd 172.27.255.255 scope global br-d97364d42154
       valid_lft forever preferred_lft forever
11: br-e98e97cb4545: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:ac:4e:35:1e brd ff:ff:ff:ff:ff:ff
    inet 172.24.0.1/16 brd 172.24.255.255 scope global br-e98e97cb4545
       valid_lft forever preferred_lft forever
    inet6 fe80::42:acff:fe4e:351e/64 scope link 
       valid_lft forever preferred_lft forever
12: br-a4b4ab0978d7: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:20:fd:b0:57 brd ff:ff:ff:ff:ff:ff
    inet 172.31.0.1/16 brd 172.31.255.255 scope global br-a4b4ab0978d7
       valid_lft forever preferred_lft forever
    inet6 fe80::42:20ff:fefd:b057/64 scope link 
       valid_lft forever preferred_lft forever
13: br-e4866286311b: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:8e:df:73:ee brd ff:ff:ff:ff:ff:ff
    inet 192.168.16.1/20 brd 192.168.31.255 scope global br-e4866286311b
       valid_lft forever preferred_lft forever
    inet6 fe80::42:8eff:fedf:73ee/64 scope link 
       valid_lft forever preferred_lft forever
14: br-fbdcacafda66: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether 02:42:02:c3:d9:49 brd ff:ff:ff:ff:ff:ff
    inet 172.20.0.1/16 brd 172.20.255.255 scope global br-fbdcacafda66
       valid_lft forever preferred_lft forever
15: br-0cb6bbaa2dcb: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether 02:42:9f:e0:a4:a4 brd ff:ff:ff:ff:ff:ff
    inet 172.29.0.1/16 brd 172.29.255.255 scope global br-0cb6bbaa2dcb
       valid_lft forever preferred_lft forever
16: br-1fa631a66ed2: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether 02:42:f6:56:af:56 brd ff:ff:ff:ff:ff:ff
    inet 172.25.0.1/16 brd 172.25.255.255 scope global br-1fa631a66ed2
       valid_lft forever preferred_lft forever
17: br-832c2ec7c010: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:f7:82:7b:15 brd ff:ff:ff:ff:ff:ff
    inet 172.18.0.1/16 brd 172.18.255.255 scope global br-832c2ec7c010
       valid_lft forever preferred_lft forever
    inet6 fe80::42:f7ff:fe82:7b15/64 scope link 
       valid_lft forever preferred_lft forever
18: br-e50cee81d109: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:ee:6c:b1:8b brd ff:ff:ff:ff:ff:ff
    inet 172.23.0.1/16 brd 172.23.255.255 scope global br-e50cee81d109
       valid_lft forever preferred_lft forever
    inet6 fe80::42:eeff:fe6c:b18b/64 scope link 
       valid_lft forever preferred_lft forever
19: br-41995dedb449: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default 
    link/ether 02:42:e1:6b:4e:27 brd ff:ff:ff:ff:ff:ff
    inet 192.168.32.1/20 brd 192.168.47.255 scope global br-41995dedb449
       valid_lft forever preferred_lft forever
    inet6 fe80::42:e1ff:fe6b:4e27/64 scope link 
       valid_lft forever preferred_lft forever
20: br-9824dd83e841: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether 02:42:cc:37:07:c9 brd ff:ff:ff:ff:ff:ff
    inet 172.21.0.1/16 brd 172.21.255.255 scope global br-9824dd83e841
       valid_lft forever preferred_lft forever
21: br-b3a0915ddff3: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default 
    link/ether 02:42:25:bf:92:39 brd ff:ff:ff:ff:ff:ff
    inet 172.28.0.1/16 brd 172.28.255.255 scope global br-b3a0915ddff3
       valid_lft forever preferred_lft forever
23: veth2c3f8fd@if22: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master docker0 state UP group default 
    link/ether 32:3c:49:63:cf:f5 brd ff:ff:ff:ff:ff:ff link-netnsid 0
    inet6 fe80::303c:49ff:fe63:cff5/64 scope link 
       valid_lft forever preferred_lft forever
25: vethe19e74b@if24: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-e4866286311b state UP group default 
    link/ether 12:ad:31:e1:c0:a2 brd ff:ff:ff:ff:ff:ff link-netnsid 1
    inet6 fe80::10ad:31ff:fee1:c0a2/64 scope link 
       valid_lft forever preferred_lft forever
27: vethe4f6f44@if26: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-a4b4ab0978d7 state UP group default 
    link/ether 56:3f:7d:4c:a5:0b brd ff:ff:ff:ff:ff:ff link-netnsid 7
    inet6 fe80::543f:7dff:fe4c:a50b/64 scope link 
       valid_lft forever preferred_lft forever
29: vethdc663dc@if28: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-e50cee81d109 state UP group default 
    link/ether ee:00:0e:16:53:72 brd ff:ff:ff:ff:ff:ff link-netnsid 11
    inet6 fe80::ec00:eff:fe16:5372/64 scope link 
       valid_lft forever preferred_lft forever
31: vethe2f8d93@if30: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-e98e97cb4545 state UP group default 
    link/ether c6:7d:95:cd:60:48 brd ff:ff:ff:ff:ff:ff link-netnsid 9
    inet6 fe80::c47d:95ff:fecd:6048/64 scope link 
       valid_lft forever preferred_lft forever
33: vethac2f8f5@if32: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-832c2ec7c010 state UP group default 
    link/ether fa:e6:23:ae:cf:02 brd ff:ff:ff:ff:ff:ff link-netnsid 2
    inet6 fe80::f8e6:23ff:feae:cf02/64 scope link 
       valid_lft forever preferred_lft forever
37: veth1a6e3f6@if36: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-41995dedb449 state UP group default 
    link/ether 42:f4:d4:bd:ef:f6 brd ff:ff:ff:ff:ff:ff link-netnsid 8
    inet6 fe80::40f4:d4ff:febd:eff6/64 scope link 
       valid_lft forever preferred_lft forever
39: veth9c33b83@if38: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master docker0 state UP group default 
    link/ether c6:de:9e:87:17:b4 brd ff:ff:ff:ff:ff:ff link-netnsid 3
    inet6 fe80::c4de:9eff:fe87:17b4/64 scope link 
       valid_lft forever preferred_lft forever
41: veth2d8650b@if40: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-58f17667ca98 state UP group default 
    link/ether ae:c2:b7:bd:12:6a brd ff:ff:ff:ff:ff:ff link-netnsid 6
    inet6 fe80::acc2:b7ff:febd:126a/64 scope link 
       valid_lft forever preferred_lft forever
43: vetha150f02@if42: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-a4b4ab0978d7 state UP group default 
    link/ether 3e:4b:30:76:4c:d4 brd ff:ff:ff:ff:ff:ff link-netnsid 13
    inet6 fe80::3c4b:30ff:fe76:4cd4/64 scope link 
       valid_lft forever preferred_lft forever
45: vethc071670@if44: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-e50cee81d109 state UP group default 
    link/ether 4e:74:21:d7:ee:a5 brd ff:ff:ff:ff:ff:ff link-netnsid 10
    inet6 fe80::4c74:21ff:fed7:eea5/64 scope link 
       valid_lft forever preferred_lft forever
47: veth6d5e78a@if46: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master docker0 state UP group default 
    link/ether 66:50:87:12:a4:91 brd ff:ff:ff:ff:ff:ff link-netnsid 5
    inet6 fe80::6450:87ff:fe12:a491/64 scope link 
       valid_lft forever preferred_lft forever
49: veth1ec50e8@if48: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-e50cee81d109 state UP group default 
    link/ether 66:f8:18:4c:8e:16 brd ff:ff:ff:ff:ff:ff link-netnsid 4
    inet6 fe80::64f8:18ff:fe4c:8e16/64 scope link 
       valid_lft forever preferred_lft forever
53: vetha5a2e92@if52: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-a4b4ab0978d7 state UP group default 
    link/ether ee:0c:1f:0f:ba:5d brd ff:ff:ff:ff:ff:ff link-netnsid 12
    inet6 fe80::ec0c:1fff:fe0f:ba5d/64 scope link 
       valid_lft forever preferred_lft forever
55: vetha425fe6@if54: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-65577ea7f86d state UP group default 
    link/ether 56:93:97:14:fb:23 brd ff:ff:ff:ff:ff:ff link-netnsid 5
    inet6 fe80::5493:97ff:fe14:fb23/64 scope link 
       valid_lft forever preferred_lft forever
57: vethf022052@if56: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master docker0 state UP group default 
    link/ether 46:18:33:cd:f2:79 brd ff:ff:ff:ff:ff:ff link-netnsid 14
    inet6 fe80::4418:33ff:fecd:f279/64 scope link 
       valid_lft forever preferred_lft forever
59: veth38b8c2a@if58: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue master br-41995dedb449 state UP group default 
    link/ether 6a:e5:91:c5:d9:2f brd ff:ff:ff:ff:ff:ff link-netnsid 5
    inet6 fe80::68e5:91ff:fec5:d92f/64 scope link 
       valid_lft forever preferred_lft forever

```

Does anyone have any ideas ?

This process really is not straightforward.....

---

### Post by Doug S on 2023-11-24
> **johantonissen said:**
> 
```

 Name          State    Autostart   Persistent
------------------------------------------------
 default       active   yes         yes
 host-bridge   active   yes         yes

```

I suggest you get rid of "default".

this:
```

<interface type="bridge">
  <mac address="52:54:00:04:49:b9"/>
  <source bridge="[COLOR="#FF0000"]host-bridge[/COLOR]"/>
  <model type="virtio"/>
  <address type="pci" domain="0x0000" bus="0x01" slot="0x00" function="0x0"/>
</interface>

```
should be this:
```

<interface type="bridge">
  <mac address="52:54:00:04:49:b9"/>
  <source bridge="[COLOR="#FF0000"]br0[/COLOR]"/>
  <model type="virtio"/>
  <address type="pci" domain="0x0000" bus="0x01" slot="0x00" function="0x0"/>
</interface>

```
> **johantonissen said:**
> but host-bridge does not show up under ip a now so when i try to boot i get an error that there is no such device as host-bridge....Its not supposed to. You have br0.
```

ip a
...
4: br0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 3e:52:f8:a4:ce:c2 brd ff:ff:ff:ff:ff:ff
    inet 192.168.2.250/24 brd 192.168.2.255 scope global br0
       valid_lft forever preferred_lft forever
    inet6 fd9d:99c7:1326:1:3c52:f8ff:fea4:cec2/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 1787sec preferred_lft 1787sec
    inet6 fe80::3c52:f8ff:fea4:cec2/64 scope link 
       valid_lft forever preferred_lft forever
...

```

From TheFu
> Also, if you are doing docker, ignore all the virsh commands. Those are for libvirt and KVM. If you are doing docker and not trying to have libvirt manage it, it won't help.Since the OP mentioned QEMU, I thought a real VM might be involved. Sorry if I am leading you astray OP.

---

### Post by johantonissen on 2023-11-24
Hi there.

Thanx for the reply again man!

Ive deleted the default.

But I don't know if what you are saying is correct, isnt th link 'host-bridge' just the name of the network its referring to ? Qemu automatically detects the name host-bridge.

```

/etc/libvirt/qemu/networks$ sudo cat host-bridge.xml
<!--
WARNING: THIS IS AN AUTO-GENERATED FILE. CHANGES TO IT ARE LIKELY TO BE
OVERWRITTEN AND LOST. Changes to this xml configuration should be made using:
  virsh net-edit host-bridge
or other application using the libvirt API.
-->


<network>
  <name>**host-bridge**</name>
  <uuid>a57c20b8-dd04-4089-b713-71f883ac4828</uuid>
  <forward mode='bridge'/>
  <bridge name='br0'/>
</network>

```

and:
```



 Name          State    Autostart   Persistent
------------------------------------------------
 host-bridge   active   yes         yes

```

my config in qemu looks like this:
```

<interface type="bridge">
  <mac address="52:54:00:04:49:b9"/>
  <source bridge="**host-bridge**"/>
  <model type="virtio"/>
  <address type="pci" domain="0x0000" bus="0x01" slot="0x00" function="0x0"/>
</interface>

```

I'm asking this because I cannot select br0 in qemu. I've tried the tip as shown below, but then my server still does not get an ip address...

```

<interface type="bridge">
  <mac address="52:54:00:04:49:b9"/>
  <source bridge="br0"/>
  <model type="virtio"/>
  <address type="pci" domain="0x0000" bus="0x01" slot="0x00" function="0x0"/>
</interface>

```

Either way. I'm very grateful for your help. I dont mean to speak up against you, just tring to get this puppy going :)

---

### Post by johantonissen on 2023-11-24
ARG IT WAS MY FIREWALL

okay everything works.

thanks for the helm man! Can you send me your paypall account or something ? I'd like to buy you a beer for your troubles!

---

### Post by TheFu on 2023-11-27
Please make this thread as SOLVED using the thread tools button.

---

