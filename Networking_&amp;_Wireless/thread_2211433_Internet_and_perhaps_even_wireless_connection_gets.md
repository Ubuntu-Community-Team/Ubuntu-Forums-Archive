---
title: "Internet and perhaps even wireless connection gets disconnected intermittently"
date: 2014-03-16
forum: Networking &amp; Wireless
---

### Post by prathamesh2 on 2014-03-16
I am new to Ubuntu and this forum. So, pardon me for my half baked knowledge.

I bought a Dell 3537 - preloaded with ubunbtu. After, upgrading to the latest updates, my wifi stopped working. I found [https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.9-rc4/](https://www.kernel.org/pub/linux/kernel/projects/backports/stable/v3.9-rc4/) and installed the driver. But, I observe the following:

Internet works absolutely fine for few minutes and then gets disconnected for few seconds. This keeps happening. I am pretty sure that connection to the wifi also is disconnected, but that isn't reflected in my network manager. My other laptop which runs Windows 7 doesn't have any issues connecting to the same network

I have tried to gather some information, which might help to solve my problem. Any help is appreciated.
 
Thank you.

PK

**uname -a**
```
Linux PK-LAPTOP-UBUNTU 3.5.0-47-generic #71~precise1-Ubuntu SMP Wed Feb 19 22:02:52 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
```

**lsb_release -a**
```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.4 LTS
Release:    12.04
Codename:    precise
```

**sudo lshw -C network**
  ```
*-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 07
       serial: 74:86:7a:50:53:60
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 latency=0 multicast=yes
       resources: irq:60 ioport:4000(size=256) memory:c0700000-c0700fff memory:c0400000-c0403fff
  *-network
       description: Wireless interface
       product: QCA9565 / AR9565 Wireless Network Adapter
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 80:56:f2:94:40:b3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.5.0-47-generic firmware=N/A ip=192.168.1.2 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:c0600000-c067ffff memory:9fb00000-9fb0ffff
```

**iwconfig wlan0**
***WHEN CONNECTED:***
```
wlan0     IEEE 802.11bgn  ESSID:"tata"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 28:28:5D:35:E9:2C   
          Bit Rate=2 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:61  Invalid misc:1   Missed beacon:0
```

***WHEN DISCONNECTED:***
```
wlan0     IEEE 802.11bgn  ESSID:"tata"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 28:28:5D:35:E9:2C   
          Bit Rate=121.5 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-27 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by varunendra on 2014-03-16
Welcome to the forums Prathamesh!

Please use code tags for posting command outputs. Follow the "Using Code Tags" link in my signature to see how. You should edit your post above to do that now.

For the wifi, please try this -
```
sudo iwconfig wlan0 power off
```
If that doesn't help, try creating a conf file to load the driver with a parameter -
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
```
Either reboot after this or manually reload the driver with -
```
sudo modprobe -rv ath9k
sudo modprobe -v ath9k
```

If these don't help, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by prathamesh2 on 2014-03-16
```
sudo iwconfig wlan0 power off
```

didn't work for me.

I am sorry, but I don't understand what do you mean by - 

> [COLOR=#000000]If that doesn't help, try creating a conf file to load the driver with a parameter -[/COLOR]
[COLOR=#000000]Code:
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf[/COLOR]


Where do you want me to create a file? What should be the name of the file? If the content of the file has an echo in it, won't it just print what follows it?
As I had mentioned earlier, I am new to ubuntu, so some of my question might be really stupid.

Also, I have gone a step further and ran your script and following is the output - [http://pastebin.ubuntu.com/7101870/](http://pastebin.ubuntu.com/7101870/)

Thank you.
PK

---

### Post by BlinkinCat on 2014-03-16
> **prathamesh2 said:**
> ```
sudo iwconfig wlan0 power off
```

didn't work for me.

I am sorry, but I don't understand what do you mean by - 



Where do you want me to create a file? What should be the name of the file? If the content of the file has an echo in it, won't it just print what follows it?
As I had mentioned earlier, I am new to ubuntu, so some of my question might be really stupid.

Thank you.
PK

Hi,

Varunendra also asked you to follow the Link to the "Wireless Script" in his signature if you had any trouble with his instructions.

You will find that is quite straight-forward.

Good luck - :p

---

### Post by prathamesh2 on 2014-03-16
I have already ran the script - please see my reply again.
Here is the output of the script - 
[URL="http://pastebin.ubuntu.com/7101870/"]
http://pastebin.ubuntu.com/7101870/[/URL]

---

### Post by prathamesh2 on 2014-03-17
Hi [COLOR=#000000]Varunendra,
[/COLOR]
I finally understood what you saying about creating ath9k.conf and loading the driver. I did that but to no avail. :(
I have ran your script and the output is at - [http://pastebin.ubuntu.com/7101870/](http://pastebin.ubuntu.com/7101870/)

Please help me with this issue.

Thanks,
PK


> **prathamesh2 said:**
> ```
sudo iwconfig wlan0 power off
```

didn't work for me.

I am sorry, but I don't understand what do you mean by - 


Where do you want me to create a file? What should be the name of the file? If the content of the file has an echo in it, won't it just print what follows it?
As I had mentioned earlier, I am new to ubuntu, so some of my question might be really stupid.

Also, I have gone a step further and ran your script and following is the output - [http://pastebin.ubuntu.com/7101870/](http://pastebin.ubuntu.com/7101870/)

Thank you.
PK

---

### Post by varunendra on 2014-03-17
Hi Prathamesh !

From your user name I'm assuming you are an Indian. If so, then first of all I'd like to wish you a very [SIZE=3]**[FONT=Comic Sans MS][COLOR="#800080"]Happy [/COLOR][COLOR="#FF0000"]H[/COLOR][COLOR="#008000"]o[/COLOR][COLOR="#0000CD"]l[/COLOR][COLOR="#B22222"]i[/COLOR] [COLOR="#FF8C00"]![/COLOR][/FONT]**[/SIZE] :D

That's also the reason why it took me so long to reply. I slept most of the day today after having fun in the morning, and now am replying posts after midnight (it's 2:15 am now).

Okay, onto the problem.

I hope you used the command **echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k** to create the file. That command automatically creates the required file and puts the required line in it.

However, one of your routers/access-points seems to be using WPA/WPA2 mixed mode and the other one WPA with TKIP. Both are highly discouraged. Another thing that looks problematic to me is that one of your access-points is using channel "**[COLOR="#FF0000"]12[/COLOR]**", while your current settings seem to allow only **channels 1 to 11**. Accordingly, please make following changes in the routers/access-points -

[indent]**1)** Set the encryption type in both routers to pure WPA2-AES (CCMP). No mixed mode, no TKIP (WPA (1) needs TKIP, so avoid that too).
**2)** Change the channels to 1 or 11. They usually offer better signal quality.[/indent]

After making any changes in the router, Save it > Reboot the router.

**Additional potential problems :**

Does your /etc/modules file really contain "lp" and "rtc" twice? That's not a problem, but may be confusing. However, the existence of "b43" in it **IS** a problem.

Please open the file with root privilege (by using command "**gksu gedit /etc/modules**"), and remove "b43" from it (also remove the 2nd pair of "lp" and "rtc" if they are written twice).

Lastly, are you located in Canada? Because the driver seems to be picking up the same regulatory domain settings as per dmesg part. We may have to force the same settings as your router supports.

Please try these for now and let me know how it goes. Sometimes you may not connect to wireless if a cable connection is working, so keep the Ethernet disconnected while trying to connect to wireless. I don't think we need a newer driver, but that is an option too if correcting/optimizing the local settings doesn't help.

---

### Post by prathamesh2 on 2014-03-18
Hi [COLOR=#000000]Varunendra

Thanks for all your help and time you are spending to solve my problem. Thank you for Holi wishes. Hope you had a great time celebrating holi. I reside in India.
I have changed router settings and I have removed double occurence of lp and rtc in the /etc/modules file. Also, b43 has been removed. Still the problem exists [/COLOR]:([COLOR=#000000]
My router setting now look like those in the image:
[/COLOR][IMG]http://s21.postimg.org/52d7ihj7r/wlan.png[/IMG][COLOR=#000000]
[/COLOR]&#8203;[COLOR=#000000]
[/COLOR]

---

### Post by varunendra on 2014-03-18
The router settings look good to me now, although you may try disabling "QoS" for a test. Of course reboot the router after saving the change as always recommended.

I had a discussion with my seniors here on the forum about these parts from your report -
```
[24332.879842] ath: regdomain 0x807c updated by CountryIE
[24332.879845] ath: EEPROM regdomain: 0x807c
[24332.879847] ath: EEPROM indicates we should expect a country code
[24332.879850] ath: doing EEPROM country->regdmn map search
[24332.879853] ath: country maps to regdmn code: 0x3a
[24332.879856] ath: Country alpha2 being used: CA
[24332.879858] ath: Regpair used: 0x3a
```
..and from the very clear explanation I got, I think this is what may be happening here -

It seems your wireless card was originally manufactured for Canada, and it is therefore telling the driver to use the same regulatory domain settings (CA). However, assuming that your router was manufactured for India and uses the same regdomain settings (IN), it is advertising that setting. Due to this discrepancy between the card and router settings, the driver is defaulting the settings to "00", which the router may not like much.

As such, I think we should try forcing the setting for "IN" (India) on the driver so that the link is consistent with the router settings. Please run the following command to do this -
```
sudo iw reg set IN
```

Then check -
```
iw reg get
```
It should show "country **IN**" and related settings. Does the connection become any better with this? Try the same thing with and without "QoS" enabled in the router.

If the behaviour is still the same, please try disabling "N" channel in the router (set it to b/g only mode) if the router provides an option to change the mode.

If still no go, please post a fresh wireless-info report with the above settings applied (in router, "QoS" and "N" channel disabled, in Ubuntu, regdomain "IN" applied).

---

### Post by prathamesh2 on 2014-03-18
Hi Varun,

By, now you must have figured out that I have two wireless routers (with wireless PK_HOME and PK_HOME_TATA) and my connection to either of them behaved in the same manner as described in my original post.
Now this is something that will be difficult for you to believe, but connection to one of my router is now working fine. An hour back I just logged in and found that my laptop was able to connect to one of them without any intermittent disconnects to one of the router (PK_HOME_TATA).
I then read your post and still went ahead with suggested changes in both routers viz. disabled the QoS, changed the type to b + g.
Also, I changed the regdomain to "IN" in both routers
iw reg get
```
country IN:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5735 - 5835 @ 40), (N/A, 20)
```


I see the same behavior that it is connecting to one of the router without disconnection (PK_HOME_TATA), while the connection to the other router is intermittent. Trust me on this, but I have seen this behavior before and both will exhibit disconnections after an hour or tomorrow.


Here is the latest output of the wireless script - 
[http://pastebin.ubuntu.com/7115935/](http://pastebin.ubuntu.com/7115935/)

---------------------------------------------------------------------------------
Update this morning - 19th March 2104
As mentioned above, although not sure why, but connection to one of my router (PK_HOME_TATA) was working fine. It was still the same with only intermittent connection to my other router (PK_HOME). Just to try something, I changed the channel on this router to 11 (I had changed it from AUTO to 1 yesterday) and it started working. Now, I have tested this for more than 90 minutes and things look good. At the end of this post, you will find screenshot of my router settings

I am not sure what fixed what, but what I am worried about is that, things might go wrong after some time , like a kernel update or this problem will occur even now if I try connecting to some external wifi network like at the airport/coffee shop.

Thank you for your help,
PK

[IMG]http://s3.postimg.org/xg9tdk7v7/mtnl.png[/IMG]

---

### Post by varunendra on 2014-03-19
> **prathamesh2 said:**
> I am not sure what fixed what, but what I am worried about is that, things might go wrong after some time , like a kernel update or this problem will occur even now if I try connecting to some external wifi network like at the airport/coffee shop.
You may choose to be happy and celebrate that it is working now, or choose to be worried that it *may* break again. I know 90 minutes is too soon to celebrate, but if it stays that way for a reasonably long time, I think it would be a good idea to pick up the former approach, because the latter one can go lifelong. :D

Anyway, there is that "**WMM**" thing in the router that has been reported to be problematic *sometimes*. So if the problem returns (I hope not), you should try disabling it and see if it helps. Usually it is related to QoS, so you may also try changing the 'QoS' state in the router (sometimes it helps, sometimes causes troubles - depends on its implementation).

Lastly, we haven't tried our last option yet - trying a backported driver, from kernels 3.12 or 3.13. Not that it is guaranteed to make things better, but is easy to try, *should be* easy to revert if needed.

---

### Post by prathamesh2 on 2014-03-19
Hi Varun,

A few minutes back the problem did occur with the same router. I switched to the working router and after sometime tried connecting to the problematic router again. And it has been working fine for past 30 minutes. I am not sure how to disable **WWM** thingy in this problematic router. I have disabled the QoS (Plz see the image below).
I will wait for sometime and see how things go, rather than [COLOR=#000000]trying a backported driver, from kernels 3.12 or 3.13 (Although, I don't know how to do it). Let me know if you think otherwise.

Thanks for all your help,
PK

[/COLOR][IMG]http://s27.postimg.org/n1kbafijn/Qos.png[/IMG]

---

### Post by varunendra on 2014-03-19
> **prathamesh2 said:**
> ..I am not sure how to disable **WWM** thingy in this problematic router..

It was in your previous screen (Interface Setup), right above the "SSID" field.

---

### Post by prathamesh2 on 2014-03-22
Hi Varun,

I waited for a while before posting this. But, after disabling WMM, looks like  my connection problem with even the other router is solved or it hasn't reoccured after doing that change.

Really appreciate all your help,
Thank you,
Prathamesh

---

### Post by varunendra on 2014-03-22
Try stressing the link with torrent downloads, intensive browsing etc., in short, do all you can to break the connection and see if our joy is persistent.

If this really proves to have helped the stability, then you just gave me another point to suggest frequently to others. Please mark the thread as **[SOLVED]** in that case. :)

However, if it breaks, I think you should try one of the latest versions of the driver as suggested in this post : [http://ubuntuforums.org/showpost.php?p=12963298](http://ubuntuforums.org/showpost.php?p=12963298)

I'm still not sure, but problems with ath9k probably started with kernel 3.5, instead of 3.8 as I earlier thought. If I'm thinking correctly this time, the latest one should work much better. But of course no need to try that if the current one is working nicely again. :)

---

### Post by prathamesh2 on 2014-03-29
Hi Varun,

Sorry for taking this long to reply, but it was intentional as I wanted to test how things go. Disabling WMM didn't solve my issue as it reoccurred. I finally went and downloaded backports-3.13.2-1 as you had suggested in this post - [http://ubuntuforums.org/showpost.php?p=12963298](http://ubuntuforums.org/showpost.php?p=12963298)
Now, everything has worked without any issue for a week and I can safely say that my issue has been resolved. I am marking this thread as SOLVED.

Thanks again for all your help,
PK

---

### Post by varunendra on 2014-03-29
Great job Prathamesh, and great feedback! Thanks! :)

---

