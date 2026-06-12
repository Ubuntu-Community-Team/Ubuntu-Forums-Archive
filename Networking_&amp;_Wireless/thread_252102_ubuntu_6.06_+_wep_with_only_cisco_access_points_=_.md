---
title: "ubuntu 6.06 + wep with only cisco access points = broken"
date: 2006-09-06
forum: Networking &amp; Wireless
---

### Post by msbrentlinger on 2006-09-06
i have an unusual issue with ubuntu + wep + cisco access points

ive used this very same hardware setup with windows and other flavors of linux and had no isues. 

it seems the issue is not even realated to the wireless card as i have the issue with compaq wl110 or cisco 350 wireless cards. 

essentially using either of the cards mentioned above i can associate and use wep with multiple linksys or netgear wireless access points. as soon as i try to use any of the many cisco 1200 series access points we use at work i cannot associate at all. if i shut wep off at the access point i can then easily associate, however using either 64 or 128 bit wep all prevent me from associating.

the odd thing is that these access points have not changed at all (i know because i administer them and have congfigs dating back to long ago and they havent changed). many, many, times i have used these very cards with other linux and windows os's and had no issues with wep and these access points. 

i just dont get it... at first i thought it was a driver issue with a particular card, but i get the same thing with either my cisco 350 card or compaq wl110 card

perhaps these cisco access points have some sort of wep weirdness that  my older linux boxes didnt care about but ubuntu 6.06 recognizes and tries to understand but cant? weird. 

basically this is all i get when using wep connecting to a cisco access point..

eg:iwevent output

10:21:35.526481   eth2     Set ESSID:"linksys"
10:21:35.598600   eth2     Set Mode:Managed
10:21:35.667653   eth2     Set Encryption key:****-****-****-****-****-****-**
10:21:35.743385   eth2     Set Encryption key:on   Security mode:restricted
10:21:35.816454   eth2     Set Encryption key:****-****-****-****-****-****-**   Security           mode:restricted
10:21:35.920307   eth2     New Access Point/Cell address:00:13:10:9D:9E:98



10:23:21.237240   eth1     Set ESSID:"work-cisco-ap"
10:23:21.310369   eth1     Set Mode:Managed
10:23:21.882222   eth1     Set Encryption key:****-****-****-****-****-****-**
10:23:21.963387   eth1     Set Encryption key:on   Security mode:restricted
10:23:22.048258   eth1     Set Encryption key:****-****-****-****-****-****-**   Security           mode:restricted
10:23:22.156027   eth1     New Access Point/Cell address:Not-Associated
10:23:22.343347   eth1     New Access Point/Cell address:Not-Associated
10:23:23.552713   eth1     New Access Point/Cell address:Not-Associated
10:23:25.221785   eth1     New Access Point/Cell address:Not-Associated



17:43:20.252350   eth1     Set ESSID:"work-cisco-ap"
17:43:20.317876   eth1     Set Mode:Managed
17:43:20.856457   eth1     Set Encryption key:****-****-****-****-****-****-**
17:43:20.921949   eth1     Set Encryption key:on   Security mode:restricted
17:43:20.989922   eth1     Set Encryption key:****-****-****-****-****-****-**   Security mode:restricted
17:43:26.031727   eth1     Tx packet dropped:FF:FF:FF:FF:FF:FF
17:43:26.856382   eth1     Tx packet dropped:00:02:8A:9E:9A:FC
17:43:27.880360   eth1     Tx packet dropped:00:02:8A:9E:9A:FC
17:43:31.263804   eth1     Tx packet dropped:FF:FF:FF:FF:FF:FF
18:00:05.215431   eth1     Tx packet dropped:00:02:8A:9E:9A:FC
18:00:05.215529   eth1     Tx packet dropped:00:02:8A:9E:9A:FC



any help would be greatly apprecaited. id be happy to provide any  lsmod or lshw, etc output youd like, or info on how im configuing the card but i think ive tried every possible incantation of iwconfig, and i dont think its a driver issue since ive have this issue with 2 diffrent types of cards that use diffrent drivers.

eg:
iwconfig eth1 key aaaaaaaaaaaaaaaaaaaa
iwconfig eth1 key s:aaaaaaaaaaaaaaaaaaaa
iwconfig eth1 key aaaa-aaaa-aaaa-aaaa-aaaa-aaaa-aa
echo '0 aa:aa:aa:aa:aa:aa:aa:aa:aa:aa' > /proc/driver/aironet/eth1/WepKey

---

### Post by msbrentlinger on 2006-09-06
the plot thickens. the following works

$ cat /etc/network/interfaces
...
# The wireless network interface
auto eth1
iface eth1 inet dhcp
wireless-essid JASPER
wireless-key AAAAAAAAAAAAAAAAAAAAAAAAAA
...

however the aforementioned ONLY works on first boot. after suspension to ram and resuming im back to the same deal (i can connect to any wep AP except my cisco APs).that is...  UNLESS i either remove and reinsert the card OR run sudo /etc/init.d/networking restart


regardless of wether im on first boot or resuming from suspension all my old scripts that use things like the following work when connecting to anything but my cisco access points

sudo iwconfig eth1 essid netgear
sudo iwconfig eth1 mode managed
sudo iwconfig eth1 key aaaaaaaaaaaaaaaaaaaaaaaaa
sudo iwconfig eth1 key restricted
sudo iwconfig eth1 key on

or 

sudo iwconfig eth1 essid linksys
sudo iwconfig eth1 mode managed
sudo iwconfig eth1 key aaaaaaaaaaaaaaaaaaaaaaaaaa
sudo iwconfig eth1 key restricted
sudo iwconfig eth1 key on

but this stuff which used to work with other linux flavors doenst work at all

sudo iwconfig eth1 essid work-cisco-ap
sudo iwconfig eth1 mode managed
sudo iwconfig eth1 key aaaaaaaaaaaaaaaaaaaaaaaaaaa
sudo iwconfig eth1 key restricted
sudo iwconfig eth1 key on


perhaps its something with cardmgr and acpi? very weird

---

