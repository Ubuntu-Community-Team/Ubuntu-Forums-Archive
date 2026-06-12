---
title: "Network Manager installed, but not showing/working (newbie)"
date: 2007-02-06
forum: Networking &amp; Wireless
---

### Post by rasmusbp on 2007-02-06
Hi 

I used to run 6.06 and my wireless networking was fine (that is, an Intel Pro 2200BG card working through Network Manager and IPW drivers). A few weeks ago, I upgraded to 6.10 (Edgy) through the automatic update applet, and then the wireless connection was completely gone. 

First, it seemed that the problem was that Network Manager (NM) had somehow been installed in the upgrade process. So I installed it again just now, and rebooted, but NM does not show anywhere - not in the task bar, as it normally did, and not in the menues. There is only the "traditional" network icon in the task bar, showing some kind of connection (lo). However, according to synpatic, NM is installed. 

I need some help, please, anyone? I'm new at linux/ubuntu, so please don't get too technical on me...  ; )

Many thanks for this great forum!

Regards,
Rasmus
Copenhagen, Denmark

---

### Post by Floppyjoe on 2007-02-06
Were you using ndiswrapper with those IPW drivers?

---

### Post by rasmusbp on 2007-02-06
I'm not 100% sure, but I think I followed this HowTo:
[http://www.ubuntuforums.org/showthread.php?t=26623&highlight=ipw+2200+howto](http://www.ubuntuforums.org/showthread.php?t=26623&highlight=ipw+2200+howto)

Which, as far as I can see, doesn't involve the use of ndiswrapper (whatever that is)...  : )

Thanks

---

### Post by Floppyjoe on 2007-02-06
Maybe check to see if your /etc/wpa_supplicant.conf file still has the right info in it. Maybe it got overwritten by the upgrade.
```
sudo gedit /etc/wpa_supplicant.conf
```

---

### Post by rasmusbp on 2007-02-06
Hmm....that file is completely empty at the moment. That must be a mistake?

Thanks

---

### Post by Floppyjoe on 2007-02-06
> **rasmusbp said:**
> Hmm....that file is completely empty at the moment. That must be a mistake?

Thanks
Well I was assuming you were using WPA encryption but if your not then that file should be empty but if you are then it needs some setup.

---

### Post by rasmusbp on 2007-02-06
Well, eventually, I want to set up WPA, but the immidiate problem is that Network Manager does not work at all - although it is installed. Can you or anyone else help with that?

Thanks

---

### Post by Floppyjoe on 2007-02-06
What is the output of your /etc/network/interfaces file?
```
sudo gedit /etc/network/interfaces
```

---

### Post by rasmusbp on 2007-02-06
that file is empty too....  :confused:

---

### Post by Floppyjoe on 2007-02-06
I think it should have these two lines in there at minimum:
> auto lo
iface lo inet loopback
The rest can be commented out or not there like yours is when using network manager.

---

### Post by rasmusbp on 2007-02-06
seems like there was something in the interface file anyway:

> auto lo
iface lo inet loopback

iface eth0 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

auto eth0



However, Network Manager still does not work or show, and I cannot see a list of available wireless networks....

Thanks!

---

### Post by Floppyjoe on 2007-02-06
It should look like this:
```
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp


```

---

### Post by rasmusbp on 2007-02-06
Ok, I changed it and rebooted, but it's still the same. 

Funny thing is that the programe "Wi-fi radar" works fine and shows me the wireless networks in the area - indeed, it says that I am connected to one of them (an unprotected one, which it must have done on its own, I sure didn't). I can see my own network, but I don't have the chance to connect here, as the disconnect button does not work. 

Thanks!

---

### Post by Floppyjoe on 2007-02-06
You can be sure wifi-radar will interfere with network manager and rewrite your /etc/network/interfaces file. If you prefer to use network manager I would remove all other network connecting programs because of this. Make sure the /etc/network/interfaces file looks like the one in my post above before you reboot after removing these programs.

Edit: also make sure all network interfaces are disabled in System/Aministration/Networking.

---

### Post by rasmusbp on 2007-02-07
Joe, thanks very much for your continuing assistance! I did exactly as you recommended in the last post, but Network Manager (NM) still does not show in the task bar or in the menu. I tried to enable the wireless connection in system > administration > networking, but it does not allow me to see any of the networks (as NM used to do). What can I do now to resolve this?

Thanks!

---

### Post by Floppyjoe on 2007-02-07
You have to have all your wireless interfaces disabled for network manager to work. Otherwise your /etc/network/interfaces file will be overwritten and network manager won't be able to control that interface. For me the network manager applet appears on the top bar as a two computers networking icon. It does not show up on the menu system. Also make sure that Network-manager-gnome is installed along with network-manager.

---

### Post by stavaroti on 2007-02-07
Hi,

Okay so I tried to reset everything as mentioned in this forum and others, but network manager still does not show my wireless connections.  The funny thing is that wifi radar will, but i can not use wifi radar because it does not allow me to to use wpa.  I have a dell 700m with a broadcom wireless chip in it, i think 1390, and here are somemore details from *-network:

*-network:0 UNCLAIMED
                description: Network controller
                product: BCM4309 802.11a/b/g
                vendor: Broadcom Corporation
                physical id: 1
                bus info: pci@02:01.0
                version: 03
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                resources: iomemory:e0204000-e0205fff irq:10

Any help will be appreciated

Thanks.

---

### Post by rasmusbp on 2007-02-07
Joe, all network interfaces are disabled. And Network-Manager-Gnome is also installed. I've attached a screendump, so these things show. The content of the etc\network\interface file is still exactly the same as you recommended. 

I guess the best thing would be to make a clean install of 6.10, or maybe even go back to 6.06, but I don't have time for this at the moment...   : (

Thanks

---

### Post by Floppyjoe on 2007-02-07
Just for curiosity's sake when you enable your wireless interface in System/Administration/Networking, what is your wireless interface called when you issue the command:
```
iwconfig
``` 
is it wlan0 or eth1 or something else?
On my laptop it was eth1 but networkmanager doesn't recognize this as a wireless designation. I had to change the designation from eth1 to wlan0 in the file /etc/iftab for network manager to see it as a wireless interface.

---

### Post by rasmusbp on 2007-02-07
Now we might be getting somewhere. Indeed, it looks like my wireless interface through the upgrade was reborn as "eth1". 

Here is the output from the command line after "iwconfig":

> lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"Victor"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:60:B3:19:0F:2D   
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=73/100  Signal level=-55 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:5

sit0      no wireless extensions.

I notice that the wireless automatically connects to "Victor", some random unprotected network in the area...

Then, I took a look in the /etc/iftab file: 
> 
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:0e:a6:3f:aa:87 arp 1
eth1 mac 00:0e:35:4f:19:04 arp 1

Could you please let me know how to change this, or perhaps post the content of your iftab file?

Thanks again!
Rasmus

---

### Post by Floppyjoe on 2007-02-07
```
sudo gedit /etc/iftab
```
Edit your file to look like this:
```
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:0e:a6:3f:aa:87 arp 1
wlan0 mac 00:0e:35:4f:19:04 arp 1 
```
then save this file.

Do not forget to disable this interface again after this change.

---

### Post by rasmusbp on 2007-02-07
Ok, I made the changes you recommended, but I still can't choose from any networks. When I access system > administration > networking, I have to write an SSID (network name) and a password before I can actually enable the device. However that does not seem to work and the device doesn't care anyway - when it is enabled, it connects to this other unprotected network on its own. 

The output of /etc/network/interfaces now:

> auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

The output of /etc/iftab now:

> 
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:0e:a6:3f:aa:87 arp 1
wlan0 mac 00:0e:35:4f:19:04 arp 1

Any ideas?

Thanks!

---

### Post by Floppyjoe on 2007-02-07
I'm assuming you rebooted your computer after these changes. I attached a screenshot from my laptop. In the top bar there is a signal strength icon which is my network manager icon showing four bars. Do you get something like this when your computer connects to the random network? When I click on it it shows me the available networks.

---

### Post by rasmusbp on 2007-02-07
I rebooted after the changes, but unfortunately I didn't get the signal strenght icon... I also tried to reinstall Network-Manager, but nothing seems to work. 

Thanks anyway!

PS Cool background...

---

### Post by Floppyjoe on 2007-02-07
So once again I'll ask you if you have both network-manager and network-manager-gnome installed? They both need to be installed. Other than that I can't see why it would not be working.

---

### Post by rasmusbp on 2007-02-07
I'm truly sorry to say that both seem to be installed. Thanks for the efforts, Joe! 
I give up on Edgy now... :( 

All the best,
Rasmus

---

### Post by mooter on 2007-02-13
I'm having problem getting network-manager to show as well, because I want to switch to wpa without resorting to ndiswrapper.
It used to show after I installed it, but somehow I disabled it; I think I did that in the Sessions dialog from System->Preferences, so I enabled it but that doesn't make a difference, I've rebooted, looked for all the files in the folders which they are, I don't understand what the problem is.  It's not a network issue, it's the icon not showing up issue.

---

### Post by Mimsy on 2007-02-13
> **rasmusbp said:**
> I'm truly sorry to say that both seem to be installed. Thanks for the efforts, Joe! 
I give up on Edgy now... :( 


I have the exact same problem in Dapper, and I was following this thread with great interest... I will continue to follow it, in case a working solution turns up. Not having network-manager-gnome show up as installed, or for that matter be able to connect to wireless networks with it, is becoming very frustrating.

Good luck!

/Mimsy

---

### Post by mooter on 2007-02-13
Also, has anyone been able to reconnect without rebooting?  Even if you have to use a dynamic address?  If I lose my connection, I have to reboot, perhaps the right network manager could handle this?

---

### Post by H.E. Pennypacker on 2007-03-01
rasmusbp, at this point, it looks like you had, under Connection Properties (that icon on the panel), "lo" selected.  You need to click on the drop down menu, and select your wireless device (probably eth1).  You will then see a vibrant orange bar displaying your internet connectivity, if there is an internet connection.

---

### Post by venome on 2007-05-27
perhaps a dumb question, but have you checked that network-manager really starts at startup?

---

