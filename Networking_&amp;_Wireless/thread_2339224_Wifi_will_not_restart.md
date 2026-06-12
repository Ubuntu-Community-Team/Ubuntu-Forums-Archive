---
title: "Wifi will not restart"
date: 2016-10-06
forum: Networking &amp; Wireless
---

### Post by poisonfor3 on 2016-10-06
I am thinking this is a problem do to the fact that the drivers for my wifi are just not quite right. I may have to live with this problem.
First the setup I have a Toshiba Satellite P875-S7310

Link to it here:
[https://www.amazon.com/dp/B00BQKW45M/ref=wl_it_dp_o_pC_nS_ttl?_encoding=UTF8&colid=1FOR0Z0H3K9JK&coliid=IS2DHKH9UXT0B](https://www.amazon.com/dp/B00BQKW45M/ref=wl_it_dp_o_pC_nS_ttl?_encoding=UTF8&colid=1FOR0Z0H3K9JK&coliid=IS2DHKH9UXT0B)

I put 16.04.1 LTS (Xenial Xerus) with Mate 1.12.1 on it. Wifi works just like it should after powering up BUT if for any reason the wifi is signal is dropped (the signal only, so if internet is down but the signal is still up and running NO PROBLEMS at all) none of the wifi networks will show up anymore. This is been a long long bug I have been trying to fix so I can not get into all the dead ends here it would be a small book. :P  I tried using different network managers like wifi radar and wicd but dead end there. 

You can get the same result if you put "ifconfig wlp2s0 down" into the command line. (the "wlp2s0" being different on some computers)

So here is an example of the problem. Everything normal then router goes down for a bit but then I can no longer see any wifi signals at all. I would think that just putting in "ifconfig wlp2s0 up" into the terminal should restore the display of the wifi signals but NOPE. Now when this happens if I run different network managers like wifi radar and wicd I can see the wifi signals and I can even hook up to them kinda . . . it shows that I am hooked up and when I run the "system monitor" program I can see internet traffic (like pings or something) but I can not run anything that hooks up to the internet like firefox, bluemoon, Konqueror, thunderbird, podcast down-loaders etc. Well I can run them they just can not see the internet. It also happens a LOT in fact about 90% of the time It will happen when I try to switch to a different wifi network.

The only way to get internet back is to restart the computer and that can be a real pain in the butt when I have certain projects going on. 

Problem solved would be ideal but I would be happy if I can have even a work around. The work around I am thinking of is to just restart the "stock" wifi network manager (I am sure it has a name I just have no idea what it is) I tried to just do a command line of "ifconfig wlp2s0 down" then "ifconfig wlp2s0 up" but that is not shutting down the whole wifi network manager just the connections and does nothing to being it back up after it fails. If there is a command line to where I can shut down the WHOLE wifi network manager and then start it back up again I think that would work as a good work around to the problem. 

I am just lost when it comes to command lines. 

Thanks for your time reading this long mess :)

---

### Post by howefield on 2016-10-06
Thread moved to the "*Networking & Wireless*" forum, probably a better fit.

---

### Post by poisonfor3 on 2016-10-07
@howefield 

Yea, the "*Networking & Wireless*" forum is a much better fit as long as people know that I am super new to Command Lines and Networking. It may sound like I kinda know what I am doing but only because I have like 30 working hours trying to fix this. Including TONS of time on this site looking. I seem to be the only person with this exact problem. I am sure I am not but seems like it. That is one of the main reason I think it has to do with the way the drivers are hooking up to the network card. I have had problems with other Linux OS not hooking up to the network card at all. For a long time when I was trying to run a MORE "open source" OS like Trisquel (and 4 other OS where the same) I would have to hook up an external wifi card to get it to work. Ubuntu and Mint seemed like the only 2 that the wifi worked out of the box. AND for no real reason I just do not like Mint. (Most likely that god awful pea green color they use on their website; orange color is so much better LOL) Drivers being the problem would also explain why wifi radar and wicd WILL hook up to the wifi but my programs within the OS DO NOT have internet access. Yet something is hooking up (to at least the router) with them because I have a small flow of traffic. BUT the driver being the problem is just a guess I do not have the computer skills to be able to track down the real problem for sure. That plus the fact that I want to upgrade to a more open source laptop (with Linux native to them) when I have the money, is why I would be very happy to have that workaround I talked about above...

Like I said there has to be Line Commands that will let me turn off the whole (wifi) Network Card driver (program) and boot it back up without having to shut down my computer and loose my place on projects I was working on.

Thanks in advance for any help.
-Annie

---

### Post by Bucky Ball on 2016-10-07
This will be simple enough. Open a terminal and copy/paste this in. You can use control+shift+v to paste it to a terminal or copy it as normal from here then Edit> Paste in the terminal.

```
sudo lshw -C network
```

You will be asked for your password. Type it in. It will be invisible. This is normal. Hit return. Copy the output from that command to a post here. Have a look at the green link in first line of my signature for how to put it between code tags so it's neater and easier to read.

Just to confirm: this is the internal wifi you are trying to fix, not a USB wireless dongle?

---

### Post by poisonfor3 on 2016-10-08
@[[COLOR=#C61919]**Bucky Ball**[/COLOR]]("https://ubuntuforums.org/member.php?u=504316")


OK I put this into terminal

```
sudo lshw -C network
```

and got this:

 ```
 *-network               
       description: Ethernet interface
       product: AR8162 Fast Ethernet
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: enp1s0
       version: 10
       serial: 00:26:6c:2e:df:27
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=alx latency=0 link=no multicast=yes port=twisted pair
       resources: irq:30 memory:c8600000-c863ffff ioport:2000(size=128)
  *-network
       description: Wireless interface
       product: Centrino Wireless-N 2200
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlp2s0
       version: c4
       serial: 9c:4e:36:62:52:9c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=4.4.0-38-generic firmware=18.168.6.1 ip=192.168.1.100 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:28 memory:c8500000-c8501fff
```


Yes, we are talking about the internal wifi the reason I even mentioned the external one is to help explain the "clues" to the underline problem I was having. I do not use the external (USB) wifi at all with Ubuntu because it is not needed. 

So you know of an easier way to get my wifi back up without shutting down my computer. (at this point not having it go down at all is just a dream LOL)

Thanks
Annie

---

### Post by kurt18947 on 2016-10-08
Have you tried this?
```
sudo service networking restart
```

You will need to do this from an account with sudo privileges. I use this occasionally when wifi doesn't wake up properly from suspend. I'm not sure if it will help in your case. There is a way to run this command without sudo privileges but I'm not sure what's involved there.

---

### Post by poisonfor3 on 2016-10-08
@[**[COLOR=#000000]kurt18947[/COLOR]**]("https://ubuntuforums.org/member.php?u=1447222")

Well something like that is what I am looking for yet did not work. Strange thing is that I never have your problem. When it wakes up from suspend it always works for me. Only when I change networks or when ever I loose the network wifi that I am on. The way I test it is I shut down my wifi router keeping the modem on since shutting it down is not needed for test. AS soon as I shut down the wifi router I loose the ability to "see" any networks. In other words I was able to see the wifi from next door before I shut down my wifi but after I shut down my wifi I can not "See" any networks at all. Strange bug. Like I said, feels like I am the only one with this exact problem. Yet I think you where on the right track with a "restart" command. 

Side note: Funny after I did my little test, I know I am not hooked up to wifi. Yet I still wrote out my post here. Then dawned on me I was offline and had to cut and past my post onto a notepad, save it. Restart system and copy and past it back here. People say working with Linux is a pain but I have had just as many problems doing things or trying to do things in windows OS; maybe because I do more with computers than watch funny cat videos and serf facebook.  8-)

---

### Post by kurt18947 on 2016-10-08
> **poisonfor3 said:**
> @[**[COLOR=#000000]kurt18947[/COLOR]**]("https://ubuntuforums.org/member.php?u=1447222")

Well something like that is what I am looking for yet did not work. Strange thing is that I never have your problem. When it wakes up from suspend it always works for me. Only when I change networks or when ever I loose the network wifi that I am on. The way I test it is I shut down my wifi router keeping the modem on since shutting it down is not needed for test. AS soon as I shut down the wifi router I loose the ability to "see" any networks. In other words I was able to see the wifi from next door before I shut down my wifi but after I shut down my wifi I can not "See" any networks at all. Strange bug. Like I said, feels like I am the only one with this exact problem. Yet I think you where on the right track with a "restart" command. 
..........................................................


I've seen behavior like you are mentioning when changing an SSID or Wifi password, making some change to a router. I can see neighbors' wifi but not my own. A full shutdown and restart of the subject PC fixes it. I only see it when making changes to the wifi router and don't do that often so haven't really thought about it. A more frequent occurrence but no common is to have the laptop PC's wifi not connect after waking from suspend. Restarting Network-Manager fixes that but it only happens perhaps once a month.

---

### Post by poisonfor3 on 2016-10-08
It has nothing to do with the router. I can be at a coffee shop and change to my personal hotspot or any place when I change to another wifi connection. Or like I said if the wifi signal goes down for any reason. In other words same thing if I am using my hot-spot (I have both t-mobile and Verizon both do the same thing) if I turn off my hotspot or try to change away from the one I am hooked up to it will loose all ability to be able to connect to anything via wifi. Exactly as if you put in the
```
ifconfig wlp2s0 down
```

command into the terminal. Exactly like it ! ! 

BUT for one thing, you can not input 

```
ifconfig wlp2s0 up
```

into the terminal to get it back up.

---

### Post by kurt18947 on 2016-10-09
I don't have your situation, I've only ever used single wifi connections away from home. I hope you're able to deciper what's going on.

---

### Post by Hadaka on 2016-10-09
Hi, please open a terminal ctrl/alt/t then Copy and paste the following command.
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
This command writes a file to your home directory.The file name is **wireless-info.txt**
From your directory please copy,paste and post the **wireless-info.txt**
thanks.

---

### Post by poisonfor3 on 2016-10-11
Like I said I have not even heard of it before. Does anyone else have an idea of a Command in Terminal that will restart the wifi card driver?

---

### Post by Bucky Ball on 2016-10-11
Please read Hadaka's post #11, follow those instructions, please.

You were previously given the command to restart networking.

```
sudo service networking restart
```

You claim it did not work. Try this:

```
sudo service network-manager restart
```

Either way, please post the wirelessinfo output for further support. We can't give you much if you don't give info requested. Thanks.

---

### Post by poisonfor3 on 2016-10-11
@Bucky Ball 

I retried the 1st command:

```
sudo service networking restart

```

Still nothing. BUT the 2nd command:

```
sudo service network-manager restart
```

Did it ! ! !

I truly felt there had to be a simple way to do that. Countless hours to fix it. Albeit just a workaround it will save so much time and effort. \\:D/ Thank you very much.

-Annabella

---

### Post by jeremy31 on 2016-10-11
There may be another workaround in store for you.  I would like you to check results for ```
iwconfig
```
Before and after you have problems, look at the Power Management setting and let us know if it changed from off to on

---

### Post by poisonfor3 on 2016-10-11
@jeremy31

OK with the internet up and running I get this:

```
root@big-bot:/home/miss# iwconfig
lo        no wireless extensions.

enp1s0    no wireless extensions.

wlp2s0    IEEE 802.11bgn  ESSID:"Wolf Network"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: F8:1A:67:3E:EF:02   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=70/70  Signal level=-34 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:52   Missed beacon:0

root@big-bot:/home/miss# 


```

I turn off the wifi router and wait for a sec. The wifi icon goes dim showing i am not connected and then re-enter it and I get This:

```
root@big-bot:/home/miss# iwconfig
lo        no wireless extensions.

enp1s0    no wireless extensions.

wlp2s0    IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          
root@big-bot:
```

Looks like "Power Management" is on. Does the "ESSID:off/any" mean it turned of the wifi antenna like the "ifconfig wlp2s0 down" command does? 

Like I said I get the same problem when I try to change wifi here is what happened when I restarted it and then tried to switch to another wifi (t-mobile ) and back to wolf network.

```
root@big-bot:/home/miss# sudo service network-manager restart
root@big-bot:/home/miss# iwconfig
lo        no wireless extensions.

enp1s0    no wireless extensions.

wlp2s0    IEEE 802.11bgn  ESSID:"T-Mobile Broadband97"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 3C:DA:2A:33:65:7A   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=70/70  Signal level=-30 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:49   Missed beacon:0

root@big-bot:/home/miss# iwconfig
lo        no wireless extensions.

enp1s0    no wireless extensions.

wlp2s0    IEEE 802.11bgn  ESSID:"Wolf Network"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: F8:1A:67:3E:EF:02   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=70/70  Signal level=-33 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:42   Missed beacon:0

root@big-bot:/home/miss# iwconfig
lo        no wireless extensions.

enp1s0    no wireless extensions.

wlp2s0    IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          
root@big-bot:
```

Here is what happens when I do the "ifconfig wlp2s0 down"command. As you can see took a bit to get it back up but at least i did not have to do a restart.

```
root@big-bot:/home/miss# ifconfig wlp2s0 down
root@big-bot:/home/miss# iwconfig
lo        no wireless extensions.

enp1s0    no wireless extensions.

wlp2s0    IEEE 802.11bgn  ESSID:"Wolf Network"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: F8:1A:67:3E:EF:02   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=70/70  Signal level=-32 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:16   Missed beacon:0

root@big-bot:/home/miss# iwconfig
lo        no wireless extensions.

enp1s0    no wireless extensions.

wlp2s0    IEEE 802.11bgn  ESSID:"Wolf Network"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: F8:1A:67:3E:EF:02   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=70/70  Signal level=-32 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:17   Missed beacon:0

root@big-bot:/home/miss# sudo service network-manager restart
root@big-bot:/home/miss# sudo service network-manager restart
root@big-bot:/home/miss# iwconfig
lo        no wireless extensions.

enp1s0    no wireless extensions.

wlp2s0    IEEE 802.11bgn  ESSID:"Wolf Network"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          
root@big-bot:/home/miss# sudo service network-manager restart
root@big-bot:/home/miss# sudo service network-manager restart
root@big-bot:/home/miss# sudo service network-manager restart
root@big-bot:/home/miss# sudo service network-manager restart
root@big-bot:/home/miss# ifconfig wlp2s0 up
root@big-bot:/home/miss# sudo service network-manager restart
root@big-bot:/home/miss# sudo service network-manager restart
root@big-bot:/home/miss# sudo service network-manager restart
root@big-bot:/home/miss# sudo service networking restart
root@big-bot:/home/miss# sudo service network-manager restart
root@big-bot:/home/miss# sudo service network-manager restart
root@big-bot:/home/miss# sudo service networking restart
root@big-bot:/home/miss# sudo service network-manager restart
root@big-bot:/home/miss# iwconfig
lo        no wireless extensions.

enp1s0    no wireless extensions.

wlp2s0    IEEE 802.11bgn  ESSID:"Wolf Network"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: F8:1A:67:3E:EF:02   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=69/70  Signal level=-41 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:53   Missed beacon:0

root@big-bot:/home/miss# 


```

Anyways, let me know if any of that means something to you.  :)

---

