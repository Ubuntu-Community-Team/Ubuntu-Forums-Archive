---
title: "Ubuntu 18.04 disconnects from network at exactly every 30 minutes"
date: 2019-04-20
forum: Networking &amp; Wireless
---

### Post by babarehner2 on 2019-04-20
Dell Precision 7520 laptop UBuntu 18.04.2 drops network (ethernet) connection at exactly every 30 minutes to Win10 machine(RDP from Win10 to Ubuntu18.04). Original install was 16.04 and has been updated to 18.04. After network connection drop, data is saved. "journalctl -u NetworkManager" indicates computer is going to sleep. Attempted to correct with "sudo systemctl mask suspend.target". With this workaround computer disconnects one time, the first 30 minutes and all data is lost. Laptop screen shows error message "see systemctl status snap.network-manager.networkmanager.service". At this time unable to log in to laptop from keyboard. But I am able to log in from the Win10 machine and no more network drops. 
Have attempted to use system settings and graphical dconf-editor to find a location where this shutdown signal is coming from. Wifi is set to NOT turn off on Settings menu.

---

### Post by kc1di on 2019-04-20
Hi Babarehner2,
Welcome to Ubuntu forums. 

Usually that is the function of the wifi powersave you can turn it off by opening the following file as root and changing the powersave=3 to powersave=2.```
/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

the file will look like this. ```
[connection]
wifi.powersave = 3
```

Change the 3 to 2 so it looks like this ```
[connection]
wifi.powersave = 2
```  Then reboot.  see if it stops the disconnects. 
good luck.  

You can change the file will any text editor but you have to have root privileges. Also you can confirm that power management is turned of with this command in a terminal
```
iwconfig
``` which will so an output similar to this. ```
wlp3s0    IEEE 802.11  ESSID:  
          Mode:Managed  Frequency:2.437 GHz  Access Point: C0:3F:0E:C7:95:E4   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:[COLOR="#FF0000"]off[/COLOR]

```

---

### Post by babarehner2 on 2019-04-26
Thank for a your reply. Below is a copy of my " [COLOR=#000000][FONT=&amp]/etc/NetworkManager/conf.d/default-wifi-powersave-on.conf" file after making the change.

[/FONT][/COLOR][connection]
wifi.powersave = 2

Below is a copy of my iwconfig output after rebooting.

lo        no wireless extensions.


wlp2s0    IEEE 802.11  ESSID:ff/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:ff   Fragment thr:ff
          Power Management:[COLOR=#ff0000]on[/COLOR]
          
enp0s31f6  no wireless extensions.

As you can see I have previously turned my wifi off because I had a suspicion that there might be a configuration problem with the wifi. Also I wanted to make sure my Windows RDP connection to the Ubuntu machine goes through the ethernet connection. 

Cheers,

Mike







[COLOR=#000000][FONT=&amp]

[/FONT][/COLOR]

---

### Post by babarehner2 on 2019-04-26
Further research leads me to this anomaly. I turned my wifi back on. Made sure my wifi.powersave=2 on both the local connection and the network connection. Then I checked iwconfig.

**Local Connection**
```

enp0s31f6  no wireless extensions.


lo        no wireless extensions.


wlp2s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:[COLOR=#FF0000]off
[/COLOR]
```
But when I RDP in from the network Windows machine I see the power management is on.

**Network Connection**
```

enp0s31f6  no wireless extensions.


lo        no wireless extensions.


wlp2s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:[COLOR=#FF0000]on
[/COLOR]
```


I wonder if there is a permission problem thrown in somewhere along with the power problem.

Cheers,

Mike

---

### Post by praseodym on 2019-04-27
Check the router settings, if it renewes its DHCP connection or IP address to/from the ISP every 30 minutes (or so).

---

### Post by babarehner2 on 2019-04-27
Looked at router settings. Did not find any problems there. Also I have another older Ubuntu laptop that runs a new install of Ubuntu 18.04 and there are [COLOR=#ff0000]NO[/COLOR] issues with dropping connections there. The laptop in question has been updated from a Dell Ubuntu 16.04 image. I have asked Dell for assistance and their last solution was to reinstall Ubuntu 16.04 and/or reinstall Windows. I am beginning to suspect it has something to do with 16.04 update and gnome desktop not playing as nice as they should. I would update the problem laptop to a clean install of 18.04 but that means a lot of reconfiguring work to get my dev environment back. Thanks for the suggestion though.

---

### Post by jeremy31 on 2019-04-27
It might be worth doing ```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
systemctl restart network-manager.service
```
That will keep Network Manager from enabling wifi power management

---

### Post by babarehner2 on 2019-04-30
Thank you for your suggestion. Unfortunately it won't work. There is no problem with the default-wifi-on.conf file. Once edited it stays at "2".

```

[connection]
wifi.powersave = 2



```

The fact is that Iwconfig gives a different output when I log in locally and when I am logging in from the network. When I login locally iwconfig tells me that PowerManagement is off. But when I log in from a network Power Management is on.

```

lo        no wireless extensions.


enp0s31f6  no wireless extensions.


wlp2s0    IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management[COLOR=#ff0000]:on[/COLOR]



```

When I do journalctl -u NetworkManager I get the following output:

```

Apr 30 12:19:36 wolf NetworkManager[8577]: <info>  [1556641176.5524] manager: NetworkManager state is now CONNECTED_SITE
Apr 30 12:19:36 wolf NetworkManager[8577]: <info>  [1556641176.5525] policy: set 'Wired connection 1' (enp0s31f6) as default for IPv4 routing and DNS
Apr 30 12:19:36 wolf NetworkManager[8577]: <info>  [1556641176.5526] device (enp0s31f6): Activation: successful, device activated.
Apr 30 12:19:37 wolf NetworkManager[8577]: <info>  [1556641177.6435] manager: NetworkManager state is now CONNECTED_GLOBAL
Apr 30 12:49:33 wolf NetworkManager[8577]: <info>  [1556642973.6437] manager: sleep: sleep requested (sleeping: no  enabled: yes)
Apr 30 12:49:33 wolf NetworkManager[8577]: <info>  [1556642973.6438] device (wlp2s0): state change: unavailable -> unmanaged (reason 'sleeping', sys-iface-state: 'managed')
Apr 30 12:49:33 wolf NetworkManager[8577]: <info>  [1556642973.6441] manager: NetworkManager state is now ASLEEP
Apr 30 12:49:33 wolf NetworkManager[8577]: <info>  [1556642973.6443] device (enp0s31f6): state change: activated -> deactivating (reason 'sleeping', sys-iface-state: 'managed')
Apr 30 12:49:33 wolf NetworkManager[8577]: <info>  [1556642973.6779] device (enp0s31f6): state change: deactivating -> disconnected (reason 'sleeping', sys-iface-state: 'managed')
Apr 30 12:49:33 wolf NetworkManager[8577]: <info>  [1556642973.7107] dhcp4 (enp0s31f6): canceled DHCP transaction, DHCP client pid 15999
Apr 30 12:49:33 wolf NetworkManager[8577]: <info>  [1556642973.7107] dhcp4 (enp0s31f6): state changed bound -> done
Apr 30 12:49:33 wolf NetworkManager[8577]: <info>  [1556642973.7129] device (enp0s31f6): state change: disconnected -> unmanaged (reason 'sleeping', sys-iface-state: 'managed')



```

So as I see it the Network Manager is going to sleep at exactly every 30 minutes but I don't know how to stop it from going to sleep or what's making the Network Manager sleep.

---

### Post by praseodym on 2019-04-30
Do you need the NWM for VPN or other things? If not, try Wicd instead

---

