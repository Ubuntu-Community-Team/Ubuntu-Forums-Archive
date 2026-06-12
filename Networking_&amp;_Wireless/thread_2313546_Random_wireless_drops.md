---
title: "Random wireless drops"
date: 2016-02-13
forum: Networking &amp; Wireless
---

### Post by checoimg on 2016-02-13
So my wireless connection in different places randomly drops and I disconnect and reconnect and it gets fixed until it happens again.

The thing is finding out if this in happening form the Kernel/Driver/OS side or just from ISP problems.

I attached a file following a network diagnostic script from here : [http://askubuntu.com/questions/425155/my-wireless-wifi-connection-does-not-work-what-information-is-needed-to-diagnos/425205#425205](http://askubuntu.com/questions/425155/my-wireless-wifi-connection-does-not-work-what-information-is-needed-to-diagnos/425205#425205)

[ATTACH]267284[/ATTACH]

---

### Post by Hadaka on 2016-02-13
Hi, your wireless report shows..
```
COWORKING           <MAC 'COWORKING' [AC7]>  Infra   11    2462 MHz  54 Mbit/s  51      &#9602;&#9604;__  WPA1 WPA2  no
COWORKING           <MAC 'COWORKING' [AC5]>  Infra   11    2462 MHz  54 Mbit/s  92      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2  no        
COWORKING           <MAC 'COWORKING' [AC1]>  Infra   11    2462 MHz  54 Mbit/s  58      &#9602;&#9604;&#9606;_  WPA1 WPA2  yes     * 
```
Access points with the same name,same frequency.
Access Point[AC7] does NOT have WPA1 WPA2 set
Access Point [AC5]does NOT have WPA1 WPA2 set
Access Point[AC1] DOES have WPA1 WPA2 set and is the connection you had when you ran the script.
If you read your Wireless-Info,txt file you will see at the bottom is your DMESG printout,it clearly shows your computer is
confused as to which COWORKING access point to attach to because both have the SSID of COWORKING. Do you have some kind of
repeater set up?..a network configuration for both with different settings? You can verify the network setting by clicking the Signal icon
then Edit connections.If you have 2 delete the one with NO WAP1 WPA2.
*If you do not own the network, then I would suggest asking the owner to change the SSID to stop the confusion.
 Once that is corrected or sorted out. There are a couple items
that should also be attended to. Open a terminal then copy and paste
```
sudo iw reg set DO
sudo sed -i 's/^REG.*=$/&DO/' /etc/default/crda
```
Next you can configure your network to to better attach to your desired [AC] access point.
please do..
```
iwconfig
```
*note the Access Point :for your wlp2s0 wireless connection, this is also know as the BSSID, please configure your network
click your network signal icon then edit connections to configure
like the attached to set your BSSID to your [AC]access point COWORKING and IPv4  IPv6 changes.
[ATTACH=CONFIG]267290[/ATTACH][ATTACH=CONFIG]267291[/ATTACH][ATTACH=CONFIG]267292[/ATTACH]

---

### Post by checoimg on 2016-02-14
> **Hadaka said:**
> Hi, your wireless report shows..

If you read your Wireless-Info,txt file you will see at the bottom is your DMESG printout,it clearly shows your computer is
confused as to which COWORKING access point to attach to because both have the SSID of COWORKING. Do you have some kind of
repeater set up?.

Yes, I was on a Coworking I go to sometimes and they have a set that handles two different wifi signals. There's a main wireless an then a backup. I will erase one of the Wifi connections and let it connect to just one. I can't tell how that "backup" wireless" works.

Thank you!! :D

---

### Post by Hadaka on 2016-02-14
Hi, if you are satisfied, please go to your first post of the thread
click TOOLS then choose SOLVED
thanks.

---

### Post by checoimg on 2016-02-15
It is happening in my house too

---

