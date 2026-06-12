---
title: "Unstable wifi connection after upgrading to 16.04"
date: 2016-11-19
forum: Networking &amp; Wireless
---

### Post by jj.wauters on 2016-11-19
Since I upgraded from Ubuntu 14.04 to 16.04 I have many problems with my wifi connection.
While a lot of people using 16.04 seems to have a broken network connection after hibernating, in my case it's on booting.
In one of the five times I am booting, I have no network connection.
Running 'sudo service network-manager restart' or similar commands don't help to restore my connection.
My only solution until now is restart/boot in windows/boot in Ubuntu. After that wifi works in Ubuntu.
Any help to solve is appreciated.

---

### Post by wildmanne39 on 2016-11-19
Are you disabling the wifi in windows before you boot into ubuntu? are you hibernating windows? if no to those questions please try:
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
``` 
Then reboot and post the output of:
```
iwconfig
```
Thanks

---

### Post by jj.wauters on 2016-11-19
1) No to your 2 questions
2) sudo sed... did not rendered anything on screen
3) after reboot iwconfig rendered next :
lo        no wireless extensions.

```
wlan0     IEEE 802.11bgn  ESSID:"WiFi-2.4-BE91"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 30:91:8F:17:BE:91   
          Bit Rate=58.5 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=69/70  Signal level=-41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:101   Missed beacon:0

eth0      no wireless extensions.
```

---

### Post by wildmanne39 on 2016-11-19
The command did not show anything because it was successful and confirmed by the iwconfig. Use if for a while and see if turning of power management helped. It is also possible the module is not getting loading but you would need to run the wireless script again while it will not connect by using this command.
```
./wireless-info
```

---

### Post by jj.wauters on 2016-11-19
Setting the parameter=2 did not solve. 
Included the new wireless-info when not connected.
Perhaps next information may be useful to you :
- when I have a connection, it remains stable during the whole time I'm working.
- when I have a connection I can disable and enable again.
- last weeks I had a lot of "Sorry, Ubuntu 16.04 has experienced an internal error" messages after starting Ubuntu.
  Is there any information in those messages that can help you?

---

### Post by wildmanne39 on 2016-11-19
When you say you have no connection when boot lost of the time, does it try to connect or is it like it does not even have a wireless card?

---

### Post by wildmanne39 on 2016-11-19
Set the router to broadcast only 802.11g make sure to click save then run the following command and change the way encryption is handled.
```
echo "options rt2800pci nohwcrypt=1" | sudo tee /etc/modprobe.d/rt2800pci.conf
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci
```
Reboot the computer.

---

### Post by jj.wauters on 2016-11-20
First I thought that in about 20% of the cases I had this network problem.
Now I found a pattern in when network is on or off.
It has cost me a lot of time in rebooting but this may be interesting :

test1
-Beginning situation : start Ubuntu/network is on
-What I did : shutdown Ubuntu/start Ubuntu
-Result : network remains on (mail, localhost, internet, ... are working)

test2
-Beginning situation : start Ubuntu/network is on
-What I did : restart Ubuntu
-Result : after each restart the network connection is down and I can't restore from within Ubuntu

I repeated test1 and test2 10 times with the same result

test3
-Beginning situation : restart Ubuntu/network is off due to test2
-What I did : click on enable/disable network
-Result : network remains off (message=Disconnected-you are now offline)

test4
-Beginning situation : start Ubuntu/network is off due to test2
-What I did : restart and select Windows loader/network is on/shutdown windows/start Ubuntu
-Result : network is on

test5
-Beginning situation : start Ubuntu/network is off due to test2
-What I did : click on enable/disable network
-Result : network comes on

So my conclusion is that (in this configuration) networking in Ubuntu 16.04 seems to work as expected when shutting down at the end of a working session. On the other hand, when **using a restart, Ubuntu locks the network card.**

---

