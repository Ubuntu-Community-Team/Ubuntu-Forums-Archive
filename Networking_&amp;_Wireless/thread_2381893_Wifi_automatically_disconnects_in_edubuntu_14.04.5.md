---
title: "Wifi automatically disconnects in edubuntu 14.04.5"
date: 2018-01-06
forum: Networking &amp; Wireless
---

### Post by rohitrobichan on 2018-01-06
[COLOR=#3B4045][FONT=Ubuntu]Wifi signal is very low in ubuntu and if i connect it will automatically disconnects after a few minutes please help me to solve this problem.[/FONT][/COLOR]

---

### Post by jeremy31 on 2018-01-06
*Thread moved to **Networking & Wireless**.*
Please see the wireless script link in my signature and post results
See if it improves after ```
sudo modprobe -r rtl8723be && sleep 20 && sudo modprobe rtl8723be ant_sel=1
```

---

### Post by rohitrobichan on 2018-01-07
It increases the strength of the wifi signal. All nearby wifi networks are showing after executing the wireless script link but can't connect to any wifi network. It is trying to connect to wifi networks but cant connect.

---

### Post by rohitrobichan on 2018-01-07
And my wifi details are
0d:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
    Subsystem: Hewlett-Packard Company Device [103c:804c]
    Kernel driver in use: rtl8723be

---

### Post by jeremy31 on 2018-01-07
Please open a terminal and enter ```
cat wireless-info.txt | nc termbin.com 9999
```
Post the URL from terminal

---

### Post by rohitrobichan on 2018-01-08
```
cat: wireless-info.txt: No such file or directory
```

---

### Post by vasa1 on 2018-01-08
> **rohitrobichan said:**
> ```
cat: wireless-info.txt: No such file or directory
```

You need to run the script recommended to you in post #2 first! Please read [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108) as well!

---

### Post by rohitrobichan on 2018-01-08
done that now result is 
```

cat: wireless-info.txt: No such file or directory
nc: getaddrinfo: Name or service not known

```
and can't connect to wireless networks as well

---

### Post by Hadaka on 2018-01-09
Hi please open a terminal...ctrl/alt/t then Copy and Paste .
 ```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
Then do..
```
cat wireless-info.txt | nc termbin.com 9999
```
This will have an output that looks this...
**[http://termbin.com/xxyy](http://termbin.com/xxyy)**  <- It wont say 'xxyy' it will be something else
copy and paste to your reply.
Thank you

---

### Post by rohitrobichan on 2018-01-09
The url is
```

http://termbin.com/b4wg

```

---

### Post by Hadaka on 2018-01-09
Thank you for posting the url, you did a great job !
Let's see if we can improve your wifi performance.
Please open a terminal...ctrl/alt/t...then Copy and Paste.
```
sudo apt-get update
```
```
sudo iw reg set IN
sudo sed -i 's/=.*/=IN/' /etc/default/crda
```
*This command changes IPv6 to Ignore and resets Network Manager...not to worry
```
sudo sed -i '/ipv6/{n;s/.*/method=ignore/}' /etc/NetworkManager/*/AndroidAP
sudo service network-manager restart
```
*This command turns your wifi off while we make some changes...not to worry
```
sudo modprobe -r rtl8723be
```
This command makes the changes.
```
echo "options rtl8723be swenc=1 msi=1 fwlps=0 ips=0 ant_sel=1" | sudo tee /etc/modprobe.d/rtl8723be.conf
```
*This command turns your wifi back on.
```
sudo modprobe -v rtl8723be
```
**Please post the output of..
```
iwconfig | awk '/Q/'
```
Thank You

---

### Post by rohitrobichan on 2018-01-10
The command
```

options rtl8723be swenc=1 msi=1 fwlps=0 ips=0 ant_sel=1 | sudo tee /etc/modprobe.d/rtl8723be.conf

```
was not working output was
```

options: command not found

```
Output of the command 
```

iwconfig | awk '/Q/'

```
is
```

lo        no wireless extensions.
eth0      no wireless extensions.

```

---

### Post by rohitrobichan on 2018-01-10
The automatic disconnecting problem is resolved now. I think it is after sudo apt-get update. But low wifi signal problem is still there.

---

### Post by jeremy31 on 2018-01-10
I would try
```
echo "options rtl8723be swenc=1 msi=1 fwlps=0 ips=0 ant_sel=1" | sudo tee /etc/modprobe.d/rtl8723be.conf
```
Then reboot and see if the signal has improved

---

### Post by Hadaka on 2018-01-10
# @jeremy31..Thank you, I have corrected my command on the post.

rohitrobichan,please accept my apology for my command error.
Thanks.

---

### Post by rohitrobichan on 2018-01-10
Resolves the problem only temporarily. Wifi is strong now but automatically disconnects after some time and can't reconnect after that.

---

### Post by rohitrobichan on 2018-01-10
and output of
```

iwconfig | awk '/Q/'

```
is
```

lo        no wireless extensions.

eth0      no wireless extensions.

          Link Quality=70/70  Signal level=-38 dBm  

```

---

### Post by Hadaka on 2018-01-10
Hi,   "Quality 70/70 " is an excellent signal strength..are you now connecting ???

---

### Post by jeremy31 on 2018-01-10
Check ```
cat /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
If it shows wifi.powersave = 3, then run the following
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
```
systemctl restart network-manager.service
```

---

### Post by Hadaka on 2018-01-10
Hi from a working wired connection please Copy and Paste..

```
sudo apt-get install linux-headers-generic git dkms build-essential
rm -rf rtlwifi_new
git clone https://github.com/lwfinger/rtlwifi_new.git
sudo dkms add ./rtlwifi_new
sudo dkms build -m rtlwifi-new -v 0.6
sudo dkms install -m rtlwifi-new -v 0.6
```

remove wired connection boot and test wireless
Thanks.

---

### Post by rohitrobichan on 2018-01-11
It shows
```

cat: /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf: No such file or directory

```

---

### Post by Hadaka on 2018-01-11
Hi, this command..
```
# cat: /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
is not valid for Ubuntu 14.04. It is for newer Ubuntu versions.

Let's do a fresh wireless diagnostic to see what  may be causing the drops.
Please do, to clear out the old file..
```
sudo rm -rf wireless-info.*
```
Then repeat the commands in   Post # 9   and post the new URL.
Thank you

---

### Post by rohitrobichan on 2018-01-11
The url is [http://termbin.com/o4z7](http://termbin.com/o4z7)

---

### Post by Hadaka on 2018-01-11
Hi, thanks for the new report..it looks great..except..

#INTERNAL-CARD RTL8723BE PCIe Wireless Network Adapter [**[COLOR=#ff0000]10ec:b723[/COLOR]**[COLOR=#ff0000][/COLOR]] **=** **Driver >** **[COLOR=#ff0000]rtl8723[/COLOR]****[COLOR=#ff0000]be[/COLOR]**    
#USB.......Bus 002 Device 003: ID **[COLOR=#ff0000]0bda:b006[/COLOR]** Realtek Semiconductor Corp **= Driver > **[COLOR=#ff0000]**rtl8723be**[/COLOR][COLOR=#ff0000][/COLOR]

The computers internal wifi card and the usb wifi have the same driver, rtl8723be ,so it's toggling
between the two and cutting off...Why do you have both ???
PLEASE remove the USB wifi and test wireless.
looking forward to a good report.
Thanks.

---

### Post by rohitrobichan on 2018-01-11
I don't have a external usb wifi. Don't know why the report shows that.

---

### Post by Hadaka on 2018-01-11
Hi, please Copy and paste all 6 lines at once, you will not see a response
until you press enter on the last command..please post the output  of the last command.
```
ping -c2 $(ip route | awk '/via/{print $3}')|awk '/ping|loss/' > ping.tst
ping -c2 localhost | awk '/ping/,/2 /' >> ping.tst
ping -c2 8.8.8.8 | awk '/ping/,/2 /' >> ping.tst
ping -c2 google.com | awk '/ping/,/2 /' >> ping.tst
cat ping.tst | awk '{print$2,$6,$8}' > ping1.tst
sed 'N;s/\n/\t/g' ping1.tst
```
Thanks.

---

### Post by rohitrobichan on 2018-01-12
```

172.30.0.1      packets 0% loss,
localhost      packets 0% loss,
8.8.8.8      packets 0% loss,
google.com      packets 0% loss,

```

---

### Post by Hadaka on 2018-01-12
hi, please post the output of..
```
route -n | grep -i ug
ip route | grep -i via
```
Thanks

---

### Post by rohitrobichan on 2018-01-12
output of```
route -n | grep -i ug
```is```
0.0.0.0         172.30.0.1      0.0.0.0         UG    0      0        0 wlan0
```and output of ```
ip route | grep -i via
``` is ```
default via 172.30.0.1 dev wlan0  proto static 
```

---

### Post by Hadaka on 2018-01-12
Hi, here is what I am finding..
wlan0     IEEE 802.11bgn  ESSID:"AndroisAP"  **[COLOR=#ff0000]<- [/COLOR]**' Hotspot' teathered connection

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          inet addr:[COLOR=#ff0000]**192.168.43.1**[/COLOR]  Bcast:192.168.43.255  Mask:255.255.255.0  **[COLOR=#ff0000]<-[/COLOR]** 'wifi IP Address'  
'
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         **[COLOR=#ff0000]192.168.43.1[/COLOR]**   0.0.0.0         UG    0      0        0 wlan0 **[COLOR=#ff0000]<-[/COLOR]**' Gateway IP Address'
**[COLOR=#ff0000]192.168.43.0[/COLOR]**    0.0.0.0         255.255.255.0   U     9      0        0 wlan0 **[COLOR=#ff0000]<- [/COLOR]**'Where to send data IP Address'

** THEN..when you actually send data out..everything changes..via the AndroidAP connection..
**[COLOR=#ff0000]172.30.0.1[/COLOR]**      packets 0% loss, **[COLOR=#ff0000]<-[/COLOR]**  'Gateway assigned by or because of AndroidAP '
localhost          packets 0% loss,
8.8.8.8            packets 0% loss,
google.com      packets 0% loss,

* whois  172.30.0.1 shows...
NetRange:       172.16.0.0 - 172.31.255.255
CIDR:           172.16.0.0/12
NetName:        PRIVATE-ADDRESS-BBLK-RFC1918-IANA-RESERVED
NetHandle:      NET-172-16-0-0-1
Parent:         NET172 (NET-172-0-0-0-0)
NetType:        IANA Special Use
OriginAS:       
Organization:   Internet Assigned Numbers Authority (IANA)
RegDate:        1994-03-15
Updated:        2013-08-30
Comment:        These addresses are in use by many millions of independently operated networks, which might be as small as a single computer connected to a home gateway, and are automatically configured in hundreds of millions of devices. **[COLOR=#ff0000]"[/COLOR]**They are only intended for use within a private context**[COLOR=#ff0000]"[/COLOR]**  **[COLOR=#ff0000]->[/COLOR]**and traffic that needs to cross the Internet will need to use a different, unique address.

Verify the AndroidAP is configured correctly
**[COLOR=#ff0000]*[/COLOR]**[https://www.greenbot.com/article/3161194/android/how-to-share-your-android-phones-connection-with-wi-fi-hotspot.html](https://www.greenbot.com/article/3161194/android/how-to-share-your-android-phones-connection-with-wi-fi-hotspot.html)

There is nothing wrong with your computer and its configuration..no errors..excellent signal,it scans and see networks,AP's,country code is set,IPv6 is ignored. This AndroidAP connection is only alloting you minimal data exchange
before it dumps the connection..I have no knowledge of AndroidAP, perhaps someone else can guide you with that.

---

### Post by rohitrobichan on 2018-01-12
I was not using AndroidAP after my wifi signal was boosted. But the issue of disconnecting wifi after a certain time persists. Now I also have another problem, wifi is not showing any networks in first booting i have to restart to show wifi connections.

---

### Post by Hadaka on 2018-01-13
Hi, please do not change access points while we are trying to find the
the problem, it makes it impossible.  Let' try a fresh report.
*First turn OFF your cell phone....then
Open a terminal and do...
```
sudo rm -rf wireless-info.*
```
Then repeat the process in post # 9 and post the url
*Note..the last url did not have the "dmesg" part of the report, be sure to
look at this one and verify it does..if it does not..delete the files  with the
above command and repeat the process. Post the url
Thanks

---

### Post by rohitrobichan on 2018-01-13
url is ```
http://termbin.com/zivi
```dmesg part is there

---

### Post by rohitrobichan on 2018-01-13
I think the problem of automatic disconnection is resolved.Don't know  how.But here is the new problem I have to restart every time to show  wireless networks. That is I can't connect to wireless networks on first  boot of ubuntu I have to restart every time to show wireless networks  available and to connect.Please help me to resolve this problem.

---

### Post by Hadaka on 2018-01-13
Hi, this is the reason you keep disconnecting..
```
 Wireless Access Points (* = current AP)
    vjcnet:          Infra, <MAC 'vjcnet' [AC3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 80
    vjcnet:          Infra, <MAC 'vjcnet' [AC6]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 77
    vjcnet:          Infra, <MAC 'vjcnet' [AC2]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 60
    vjcnet:          Infra, <MAC 'vjcnet' [AC7]>, Freq 2467 MHz, Rate 54 Mb/s, Strength 60
    vjcnet:          Infra, <MAC 'vjcnet' [AC4]>, Freq 2427 MHz, Rate 54 Mb/s, Strength 47
    vjcnet:          Infra, <MAC 'vjcnet' [AC8]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 47
    vjcnet:          Infra, <MAC 'vjcnet' [AC5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 47
   **[COLOR=#ff0000]*[/COLOR]**vjcnet:         Infra, <MAC 'vjcnet' [AC1]>, Freq 2442 MHz, Rate 54 Mb/s, Strength 70
```

You have connected to one of many vjcnet [access points]. You are currently connected to **[COLOR=#ff0000]*[/COLOR]**[AC1] with a
 signal strength of 70
[AC3] and [AC6] both have higher signal strengths so it is roaming to the highest signal attempting
to connect.
We will attempt to fix that..but first lets see if we can fix the problem of having to log back 

First click the wifi signal icon...[upper right area]. 
Then click 'Edit Connections'
Then click the 'Wireless' tab
Then click..vjcnet..then click 'Edit'
make sure the box is checked for ..'Connect Automatically' then click save....Next do the same for
AndroidAP..but..make sure the connect automatically box is NOT checked.
Do that and then we will work on the next issue.
Please report back when this is complete.
Thanks.

---

### Post by Hadaka on 2018-01-13
Hi, Please be sure you have completed the previous post before you do this..
Then please open a terminal then Copy and Paste..
```
sudo iwlist wlan0 scan | egrep -i 'ssid|quality|cell'
```
 
*Eample of output
          Cell 01 - Address: 48:5f:66:A1:59:6C...........<- **[COLOR=#ff0000]BSSID[/COLOR]**
                    Quality=56/70  Signal level=-54 dBm..<- **[COLOR=#ff0000]QUALITY[/COLOR]** ..SIGNAL STRENGTH      
                    ESSID:"FiOS-IT3OL"...................<- ESSID 'VJCNET'
          Cell 02 - Address: 00:0E:3B:0F:FD:C8
                    Quality=38/70  Signal level=-72 dBm  
                    ESSID:"sysrpt"
          Cell 03 - Address: B0:5A 4A:88:72:BD
                    Quality=29/70  Signal level=-81 dBm  
                    ESSID:"HP-Print-BD-Officejet Pro 8610"
          Cell 04 - Address: A0:8E:78:3B C5:1E
                    Quality=29/70  Signal level=-81 dBm  
                    ESSID:"MySpectrumWiFi18-2G"
*Example..."FiOS-IT3OL" has the highest Quality signal.."Quality=56/70"..BSSID "48:5f:66:A1:59:6C"..Example*
     
Look for the highest 'Quality number in the list of 'VJCNET'
*Important...Write down the BSSID . *Example..48:5f:66:A1:59:6C
Then....
Click the wifi icon [upper righ area]
Click Edit Connections
Click Wireless tab
Click vjcnet
Click Edit

Enter the BSSID from the highest vjcnet scan
#*** SEE ATTACHED
Click Save
[ATTACH=CONFIG]278171[/ATTACH]
boot and test wireless

---

### Post by rohitrobichan on 2018-01-14
Done this but the issue persists. The problem is in some booting after a shutdown wifi is not working. Don't even show any available wireless connections.

---

### Post by Hadaka on 2018-01-14
Hi, please do 3 things.

1. please post a screenshot of the vjcnet connection to verify it  has the BSSID field filled out.

2. Click the wifi icon, Edit connections , wireless..and DELETE ALL connections except vjcnet

3. ```
sudo rm -rf wireless-info*
echo "rtl8723be" | sudo tee -a /etc/modules
```
     Then repeat the process in post # 9 and post the NEW url 

Thanks

---

### Post by rohitrobichan on 2018-01-16
sorry for the delay I have been trying to do this but every time when  using the commands in post # 9 it shows error```
Pastebin failed,  error message is:

Failed to contact the server: [Errno socket error] timed out
```At last it completed without errors. The url is ```
http://termbin.com/mrtq
``` The  screen shot you asked is attached here

---

### Post by Hadaka on 2018-01-16
Hi, thanks for the screen shot and the new report.

Why and where is this static connection set...??
 ```
IPv4 Settings:
    Address:         172.30.11.223
    Prefix:          16 (255.255.0.0)
    Gateway:         172.30.0.1

    DNS:             8.8.8.8
    DNS:             202.138.103.100
    DNS:             202.138.96.2
```
Please open a terminal then Copy and Paste
```
sudo sed -i '/ipv6/{n;s/.*/method=ignore/}' /etc/NetworkManager/*/vjcnet
sudo service network-manager restart
```
Please post the output of..
```
cat /etc/network/interfaces
```
Then do..
Click the wifi icon [upper righ area]
Click Edit Connections
Click Wireless tab
Click vjcnet
Click Edit
Click IPv4 Settingts tab
and post a screenshot of the IPv4 screen for vjcnet
thanks

---

### Post by rohitrobichan on 2018-01-17
I haven't setup any static connections.
After the code```

sudo service network-manager restart
```I haven't been able to connect to wifi before restart.Anyway output of```
cat /etc/network/interfaces
``` is ```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


``` IPv4 screenshot is attached

---

### Post by Hadaka on 2018-01-17
I have no idea where this is being set..
IPv4 Settings:
    Address:         172.30.11.223 **[COLOR=#ff0000]<- [/COLOR]**[COLOR=#ff0000][/COLOR]Router maybe ???
    Prefix:          16 (255.255.0.0)
    Gateway:         172.30.0.1
Since you dont own the router you cant change that...so there is no
way to make that correction 172.30.**[COLOR=#ff0000]11[/COLOR]**[COLOR=#ff0000][/COLOR] is outside the gateway routing table
172.30.**[COLOR=#ff0000]0[/COLOR]**[COLOR=#ff0000][/COLOR][COLOR=#ff0000][/COLOR]
The Network Manager command simply says...
"Find the line that says..IPv6..then go to the next line and replace *anything
  that is there with method=ignore. Then restart NetworkManager
[COLOR=#ff0000][/COLOR]```
sudo sed -i '/ipv6/{n;s/.*/method=ignore/}' /etc/NetworkManager/*/vjcnet
sudo service network-manager restart
```
To do it manually..open a terminal and do..
```
sudo gedit /etc/NetworkManager/system-connections/vjcnet
```
Then change the line *below [IPv6] from method=auto to method=ignore.
Close and save gedit.
then do..
```
sudo service network-manager restart
```
to write the change to that file.
Thanks.

---

### Post by rohitrobichan on 2018-01-21
Thank you very much #Hadaka. My problem is solved now. You have been  very helpful. I have been testing my device for 4 days and my wifi  network have shown no problems and working perfectly. Thank you Hadaka  for spending your valuable time for solving my problem. I am thankful  everyone who participated this forum for helping me. Thanks to #jeremy31  #vasa1 and special thanks to #ubuntuforums.org.

---

### Post by Hadaka on 2018-01-21
Glad the wifi issue has been resolved.
Thank You for marking the thread solved.

---

