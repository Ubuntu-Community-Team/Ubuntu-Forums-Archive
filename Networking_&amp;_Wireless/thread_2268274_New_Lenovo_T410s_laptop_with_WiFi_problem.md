---
title: "New Lenovo T410s laptop with WiFi problem"
date: 2015-03-07
forum: Networking &amp; Wireless
---

### Post by danne33 on 2015-03-07
Got a new Lenovo T410s laptop. Everything was working fine with internet and downloading all the updates and so on.
After a few reboots the WiFi started acting weird. After a while it compeletly dropped and now I can't even find wlan0 in ifconfig -a.
However Internet works fine if I use USB live OS or log into dual boot Windows 7. 
Any ideas how to fix it?
> lspci -nn | grep 0280
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6200 [8086:4239] (rev 35)

Edit:
Now it goes sometimes up and sometimes down. However if I just press on my WiFi in Network-manager applet then it is up again. 
The WiFi symbole is blicking a lot. However the connection very stable in Windows 7.
Is there anyway to automatically reconnect when connection drops?
Was thinking to update the firmware driver. Found this page but I don't know how to install it.
[ https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi]("https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi")

Edit 2:
Think the latest drivers are now installed but still the WiFi symbol on the laptop is blinking constantly. 
> dmesg | grep iwldvm
[    4.496795] iwlwifi 0000:03:00.0: loaded firmware version 9.221.4.1 build 25532 op_mode iwldvm[URL="https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi"]

[/URL]The connection is still not that good in Ubuntu 14.04 but it is working. In Windows 7 is it perfect and never blinks.

---

### Post by chili555 on 2015-03-08
I own and use successfully two Intel wireless devices. I have honed a few techniques in several years and thousands of forum posts.

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

If these changes do not help, please try:```
sudo -i
echo "options iwlwifi 11n_disable=8"  >>  /etc/modprobe.d/iwlwifi.conf
exit
```Reboot.

Finally, Network Manager will default to ethernet if it's available. Please make your tests with the ethernet detached.

---

### Post by Bucky Ball on 2015-03-08
*Thread moved to **Networking & Wireless**.*

---

### Post by danne33 on 2015-03-09
The following changes were really effective:
Set channel width of 20  MHz in the 2.4 GHz band instead of automatic 20/40 MHz. 
Set fixed channel to 6, rather than  automatic channel selection.
Set router to auto B, G and N. 
Ignore IPv6 in Network Manager.
Wanted to choose WPA2-AES but the only option was WPA and WPA2 mixed mode.

>  sudo iw reg get
country GB:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR

Really weird that is it written GB. Right now I have absolutely no connection to GB. 
I use VPN but never connected to Great Britian.
Should I still do the following steps that you mentioned but to GB even if I have have no connection there?
sudo iw reg set IS
gksudo gedit /etc/default/crda
REGDOMAIN=IS

There was some errors here: 
> dmesg | grep iwl
[    4.746874] iwlwifi 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[    4.747039] iwlwifi 0000:03:00.0: irq 44 for MSI/MSI-X
[    4.768139] iwlwifi 0000:03:00.0: Direct firmware load failed with error -2
[    4.768144] iwlwifi 0000:03:00.0: Falling back to user helper
[    5.033041] iwlwifi 0000:03:00.0: Direct firmware load failed with error -2
[    5.033046] iwlwifi 0000:03:00.0: Falling back to user helper
[    5.135061] iwlwifi 0000:03:00.0: loaded firmware version 9.221.4.1 build 25532 op_mode iwldvm
[    5.194968] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    5.194973] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    5.194974] iwlwifi 0000:03:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    5.194977] iwlwifi 0000:03:00.0: Detected Intel(R) Centrino(R) Advanced-N 6200 AGN, REV=0x74
[    5.195140] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[    5.235878] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    6.012232] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[    6.019831] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x1
[    6.232812] iwlwifi 0000:03:00.0: L1 Enabled - LTR Disabled
[    6.240124] iwlwifi 0000:03:00.0: Radio type=0x1-0x3-0x1


Is it a problem?

Now the connection is really good. The WiFi symbole blinks sometimes but it is much more rarely.

---

### Post by chili555 on 2015-03-09
> **danne33 said:**
> The following changes were really effective:
Set channel width of 20  MHz in the 2.4 GHz band instead of automatic 20/40 MHz. 
Set fixed channel to 6, rather than  automatic channel selection.
Set router to auto B, G and N. 
Ignore IPv6 in Network Manager.
Wanted to choose WPA2-AES but the only option was WPA and WPA2 mixed mode.



Really weird that is it written GB. Right now I have absolutely no connection to GB. 
I use VPN but never connected to Great Britian.
Should I still do the following steps that you mentioned but to GB even if I have have no connection there?
sudo iw reg set IS
gksudo gedit /etc/default/crda
REGDOMAIN=IS

There was some errors here: 


Is it a problem?

Now the connection is really good. The WiFi symbole blinks sometimes but it is much more rarely.May I assume you set REGDOMAIN=IS because you are actually, really in Iceland? If not, I'd change it to your actual location. 

The seeming errors are not really errors. As you can see here, there are three possible firmware files available for your device.


[ATTACH=CONFIG]260538[/ATTACH]

I think the driver is looking for the oldest file and doesn't find it; then the next oldest and doesn't find it and then it finds and loads the newest. My *dmesg* shows the exact same thing.

I am glad it's working! Please use thread tools at the top to mark Solved.

---

