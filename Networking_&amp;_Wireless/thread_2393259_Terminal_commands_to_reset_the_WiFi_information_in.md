---
title: "Terminal commands to reset the WiFi information in Ubuntu 18.04"
date: 2018-05-31
forum: Networking &amp; Wireless
---

### Post by jgwphd on 2018-05-31
What are the Ubuntu 18.04 terminal commands needed to reset the WiFI connection. I'd like to erase all information associated with a WiFI connection (as if it is a newly installed 18.04) and reset/restart the network manager ....or whatever is used to manage the WiFi network connections. BTW, the network controller from lspci command is: 02:00.0 Network controller: Intel Corp Centrino Ultimate-N 6300 (rev35) 

Background: I had a WiFi connection error early during a "clean install" of 18.04 on a Dell Laptop (I think it just installed it without the WiFi connection being active). Earlier it ran 17.10 with WiFi just fine 30 minutes before the new install of 18.04. Everything including Ethernet works fine and I can see the WiFi networks and select a network but whatever network I select I keep getting an "authentication required" message loop. Also the "nmcli d wifi list" command shows the wifi networks.  So the WiFi hardware works. I don't want to do a reinstall of 18.04 (but if I do I will do it while connected to Ethernet this time instead of WiFi to avoid problems). I am thinking a command to wipe clean any left over connection information along with a reboot, if needed, would probably solve my problem. Of course if any one has any better ideas please let me know. Thanks!

---

### Post by chili555 on 2018-06-01
> I am thinking a command to wipe clean any left over connection information along with a reboot, if needed, would probably solve my problem. Then the command is:```
sudo rm /etc/NetworkManager/system-connections/*
sudo service network-manager restart
```It may take a reboot.

If it doesn't solve this, then post back and we'll continue troubleshooting:> whatever network I select I keep getting an "authentication required" message loop.

---

### Post by jgwphd on 2018-06-01
Thanks for your assistance and I do need your help. I went back and re-installed 18.04 with the Ethernet cable connected. I had no installation errors.  Everything including Ethernet works fine and I can see the WiFi  networks and select a network but whatever network I select I keep  getting an "authentication required" message loop. The message reappears every 90 seconds after I click on connect. I checked my WiFi password multiple times and it works on another machine I have. So I know its good. This is so odd since the machine had Ubuntu 17.10 working with WiFi just the other day. 

I have a Dell Latitude Model E6430. The "lspci" command shows a line with "02:00.0 Network controller: Intel Corp Centrino Ultimate-N 6300 (rev35)" The "lshw -C network" command shows on the configuration line "driver=lwlwifi" (command output is below this note). I have a manual WiFi switch to turn off and on the WiFi adapter and when I turn it off and back on you can see the networks being reported in the select network list. The "nmcli d wifi list" shows a selection of detected networks and security is listed as WPA2 for all of them. It seems clear to me that the WiFi hardware is working. I suspect a driver issue???  ...your thoughts about that?  I noticed at: [https://www.intel.com/content/www/us/en/support/articles/000006507/network-and-i-o/wireless-networking.html](https://www.intel.com/content/www/us/en/support/articles/000006507/network-and-i-o/wireless-networking.html) that my wireless adapter was discontinued as of November 2017. ...after 17.10 but before 18.04. Could 18.04 have changed from 17.10 and not include the correct driver?

Thinking I have a driver issue I went to "software and updates" and selected the additional drivers tab...it thinks a bit and finally reports "No additional drivers available". Is the "iwlwifi" driver, from the lshw command, the correct one? The Intel website at: [https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi?action=AttachFile&do=get&target=iwlwifi-6000-ucode-9.221.4.1.tgz](https://wireless.wiki.kernel.org/en/users/Drivers/iwlwifi?action=AttachFile&do=get&target=iwlwifi-6000-ucode-9.221.4.1.tgz) shows a list of drivers with module name "iwldvm" and three "firmware" sections listed for this Centrino Ultimate-N 6300 (it is in the second table lower on the page). I assume these are drivers? Some of my many questions are: Am I at the right place for this Intel WiFi Centrino Untimate-N 6300 adapter? If so which one of the three selections should I download. And finally how do I install the driver? Also, I may be lost and is it something else. Again many thanks for your assistance. 

$ lshw -C network
WARNING: you should run this program as super-user.
       description: Wireless interface
       product: Centrino Ultimate-N 6300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: 35
       serial: 24:77:03:da:28:00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.15.0-22-generic firmware=9.221.4.1 build 25532 latency=0 link=no multicast=yes wireless=IEEE 802.11
     resources: irq:31 memory:f7d00000-f7d01fff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

---

### Post by chili555 on 2018-06-01
> whatever network I select I keep getting an "authentication required" message loop.As we suspected. Removing the existing connection information has no bearing on your problem.> Could 18.04 have changed from 17.10 and not include the correct driver?
Nope.> I went to "software and updates" and selected the additional drivers tab...it thinks a bit and finally reports "No additional drivers available"The only wireless drivers that the tool installs are for Broadcom. You have none.> a driver issue??? ...your thoughts about that?Actually, I suspect a router issue, but I'll cover that in a few moments.> The Intel website at: [https://wireless.wiki.kernel.org/en/...-9.221.4.1.tgz](https://wireless.wiki.kernel.org/en/...-9.221.4.1.tgz) shows a list of drivers with module name "iwldvm" and three "firmware" sections listed for this Centrino Ultimate-N 6300 (it is in the second table lower on the page). I assume these are drivers? These are firmware files only, not drivers. Usually, the package *linux-firmware* has the latest non-experimental, developers version firmware files as soon as they are released by Intel. Let's see what firmware version is loaded for your device:```
dmesg | grep iwl
```The Intel site you link suggest that you need 6000-ucode-4 or some such. What actually loaded?

Please undertake the steps at my post #2 here and tell us if there is any improvement: [https://ubuntuforums.org/showthread.php?t=2392705](https://ubuntuforums.org/showthread.php?t=2392705)

---

### Post by jgwphd on 2018-06-02
@chili55, Many many thanks for your assistance. I am currently traveling the next two days. But I brought along the laptop. After I read your comment about the router, I tried WiFi in the hotel ...and it worked!! So it has to be something associated with my laptop and/or my home AT&T router (Pace Pic Model 5268AC). I noticed errors in the output from the "dmesg | grep iwl" command. The output of the command follows: 

[   17.709630] iwlwifi 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[   17.942306] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-6000-6.ucode failed with error -2
[   17.943809] iwlwifi 0000:02:00.0: Direct firmware load for iwlwifi-6000-5.ucode failed with error -2
[   17.969391] iwlwifi 0000:02:00.0: loaded firmware version 9.221.4.1 build 25532 op_mode iwldvm
[   17.984084] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   17.984085] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   17.984086] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   17.984088] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Ultimate-N 6300 AGN, REV=0x74
[   18.413986] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   18.869911] iwlwifi 0000:02:00.0 wlp2s0: renamed from wlan0
[   25.706946] iwlwifi 0000:02:00.0: Radio type=0x0-0x3-0x1
[   25.958756] iwlwifi 0000:02:00.0: Radio type=0x0-0x3-0x1
  
I am not sure how to interpret the output but I see the words "failed" and "error" in the output. I guess I have a firmware problem! Your thoughts?  How do I fix this? ...or do you need more information?   ..and, if you know, I am very curious why this problem showed up in 18.04 and not 17.10. I appreciate any explanation you can provide. Again thanks for your assistance!

---

### Post by chili555 on 2018-06-03
>  iwlwifi 0000:02:00.0: loaded firmware version 9.221.[COLOR="#FF0000"]4[/COLOR].1 build 25532 op_mode iwldvmThe driver looked for the -6 version of the firmware and failed to find it. It looked for -5 and failed. It looked for -4 and found and loaded it. There is no error that is significant or even harmful here.

As far as I know, the only non-experimental, non-developer-mode firmware that even exists for your device is -4. The driver *iwlwifi* is written, however, to load later versions automagically should they be developed by Intel, released and included in the Ubuntu package *linux-firmware*. Very clever, in my opinion!

Those of us with older and yet perfectly serviceable Intel devices can probably look forward to no new firmware.

All of the wireless hardware manufacturers are in an arms race of sorts. They sell product when they have new features, the device is smaller, runs on less power, has greater range, etc. Your 6300 and my 7260 work perfectly well in 99% of all cases. However, they will never be the focus of development by Intel unless a bug or flaw is discovered. I would think that if none has emerged after all these years, there is none.> if you know, I am very curious why this problem showed up in 18.04 and not 17.10.I do not.> Pace Pic Model 5268ACProbably set to the default (read: dumbed down) WPA and WPA2 mixed mode, AES and TKIP mixed mode and auto channel select. All of these are stumbling points for Linux drivers. Here is an interesting thread: [https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection](https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection)>  Not all clients are great at honoring channel switch announcements from the AP, so an AP that changes channels on the fly risks having clients fall off the network every time it does so.Sound familiar??

---

### Post by jgwphd on 2018-06-03
Thanks for the information, I will play with my router settings when I get back in a few days. The router is set to defaults unless AT&T changed something when they did the install. Are you suggesting I turn off mixed mode and auto channel select? I can try that, but I worry about changing router settings since I might effect one or more of the twenty or so other WiFi connected devices in my house that currently work fine. 

I'd like to see if I can change something in the Dell Latitude first to get it to work at home (I know it works on the road). In that regard, I was wondering about the first error message regarding power management "[   17.709630] iwlwifi 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control". Could that have triggered this situation (I am thinking this simply because it is the first error message, and Active State Power Management enablement can be configured by BIOS or by an OS). It appears this ASPM message is coming from the driver. Is that correct?  Is the Intel WiFi driver asking something of ASPM? ....see the bug report at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1666651](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1666651) which states "This is just a warning to report that a power management operation  requested by a driver cannot be performed due to the firmware on the  machine. Unless you are seeing problems you believe are associated with  this message, it is perfectly safe to ignore it."). Since I am "seeing problems" and this machine worked with 17.10 maybe through some convoluted path this is the root cause of WiFi authentication loop. I am thinking I should start by going into Bios and change the ASPM setting and see what happens. 

ALSO, one more piece of information which I didn't think was useful prior to this discussion, but now maybe it is. I noticed when I turn on the WiFi adapter with the slide switch on the side of the Dell Latitude the WiFi light near the keyboard goes on briefly and then flickers and then goes out. Also, every time I select a network to connect it does the same thing!  ...and after 90 seconds always returns to the authentication message. Is the WiFi adapter being inadvertently turned off (maybe due to auto channel select changing the channel) and ASPM is involved somehow? Your thoughts?

---

### Post by chili555 on 2018-06-03
> The router is set to defaults unless AT&T changed something when they did the install. Are you suggesting I turn off mixed mode and auto channel select? I can try that, but I worry about changing router settings since I might effect one or more of the twenty or so other WiFi connected devices in my house that currently work fine. Yes, I recommend it. Period. Full stop. In full disclosure, I not only have an Intel wireless device but I also have AT&T and one of their Uverse 5268AC monsters!

I recommended it already in post #4 and I still think it's advisable. As for other devices on the network, unless Grandpa has brought over his twenty year old Gateway laptop, it is probable that every device does WPA2-AES and, of course, nobody will be troubled by a fixed channel. Even my first generation iPad does WPA2-AES! It is simple to experiment; make a few notes as you make the recommended changes and you can easily revert them if needed.>  iwlwifi 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM controlFrankly, that has no bearing whatever on your issue. I have seen, and you can verify with Google, this same message from the driver iwlwifi for ten or more years on perfectly operating Intel wireless and, for that matter, many other drivers! I doubt that it has any effect whatever here except that it puts a message in the logs for all of us to worry about.

I can suggest a few things that we can try that may *or may not* help a connection to a poorly configured router, but why? I think you can have this fixed in five minutes.

---

### Post by jgwphd on 2018-06-04
Thanks for your assistance. I will be back home Wednesday or Thursday and make the changes to the router once I figure out what setting or settings to change. I haven't been into this router yet (I haven't had the need till now). I hate to ask for any more of your generous assistance but do you have any suggestions on where and what setting to start with  ...otherwise I'll hunt around and see what I can find. I am very cautious because I am nervous that I'll cause other problems. Again Many Thanks!

---

### Post by chili555 on 2018-06-04
The wifi channel default is auto, reset to 1, 6 or 11, whichever has the least other access points. Check from the terminal: 

```
nmcli dev wifi list
```Here is a sample from my machine:
```
IN-USE  SSID                   MODE   CHAN  RATE        SIGNAL  BARS  SECURITY  
        GBR1                   Infra  6     195 Mbit/s  90      &#9602;&#9604;&#9606;&#9608;  WPA2      
*       GBR5                   Infra  149   405 Mbit/s  75      &#9602;&#9604;&#9606;_  WPA2      
        nx2.4                  Infra  1     195 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA1 WPA2 
        --                     Infra  6     130 Mbit/s  50      &#9602;&#9604;__  WPA2      
        MC1                    Infra  11    130 Mbit/s  50      &#9602;&#9604;__  WPA2      
        MC5                    Infra  153   405 Mbit/s  45      &#9602;&#9604;__  WPA2      
        DIRECT-X7-FireTV_69ab  Infra  153   130 Mbit/s  15      &#9602;___  WPA2  

```
As you can see from my example, the only access point on channel 11 is somewhat far away, therefore, I’d pick 11.

Channel Bandwidth: 20 MHz 

Authentication type: set to WPA2-PSK (AES) only. *NOT* mixed (up) mode WPA/WPA2-TKIP/AES catch me if you can.

Despite AT&Ts suggestion otherwise, I’d set the name of the SSID to different names in the 2.4 GHz segment from the 5 GHz segment. I suggest something like jgwphd2.4 and jgwphd5. This will prevent the wireless endlessly hopping from one segment to the other always looking for a better connection, much like my ex-girlfriend.

Make all the above changes to the 5 GHz segment except that the channel bandwidth is fine at the default.

After making these changes, power-cycle the router. 

Test both the 2.4- and 5 GHz segments to see which gives the most stable connection and stick to it.

---

### Post by jgwphd on 2018-06-07
I changed the router configuration from "Auto" to channel 1 at 2.4Gz and set to channel 136 at 5Gz. I then had to recycle power on the router for the two changes to take effect and it worked!. That's the only change I made. The authentication type was already set at WPA2-PSK (AES) so I didn't need to change that. I decided to leave the SSID the same (what AT&T had originally set ...I guess their default) since everything in the house works  ...so far.... :-)   I greatly appreciate your assistance. Again, many thanks!!!!

The only thing I am curious about. Is why 17.10 worked fine and going to 18.04 didn't. Nothing else changed! ...BTW, some additional background, a few days ago I was trying to get more of a diagnosis of the problem and I re-tried a reinstall of 18.04 using the CD/DVD with only WiFi and it wouldn't connect as well and went into the authorization loop during that attempted install. So at that time I stopped it and did it with Ethernet. It sure seems the problem existed with the initial 18.04 but not with 17.10 which had all the latest updates (using software updater). Somehow I feel there was a change somewhere between 17.10 and 18.04 that lead to the discovery of this problem. That's the only mystery I have about this. I'll close this problem as solved in few days ....in case someone wants to comment. 

Also, do you know how I can change the Ubuntu forum thread title to something that represents the actual problem instead of "Terminal commands to reset the WiFi...." so if anyone else has this problem they can easily discover this thread and try my fix. Again, my sincerest appreciation for your assistance!

---

### Post by chili555 on 2018-06-07
>  why 17.10 worked fine and going to 18.04 didn'tI haven't any idea.> do you know how I can change the Ubuntu forum thread title I assume that, somewhere at the top, possibly thread tools, one can edit the original post. I really don't know as I very seldom ask here; I answer.>  and it worked!.Awesome! Glad it's working.

If, at some later time, you find that your wireless randomly drops and reconnects, check to see what frequency it is connected at:```
iwconfig
``````
wlp3s0    IEEE 802.11  ESSID:"GBR5"  
          Mode:Managed  [COLOR="#FF0000"]Frequency:5.745 GHz [/COLOR] Access Point: xx:2B:B0:DC:45:xx
          Bit Rate=866.7 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=64/70  Signal level=-46 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:445   Missed beacon:0


```If you find that it has roamed from channel 1 to channel 136, then please reconsider renaming the SSIDs.

---

### Post by jgwphd on 2018-06-08
Many thanks for diagnosing my problem, the fix, the command reference and your advice about the SSID. I'll probably change the SSIDs as soon as I see any strange behavior. I really appreciate your assistance!  Best Regards!

---

