---
title: "Connecting to WPA &amp; WPA2 enterprise Wi-Fi"
date: 2017-02-17
forum: Networking &amp; Wireless
---

### Post by pokehge on 2017-02-17
I'm having a hard time trying to connect to a WPA protected wi-FI  with My Lenovo 710s running Ubuntu 16.04.1 LTS. The wi-fi does not need  any CA certificate only username and paasword. The problem im having is  that sometimes it connects, sometimes it just randomly dc's and Im not  able to reconnect and sometimes I cant connect at all. I can connect to  any other wi-fi except this one.
  I've tried Downgrading My wpa_supplicant to version 2.1 with no luck.


  Thanks in advance.

---

### Post by TheFu on 2017-02-17
How close is the laptop to the wifi antenna?  5 ft? Line of sight? or 200 ft around a corner of a brick/cement bldg?

Some wifi cards need extra help to work with some APs.  Changes to the AP settings AND sometimes options for the wifi card driver are needed.

There is a wifi-info script in these forums. Find that, run it, and post the output back here for more help.  Also the exact type of AP being used and info about it would be helpful.

Along with all the other stuff, the output from 
```
sudo iwlist scan| egrep 'SSID|wlan|Channel|Quality|Cell'

``` would be helpful.

Please use **code tags**, like I did above, so things are readable.

---

### Post by pokehge on 2017-02-17
> **TheFu said:**
> How close is the laptop to the wifi antenna?  5 ft? Line of sight? or 200 ft around a corner of a brick/cement bldg?

Some wifi cards need extra help to work with some APs.  Changes to the AP settings AND sometimes options for the wifi card driver are needed.

There is a wifi-info script in these forums. Find that, run it, and post the output back here for more help.  Also the exact type of AP being used and info about it would be helpful.

Along with all the other stuff, the output from 
```
sudo iwlist scan| egrep 'SSID|wlan|Channel|Quality|Cell'

``` would be helpful.

Please use **code tags**, like I did above, so things are readable.

Thanks for your answer!

I was in a rush and left my laptop at work, but I'll try those things and reply as soon as I get back on Monday. I'm actually not sure where the antenna is, but I had the Wi-Fi working flawlessly for 2 days so I doubt that it's that.

---

### Post by TheFu on 2017-02-17
Things change. In 2 days, a new AP could have been setup by someone else that trashes your connectivity.

wifi signals get interference all the time as different devices come in and out of range. Interference is a huge problem with wifi. You need to know where the antenna is or it isn't worth the effort, IMHO.  Trying to connect to an AP too far away is a waste of time.  Same for trying to connect when there are different SSIDs on the same channel of similar signal strengths.

I always use wired whenever possible.  I'm typing this on a chromebook with a USB3-to-ethernet adapter.  Wifi is available, but after working 1200+ deployments in my career, I've learned to avoid wifi whenever possible.  Makes me much happier.

If it worked 2 days ago, it probably is NOT driver or Ubuntu settings related. I would start with the environment.

---

### Post by pokehge on 2017-02-20
```


Output for 
sudo iwlist scan| egrep 'SSID|wlan|Channel|Quality|Cell':lo        Interface doesn't support scanning.

          Cell 01 - Address: 44:D9:E7:88:F6:01
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=49/70  Signal level=-61 dBm  
                    ESSID:"Can connect"
          Cell 02 - Address: 44:D9:E7:88:F6:00
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/70  Signal level=-62 dBm  
                    ESSID:"Can't connect"
          Cell 03 - Address: 44:D9:E7:88:91:00
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    ESSID:"Can't connect"
          Cell 04 - Address: 04:18:D6:76:E3:A0
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=48/70  Signal level=-62 dBm  
                    ESSID:"Can't connect"
          Cell 05 - Address: 44:D9:E7:88:91:01
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/70  Signal level=-73 dBm  
                    ESSID:"Can connect"
          Cell 06 - Address: 04:18:D6:DA:AC:E0
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    ESSID:"Can't connect"
          Cell 07 - Address: 04:18:D6:77:0A:40
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=50/70  Signal level=-60 dBm  
                    ESSID:"Can't connect"
          Cell 08 - Address: 04:18:D6:77:0A:41
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=49/70  Signal level=-61 dBm  
                    ESSID:"Can connect"
          Cell 09 - Address: 04:18:D6:DA:AC:E1
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=48/70  Signal level=-62 dBm  
                    ESSID:"Can connect"
          Cell 10 - Address: 44:D9:E7:88:F6:10
                    Channel:36
                    Frequency:5.18 GHz (Channel 36)
                    Quality=35/70  Signal level=-75 dBm  
                    ESSID:"Can't connect"

```
I switched the SSID to "Can connect" and "Can't connect" since I can connect to the guest wi-fi but not the employee one.

---

### Post by pokehge on 2017-02-20
I'm sorry for the double post but I'm having all kinds of trouble editing/posting today.

Here is the wireless-info.txt:

[http://pastebin.com/YzU17A6k](http://pastebin.com/YzU17A6k)

---

### Post by TheFu on 2017-02-20
whoever setup this wifi doesn't appear to understand RF. Putting nearby APs on the same channel is a terrible idea. They should rotate between ch1, ch6 and ch11 in the USA. These are the only 2.4GHz channels that don't overlap in the USA spectrum.  Other countries have different allowed channels, like Japan adds ch13 which should ALWAYS be used there.  Using the same channel **and** same SSID means the clients can't figure out which AP to connect with. 

Then there is the signal strength.  In my home, I'm seeing -32dB- -44dB for signal levels.  Those in the -50 and higher levels are down the street - in different bldgs. You need a closer AP. Or did I misread the signal strengths posted above?

The posting issues have been happening to me too, but I get a warning first, so I've learned not to dbl post by saving the post into my xbuffer, then reloading the thread. Almost always, my post actually did go through and no other actions are needed.  Actually got an error posting this replay.  "Must wait 30 seconds ..."

---

### Post by pokehge on 2017-02-20
Okay, so there is an AP right next to me, which rules out that problem, any other suggestions?

---

### Post by wildmanne39 on 2017-02-20
Please do:
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
The wireless file shows:
```
auto lo
iface lo inet loopback
 
auto wlan0
iface wlan0 inet dhcp
```
It also shows network manger is installed and running if that is the case them that file should only have the following in it:
```
auto lo
iface lo inet loopback
```
This command should reset that file:
```
echo -e "auto lo\niface lo inet loopback" | sudo tee /etc/network/interfaces
```
If you still have trouble after doing the above commands please run the wireless script again and post the file again.
Thanks

---

### Post by TheFu on 2017-02-20
> **pokehge said:**
> Okay, so there is an AP right next to me, which rules out that problem, any other suggestions?

You moved?  Or that AP isn't on?

That number of APs all using the same channels is a poor design.

---

### Post by wildmanne39 on 2017-02-20
I have to +1 this:
> That number of APs all using the same channels is a poor design. 
it is a nightmare for network manager.

---

### Post by TheFu on 2017-02-20
> **wildmanne39 said:**
> I have to +1 this:

it is a nightmare for network manager.

Plus all those signals are about the same, bad, signal strength, so there isn't clear AP to connect with will always be in question by the NIC firmware. It will likely require futzing with some wifi NIC settings that we generally don't need to futz with to get any connection stable.

If I were staying at this hotel, I'd talk to the general manager about this poor design. I'd explain that each AP using the same channel was like his wife talking to him about multiple different topics, from every direction, all the same-channel APs and he wouldn't know which to actually listen to.

He probably doesn't know any better (he shouldn't need to know) and the company that put this in must have left it misconfigured. If they used a central wifi management system, the APs would self-correct for channel diversity using the best options possible automatically. Even the cheapest solutions from Ubiquiti do this.

<rant>
This is why I always travel with a portable wifi travel router and use the plugged in ethernet port in the room. My AP, my security and I'm behind a router I control.   I have had to sit in a lobby to do work a few times because the wifi sucked and there wasn't any wired connection in the room.  I always try to look overly relaxed - like a bum when I do this. Want to make the hotel feel the pain (of some guy in a bathrob and slippers hanging out in the lobby) that I'm feeling too. ;)   
</rant>

---

### Post by pokehge on 2017-02-21
> **TheFu said:**
> You moved?  Or that AP isn't on?

That number of APs all using the same channels is a poor design.

I have been sitting next to the AP all the time apparently.


> **wildmanne39 said:**
> Please do:
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
The wireless file shows:
```
auto lo
iface lo inet loopback
 
auto wlan0
iface wlan0 inet dhcp
```
It also shows network manger is installed and running if that is the case them that file should only have the following in it:
```
auto lo
iface lo inet loopback
```
This command should reset that file:
```
echo -e "auto lo\niface lo inet loopback" | sudo tee /etc/network/interfaces
```
If you still have trouble after doing the above commands please run the wireless script again and post the file again.
Thanks
  
Erm, so I ran the commands and nothing happened, I then deleted the old configuration in ```
 [/etc/NetworkManager/system-connections/SSID]("http:///etc/NetworkManager/system-connections/SSID")
``` and now this box keeps popping up: [http://imgur.com/a/SO0VD](http://imgur.com/a/SO0VD)
I'm certain the credentials are right because I use the same for other work related stuff.

Also, here is the new wireless script: [http://pastebin.com/apFGcArM](http://pastebin.com/apFGcArM)

---

### Post by pokehge on 2017-02-26
After further research I'm assuming that the problem has something to do with the fact that its WPA protected, should I try downloading another version of the wpa_supplicant?

---

### Post by TheFu on 2017-02-26
I've never seen that issue.  If you've connected to the wifi network, I would think the problem wasn't with authentication.

---

### Post by wildmanne39 on 2017-02-26
If your company does not use IPV6 then set that to ignore in network manager because it causes issues with all linux distributions. Please change network manager settings to match the screenshots.

Let try a driver parameter:
```
echo "options iwlwifi 11n_disable=1 swcrypto=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwldvm
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
Thanks

---

