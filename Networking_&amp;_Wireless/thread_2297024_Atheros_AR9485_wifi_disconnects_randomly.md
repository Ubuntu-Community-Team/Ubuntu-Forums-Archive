---
title: "Atheros AR9485 wifi disconnects randomly"
date: 2015-09-30
forum: Networking &amp; Wireless
---

### Post by sethj3 on 2015-09-30
I originally posted this on Ask Ubuntu, but having not received any help there I am reposting it here. I'm offering a "bounty" (in AU terms) of 100 points for anyone who solves this for me ;p  

[HR][/HR]
I recently bought a new computer that has an Atheros AR9485 wireless NIC. So far it has been working ok except this one issue: Randomly (as far as I can tell) it will completely lose the internet connection. The indicator in the top panel will still say we are connected but the machine has no internet connectivity whatsoever.  

I've been able to get it working again by simply disconnecting from my wireless AP and then reconnecting, but this is annoying. Is there anything I can do to make the connection more stable?  

I have tried passing the nohwcrypt=1 to the driver, but that made it impossible to connect to any AP, it just infinity attempted to connect.


```

sudo modprobe -rfv ath9k
sudo modprobe -v ath9k nohwcrypt=1

```

I've also tried upgrading my kernel to Linux 4.0 but the problem persists.


Exact chip:

```

02:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)  
```

Driver: 

```

$ ls /sys/class/net/wlan0/device/driver/module/drivers
  pci:ath9k  platform:ath9k 
``` 

and `lsmod`:

```

user@host:~$ lsmod | grep -e ath -e ndis
    ath3k                  20480  0 
    bluetooth             491520  9 bnep,ath3k,btusb
    ath9k                 147456  0 
    ath9k_common           32768  1 ath9k
    ath9k_hw              458752  2 ath9k_common,ath9k
    ath                    32768  3 ath9k_common,ath9k,ath9k_hw
    mac80211              724992  1 ath9k
    cfg80211              540672  4 ath,ath9k_common,ath9k,mac80211  
```

I'm running Ubuntu 15.04 on Linux 4.0.0-040000-generic on a Lenovo G510.

---

### Post by sethj3 on 2015-09-30
Here is the output from the wireless scrip: [http://paste.ubuntu.com/12625978/](http://paste.ubuntu.com/12625978/)  

I've also started wondering if it might have anything to do with my 2.4GHz wireless mouse and just a lousy antenna..

---

### Post by jeremy31 on 2015-09-30
I would set the regulatory info with ```
sudo iw reg set US
``` I would also change the wireless router to channel 9 instead of being crowded on channel 1 with 8 other access points

---

### Post by sethj3 on 2015-09-30
Cool, I gave those a shot (actually changed to channel 7). Would you mind also explaining how to unset the iw command? I accidentally applied two potential fixes to my problem and won't know which fixed it unless I can figure out how to unset one.  

Thanks!

---

### Post by jeremy31 on 2015-09-30
You should be able to put it back where it was with ```
sudo iw reg set 00
``` and you can check with ```
iw reg get
```

I have a Lenovo with a AR9485 but I don't have any close neighbors with wifi and your channel and regulatory settings are the only issues I saw.  I know chili555 would suggest using 20Mhz instead of 40 if you have that option on the wireless router

Here is one of his posts copied

[COLOR=#000000][FONT=verdana]First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router.[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]Next, I recommend that your regulatory domain be set explicitly. Check yours:[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]sudo iw reg get
If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) 
Then set it temporarily:[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]sudo iw reg set IS
Of course, substitute your country code if not Iceland. Set it permanently:[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]gksudo gedit /etc/default/crda
Use nano or kate or vim if you don't have the text editor gedit.[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]Change the last line to read:[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]REGDOMAIN=IS
Proofread carefully, save and close the text editor.[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png) This example is for ethernet, but you want wireless.[/FONT][/COLOR]

---

### Post by sethj3 on 2015-11-29
This fixed my problem! Thanks Jeremy. If you want to post an answer on my Ask Ubuntu question ([https://askubuntu.com/questions/673156/atheros-ar9485-wifi-disconnects-randomly](https://askubuntu.com/questions/673156/atheros-ar9485-wifi-disconnects-randomly)) I will give you the bounty I offered when I first asked the question.  

(sorry for the late reply, I wanted to make sure it was definitely fixed and then life got really busy)

---

### Post by jeremy31 on 2015-11-30
I posted the answer at askubuntu, but I see no reason for the bounty as I am more interested in helping people than points.  Fabby sent me a message about your question and I thought my suggestions were already covered

---

