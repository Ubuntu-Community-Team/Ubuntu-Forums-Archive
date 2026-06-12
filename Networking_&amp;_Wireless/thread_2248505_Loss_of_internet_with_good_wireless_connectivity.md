---
title: "Loss of internet with good wireless connectivity"
date: 2014-10-15
forum: Networking &amp; Wireless
---

### Post by mark-lamorey on 2014-10-15
I lose internet connectivity - cannot ping any site and web browsers stall on trying to resolve the address.
I think it is an issue with DNS / DHCP - using  [ cat /var/log/syslog | grep -i dhcp  ] I get the below last entry.
 
Oct 14 20:35:54 TINY NetworkManager[1047]: <info> (wlan0): canceled DHCP transaction, DHCP client pid 1892

Any thoughts on how to debug / figure out why this happens ?

---

### Post by irv on 2014-10-15
Was it working and then just stopped? Can you ping your router or another PC on your network? Have you tried rebooting? Have you tried rebooting your router? I would start with all this to see it starts working again, if it was working?

---

### Post by Michael_McKenney on 2014-10-15
Check your ifconfig.  Can you ping your DNS servers?  Can you ping your gateway address (router)?   Did you lose your settings for gateway and DNS servers?

---

### Post by mark-lamorey on 2014-10-15
Seems like whenever I come hear to post I lose my internet :mad:
But rebooting fixes everything.
I never reboot the router or the modem as they work for all the other devices.

I cannot ping my DNS 192.168.1.1 or anything else.
The wireless script says I have good signal coming across the WiFi signal 

wlan0     IEEE 802.11bgn  ESSID:"LamNet"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: <MAC 'LamNet' [AN4]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=46/70  Signal level=-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:225   Missed beacon:0

---

### Post by jeremy31 on 2014-10-15
> **mark-lamorey said:**
> Seems like whenever I come hear to post I lose my internet :mad:
But rebooting fixes everything.
I never reboot the router or the modem as they work for all the other devices.

I cannot ping my DNS 192.168.1.1 or anything else.
The wireless script says I have good signal coming across the WiFi signal 

wlan0     IEEE 802.11bgn  ESSID:"LamNet"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: <MAC 'LamNet' [AN4]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=46/70  Signal level=-64 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:225   Missed beacon:0

Can you post the result of the wireless_script from the sticky post "before posting....

---

### Post by davit2 on 2014-10-16
do you use VPN?
check your /etc/resolv.conf when everything is ok, and check it again when connection is lost. put the output of /etc/resolv.conf here.

---

### Post by mark-lamorey on 2014-10-16
Interesting 

nameserver 127.0.1.1

This is not what I expected , I will check it when things break.
Thxs !

---

### Post by irv on 2014-10-16
Why don't you post your Active Network Connections when you have a connection and then post it when you don't.
[ATTACH=CONFIG]257271[/ATTACH]

Also I would still say reboot the router. All my other stuff that was using wireless was working but I was having trouble with one connection so I rebooted my router and it fixed the problem. I believe that rebooting the router clears it and you have a fresh connection on everything on your network.
The ip address you posted is just your local host address.

---

### Post by mark-lamorey on 2014-10-16
Ok, I took the advice and rebooted modem and router - no fails yet, but only been a few hours.
Prior to that I took the snapshots you suggested with internet and without and they both look identical.
My DNS looks local 192.168.1.1

I ran the wireless script before and after , but cannot figure out how to attach...

---

### Post by mark-lamorey on 2014-10-16
Remembered that I can not post files in quick reply...
[ATTACH=CONFIG]257279[/ATTACH]

Above file is with good connectivity to internet
Hopefully, these come through ok
Below is with good wireless signal but no internet connectivity

[ATTACH=CONFIG]257280[/ATTACH]

---

### Post by jeremy31 on 2014-10-16
For some reason your firewall is very active when you have no internet connectivity, try disabling UFW and see if the problem persists
It wouldn't hurt to do this ```
sudo iw reg set US
``` if iw is not installed for whatever reason then ```
sudo apt-get install iw
```
Then repeat the sudo iw reg set US command

---

### Post by mark-lamorey on 2014-10-16
Ok, I see that now that UFW is blocking (not sure why I missed that)
- I will try to track down which PID it is blocking first - not sure if worthwhile.

I have IW installed, and curious what the "set US" command does.
"MAN IW" has very limited information

---

### Post by mark-lamorey on 2014-10-17
Looks like I I can restart networking if I turn disconnect from my wireless and turn off Gufw, and then reconnect to the wireless port.
I will try to keep track of in what order I turn things back on to see if it makes a difference.

If I understand this correctly my network connection for Ubuntu is getting shut down because my firewall is going haywire ?
Or is it because of malicious activity (inside to outside or vice versa). Any thoughts on how can I tell the difference on all counts ?

---

### Post by mark-lamorey on 2014-10-18
After much help and continued searching I think this is fixed - the key was searching on RTL8723BE and then I saw many others with a very similar problem.

Running the below seemed to make everything stable :
echo "options [COLOR=#417394]rtl8723be[/COLOR] fwlps=N ips=N" | sudo tee /etc/modprobe.d/rtl8723be.conf

If I understand things it keeps the wireless from going into sleep of power saving mode as the driver does not seem to wake up properly.

Thanks to all ...

---

