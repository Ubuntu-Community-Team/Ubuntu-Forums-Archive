---
title: "A well-known &quot;eduroam&quot; wifi disconnecting problem"
date: 2017-12-27
forum: Networking &amp; Wireless
---

### Post by tomas96 on 2017-12-27
Hello guys,

I have really disaster and annoying problem: my computer always randomly disconnects from "eduroam" wifi without any reason. Then I have to connect to it again. I investigated dozens of similar and same issues in the forums and some web-sites like "stackoverflow", however I didn't find any clear reason and solution for my problem. That's why I'm writing here.

I want to tell, that solution to connect to concrete wifi instance does not work. The wifi still disconnects.

I found here [good script]("https://ubuntuforums.org/showthread.php?p=12350385#post12350385"), which brings all necessary information into one file for solving the problem: [https://pastebin.ubuntu.com/26266068/](https://pastebin.ubuntu.com/26266068/)

I'm using Lenovo Y50-70 computer and running Linux Ubuntu 16.04 along with Windows 10 (dual-boot). I want to confirm that Wifi works perfectly on Windows (everywhere) and on Linux only using not enterprise wifi.

Eduroam's connection information:
[LIST]
[*]Security: WPA & WPA2 Enterprise
[*]Authentication: PEAP
[*]CA Certificate: AddTrust_External_Root.pem
[*]PEAP version: Automatic
[*]Inner auth: MSCHAPv2
[/LIST]

I tried these solutions (but none of them fixed my problem):
[LIST]
[*][https://askubuntu.com/questions/841620/my-ubuntu-16-04-keeps-disconnecting-from-the-wi-fi-eduroam-why](https://askubuntu.com/questions/841620/my-ubuntu-16-04-keeps-disconnecting-from-the-wi-fi-eduroam-why)
[*][https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617](https://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617)
[*][https://ubuntuforums.org/showthread.php?t=2328764](https://ubuntuforums.org/showthread.php?t=2328764)
[*]Setting IPv6 to "Ignore".
[/LIST]

I would appreciate any helpful information.

Thank you for your time.

---

### Post by Hadaka on 2017-12-28
Hi, your wireless diagnostic report shows atleast one other "5 MHz eduroam essid"
the dmesg section of the report indicates it is roaming back and forth between essid's

eduroam  <MAC [AN3]> Infra  44 5220 MHz 54 Mbit/s  42  &#9602;&#9604;__  WPA2 802.1X    yes * [COLOR=#ff0000]**<-**[/COLOR]
eduroam  <MAC [AN8]> Infra  36 5180 MHz 54 Mbit/s  24  &#9602;___  WPA2 802.1X    no

Bind the mac address of [access point 3] in your Computer's wifi configuration..see attached...
[ATTACH=CONFIG]277951[/ATTACH]

Since you have no access to the Eduroam router..
*You also might consider buying a repeater or converting an old router 
into a repeater/extender and filter it also...
MAC Address Filtering
```
 The Range Extender/Repeater features MAC Address Filtering that
 only allows authorized MAC Addresses to associate with the Range Extender.
```

*IWCONFIG..power mgmt. is on..it should be off
```
wlp8s0    IEEE 802.11abg  ESSID "eduroam"  
          Mode:Managed  Frequency:5.22 GHz  Access Point: <MAC 'eduroam' [AN3]>   
          Retry short limit 7   RTS thr off   Fragment thr off
          Power Management [COLOR=#ff0000]**on**[/COLOR]
```
Please do..
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
boot and test wireless.
Thanks

---

### Post by tomas96 on 2018-01-02
Hello, @Hadaka,

Thank you for your help and time. 

Your first solution I already tried and still using it long time. However, it doesn't help me, unfortunately. I always bind wifi to concrete MAC address, but it still disconnects after some time (maybe a bit later, than without binding). 

Regarding your second solution, I will try and surely write here how it was.

I noticed one strange thing after another attempt fixing my problem. I added to "/etc/modprobe.d/options.conf" file this line:
```
options iwlagn 11n_disable=1 11n_disable50=1
```

The problem of disconnecting seemed to be solved. However, not fully. Now it "doesn't disconnect" (I don't receive alert that Wifi network is disconnected). It just shows full wifi connection (all four wifi lines are filled) and there are no connection actually.... 

Any ideas?

---

### Post by Hadaka on 2018-01-02
Hi, you state..
"I noticed one strange thing after another attempt fixing my problem. I added to "/etc/modprobe.d/options.conf" file this line"```
options iwlagn 11n_disable=1 11n_disable50=1
```
Strange indeed since your wireless driver is a Broadcom driver..."WL"
and the above driver.."iwlagn"..is an INTEL driver, those options should have ZERO
effect on a Broadcom wifi card. Please do...to remove..
```
sudo sed -i '/11n/ d' /etc/modprobe.d/options.conf
```
The dmesg part of the report shows that you are indeed roaming..
other than binding the mac address of the strongest eduroam signal, I really have no
other suggestions.

---

