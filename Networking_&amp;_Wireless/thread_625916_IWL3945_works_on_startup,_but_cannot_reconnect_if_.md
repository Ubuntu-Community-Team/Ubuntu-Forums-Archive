---
title: "IWL3945 works on startup, but cannot reconnect if connection lost"
date: 2007-11-28
forum: Networking &amp; Wireless
---

### Post by R. McC on 2007-11-28
I've been having trouble for a while with my wireless.  For the most part, it works great, no problems.  However, if the router hiccups and the connection is lost for whatever reason, I can't get it back unless I reboot.  I'm left hanging when trying to reconnect via nm-applet at stage 2 of 5, and then am unceremoniously informed that the 120 second timeout has expired and I should "get a better card" or some such nonsense.

```
Nov 28 00:57:49 Prowler NetworkManager: <debug> [1196229469.298893] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'eureka' 
Nov 28 00:57:49 Prowler NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/wlan0 / eureka 
Nov 28 00:57:49 Prowler NetworkManager: <info>  Deactivating device wlan0. 
Nov 28 00:57:49 Prowler NetworkManager: <info>  Device wlan0 activation scheduled... 
Nov 28 00:57:49 Prowler NetworkManager: <info>  Activation (wlan0) started... 
Nov 28 00:57:49 Prowler NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 28 00:57:49 Prowler NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Nov 28 00:57:49 Prowler NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 28 00:57:49 Prowler NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Nov 28 00:57:49 Prowler NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Nov 28 00:57:49 Prowler NetworkManager: <info>  Activation (wlan0/wireless): access point 'eureka' is encrypted, but NO valid key exists.  New key needed. 
Nov 28 00:57:49 Prowler NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network 'eureka'. 
Nov 28 00:57:49 Prowler NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Nov 28 00:57:49 Prowler NetworkManager: <info>  Activation (wlan0) New wireless user key for network 'eureka' received. 
Nov 28 00:57:49 Prowler NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Nov 28 00:57:49 Prowler NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Nov 28 00:57:49 Prowler NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Nov 28 00:57:49 Prowler NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Nov 28 00:57:49 Prowler NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Nov 28 00:57:49 Prowler NetworkManager: <info>  Activation (wlan0/wireless): access point 'eureka' is encrypted, and a key exists.  No new key needed. 
Nov 28 00:57:50 Prowler NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (0/10). 
Nov 28 00:57:50 Prowler NetworkManager: <info>  supplicant_interface_init() - connect to global ctrl socket (1/10). 
Nov 28 00:57:50 Prowler NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant3^I' 
Nov 28 00:57:50 Prowler NetworkManager: <info>  SUP: response was 'OK' 
Nov 28 00:57:50 Prowler NetworkManager: <info>  supplicant_init() - connect to device ctrl socket (1/10). 
Nov 28 00:57:50 Prowler NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
Nov 28 00:57:50 Prowler NetworkManager: <info>  SUP: response was 'OK' 
Nov 28 00:57:50 Prowler NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
Nov 28 00:57:50 Prowler NetworkManager: <info>  SUP: response was '0' 
Nov 28 00:57:50 Prowler NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 657572656b61' 
Nov 28 00:57:50 Prowler NetworkManager: <info>  SUP: response was 'OK' 
Nov 28 00:57:50 Prowler NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 proto WPA2' 
Nov 28 00:57:50 Prowler NetworkManager: <info>  SUP: response was 'OK' 
Nov 28 00:57:50 Prowler NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt WPA-PSK' 
Nov 28 00:57:50 Prowler NetworkManager: <info>  SUP: response was 'OK' 
Nov 28 00:57:50 Prowler NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 psk <key>' 
Nov 28 00:57:50 Prowler NetworkManager: <info>  SUP: response was 'OK' 
Nov 28 00:57:50 Prowler NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
Nov 28 00:57:50 Prowler NetworkManager: <info>  SUP: response was 'OK' 
Nov 28 00:57:50 Prowler NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Nov 28 00:59:50 Prowler NetworkManager: <info>  Activation (wlan0/wireless): association took too long (>120s), failing activation. 
Nov 28 00:59:50 Prowler NetworkManager: <info>  Activation (wlan0) failure scheduled... 
Nov 28 00:59:50 Prowler NetworkManager: <info>  Activation (wlan0) failed for access point (eureka) 
Nov 28 00:59:50 Prowler NetworkManager: <info>  Activation (wlan0) failed. 
Nov 28 00:59:50 Prowler NetworkManager: <info>  Deactivating device wlan0. 

```

I took the (for me, anyway) drastic step of flat-out disabling network manager last night, switching purely to ndiswrapper (using most of the instructions in this thread), which seems to be working fine for now.  I haven't yet experienced a router hiccup to know if it'll come back properly or not.

However, I'm sort of faced with two issues:  
1) I haven't determined *why* nm-applet wouldn't restore the connection.  This is very bothersome to me; I'd at least like to understand what wasn't working, even if it can't be fixed.
2) In the manual configuration solution, there's no way (without opening a terminal) to at-a-glance determine current connection status.  I'd like to have the nm-applet signal strength icon back.  How hard is it to write your own, and how might I go about doing this (maybe some resources explaining some of the ins and outs)?  Or does something like this already exist?  

Thanks!

---

### Post by davisond on 2007-12-14
I have similar problems to you and am also much bothered by the fact that networkmanager seems unable to operate without a gui login.  What is this - windows??

Personally I think the whole networkmanager setup needs rethinking in ubuntu, it's just poor for anyone other than a windows refugee that is happy to reboot a machine every 5 minutes when something goes wrong and never uses console based network apps (like mutt/slrn/nmap and many others that I'd like to use sometimes without being forced to load up the whole of gnome).

Regarding your second question, take a look at conky.  It's a highly configurable system monitor and one of the things it can do is show all of your wireless stats, including connection strength.

Cheers,

---

### Post by R. McC on 2007-12-14
Thanks for the tips, DavisonD.

Unfortunately, the problem continued to recur even without nmapplet governing my connection.  I would posit that it's either related to the IWL3945 wireless driver or a problem with the router at this point.  I have since replaced the router and the problem has not reoccurred, though I have not done any experimentation to find out what happens if it goes down, which it has not yet of its own accord.

---

### Post by melvis02 on 2007-12-21
Don't know if this will help you out, and it's certainly not a permanent solution, but instead of rebooting your system completely, try removing and reloading the module, i.e.:
```
sudo modprobe -r iwl3945
sudo modprobe iwl3945
```
When I get disconnected, I also can't reconnect unless I do this or reboot.  Have tried using wicd as an alternative to nm-applet, but to no avail.

--Trey

---

### Post by R. McC on 2007-12-21
That's a good suggestion.  Next chance I get to test this out, I'll try that.

Thanks!  I'll let you know if it works.

---

### Post by R. McC on 2007-12-25
> **melvis02 said:**
> Don't know if this will help you out, and it's certainly not a permanent solution, but instead of rebooting your system completely, try removing and reloading the module, i.e.:
```
sudo modprobe -r iwl3945
sudo modprobe iwl3945
```
When I get disconnected, I also can't reconnect unless I do this or reboot.  Have tried using wicd as an alternative to nm-applet, but to no avail.

--Trey
Hi Trey,

Your suggestion works!  Unfortunately, however, it's more of a workaround than a real fix.  The connection still drops fairly frequently at lower reception levels (<50%), which tends to leave me continuously unloading and reloading my modules over a period of just a few minutes, since the connection doesn't keep itself alive.

Is it worth logging this as a bug?  Or is there something else obvious that I'm missing?

Thanks!

---

### Post by melvis02 on 2007-12-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/178629](https://bugs.launchpad.net/ubuntu/+bug/178629) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I was going to say it's probably worth posting a bug report and seeing what happens, because I had searched before looking for other documented cases of this and hadn't found any.  But then I searched again and found your bug post :).  I haven't done much work to figure out what's going on, but if I start to find more info I'll add it to the bug post.

---

