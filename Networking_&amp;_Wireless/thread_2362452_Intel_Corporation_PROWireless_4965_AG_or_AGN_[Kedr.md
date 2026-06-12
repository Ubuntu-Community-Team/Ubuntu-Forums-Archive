---
title: "Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4229]"
date: 2017-05-29
forum: Networking &amp; Wireless
---

### Post by djhbrown2 on 2017-05-29
Kubuntu 17.04
 cannot create visible or working wifi hotspot using "Edit your Network Connections"

have tried following various advices in various threads - all that happened was i lost my wired connection to and had to recover from a prior edition of installation

  
d@d-HP-Pavilion-dv6700-Notebook-PC:~$ lspci -vvnn | grep Network
02:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection [8086:4229] (rev 61)
d@d-HP-Pavilion-dv6700-Notebook-PC:~$ lspci -vvnn | grep -A 9 Network | grep Kernel
        Kernel driver in use: iwl4965
        Kernel modules: iwl4965

---

### Post by wildmanne39 on 2017-05-29
Please click on the wireless script in my signature and follow the directions to run it and paste the output to pastebin, then the link back here.

---

### Post by djhbrown2 on 2017-06-07
i switched back to xubuntu 16.04 as earlier installs of xubuntu used to work - but this one seems not to.  i cannot find out whether it is the HP hotspot that isn't working, or the ASUS that's trying to use it.  both seems to have wifi configuration issues, based on what other posters have said in various forums.

anyhow, here is the pastebin results for the HP: [http://paste.ubuntu.com/24804458/](http://paste.ubuntu.com/24804458/)

---

### Post by wildmanne39 on 2017-06-07
Please try:
```
 sudo iwconfig wlp2s0 mode managed
```
if it does connect reboot

---

### Post by djhbrown2 on 2017-06-08
d@d-HP-Pavilion-dv6700-Notebook-PC:~$  sudo iwconfig wlp2s0 mode managed
[sudo] password for d: 
d@d-HP-Pavilion-dv6700-Notebook-PC:~$ 

<rebooted>
during reboot, the following messages flash past (i dont know how to pause the reboot to read them properly):
<something about sdc no page caching>
<a few messages about inode>
"iwl4965 on demand firmware reload" <the Intel proprietary driver had been added a while back in an attempt to get wifi to work)

d@d-HP-Pavilion-dv6700-Notebook-PC:~$ sudo iwconfig wlp2s0 mode managed
d@d-HP-Pavilion-dv6700-Notebook-PC:~$ iwconfig
enp6s0    no wireless extensions.

lo        no wireless extensions.
wlp2s0    IEEE 802.11  ESSID[IMG]https://ubuntuforums.org/images/smilies/icon_surprised.gif[/IMG]ff/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry short limit:7   RTS thr[IMG]https://ubuntuforums.org/images/smilies/icon_surprised.gif[/IMG]ff   Fragment thr[IMG]https://ubuntuforums.org/images/smilies/icon_surprised.gif[/IMG]ff
          Power Management[IMG]https://ubuntuforums.org/images/smilies/icon_surprised.gif[/IMG]ff

i don't know how to turn auto-emoticons off (the paste as plain text button is always greyed out)
question: since i want HP to share its wired connection via wifi, shouldn't i use mode Master?

Create New Wi-Fi Network,,, offers only Network Security WEP tried various length passwords, in each case HP says it is connected to the wifi network created; ASUS can see it, but password never accepted

created WPA2 Hotspot called "2test" Method: Shared to other computers by Settings..Network Connections... 
but Create New Wifi Network..Connection: 2test Save produces 
(2) Connection '2test' is not available on the device wlp2s0 at this time.

i should add that the same hardware (ie HP hotspot + ASUS client) used to work with WPA2 under an earlier version of xubuntu, maybe 14,04

---

### Post by wildmanne39 on 2017-06-08
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

That is how to make the output not have smiley faces ^^^.

You can not connect to the wifi at all is that correct? nothing to do with trying to create a hotspot right?

Once you can connect to the wifi then the following may help create the hotspot.

In Ubuntu 16.04, there&#8217;s a Hotspot mode in the WiFi connection editing settings. 

First disable WiFi and connect your computer to a wired network, then click Edit Connections on the network menu>>> click Add on the network connections to add a new connection:

Choose WiFi from the drop-down box in the next window and click Create button.

When the editing WiFi hotspot window pops up, follow these steps:

Type in connection name, SSID, select Hotspot mode>>>In Wifi Security tab, select WPA & WPA2 Personal and type in a password then under the IPv4 Settings tab, select mode &#8220;Share to other computers&#8221;

After you clicked the save button, enable WiFi and click Connect to Hidden Wi-Fi network and select connect to the connection you just created.

Your network menu should now have the WiFi hotspot connection:

```
sudo systemctl restart NetworkManager.service
```

Then enable WiFi and it should connect.

---

### Post by djhbrown2 on 2017-06-08
on HP laptop:
First disable WiFi - *check*
and connect your computer to a wired network,*check*
then  click Edit Connections on the network menu *check *  - comment: in Xubuntu 16.04, this is called Settings:Hardware:Network Connections,  There is also Settings:System:Network which pops up a window to configure the wired connection.
>>> click Add on the  network connections to add a new connection: *check*
Choose WiFi from the drop-down box in the next window and click Create button. *check*

When the editing WiFi hotspot window pops up, follow these steps:

Type in connection name, SSID, select Hotspot mode>>>In Wifi  Security tab, *check*
select WPA & WPA2 Personal and type in a password then  under the IPv4 Settings tab, select mode &#8220;Share to other computers&#8221;

After you clicked the save button, enable WiFi and click Connect to  Hidden Wi-Fi network and select connect to the connection you just  created.  *check*

result: **Failed to activate connection** (2) Connection 'Wi-Fi connection 1' is not available on the device wlp2s0 at this time.

Your network menu should now have the WiFi hotspot connection: *no, it doesn't, for above reason*

however, i used to be able to create a wifi hotspot on the HP that the ASUS can see (but only could connect to with WiFi Security = None), using this method:
(instead of Connect to Hidden Network)
Create New WiFi Network...

but, since having done sudo iwconfig wlp2s0 mode managed
as previously advised, i now get the same error message  **Failed to activate connection** (2) Connection 'Wi-Fi connection 1' is not available on the device wlp2s0 at this time.

follow-up questions:
1. as mentioned before, the HP+ASUS hardware used to work on, i think, Xubuntu 14.04 (or maybe 12.04, i dont remember now) with WPA2, so maybe i should go back to that version?
2. looking at iwconfig,
       **mode**   Set the operating mode of the device, which depends on the  net-
              work  topology. The mode can be *Ad-Hoc* (network composed of only
              one cell and without Access Point), *Managed* (node connects to  a
              network  composed  of  many Access Points, with roaming), *Master*
              (the node is the synchronisation master or  acts  as  an  Access
              Point),  *Repeater* (the node forwards packets between other wire-
              less  nodes),  *Secondary*  (the  node  acts  as  a  backup   mas-
              ter/repeater), *Monitor* (the node is not associated with any cell
              and passively monitor all packets on the frequency) or *Auto*.
              **Example** **:**
                   *iwconfig* *eth0* *mode* *Managed*
                   *iwconfig* *eth0* *mode* [I]Ad-Hoc

[/I]it seems to me that the mode i require is Repeater (or maybe Secondary), since i want the HP to share its wired connection by wifi with the ASUS?
however, this might mean that i couldnt then use the HP as a client elsewhere?

---

### Post by wildmanne39 on 2017-06-08
This:
> Type in connection name, SSID, select Hotspot mode>>>In Wifi Security tab, select WPA & WPA2 Personal and type in a password then under the IPv4 Settings tab, select mode “Share to other computers”

should have changed it back to shared mode.

You did not answer my question does the wifi work for internet connections while it is in managed mode if not then the hotspot is not going to work,  the wifi has to work first.

---

### Post by djhbrown2 on 2017-06-08
> **wildmanne39 said:**
> This:

should have changed it back to shared mode.

You did not answer my question does the wifi work for internet connections while it is in managed mode if not then the hotspot is not going to work,  the wifi has to work first.

does the wifi work?
several answers:
1. in 2015, under xubuntu 14.04, it worked
2. in 2017, under kubuntu 17.04, it did not work at all
3. in 2017, under xubuntu 16.04, it only works with WiFiSecurity = none
4. since adding mode managed, i always get the error
**Failed to activate connection** (2) Connection 'Wi-Fi connection 1' is not available on the device wlp2s0 at this time.

---

### Post by wildmanne39 on 2017-06-08
Here is your issue:
> WIFI-PROPERTIES.AP:                     no
From the output of the script, your driver does not support ap mode and there is not another driver for device.

---

### Post by djhbrown2 on 2017-06-08
er, um, i trust it makes sense to you, but it doesnt to me, unless *AP:no* is a consequence of having done
mode managed

how can i undo that?  can i, for example, set
mode Auto
?

PS here is the answer to my question: no, i can't!
d@d-HP-Pavilion-dv6700-Notebook-PC:~$ sudo iwconfig wlp2s0 mode Auto
[sudo] password for d: 
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlp2s0 ; Invalid argument.
d@d-HP-Pavilion-dv6700-Notebook-PC:~$ sudo iwconfig wlp2s0 mode Seondary
Error for wireless request "Set Mode" (8B06) :
    invalid argument "Seondary".
d@d-HP-Pavilion-dv6700-Notebook-PC:~$

update: i'm now downloading xubuntu 14.04 iso again and will rebuild it on both HP and ASUS and post back here results of trying to wifi with that.  my guess is something changed in the way encryption is handled between Ubuntu 14,04 and later editions

---

### Post by wildmanne39 on 2017-06-08
It means your driver does not support AP mode anymore, and no amount changing any settings will change that.

I will say it again if you did this according to my directions in my previous post:
> Type in connection name, SSID, select Hotspot mode>>>In Wifi Security tab, select WPA & WPA2 Personal and type in a password then under the IPv4 Settings tab, select mode “Share to other computers”
That would have set it to a shared connection.

---

### Post by djhbrown2 on 2017-06-08
i followed your directions to the letter, noting check at each step

i agree that in its current setup, it looks like it's never going to work. but it did use to work, under 14.04, so im going to try that and will repost here when ive done so.  it will take me quite some time to do this, as its still downloading as we speak, and then i have to install it on 2 laptops.

it presumably is a driver issue, but whether that's because of Intel or Ubuntu i have no idea; drivers are a mystery to me

---

### Post by wildmanne39 on 2017-06-08
I do not use windows, so I can only tell you that the driver that you are using at this time in Ubuntu does not support AP mode.

---

### Post by djhbrown2 on 2017-06-08
windows?!  no - i mean xubuntu 14.04.  it used to work with WPA2 between HP and ASUS, although i recall that an Apple smartphone could only wifi through the HP in security=none connections.

ive tried Fedora 21, 24, 25, Debian 8, no luck there either... sigh... i'm sure it's a really simple fix to the cryptography, but have no idea what that fix is

definitely, the HP laptop hardware is capable of acting as a hotspot and the ASUS hardware is capable of using it.  but i long ago threw away the Windows oses they came with, and wouldnt want them back.

ok 14.04 is downloaded now, so time to reinstall everything for the 100th time....

---

### Post by djhbrown2 on 2017-06-10
Xubuntu 14.04 refused to boot, so i reinstalled Xubuntu 16.04 on both machines. 
 HP can create a wifi hotspot that ASUS can use, but only with security=none. 
Connection information  says driver is iwl4965

Panel...connections.Create New Wifi Network only offers WEP
.. Edit Connections also only offers WEP for the nework created

but Settings... Network Connections..Add.. Wifi..Create... offers WEP, LEAP, Dynamic WEP and WPA2
this seems inconsistent to me

installed linux-firmware 1.157.10

[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/269926](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules/+bug/269926) talks about iwlwifi-4965-2.ucode but (a) i dont know whether HP Pavilion dv6000 requires that and (b) i dont know how to install linux-restricted-modules-common



here is some dmesg output:
```

[   12.094218] iwl4965: Intel(R) Wireless WiFi 4965 driver for Linux, in-tree:
[   12.094219] iwl4965: Copyright(c) 2003-2011 Intel Corporation
[   12.094293] iwl4965 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[   12.094414] iwl4965 0000:02:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
[   12.108236] ACPI Warning: SystemIO range 0x0000000000001028-0x000000000000102F conflicts with OpRegion 0x0000000000001000-0x000000000000107F (\PMIO) (20160422/utaddress-255)
[   12.108242] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   12.108249] ACPI Warning: SystemIO range 0x00000000000011B0-0x00000000000011BF conflicts with OpRegion 0x0000000000001180-0x00000000000011BB (\GPIO) (20160422/utaddress-255)
[   12.108252] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   12.108253] ACPI Warning: SystemIO range 0x0000000000001180-0x00000000000011AF conflicts with OpRegion 0x0000000000001180-0x00000000000011BB (\GPIO) (20160422/utaddress-255)
[   12.108256] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   12.108256] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   12.132648] iwl4965 0000:02:00.0: device EEPROM VER=0x36, CALIB=0x5
[   12.133035] iwl4965 0000:02:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   12.201336] r852: Non dma capable device detected, dma disabled
[   12.201347] r852: driver loaded successfully
[   12.268968] iwl4965 0000:02:00.0: loaded firmware version 228.61.2.24
..............
[   15.715737] input: HP WMI hotkeys as /devices/virtual/input/input12
[   15.716472] iwl4965 0000:02:00.0: RF_KILL bit toggled to disable radio.
[   15.716966] iwl4965 0000:02:00.0: RF_KILL bit toggled to enable radio.
[   15.716968] iwl4965 0000:02:00.0: On demand firmware reload
[   15.716994] ieee80211 phy0: Hardware restart was requested
[   15.723454] iwl4965 0000:02:00.0 wlp2s0: renamed from wlan0
........................
[   25.975017] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   26.228180] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   26.235308] IPv6: ADDRCONF(NETDEV_UP): enp6s0: link is not ready
[   26.245232] r8169 0000:06:00.0 enp6s0: link down
[   26.245243] r8169 0000:06:00.0 enp6s0: link down
[   26.245283] IPv6: ADDRCONF(NETDEV_UP): enp6s0: link is not ready
[   27.993652] r8169 0000:06:00.0 enp6s0: link up
[   27.993662] IPv6: ADDRCONF(NETDEV_CHANGE): enp6s0: link becomes ready
[   33.496426] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   44.609068] sd 6:0:0:0: [sdc] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[   44.609074] sd 6:0:0:0: [sdc] tag#0 Sense Key : Hardware Error [current] [descriptor] 
[   44.609078] sd 6:0:0:0: [sdc] tag#0 Add. Sense: No additional sense information
[   44.609083] sd 6:0:0:0: [sdc] tag#0 CDB: ATA command pass through(16) 85 06 20 00 00 00 00 00 00 00 00 00 00 00 e5 00
[   44.750868] Bluetooth: RFCOMM TTY layer initialized
[   44.750875] Bluetooth: RFCOMM socket layer initialized
[   44.750881] Bluetooth: RFCOMM ver 1.11
[   45.113064] sd 6:0:0:0: [sdc] tag#0 FAILED Result: hostbyte=DID_ERROR driverbyte=DRIVER_SENSE
[   45.113068] sd 6:0:0:0: [sdc] tag#0 Sense Key : Hardware Error [current] [descriptor] 
[   45.113070] sd 6:0:0:0: [sdc] tag#0 Add. Sense: No additional sense information
[   45.113073] sd 6:0:0:0: [sdc] tag#0 CDB: ATA command pass through(12)/Blank a1 06 20 da 00 00 4f c2 00 b0 00 00
[  208.606376] show_signal_msg: 30 callbacks suppressed
[  208.606379] plugin-containe[1798]: segfault at 30 ip 00007fca48a697d8 sp 00007fff011cc6f0 error 4 in libgdk-x11-2.0.so.0.2400.30[7fca48a13000+b0000]

```

---

### Post by wildmanne39 on 2017-06-10
Please do:
```
echo "options iwl4965 11n_disable=1 swcrypto=1" | sudo tee /etc/modprobe.d/iwl4965.conf
sudo modprobe -rfv iwl4965
sudo modprobe -v iwl4965
```
That is all I know to try, but again if the driver does not support AP mode then you will never get it to work as one.

I suspect this laptop may have been connected to your other one but it was not actually the AP as you remember, if you want to use it on the internet run the above command and I recommend implementing the changes in the new install that you did in the old one from this thread, and getting it off of Ad-Hoc to infrastructure or client as I believe it is called in the newer releases, and change the encryption to WPA2 only if you have that option, after you run the above commands you should be able to actually connect to WPA2.

---

### Post by djhbrown2 on 2017-06-10
it looks to me as if you think iwl4965 had become corrupted, so your steps remove and replace it.  is my understanding correct?

```

d@d-HP-Pavilion-dv6700-Notebook-PC:~$ echo "options iwl4965 11n_disable=1 swcrypto=1" | sudo tee /etc/modprobe.d/iwl4965.conf
[sudo] password for d: 
options iwl4965 11n_disable=1 swcrypto=1
d@d-HP-Pavilion-dv6700-Notebook-PC:~$ sudo modprobe -rfv iwl4965
rmmod iwl4965
rmmod iwlegacy
rmmod mac80211
rmmod cfg80211
d@d-HP-Pavilion-dv6700-Notebook-PC:~$ sudo modprobe -v iwl4965
insmod /lib/modules/4.8.0-36-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/4.8.0-36-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/4.8.0-36-generic/kernel/drivers/net/wireless/intel/iwlegacy/iwlegacy.ko 
insmod /lib/modules/4.8.0-36-generic/kernel/drivers/net/wireless/intel/iwlegacy/iwl4965.ko 11n_disable=1 swcrypto=1 
d@d-HP-Pavilion-dv6700-Notebook-PC:~$ 

```

Create New Wifi Network still only offers WEP
creating a connection with Settings...Network Connections.. Add (SSID=ffs)  ... security = WPA and WPA2 Personal [I]done
[/I]Create New Wifi *Network..Connection=ffs...*Create[I]..produces:

[/I]**Failed to activate connection**
(2) Connection 'ffs' is not available on the device wlp2s0 at this time

Edit Connections...ffs.. Edit..security=None... Save...Create New Wifi Network,,, Connection:ffs...Create.. [I]oh no, now this doesnt work either, 
[/I]Edit Connections...ffs..Delete..Create New Wifi Network,,, Connection:ffs...Create.. WiFi Security= None.. Connection established

booting up ASUS machine..WiFi Networks are Available..*click on* ffs... Connection Established...open Firefox...*it works*

so no change.  the problem is not the driver per se, it's the security module of network manager that isnt working for me.  both laptops can see several other wireless hotspots ion the neighbourhood, so they can see mine too, and use it, since its unsecured.

back on HP laptop, Edit Connections..ffs (still being used by ASUS).. _Mode has been set to Ad-Hoc, whereas i had chosen Hotspot !_  Security=None ... change it to WEP (WPA is not on the dropdown list)... Save

***and the ASUS internet connection is still working!  HP thinks security of ffs is WEP, but ASUS thinks its None!!***

it looks to me that Network Connections is in a big mess; i would have expected changing the security of a connection to have immediate effect, whereas it looks like its only remembering it for next time....
let's test that:

on HP: Wireless..Disconnect..
on ASUS: still thinks its connected!, but Firefox is stuck - it doesnt even know it cant connect; it still thinks it's connected to ffs, which is no longer active

some questions, if i may:
1. are you the author of network connections manager?  if not, do you know who is and how i can contact them?
2. would you agree that my best bet is to try to go back to Xubuntu 11.10?  as i mentioned earlier, there WAS a time when it worked, but i cant remember what version of Xubuntu is was using at the time.  i had thought iy was 12.02 as i still have an old cd with that on, but when i tried it, it didnt work; so maybe it was an even older version that did.
3. from another thread, i saw someone saying that their wifi stopped  working after they upgraded from Ubuntu 11.10 to 12.02, so maybe that's  when the change to the driver occurred and it's still the same, probably  because few people have such old hardware. Is firmware is independent of OS?  i am sure the original firmware supplied by HP would have worked, but maube Ubuntu is keen to replace all proprietary software, including firmware, with its own, and something went wrong during the change from 11.10 to 12.02 as far as people with dv6000 hardware is concerned.  if firmware is independent of OS, maybe i should try to get the original driver from HP? - but maybe that is what iwlwifi-4965 is?  is there a way to find out whether the author of iwlwifi-4965 is Intel or someone in Ubuntu?
4. Unless you have a better idea, i am going back to Xubuntu 11.10.  Either that, or ....

---

### Post by wildmanne39 on 2017-06-10
No we did not replace the driver, we only added parameters to make it work better.

You have to go into the router to change the encryption to WPA2 then you save the setting and reboot the router, then you go into network manager and change the settings to WPA and WPA2 and save the settings then reboot the computer and if you have not manually changed something else it should connect to the internet, but it can not be used as an AP. If you go to an old version and go online you will get hacked jacked and cracked.

If it does not connect I recommend you run the wireless script again so we can see what it looks like after you reinstalled.

Any setting you change, unless I ask you to run code should be done in network manager, not be editing a file. Did you change the settings in network manager? then save them? or did you edit a file? if you edit a a file that is an additional issue.

No I did not right the book, but I have been doing this for 6 years and I am pretty sure this old driver never had the capability to be used as an AP, there use to be an application called hostpd I think, maybe it allowed it to be an AP but the new Ubuntu's do not use it anymore.  I am almost positive the driver would still have had to have that capability for the app to work.

That is obviously an old computer, my recommendation would be to research and find a good cheap usb adapter that allows you to do what you want to do and buy it because going backwards is not a good idea especially that far back.

---

### Post by djhbrown2 on 2017-06-10
i could see you have had a long-term involvement with ubuntu wifi, so i reckon if you cant fix my problem, no-one can.

you keep saying my old driver doesnt have the capability to be an AP - if AP means "Access Point" and if that means "access to internet" then i am 100% sure that the HP dv6000 DOES have that capability, because it can serve as a wifi router for the ASUS to connect to, which it can, but only provided security=none.

trying to change the security settings on the HP WiFi hotspot (=Ad-Hoc, whatever than means) to WEP or WPA doesnt work - but like i said, there was a time when it did.

for sure, older software can be cracked, jacked etc, but since NSA can do that to everyone anyway, i dont care if some spotty teenager can do it too.  i would rather have a setup that casual borrowers of bandwidth cant tap into, as that would slow what's left for me.  determined and competent hackers can get into anything, i would guess.

there is another possible solution for me: my internet connection is via a single-line wired connection - but maybe there is a router on the market which would provide wifi throughout the whole house?  if so, i wouldn't have to use the HP as the router; it and the ASUS can both be clients.

All i want to do is be able to use internet from the garden, so i can sit outside in the fresh air whilst bashing my brains out with software - that's not too much to ask, is it?

Ubuntu seems to not want me to use 11.10 - it says it will take 9 more hours to download it from [http://old-releases.ubuntu.com/releases/xubuntu/releases/11.10/release/](http://old-releases.ubuntu.com/releases/xubuntu/releases/11.10/release/) :)

---

### Post by wildmanne39 on 2017-06-10
You can always get an wifi extender that will increase the range of your wifi signal. 

There are a few people here that are better at wireless then I am maybe one of them will pop in.

---

### Post by djhbrown2 on 2017-06-10
from experiences of a couple of years ago, the range of the HP wifi transmitter is enough to cover the whole house (and both it and the newer ASUS can detect signals from other transmitters several houses away - but the ASUS has its won configuration problems; i tried using it as the router instead of the HP but that didnt work either.  the common factor is Ubuntu network manager) - all i need now is a touch of security.  only 7 hours to go before i can test 11.10 :)

it's very decent of you to try and help me; greatly appreciated.

current state of affairs (still on 16.04) here:
[http://paste.ubuntu.com/24828921/](http://paste.ubuntu.com/24828921/)

i forgot i had disconnected ffs lovely isnt it, how smart editors think they know what's best? god knows who writes these things and assumes formats will continue after a space regardless of whether that makes any sense or not i better not rant too much about software writers :)

even a newline doesnt change anything

and remove format button doesnt stop it either

not even when i select text and remove format

never mind, here is the pastebin from a new run of the script, after HP thinks its has created a WEP connection:

[http://paste.ubuntu.com/24828995/](http://paste.ubuntu.com/24828995/)

oh, theres an unlink button,,,, great, it unlinked everything... dont board software writers ever test anything?!

it's tough to write software that works - which to my way of thinking is all the more reason why writers should test their stuff before releasing it

sorry about the rant... so, back at the ASUS keyboard, the "Connect" button is greyed out until i reach the 5th character of the password (which is 8 characters long) but when i type the 6th character it greys out again; 5 characters later, it lights up
so it likes passwords of length 5 and 13
ok, software is the boss, i am merely its vassal, so i hop over to HP and change the ffs password to 5 characters
(i imagine you can guess what ffs stands for)
oh, 11.10 download is only 6 hours away now, at 17kbs...
HP thinks ffs is disconnected, but its menubar thinks its still connected - HP is psychizophrenic :)
delete ffs altogether, start over
it asks me "are you sure?" i want to tell it "yes, i am - you are so sure of yourself, but you are so wrong!"
omg, even after i deleted it, the menubar notifier still thinks its alive!
creating ffs2 with 5-character password... Connection Established
over to ASUS... click on ffs2... type in password... click on Connect.... after about 2 mins it says "Disconnected, you are now offline"
it didnt know i was offline before i tried to connect!
i wonder what HP thinks? here is a 3rd pastebin, of the situation now:
[http://paste.ubuntu.com/24829111/](http://paste.ubuntu.com/24829111/)

Edit connections...WiFi, security-None, fails same way as before, BUT
delete ff3; panel..Create New Wifi Connection,,, ffaliffe.. security=none .. Connection established
over to ASUS.. connect to ffaliffe connection established, test Firefox ... [B][I]works

from the above i conclude that
1. hardware is working
2. drivers are working
3, ubuntu encryption software is not working or at least is incompatible with Intel/ASUS drivers, and no tinkering is going to ever change that
4. therefore, if 11.10 doesnt work any more, i will buy 2 macs[/I][/B]

---

### Post by djhbrown2 on 2017-06-12
this update comes to you from my ASUS (under Xubuntu16/04), which accesses internet via wifi through the HP which created a WEP hotspot under Fedora26.  i'd be happy to share any info if you'd like Ubuntu to be able to achieve the same feat.

after what feels like decades of trialing and erroring, i now think the Ubuntu wifi development team deprecate WEP and have rewritten the legacy driver to prevent WEP being used; however, the Intel wifi proprietary driver only supports WEP; the iwlwifi legacy driver in the recommended debian nonfree wifi firmware package has the same name as the one supplied by linux-firmware and ubuntu dkpg refuses to overwrite it because it's non-free; there was an earlier version of Ubuntu that would create a WPA2 hotspot, but ive been unable to boot from the archived .iso image of Xubuntu 10.4 on either machine.  however, fedora 26 did boot, so im using that.

---

