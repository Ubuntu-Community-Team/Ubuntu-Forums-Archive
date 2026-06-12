---
title: "ubuntu 17.10 server cannot set mtu with netplan"
date: 2017-12-21
forum: Networking &amp; Wireless
---

### Post by cryptz on 2017-12-21
hello,

i have mtu set to 9000 in netplan but when i do netplan apply the interface stays at 1500. If i change it with ip link set it works until reboot. Is there a way to make the change persistent? 

I have a bond interface, but the change is not related to the bond. Here is my netplan file. The two adapters set to 9000 never change, they stay 1500 unless i use the ip link set command. I noted that the site removes leading spaces, if netplan indenting does infact matter just know my file is formatted properly.

network:
  version: 2
  renderer: networkd
  ethernets:
      eno1:
          match:
              macaddress: 25:5e:56:73:3c:10
      eno2:
          match:
              macaddress: 25:5e:56:73:3c:11
      enp175s0f0:
         mtu: 9000
         addresses: [10.10.12.1/29]


      enp175s0f1:
         mtu: 9000
         addresses: [10.10.11.1/29]
  bonds:
      bond0:
                  parameters:
                    mode: 802.3ad
                  interfaces: [eno1, eno2]
                  addresses: [10.10.10.7/24]
                  gateway4: 10.10.10.1
                  nameservers:
                          addresses: [10.10.10.10, 10.10.10.11, 8.8.8.8]

---

### Post by TheFu on 2017-12-21
/etc/network/interfaces

Edit that file.  I have **no clue** what a "netpan" is.

---

### Post by chili555 on 2017-12-21
> **TheFu said:**
> /etc/network/interfaces

Edit that file.  I have **no clue** what a "netpan" is.Please see the question and answer here: [https://askubuntu.com/questions/976464/etc-network-interfaces-is-ignored](https://askubuntu.com/questions/976464/etc-network-interfaces-is-ignored)

---

### Post by cryptz on 2017-12-21
as mentioned by chili, /etc/network/interfaces is depreciated and netplan is the replacement. it does not seem to be honoring mtu settings. i found bugs dating back to feb 2017 but they appear to have been fixed.

---

### Post by chili555 on 2017-12-21
>  I noted that the site removes leading spaces, if netplan indenting does infact matter just know my file is formatted properly.
The spacing, indentation, etc. will show correctly enclosed in code tags. Please see the top of the reply box** #**.

Do you mind if we take a look?

---

### Post by cryptz on 2017-12-21
i just wanted to follow up and let everyone know i resolved the issue. I found out that all netplan really does is generate the systemd-networkd config files for you. When I inspected those files I found that the criteria for [COLOR=#000000]enp175s0f0.link was set to match "original name" [/COLOR][COLOR=#000000]enp175s0f0 

I know that sometimes the systems boot and the adapters are then renamed, so on a hunch i added the match macaddress line for both [/COLOR][COLOR=#000000]enp175s0f0 and [/COLOR][COLOR=#000000]enp175s0f1

that caused the [/COLOR][COLOR=#000000]enp175s0f0.link file to no longer have the original name match clause and instead the match macaddress (with the correct mac) clause. This apparently matches at boot without issue as my mtu is correctly set to 9000.[/COLOR]

---

### Post by daxtens on 2018-03-12
Hi all,

FYI, this is being tracked on Launchpad: [LP: #1724895]("https://bugs.launchpad.net/netplan/+bug/1724895").

cryptz, you've come to exactly the same conclusion about the cause that I did on the bug, and as far as I know the workaround is still to match on mac addresses.

I'm not quite sure what the best fix to propose is: matching on the renamed name is potentially fragile, but the current behaviour is also bad.

---

