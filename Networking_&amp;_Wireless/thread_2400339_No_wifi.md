---
title: "No wifi"
date: 2018-09-05
forum: Networking &amp; Wireless
---

### Post by leonkingston on 2018-09-05
So i am new to Ubuntu (i use Ubuntu Mate)
And I just Can't get Wi-fi?  i tried some commands in terminal but nothing works...
None of the wi-fi connections in my area are not showing...

thank you for your help!

---

### Post by NM5TF on 2018-09-05
which commands did you try ???
is your wifi adapter even recognized ???

we need more information to be able to help you

post the results of these please

```
inxi -S -N
```
it should look something like this

```
tommy@tommy ~]$ inxi -S -N
System:    Host: tommy Kernel: 4.18.5-arch1-1-ARCH x86_64 bits: 64 Desktop: Xfce 4.12.4 Distro: Arch Linux
Network:   Card: Edimax EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS] driver: rtl8192cu
```


```
ip link
```

it should look something like mine

```
[tommy@tommy ~]$ ip link
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: wlp0s2f1u10: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DORMANT group default qlen 1000
    link/ether 80:1f:02:b6:d2:ce brd ff:ff:ff:ff:ff:ff

```

line #2 is my wifi adapter info showing it is UP

---

### Post by wildmanne39 on 2018-09-05
*Thread moved to **Networking & Wireless for a more appropriate fit**.*

---

### Post by leonkingston on 2018-09-05
after inxi command i get this:

System:    Host: leon-HP-Compaq-nx6325-RH498ES-AKN Kernel: 4.15.0-33-generic i686 (32 bit) Desktop: MATE 1.12.1
           Distro: Ubuntu 16.04 xenial
Network:   Card-1: Broadcom NetXtreme BCM5788 Gigabit Ethernet driver: tg3
           Card-2: Broadcom BCM4311 802.11b/g WLAN

after ip link:

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: enp2s1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DEFAULT group default qlen 1000
    link/ether 00:17:08:3f:eb:e8 brd ff:ff:ff:ff:ff:ff


what should I do?

---

### Post by NM5TF on 2018-09-05
ip link line #2 is only showing your ethernet connection....no wifi adapter shows up

are you trying to connect to your wifi with your ethernet cable plugged in ???

that will NOT work as it will always select ethernet over wifi.....

try to boot up without the ethernet cable connected...

one more little thing....when posting terminal outputs, please use code tags to make it easier to read....use the "go advanced" reply tab...copy the output,
select the # icon & paste the output between the #s

tommy

---

### Post by leonkingston on 2018-09-06
when i boot up without ethernet cable plugged in, its i just the same...when i click the wi-fi like icon on the top right corner beside the bluetooth and sound no wi-fi connections show up? not even a word about wifi...

what should i do man? i am really angy because i like this system and i want it to work nice...


thank you!

---

### Post by chili555 on 2018-09-06
> Card-2: Broadcom BCM4311 802.11b/g WLANThere you go.

Please see: [https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by NM5TF on 2018-09-06
it sounds like you are missing the chip firmware...

you might find some help here   [https://ubuntu-mate.community/t/broadcom-wireless-tip/12844]("https://ubuntu-mate.community/t/broadcom-wireless-tip/12844")

---

### Post by leonkingston on 2018-09-06
when  i type iwconfig i get this:
```
enp2s1    no wireless extensions.

lo        no wireless extensions.


```


what does it mean?

---

### Post by NM5TF on 2018-09-06
did you follow chilli555s advice ???   he is a networking guru...

---

### Post by leonkingston on 2018-09-06
yes i did...but hes pci.ds or whatever is it called are only for classic ubuntu and like i said i am using Ubuntu mate...actually ubuntu mate 16.04
...is it really that hard just to get wifi working oh god..
please help..

thank you!

---

### Post by leonkingston on 2018-09-06
yes....but nothing helped so far..i am losing my mind...

thanks for any help i get!

---

### Post by chili555 on 2018-09-06
```
but hes pci.ds or whatever is it called are only for classic ubuntu and like i said i am using Ubuntu mate...
```That is not the case. Please open a terminal Ctrl+Alt+t and run: ```
lspci -nnk | grep 0280 
```You will find that the pci.id is likely 14e4:4311.

Then follow the link I suggested and the exact process is clearly shown.

---

### Post by NM5TF on 2018-09-06
> **leonkingston said:**
> yes i did...but hes pci.ds or whatever is it called are only for classic ubuntu and like i said i am using Ubuntu mate...actually ubuntu mate 16.04
...is it really that hard just to get wifi working oh god..
please help..

thank you!

they are BASICALLY the same OS with some subtle differences....from this ask Ubuntu page   [http://https://askubuntu.com/questions/620386/whats-the-difference-between-ubuntu-mate-and-ubuntu]("http://https://askubuntu.com/questions/620386/whats-the-difference-between-ubuntu-mate-and-ubuntu")

"Ubuntu MATE, on the other hand, is a derivative of Ubuntu, a sort of "child OS" based off Ubuntu, but with changes to the default software and design, most notably the use of the MATE DE instead of the default Ubuntu DE, Unity."

I also use Mint MATE as an alternate OS from time to time.....have never had any problems with my wifi being recognized/loaded automatically.....have you used your wifi with WinDoze before switching to Ubuntu to be sure
the adapter actually is working ???

tommy

---

