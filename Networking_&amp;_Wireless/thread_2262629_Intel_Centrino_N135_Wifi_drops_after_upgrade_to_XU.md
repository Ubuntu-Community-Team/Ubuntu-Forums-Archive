---
title: "Intel Centrino N135: Wifi drops after upgrade to XUbuntu 14.10"
date: 2015-01-26
forum: Networking &amp; Wireless
---

### Post by mchl.nix on 2015-01-26
Hello, this is a mirror to a question I posted on askUbuntu. After a user there tried to help me over the span of the whole day, he suggested posting my problem here. I hope you can shed some light into my situation.

I upgraded yesterday from xUbuntu 14.04 to 14.10, because I hoped to have better bluetooth recognition. (I didn't).

  **Before the upgrade**

  Wifi would drop out seemingly randomly. More often, when there was  more space/stuff between me and my router, but also when nothing  changed. 
  Time could be between 2 days and (in extreme cases) a few minutes.
  I need to disable-enable the whole network by using the dropdown  menu, because after losing connection the SSID of the router is not in  the menu for me to choose. The router itself does not lose connection to  any other device and I'm connected to it again after 5 seconds, after  re-enabling the network.

  **After the upgrade**

  Wifi drops out faster now ~10-30 minutes.
  [HR][/HR]  I already tried [this solution]("http://ubuntuforums.org/showthread.php?p=13119513#post13119513"). But it didn't work. 
  Output of '[The Script]("http://askubuntu.com/questions/425155/my-wireless-wifi-connection-does-not-work-what-information-is-needed-to-diagnos/425205#425205")' (too long): [http://paste.ubuntu.com/9850671/](http://paste.ubuntu.com/9850671/)

  Any further information will be gladly provided. I would be very  grateful for some help and even a little explanation what the problem is  if possible.
  [B]
Update 1[/B]

  ```
Jan 24 17:21:37 Laptop kernel: [ 7755.037954] wlan0: deauthenticated from xx:xx:xx:xx:xx:xx (Reason: 7=CLASS3_FRAME_FROM_NONASSOC_STA)
```
  This line appears everytime my connection drops. Might be connected to [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux-firmware/+bug/1293569")

  **Update 2**

  For the time being, I made a script automatically reconnecting me.
  ```
#!/bin/bash
while :
do
        if ! ping -c 3 -W 1 192.168.2.1 >/dev/null 2>&1; then
                notify-send 'Network gone down' 'Reconnecting...'
                nmcli nm enable false;
                sleep 0.5;
                nmcli nm enable true;
                sleep 10
        fi
        sleep 1
done
```
  IP address might need to be changed. It  may also produce some false positives. It is a hack, after all. Still  better than manually clicking through menus every time, though.

  **Update 3**

  Current output of 'The script': [Here]("http://paste.ubuntu.com/9870590/")

**Update 4**

Output of the Skript now: [http://paste.ubuntu.com/9902174/](http://paste.ubuntu.com/9902174/)


Any help in clearing this up would be helpful. The script above is  working good enough, since it mostly stays within the timeout rate of  most networking application. But it would be of course better to have a  working solution.

**Update 5**
Have been at my parents place for the weekend. No disconnects  whatsoever. So it seems that my home router is playing a role in this,  too.

Script output for this router: [Click]("http://paste.ubuntu.com/9994618/")


My wifi card is an Intel Centrino N135.

What was already tried:


[LIST]
[*]Changed the channel of my router to 11, 6, 1 
[*][FONT=courier new]echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
[/FONT] 
[*][FONT=courier new]11n_disable=8 to 1[/FONT] 
[*]Disabled ufw with [FONT=courier new]sudo ufw disable[/FONT] 
[*]Updated script in Update 3 
[*]Tried setting [FONT=courier new]sudo iw reg set **DE**[/FONT] 
[*]Tried setting[FONT=courier new] iwconfig wlan0 power off
[/FONT] 
[*]Purged [FONT=courier new]tlp[/FONT] package 
[*][FONT=courier new]echo "options iwlwifi [COLOR=#000000]uapsd_disable=Y" | sudo tee -a /etc/modprobe.d/iwlwifi.conf[/COLOR][/FONT]
[*][FONT=courier new]sudo sed -i 's/^REG.*=$/&**DE**/' /etc/default/crda[/FONT]
[*]Setting the router to* WPA/TKIP*, because another router with this configuration worked flawlessly 
[/LIST]

---

### Post by jeremy31 on 2015-01-26
The command is ```
sudo iw reg set DE
``` and this is something new and it might help ```
echo "options iwlwifi [COLOR=#000000]uapsd_disable=Y" | sudo tee -a /etc/modprobe.d/iwlwifi.conf[/COLOR]
```[COLOR=#000000] reboot and cross your fingers

Run the script again and post results if it doesn't help[/COLOR]

---

### Post by mchl.nix on 2015-01-27
[HR][/HR]Wifi seems stable right now. Will try the new command, once I verified, that it didn't just magically fixed itself.

Did not work either, unfortunately.

[B]Update 4

[/B]
[Skript-Output]("http://paste.ubuntu.com/9902174/")

---

### Post by mchl.nix on 2015-02-01
Have been at my parents place for the weekend. No disconnects whatsoever. So it seems that my home router is playing a role in this, too.

Script output for this router: [URL="http://paste.ubuntu.com/9994618/"]Click


[/URL]

---

### Post by jeremy31 on 2015-02-01
Setting the country code could fix it, if you are in Germany
```
sudo iw reg set DE
```
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo sed -i 's/^REG.*=$/&DE/' /etc/default/crda
```
Reboot[/FONT][/COLOR]

---

### Post by mchl.nix on 2015-02-02
Did not help either, unfortunately.

I'm starting to think it's an  issue with my router. But no other device (android, ios, windows  laptop) has these issues. And it did get worse, when upgrading to 14.10.

I'm at a loss.

---

### Post by jeremy31 on 2015-02-02
The strange thing is that the router at your parents router reported this ```
[COLOR=#000000]IE: IEEE 802.11i/WPA2 Version 1[/COLOR]                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
```
And TKIP is usually a problem with Linux and your router shows no sign of TKIP or WPA version 1, so a possiblity would be to enable WPA and TKIP on your router and see if it works better

---

### Post by mchl.nix on 2015-02-05
I made the change, but the network is still cutting out.

This is really a mystery.

---

