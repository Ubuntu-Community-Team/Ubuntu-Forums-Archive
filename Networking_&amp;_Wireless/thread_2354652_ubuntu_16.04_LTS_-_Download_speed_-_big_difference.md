---
title: "ubuntu 16.04 LTS - Download speed - big difference between browsers"
date: 2017-03-04
forum: Networking &amp; Wireless
---

### Post by ubu112 on 2017-03-04
I have Acer Aspire One AOA150/ZG5,with Ubuntu 16.04 LTS.I made many test with speedtest.net,wired and wireless.I noted unstability changing server,but the big difference is between Chromium and Firefox.Here same results:with **Chromium** 40+(wireless) 39 (the best,wired),with **Firefox **21 (wireless) 10 (wired).Can,please,someone help me to understand the big difference between Chromium and Firefox and if it's normal the unstability changing server.Thank you 

---

### Post by chili555 on 2017-03-10
First of all, I thought you bought an external wireless device and were pretty happy with it: [https://ubuntuforums.org/showthread.php?t=2354312&p=13614547#post13614547](https://ubuntuforums.org/showthread.php?t=2354312&p=13614547#post13614547) Is that no longer true? Why?

Second, were you able to make all the changes I suggested in my post here? [https://ubuntuforums.org/showthread.php?t=2354312&p=13614535#post13614535](https://ubuntuforums.org/showthread.php?t=2354312&p=13614535#post13614535)

Third, what is the channel congestion where you are trying to connect with wireless?```
sudo nmcli dev wifi list
```Here is a sample from my location:```
*  SSID        MODE   CHAN  RATE       SIGNAL  BARS  SECURITY  
   GBR1        Infra  6     54 Mbit/s  92      &#9602;&#9604;&#9606;&#9608;  WPA2      
*  GBR5        Infra  149   54 Mbit/s  71      &#9602;&#9604;&#9606;_  WPA2      
   nx2.4       Infra  1     54 Mbit/s  49      &#9602;&#9604;__  WPA1 WPA2 
   Portal      Infra  11    54 Mbit/s  34      &#9602;&#9604;__  WPA2      
   MAHB Wi-Fi  Infra  6     54 Mbit/s  29      &#9602;___  WPA2      
   MAHB Wi-Fi  Infra  6     54 Mbit/s  27      &#9602;___  WPA2      
   MAHB Wi-Fi  Infra  6     54 Mbit/s  27      &#9602;___  WPA2     
```Please notice that there are many stations on channel 6 here; I am on channel 149! I have no interference and congestion issues at all.

Next, you might see what the speed is from the command line: ```
wget -O speedtest-cli https://raw.githubusercontent.com/sivel/speedtest-cli/master/speedtest.py
chmod +x speedtest-cli
./speedtest-cli
```Finally, frankly, I don't really understand myself all the mechanics of Chromium vs. Firefox. Chromium works better for me, so I just use it.

---

### Post by ubu112 on 2017-03-10
First of all,thank you for your answer and sorry if I'm disturbing you.1)I'm still happy with the adapter you suggested to me.For example(with Chromium) my download speed was 21+,now is 40+.I didn't have the same improvement with Firefox,because it's the same than before and I can't explain why the wired download speed is less than the wireless speed (10).Is there something that can be done? As I asked (...547)according to your opinion,now I passed from wireless g to n,if I'd use an ac adapter on 2,4 Ghz I'd have more speed?It's true that working on 5 Ghz [COLOR=#000000]it disconnect with more distance from router,changing weather,walls or it's just for me? 2)yes,I made all the changes you suggested to me 3) In this post for "unstability" I mean when (with speedtest.net) I  test the download speed with the server A,isn't the same with the server B,it's normal?4) PLEASE,can you explain to me:"[/COLOR][COLOR=#000000]there are many stations on channel 6"?how and where can I change station?5)I tried the speed from the command line:first row gave me 1,75 MB/s x 8=19 Mbit/s (is it correct?),second row no output,third 34,74 Mbit/s and I fund in "Home" a file "speedtest-cli".Can you,please,explain to me what this mean? 6)Last,(post ....547,latest row)if you want,curiosity?Thank you very much[/COLOR]

---

### Post by chili555 on 2017-03-11
> according to your opinion,now I passed from wireless g to n,if I'd use an ac adapter on 2,4 Ghz I'd have more speed?If your router is capable of AC speeds and if the service that you are paying for and getting from your internet service provider (ISP) are greater than N speeds, usually 72 Mbps, then yes.> It's true that working on 5 Ghz it disconnect with more distance from router,changing weather,walls or it's just for me?That's quite true for us all. However, in my two-story, 300 sq. meter house, 5 gHz reaches everywhere reliably.> (with speedtest.net) I test the download speed with the server A,isn't the same with the server B,it's normalQuite normal. I suggest that you experiment a few times to find the fastest server, typically the server closest to your home, and stick with it. It doesn't do much good to compare Chromium to Firefox to wireless to ethernet to different servers and different speed test sites. It is far better to troubleshoot and try to fix any problems while holding all the variables fixed.> PLEASE,can you explain to me:"there are many stations on channel 6"?how and where can I change station?First, find the channels in use in your area from the command line:```
sudo nmcli dev wifi list
```As you saw in the example above, in my area there are four routers on channel 6. Therefor, we'd expect channel 6 to have the potential for interference and congestion. In that case, I'd recommend setting a channel other than 6. The channels with the least overlap are 1, 6 and 11. In the example I gave above, I see a single router on channel 11 that is pretty low in signal strength suggesting that it is farther away, so I'd probably try channel 11.

However, the wireless device I'm using now is capable of 5 gHz traffic. I see no other 5 gHz routers nearby, so I set my router to use a 5 gHz channel, in my case, 149. I have not guaranteed myself great speeds; I am simply trying to reduce the chance for poor speeds caused by interference.

The channel setting is in the router. Here is an example router administration page, although yours is probably different: [http://sw.nohold.net/Linksys/Images/kb4009-004_en_v7.png](http://sw.nohold.net/Linksys/Images/kb4009-004_en_v7.png)> I tried the speed from the command line:first row gave me 1,75 MB/s x 8=19 Mbit/s (is it correct?),second row no output,third 34,74 Mbit/sI'm not at all sure what you mean. Here is my result and please tell me what the corresponding numbers are in your test and, of course, tell me the test result for both wired and wireless.```
chili@T440p:~$ ./speedtest-cli
Retrieving speedtest.net configuration...
Retrieving speedtest.net server list...
Testing from AT&T Internet (xxx.140.129.xx)...
Selecting best server based on latency...
Hosted by AT&T (Charlotte, NC) [25.41 km]: 13.285 ms
Testing download speed........................................
Download: 152.23 Mbit/s
Testing upload speed..................................................
Upload: 139.23 Mbit/s

```These results are wireless.> I fund in "Home" a file "speedtest-cli".Can you,please,explain to me what this mean? That is the script that runs, you can keep it and run it again whenever you'd like to troubleshoot.

---

### Post by ubu112 on 2017-03-11
1)Yes,I have an AC router and (with Windows) it works on 5 Ghz 2)with 5 Ghz sometimes I can't reach every corner 100sq.meter and I have to go on 2,4 Ghz 3)I tried all channels and the best is 6 on 2,4 Ghz but I don't have channel 149 on 5 Ghz 4) where you have Download 152.23 Mbit/s, I have 34,74 Mbit/s(wireless) 5) I notice that with Chromium I use speedtest.net beta,because Chromium doesn't have Flash Player,would this mean something? 6) Is better to use the script than speedtest.net?always with the code:"./speedtest/cli"? 7)I insist,how can I learn something more about Linux-Ubuntu?Thank you

---

### Post by chili555 on 2017-03-11
> I notice that with Chromium I use speedtest.net beta,because Chromium doesn't have Flash Player,would this mean something?Not in and of itself. Some speedtest sites use flash, some use HTML5 and some, such as speedtest-cli, use neither. What's important is to use one or the other consistently. Let's compare it to Windows. If there is a big difference between speetest.net in Firefox in Windows vs. Ubuntu, let's try to troubleshoot why.>  where you have Download 152.23 Mbit/s, I have 34,74 Mbit/s(wireless)It actually sounds pretty reasonable to me. This suggests that your driver, ath5k, and hardware combination is not capable of 802.11N: [https://en.wikipedia.org/wiki/Comparison_of_open-source_wireless_drivers#Driver_capabilities](https://en.wikipedia.org/wiki/Comparison_of_open-source_wireless_drivers#Driver_capabilities) Therefore, assuming that you are connected at G speeds and some distance from the router, with overhead, I'd guess that 35 Mbps is reasonable. Of course, a lot depends on the speeds you pay for and receive from your ISP.

Have you tried again blacklisting ath5k and trying the USB? What is the result?> Is better to use the script than speedtest.net?always with the code:"./speedtest/cli"?I think so because it eliminates the variable of flash vs. HTML5.> I insist,how can I learn something more about Linux-Ubuntu?You are asking the wrong person in the wrong forum. Aside from the narrow subject of wireless, I know little; just enough to not wreck my system too often. You might ask here: [https://ubuntuforums.org/forumdisplay.php?f=326](https://ubuntuforums.org/forumdisplay.php?f=326) The sticky posts at the top seem very helpful.

---

### Post by ubu112 on 2017-03-11
You know little???I'd like to learn a little bit of your "little".The question is:how did you learn this "little"?1)maybe,I understand wrong,the big difference is in Ubuntu with Firefox vs Chromium2)I already blacklisted "ath5k",this doesn't mean that I blacklisted the wireless g card?and,with the adapter,I'm using wireless N?can be checked if "ath5k" is blacklisted? 3)my connection speed,from my ISP, is: D 300 Mbit/s,U 20 Mbit/s.Thank you "chili555"

---

### Post by chili555 on 2017-03-11
> You know little???I'd like to learn a little bit of your "little".The question is:how did you learn this "little"?I read a book that came with a CD of Linux Mandrake back about 16 years ago. I must have read that book ten times before I had the nerve to actually install! After I got connected to the internet, a major pain in 2001, I just Googled for solutions. I was not surprised to find that any problem I ever had was reported and usually solved by some else previously. I kept a text file of how tos and added to it frequently. Mostly, I learned from trial and error. > maybe,I understand wrong,the big difference is in Ubuntu with Firefox vs ChromiumAs I said, I don't understand it either. I assume it has to do with flash vs. HTML5. In my case, Chromium is faster and more stable and so I use it. I don't have the time or patience to take Firefox apart to see what is wrong with it. My strong suspicion is that flash is most of what's wrong with it.> I already blacklisted "ath5k",this doesn't mean that I blacklisted the wireless g card?and,with the adapter,I'm using wireless N?can be checked if "ath5k" is blacklisted?I assumed that you were again using the internal device because of what you conveyed in your Private Message: [http://www.imgur.com/swTOUBh](http://www.imgur.com/swTOUBh)

No??

What does this tell us?```
lsmod | grep ath
iw list
dmesg | grep ath
```

---

### Post by ubu112 on 2017-03-11
I just send - [http://www.imgur.com/q8GJ0eo](http://www.imgur.com/q8GJ0eo) - because the output of " iw list "is too long and I don't know how to send it.Take a look,please,because I don't understand.I tried to unplug the adapter,it disconnects itself and I can't connect without it because I don't see no connections available.This mean that the wireless g card is blacklisted? Thank you

---

### Post by chili555 on 2017-03-11
The Imgur link says, "Zoinks! You've taken a wrong turn." Please try again.

---

### Post by ubu112 on 2017-03-11
[http://i.imgur.com/q8Gj0eo.png](http://i.imgur.com/q8Gj0eo.png) - this must be the right one.Thank you

---

### Post by chili555 on 2017-03-11
Are you aware that you can copy and paste from the terminal to post your terminal outputs here? Just remember to enclose them in code blocks by highlighting them and clicking the**[SIZE=4] #[/SIZE]** button at the top of the reply box.

May I also see: ```
dmesg | grep wlx
```I will plug in my own TP Link now to try to help.

---

### Post by jeremy31 on 2017-03-11
The # is only available in advanced reply, the same can be accomplished by using [noparse]```
 and 
```[/noparse] around your terminal results

More info in the code tags link in my signature

---

### Post by ubu112 on 2017-03-11
[http://i.imgur.com/ISgaGWu.png](http://i.imgur.com/ISgaGWu.png)

---

### Post by chili555 on 2017-03-11
> **jeremy31 said:**
> The # is only available in advanced reply, the same can be accomplished by using [noparse]```
 and 
```[/noparse] around your terminal results

More info in the code tags link in my signatureIt is available in the ordinary* Reply to Thread *but not in *Quick Reply*. I assume that's what you mean.

---

### Post by chili555 on 2017-03-11
I have tweaked every setting I know of to try to coax my identical TP Link TL-WN722N to higher speeds.

First, it is an 802.11 B, G and N device with just one impressive antenna. It will, under laboratory-grade test conditions, do 72.2 Mbps. While that is quite fast, it is not likely achievable in an ordinary home or office where the device is many feet from the router and there are many other wireless devices nearby. It is also nowhere as fast as your 300 Mbps or my 1000 Mbps available.

With every tweak I can use, for the TP Link, I get:```
chili@T440p:~$ ./speedtest-cli 
Retrieving speedtest.net configuration...
Retrieving speedtest.net server list...
Testing from AT&T Internet (107.140.129.95)...
Selecting best server based on latency...
Hosted by AT&T (Charlotte, NC) [25.41 km]: 12.423 ms
Testing download speed........................................
Download: 43.42 Mbit/s
Testing upload speed..................................................
Upload: 32.52 Mbit/s

```That's probably about as good as it gets.

Using my internal device, an Intel 7260 capable of 802.11AC, I get this: [http://www.dslreports.com/speedtest/7109859](http://www.dslreports.com/speedtest/7109859)

I strongly suspect that, in order to get giant speeds, you'll need to swap out your internal wireless or get a better USB than the US$12 TP Link we both have.

Jeremy is looking in; perhaps he has other suggestions.

Do we now need to troubleshoot your ethernet?

---

### Post by ubu112 on 2017-03-11
What do you think about my imgur images?I'm working in wireless G or N?I can only change adapter,because I use notebooks.Do you know better adapters?About my ethernet,can I use speedtest from terminal?and can we improve my ethernet speed?Now I tested my download speed with the terminal and I had: 61+ (wired) and 20+ (wireless),one hour ago was 30+(wireless).More test I make less I understand.I'm 5/6 feet from my router.Thank you

---

### Post by chili555 on 2017-03-12
> What do you think about my imgur images?I'm working in wireless G or N?It is impossible to tell if you are in G or N mode. As to the Imgur images themselves, I wish, as I said before, that you instead copied and pasted the output into the reply, like this from my machine:```
chili@T440p:~$ dmesg | grep iwl
[    5.676579] iwlwifi 0000:03:00.0: loaded firmware version 17.352738.0 op_mode iwlmvm
[    5.714148] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    5.716210] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[    5.716474] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[    5.941905] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    6.043879] iwlwifi 0000:03:00.0 wlp3s0: renamed from wlan0
[    8.618760] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[    8.619023] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[    8.834355] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled
[    8.834616] iwlwifi 0000:03:00.0: L1 Enabled - LTR Enabled

```It's faster and easier for us all.> I can only change adapter,because I use notebooks.It is perfectly possible to change the card in a notebook, I have done it a few times including the machine I'm using right now. You just have to be aware of whitelisting: [http://goughlui.com/2014/08/02/laptop-wireless-card-whitelists-an-upgrade-nightmare/](http://goughlui.com/2014/08/02/laptop-wireless-card-whitelists-an-upgrade-nightmare/) Taking a screwdriver to a perfectly operating notebook is not for everyone; I understand.> About my ethernet,can I use speedtest from terminal?Certainly. Let's stay consistent.>  can we improve my ethernet speedPossibly. Let's start with some details about your ethernet. With it connected, please run and post:```
ifconfig
```This will tell you the ethernet interface, something like enp0s5 or some such. Use that for the next command:```
sudo ethtool enp0s5
```Of course, substitute the interface name you found above. 

Also, we'd like to see:```
dmesg | grep enp
lspci -nnk | grep 0200 -A2
```> More test I make less I understand.Ha ha ha! You and me both!

---

### Post by ubu112 on 2017-03-12
[FONT=arial][SIZE=4]Changing card is not for me.

[/SIZE][/FONT]```
user@user-AOA150:~$ ifconfig
enp2s0    Link encap:Ethernet  IndirizzoHW 00:1e:68:fd:8b:6b  
          indirizzo inet: Bcast:  Maschera:255.255.255.0
          indirizzo inet6: fe80::f9bc:b7f4:c5c1:9dbf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9790 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8057 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:7310991 (7.3 MB)  Byte TX:1437686 (1.4 MB)


lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1158 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1158 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1 
          Byte RX:98586 (98.5 KB)  Byte TX:98586 (98.5 KB)

```

```


user@user-AOA150:~$ sudo ethtool enp2s0
[sudo] password di user: 
Settings for enp2s0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                         100baseT/Half 100baseT/Full 
    Link partner advertised pause frame use: Symmetric Receive-only
    Link partner advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
                   drv probe ifdown ifup
    Link detected: yes
```

```
user@user-AOA150:~$ dmesg | grep enp[    3.227855] r8169 0000:02:00.0 enp2s0: renamed from eth0
[   40.571683] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   40.581339] r8169 0000:02:00.0 enp2s0: link down
[   40.581495] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[  334.770947] r8169 0000:02:00.0 enp2s0: link up
[  334.770977] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready
user@user-AOA150:~$ lspci -nnk | grep 0200 -A2
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Acer Incorporated [ALI] RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [1025:015b]
    Kernel driver in use: r8169
--
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Foxconn International, Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [105b:e008]
    Kernel modules: ath5k
```

[FONT=arial][SIZE=3]I tried but I didn't understand how to make "windows",please,explain to me how I can do.
[/SIZE][/FONT]
[FONT=arial][SIZE=3]Thank you[/SIZE][/FONT]
[FONT=arial][SIZE=4]
[/SIZE][/FONT]

---

### Post by chili555 on 2017-03-14
> I tried but I didn't understand how to make "windows",please,explain to me how I can do.I'm sorry if I misunderstood your earlier comment; I thought that you were dual-booting with Windows:> 1)Yes,I have an AC router and (with Windows) it works on 5 GhzMy hope was that, using the same computer and the same wireless or ethernet device, you could do speed tests so that we could compare them. I apologize if I misunderstood.

> Speed: 100Mb/s
Duplex: FullYour ethernet card uses the sometimes tricky driver r8169. It is telling us that it has negotiated a speed of 100 Mbps with the router and detects a link. There is always a bit of overhead with any connection, either wireless or ethernet. Please see: [https://en.wikipedia.org/wiki/Fast_Ethernet](https://en.wikipedia.org/wiki/Fast_Ethernet)> The MII fixes the theoretical maximum data bit rate for all versions of Fast Ethernet to 100 Mbit/s. The data signaling rate actually observed on real networks is less than the theoretical maximum, due to the necessary header and trailer (addressing and error-detection bits) on every frame, the occasional "lost frame" due to noise, and time waiting after each sent frame for other devices on the network to finish transmitting.With a 300 Mbps line from your internet service provider, I would expect a speed test result in the high 80s or low 90s. 

With the wireless turned off, what is your actual result?```
./speedtest-cli
```

---

### Post by ubu112 on 2017-03-14
With
> I tried but I didn't understand how to make "windows" it refers to your post 12 and then the Jeremy post 

I use Acer Aspire One just with Ubuntu 16.04 LTS and I use an Asus K73 with Windows 10.I have an AC router.

To be honest I didn't understand very well your explanation about driver "r8169" and "MII".

Now,I'm not at home and I can't make the speedtest.What do you mean 

> with wireleless turned off

I just unplug the adapter?

Later,I send you the speedtest result.Thank you

(Do you think that my editing is a little bit better?)

---

### Post by chili555 on 2017-03-14
> To be honest I didn't understand very well your explanation about driver "r8169" and "MII".r8169 is the name of your ethernet driver; mii is its dependency. > Now,I'm not at home and I can't make the speedtest.What do you mean 

[QUOTE]with wireleless turned off
I just unplug the adapter?[/QUOTE]No, all you need do is click the Network Manager icon and un-check *Enable Wi-Fi.*

[ATTACH=CONFIG]274150[/ATTACH]

> Do you think that my editing is a little bit better?Very much so! Thanks.

---

### Post by ubu112 on 2017-03-14
I just made speedtest (wired):

- with terminal : 40,66 Mbit/s

- with Chromium : 28,68 Mbit/s

- with Firefox : 9,73 Mbit/s

Always it depens from which server has been chosen

Unfortunately less than expected,what do you think about it?Is it normal?isn't it too low?why the upload 

speed is pretty stable and the download speed is so unstable?

Thank you

---

### Post by chili555 on 2017-03-15
> Unfortunately less than expected,what do you think about it?I agree; it's too slow. Please try an experiment; if it helps, we can make it permanent. From the terminal:```
sudo ethtool -s enp2s0 autoneg off
```Check to see if it sticks:```
sudo ethtool enp2s0
```We hope it says:```
<snip>
	PHYAD: 1
	Transceiver: internal
	[COLOR="#FF0000"]Auto-negotiation: off[/COLOR]
	MDI-X: on (auto)
	Supports Wake-on: pumbg
	Wake-on: g
<snip>
```If so, then:```
./speedtest-cli
```And then post the result. We hope it is a big improvement over 40.66 Mbps.

---

### Post by ubu112 on 2017-03-15
Before using your codes,I made 2 speedtest:

```
user@user-AOA150:~$ ./speedtest-cli

Retrieving speedtest.net configuration...
Testing from Vodafone 
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by Fastweb SpA  [1.15 km]: 21.452 ms
Testing download speed................................................................................
Download: 76.50 Mbit/s
Testing upload speed....................................................................................................
Upload: 19.00 Mbit/s
user@user-AOA150:~$ ./speedtest-cli

Retrieving speedtest.net configuration...
Testing from Vodafone 
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by Vodafone  [1.15 km]: 21.774 ms
Testing download speed................................................................................
Download: 33.79 Mbit/s
Testing upload speed....................................................................................................
Upload: 18.49 Mbit/s
user@user-AOA150:~$ 



```

Look the diference between these 2 speedtest!!!

After:

```
user@user-AOA150:~$ sudo ethtool -s enp2s0 autoneg off[sudo] password di user: 
user@user-AOA150:~$ sudo ethtool enp2s0
Settings for enp2s0:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  Not reported
    Advertised pause frame use: No
    Advertised auto-negotiation: No
    Speed: 100Mb/s
    Duplex: Full
    Port: MII
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: off
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
                   drv probe ifdown ifup
    Link detected: yes



```

New 2 speedtest:

```
user@user-AOA150:~$ ./speedtest-cliRetrieving speedtest.net configuration...
Testing from Vodafone 
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by Vodafone  [1.15 km]: 20.469 ms
Testing download speed...............................................................................
.Download: 29.52 Mbit/s
Testing upload speed....................................................................................................
Upload: 18.60 Mbit/s
user@user-AOA150:~$ ./speedtest-cli
Retrieving speedtest.net configuration...
Testing from Vodafone 
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by CWNET  [1.15 km]: 21.984 ms
Testing download speed................................................................................
Download: 87.92 Mbit/s
Testing upload speed....................................................................................................
Upload: 18.72 Mbit/s





```

The difference is still big,but for the first time I see: 87,92 Mbit/s.

What do you think?Which will be the right one?and will I have  30 or 88 Mbit/s?Thank you

---

### Post by chili555 on 2017-03-16
Whaaatt??? Why is one test from Vodafone and the other from CWNET? I don't understand.

I think that the 88 Mbps is probably just fine for the card and driver combination you have. If you'd like to make the autoneg part permanent, please do:```
sudo gedit /etc/rc.local
```Use nano or kate or leafpad if you don't have the text editor gedit. Right above the line exit 0, add a new line:```
ethtool -s enp2s0 speed 100 autoneg off
```Just to be perfectly clear, the file should now read:```
#!/bin/sh -e
ethtool -s enp2s0 speed 100 autoneg off
exit 0

```Proofread carefully, save and close the text editor. Reboot and use your fast ethernet to post a reply explaining Vodafone vs. CWNET.

---

### Post by ubu112 on 2017-03-16
Is this script correct?

```

#!/bin/sh -e#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
ethtool -s enp2s0 speed 100 autoneg off
exit 0


```

Before,I had inthe terminal

```

user@user-AOA150:~$ sudo gedit /etc/rc.local[sudo] password di user: 


(gedit:2732): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files



```

Why this "Gtk-WARNING?Where is saved the "script?

Now I reboot and send you the result.



Here the 2 results:

```
user@user-AOA150:~$ ./speedtest-cli

Retrieving speedtest.net configuration...
Testing from Vodafone 
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by Vodafone  [1.15 km]: 21.589 ms
Testing download speed................................................................................
Download: 13.06 Mbit/s
Testing upload speed....................................................................................................
Upload: 10.67 Mbit/s
user@user-AOA150:~$ ./speedtest-cli
Retrieving speedtest.net configuration...
Testing from Vodafone
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by Fastweb SpA [1.15 km]: 22.317 ms
Testing download speed................................................................................
Download: 73.64 Mbit/s
Testing upload speed....................................................................................................
Upload: 18.61 Mbit/s



```
Unfortunately,as you can see,I can't use the same server,it's set by speedtest.

What do think about it? Thank you

---

### Post by chili555 on 2017-03-20
I think the test result of 73.64 Mbps is very good but not great. I have no idea why the test selects test sites that vary so widely. When I run the test, I get the same site every time and a variation of perhaps 10%. I have no idea why your tests are so variable.

I suggest that you try a better driver:```
sudo apt-get install r8168-dkms
```Note to searchers and my many colleagues: This package is often suggested as a fix for flaky performance from this device and, I admit, sometimes, it seems to help. However, the notes say:> This driver should only be used for devices not yet supported by the
in-kernel driver r8169. Please see the README.Debian for instructions how
to report bugs against r8169 that made it necessary to use r8168-dkms.

Installation of the r8168-dkms package will disable the in-kernel r8169
module. To re-enable r8169, the r8168-dkms package must be purged.

This package provides the dkms source code for the r8168 kernel modules.
Kernel source or headers are required to compile these modules.In short, this shouldn't help but often seems to be beneficial. It costs nothing to try it, so let's do so. Reboot.

Next, you might power cycle your router to see if it helps or changes the speeds. Simply unplug it, wait a few moments and plug it back in. Now run the test again:```
./speedtest-cli
```Is there any improvement? If so, and if the router's firmware is fully updated, then perhaps it is the router and not Ubuntu.

Aside from these steps, I regret that I have no other suggestions.

---

### Post by ubu112 on 2017-03-20
First of all,thank you,chili555,for your answer and for your kindness.If you'll come in my country you are invited for dinner.

About your post,can you,please,explain to me:

> [COLOR=#000000]* To re-enable r8169, the r8168-dkms package must be purged.*[/COLOR]

I mean is it easy to come back or not?

I'd have a question for you,about "make changes permanent,when you manipulate Ethernet card",that I fund on Google,but[U] I don't 

really want to offend your experience[/U].What do you think?may I send you the link?can it be something interesting?

THANK YOU

---

### Post by chili555 on 2017-03-22
> I mean is it easy to come back or not?Very easy; all you'd need do is:```
sudo apt-get purge r8168-dkms
```> ?may I send you the link?can it be something interesting?Certainly, please post it right here.

By the way, you cannot "offend my experience." I am happy to learn more about networking and drivers, etc. in Ubuntu and hope that I learn more every day!

---

### Post by ubu112 on 2017-03-22
I meant,if for some reason I'd want to re-enable r8169,is it easy to purge r8169-dkms?

About "making changes on ethernet card permanet" I made a try,copied from an expert post (2013) called "chili555":

> 

[FONT=&amp]ethtool -s enp2s0 speed 100 [COLOR=#ff0000]d[/COLOR][COLOR=#ff0000]uplex full[/COLOR] autoneg off[/FONT]



but, it doesn't work.Then,as I told you, I fund ,on Google,this:

[http://www.thegeekstuff.com/2010/10/ethtool-command](http://www.thegeekstuff.com/2010/10/ethtool-command)

What do you think about it?and it's better to insist in this way or try to change driver? Thank you

---

### Post by chili555 on 2017-03-22
> but, it doesn't workThen don't use it.

That's the point here. Everything I've suggested can be tried and, if not successful, reversed. I haven't any way to judge which is going to work best with your exact ethernet card, your exact router and your exact internet service provider. You need to try these things and find out.> I meant,if for some reason I'd want to re-enable r8169,is it easy to purge r8169-dkms?I assume you mean is it easy to purge r8168-dkms. Yes, it is exactly as I stated in my last post:```
sudo apt-get purge r8168-dkms
```Reboot.

---

### Post by ubu112 on 2017-03-22
After the " r8168-dkms "installation,I have:

> 
user@user-AOA150:~$ ./speedtest-cli
Retrieving speedtest.net configuration...
Testing from Vodafone .
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by Vodafone  [3.57 km]: 20.957 ms
Testing download speed................................................................................
Download: 46.81 Mbit/s
Testing upload speed....................................................................................................
Upload: 18.69 Mbit/s
user@user-AOA150:~$ ./speedtest-cli
Retrieving speedtest.net configuration...
Testing from Vodafone 
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by Fastweb SpA  [3.57 km]: 21.695 ms
Testing download speed................................................................................
Download: 36.33 Mbit/s
Testing upload speed....................................................................................................
Upload: 19.03 Mbit/s
user@user-AOA150:~$ ./speedtest-cli
Retrieving speedtest.net configuration...
Testing from Vodafone 
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by CWNET  [3.57 km]: 22.034 ms
Testing download speed................................................................................
Download: 48.34 Mbit/s
Testing upload speed....................................................................................................
Upload: 19.07 Mbit/s
user@user-AOA150:~$ 




Before,I had: 51,37 Mbit/s and 48,17 Mbit/s.What do you think about it?Thank you

---

### Post by ubu112 on 2017-03-22
WIRELESS ALARM

Look at these speedtest:

> user@user-AOA150:~$ ./speedtest-cliRetrieving speedtest.net configuration...
Testing from Vodafone .
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by Vodafone  [3.57 km]: 25.728 ms
Testing download speed................................................................................
Download: 8.45 Mbit/s
Testing upload speed....................................................................................................
Upload: 18.16 Mbit/s
user@user-AOA150:~$ ./speedtest-cli
Retrieving speedtest.net configuration...
Testing from Vodafone 
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by Vodafone  [3.57 km]: 31.024 ms
Testing download speed................................................................................
Download: 3.84 Mbit/s
Testing upload speed....................................................................................................
Upload: 18.48 Mbit/s
user@user-AOA150:~$ 




After making test wired,I thought try with TP-LINK adapter and I had a bad surprise.

What can I do now? Thank you

---

### Post by chili555 on 2017-03-22
As I said previously, I have no other suggestions to offer. I have recommended many things in the pages above and I deeply regret that I am out of ideas. Sorry.

---

### Post by ubu112 on 2017-03-22
Sorry chili555,what do you think about this new wireless problem? can it depend on driver change?

Can you,please,help me to come back at the old situation? Thank you

---

### Post by chili555 on 2017-03-23
I am not sure I understand "come back at the old situation." Do you mean to return to the built-in wireless device? If so, you can do so temporarily by simply removing the USB wireless, detaching the ethernet cable and rebooting. Since the driver for the internal device is blacklisted, after the reboot, load it from the terminal:```
sudo modprobe ath5k
```If you wish to make the change permanent; that is, use the internal wireless by default, then remove the blacklist:```
gksudo gedit /etc/modprobe.d/blacklist.conf
```Use nano or kate or leafpad if you don't have the text editor gedit. Change the line:```
blacklist ath5k
```To read:```
#blacklist ath5k
```The** # **makes the line a comment that is ignored by the system. Proofread carefully, save and close the text editor.

Your speedtest results are all over the place with two different wireless devices and ethernet. I think it is time for you to consider that it is not Ubuntu at all, but that it is either the router, DSL or cable modem or your internet service provider that is at fault.

Assuming that just a few settings are made, all of which I've suggested to you previously and all of which I assume you've made, networking in Ubuntu works quite well. Please see: [https://ubuntuforums.org/showthread.php?t=2354312&p=13614535#post13614535](https://ubuntuforums.org/showthread.php?t=2354312&p=13614535#post13614535)

---

### Post by ubu112 on 2017-03-23
For "old situation" I mean when the Tp-Link,you suggested to me,worked.If you take a look at #1-2 thread,the adapter worked at 40+ with Chromium.

Now,after the driver change,with the adapter my speedtest gave me 8,45 and 3,84 Mbit/s.

I'd need your help to come back to 40+Mbit/s,with the Tp-Link.

Do you suggest to me to keep the new driver or come back to the old driver?

With the Windows computer,the speetest gave me, yestarday, 195 Mbit/s (wireless).Probably is my small and limited Acer that gives some problems.

Would you be so kind to help me? Thank you

---

### Post by chili555 on 2017-03-23
If you have not changed the blacklist file, then simply insert the TP-Link and you are all set.

As I have said three times now, we have tried everything I know of or can Google to try. I haven't any further suggestions.

---

### Post by ubu112 on 2017-03-23
Can you,please,explain to me what this mean?

> [COLOR=#000000]If you have not changed the blacklist file, then simply insert the TP-Link and you are all set.[/COLOR]

Why have I to insert the Tp-Link into the blacklist file?

May I have your opinion? I changed driver and seem that wired is more stable,but when I connect wireless (Tp-Link,that worked very well)the speed is very low (not always).If I 

try to come back to the native driver,to see if it works like before,do you think is wrong?

Thank you

---

### Post by chili555 on 2017-03-24
If you wish to try the internal, then follow the instructions I gave in my post just above. If you wish to use the USB then nothing further is required; just insert it and use it.

We have tried everything I know of or can Google to try. I haven't any further suggestions.

---

### Post by ubu112 on 2017-03-24
I apologize if I disturbed you or I made something wrong.

From my point of view,it's correct to show you this:

> user@user-AOA150:~$ dmesg | grep enp[    3.192692] r8169 0000:02:00.0 enp2s0: renamed from eth0
[   44.349874] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[   44.361335] r8169 0000:02:00.0 enp2s0: link down
[   44.361509] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
user@user-AOA150:~$ lspci -nnk | grep 0200 -A2
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Acer Incorporated [ALI] RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [1025:015b]
    Kernel driver in use: r8169
--
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Foxconn International, Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [105b:e008]
    Kernel modules: ath5k
user@user-AOA150:~$ 




I installed r8168-dkms,but r8169 is still working,or I'm wrong?

Thank you

---

### Post by chili555 on 2017-03-25
> I installed r8168-dkms,but r8169 is still working,or I'm wrong?Find out which driver is loaded:```
lsmod | grep r816
```If r8169 is loaded, instead of r8168, did you reboot? Was there a problem with the install?```
sudo dkms status
sudo dpkg -s r8168-dkms
```

---

### Post by ubu112 on 2017-03-25
Thank you chili555 for your reply.

> user@user-AOA150:~$ lsmod | grep r816
r8169                  77824  0
mii                    16384  1 r8169
user@user-AOA150:~$ sudo dkms status
[sudo] password di user: 
r8168, 8.041.00, 4.4.0-67-generic, i686: installed
user@user-AOA150:~$ sudo dpkg -s r8168-dkms
Package: r8168-dkms
Status: install ok installed
Priority: extra
Section: non-free/kernel
Installed-Size: 1083
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: r8168
Version: 8.041.00-1
Depends: dkms (>= 2.1.0.0)
Conffiles:
 /etc/modprobe.d/r8168-dkms.conf 5c1e04e15490158658d92fc6ddbd9d40
Description: dkms source for the r8168 network driver
 r8168 is the Linux device driver released for RealTek RTL8111B/RTL8168B,
 RTL8111/RTL8168, RTL8111C/RTL8111CP/RTL8111D(L), RTL8168C/RTL8111DP/RTL8111E,
 RTL8168E/RTL8111F/RTL8411, RTL8111G/RTL8111GUS/RTL8411B(N), RTL8118AS
 Gigabit Ethernet controllers with PCI-Express interface.
 .
 This driver should only be used for devices not yet supported by the
 in-kernel driver r8169. Please see the README.Debian for instructions how
 to report bugs against r8169 that made it necessary to use r8168-dkms.
 .
 Installation of the r8168-dkms package will disable the in-kernel r8169
 module. To re-enable r8169, the r8168-dkms package must be purged.
 .
 This package provides the dkms source code for the r8168 kernel modules.
 Kernel source or headers are required to compile these modules.
Original-Maintainer: Andreas Beckmann <anbe@debian.org>
Homepage: [https://github.com/mtorromeo/r8168](https://github.com/mtorromeo/r8168)
user@user-AOA150:~$ 




For the second part seems loaded,but the first code?I don't know,you are the expert.

Thank you

---

### Post by chili555 on 2017-03-25
So, did you reboot after you installed it?

What does this tell us?```
cat /etc/modprobe.d/r8168-dkms.conf
```Are there any interesting messages if you load it manually?```
sudo modprobe -r r8169
sudo modprobe r8168
```

---

### Post by ubu112 on 2017-03-25
Yes,I rebooted

```
user@user-AOA150:~$ cat /etc/modprobe.d/r8168-dkms.conf
# settings for r8168-dkms

# map the specific PCI IDs instead of blacklisting the whole r8169 module
alias    pci:v00001186d00004300sv00001186sd00004B10bc*sc*i*    r8168
alias    pci:v000010ECd00008168sv*sd*bc*sc*i*            r8168


# if the aliases above do not work, uncomment the following line
# to blacklist the whole r8169 module
#blacklist r8169
user@user-AOA150:~$ sudo modprobe -r r8169
[sudo] password di user: 
user@user-AOA150:~$ sudo modprobe r8168
user@user-AOA150:~$ 



```

I don't really know what "if you load it manually"mean but I don't have output.What this means?

Probably this doesn't mean nothing,but I'm connected wireless

Thank you

---

### Post by chili555 on 2017-03-25
> # settings for r8168-dkms

# map the specific PCI IDs instead of blacklisting the whole r8169 module
alias pci:v00001186d00004300sv00001186sd00004B10bc*sc*i* r8168
alias pci:v000010ECd00008168sv*sd*bc*sc*i* r8168


# if the aliases above do not work, uncomment the following line
# to blacklist the whole r8169 module
#blacklist r8169In order to load r8168 on boot, the conflicting module r8169 must be blacklisted. We wonder why the blacklist declaration is commented out. Let's fix it.```
gksudo gedit /etc/modprobe.d/r8168-dkms.conf
```Use nano or kate or leafpad if you don't have the text editor gedit. Change the last line to remove the #, so that it now reads:```
# settings for r8168-dkms

# map the specific PCI IDs instead of blacklisting the whole r8169 module
alias pci:v00001186d00004300sv00001186sd00004B10bc*sc*i* r8168
alias pci:v000010ECd00008168sv*sd*bc*sc*i* r8168


# if the aliases above do not work, uncomment the following line
# to blacklist the whole r8169 module
blacklist r8169
```Proofread carefully, save and close the text editor. Reboot.

You should be all set.

---

### Post by ubu112 on 2017-03-25
I made changes and rebooted.

Now,what have I to do ?just speedtest?

Thank you

---

### Post by chili555 on 2017-03-25
> **ubu112 said:**
> I made changes and rebooted.

Now,what have I to do ?just speedtest?

Thank youYes, please. Then compare the results to your previous tests using the ethernet. It may, however, be hard to judge sine the test results seem to be inconsistent. They seem to be good from one server and bad from another and good on one day and bad on another.

---

### Post by ubu112 on 2017-03-25
The first 3 are: wireless with Tp-Link
The second 3 are: wired

> user@user-AOA150:~$ ./speedtest-cli
Retrieving speedtest.net configuration...
Testing from Vodafone 
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by Fastweb SpA  [4.82 km]: 26.043 ms
Testing download speed................................................................................
[COLOR=#ff0000]Download: 6.78 Mbit/s[/COLOR]
Testing upload speed....................................................................................................
Upload: 12.54 Mbit/s
user@user-AOA150:~$ ./speedtest-cli
Retrieving speedtest.net configuration...
Testing from Vodafone 
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by Fastweb SpA  [4.82 km]: 33.598 ms
Testing download speed................................................................................
[COLOR=#ff0000]Download: 3.36 Mbit/s[/COLOR]
Testing upload speed....................................................................................................
Upload: 15.04 Mbit/s
user@user-AOA150:~$ ./speedtest-cli
Retrieving speedtest.net configuration...
Testing from Vodafone 
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by Vodafone  [4.82 km]: 33.596 ms
Testing download speed................................................................................
[COLOR=#ff0000]Download: 14.24 Mbit/s[/COLOR]
Testing upload speed....................................................................................................
Upload: 18.17 Mbit/s
-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
user@user-AOA150:~$ ./speedtest-cli
Retrieving speedtest.net configuration...
Testing from Vodafone 
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by Vodafone  [4.82 km]: 20.965 ms
Testing download speed................................................................................
[COLOR=#ff0000]Download: 30.32 Mbit/s[/COLOR]
Testing upload speed....................................................................................................
Upload: 18.34 Mbit/s
user@user-AOA150:~$ ./speedtest-cli
Retrieving speedtest.net configuration...
Testing from Vodafone 
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by Vodafone [4.82 km]: 21.024 ms
Testing download speed................................................................................
[COLOR=#ff0000]Download: 37.47 Mbit/s[/COLOR]
Testing upload speed....................................................................................................
Upload: 18.90 Mbit/s
user@user-AOA150:~$ ./speedtest-cli
Retrieving speedtest.net configuration...
Testing from Vodafone 
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by CWNET  [4.82 km]: 21.699 ms
Testing download speed................................................................................
[COLOR=#ff0000]Download: 30.98 Mbit/s[/COLOR]
Testing upload speed....................................................................................................
Upload: 19.03 Mbit/s
user@user-AOA150:~$ 




PLEASE,tell me what's going on WIRELESS.Instead,wired are lower but more stable.Am I wrong?

Which is your opinion?I'd like to come back to the old speed (wired and wireless)

Thank you

---

### Post by chili555 on 2017-03-25
We have tried everything I know of or can Google to try. I haven't any further suggestions.

---

### Post by ubu112 on 2017-03-25
[FONT=arial]I made as few hours ago and now:

[QUOTE[/FONT]user@user-AOA150:~$ ./speedtest-cli
Retrieving speedtest.net configuration...
Testing from Vodafone 
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by Vodafone  [4.82 km]: 24.816 ms
Testing download speed................................................................................
[COLOR=#ff0000]Download: 35.74 Mbit/s[/COLOR]
Testing upload speed....................................................................................................
Upload: 18.18 Mbit/s
user@user-AOA150:~$ ./speedtest-cli
Retrieving speedtest.net configuration...
Testing from Vodafone 
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by CWNET  [4.82 km]: 25.385 ms
Testing download speed................................................................................
[COLOR=#ff0000]Download: 33.35 Mbit/s[/COLOR]
Testing upload speed....................................................................................................
Upload: 18.23 Mbit/s
user@user-AOA150:~$ ./speedtest-cli
Retrieving speedtest.net configuration...
Testing from Vodafone 
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by Vodafone  [4.82 km]: 25.376 ms
Testing download speed................................................................................
[COLOR=#ff0000]Download: 26.57 Mbit/s[/COLOR]
Testing upload speed....................................................................................................
Upload: 18.78 Mbit/s
------------------------------------------------------------------------------------------------------------------------------------------------------------------------
user@user-AOA150:~$ ./speedtest-cli
Retrieving speedtest.net configuration...
Testing from Vodafone
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by Vodafone  [4.82 km]: 20.658 ms
Testing download speed................................................................................
[COLOR=#ff0000]Download: 47.08 Mbit/s[/COLOR]
Testing upload speed....................................................................................................
Upload: 19.00 Mbit/s
user@user-AOA150:~$ ./speedtest-cli
Retrieving speedtest.net configuration...
Testing from Vodafone 
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by SIPORTAL  [4.75 km]: 21.568 ms
Testing download speed................................................................................
[COLOR=#ff0000]Download: 43.32 Mbit/s[/COLOR]
Testing upload speed....................................................................................................
Upload: 19.06 Mbit/s
user@user-AOA150:~$ ./speedtest-cli
Retrieving speedtest.net configuration...
Testing from Vodafone 
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by SIPORTAL   [4.75 km]: 21.438 ms
Testing download speed................................................................................
[COLOR=#ff0000]Download: 51.68 Mbit/s[/COLOR]
Testing upload speed...................................................................................................
.Upload: 18.98 Mbit/s
user@user-AOA150:~$ 


[FONT=arial]][/QUOTE]

How do you explain these new results?I mean this improvement

]After these good news,I tried to pass from wired to wireless (Tp-Link)and when I tried to make a new speedtest:

> [/FONT]user@user-AOA150:~$ ./speedtest-cliRetrieving speedtest.net configuration...
Cannot retrieve speedtest configuration
ERROR: <urlopen error [Errno -3] Temporary failure in name resolution>
user@user-AOA150:~$ ./speedtest-cli
Retrieving speedtest.net configuration...
Cannot retrieve speedtest configuration
ERROR: <urlopen error [Errno -3] Temporary failure in name resolution>
user@user-AOA150:~$ 


[FONT=arial]

This is not the first time.Do you know what that mean and what have I to do?

Thank you[/FONT]

---

### Post by ubu112 on 2017-03-27
In the previous post seem to be all good, now I'm connected wireless,with Tp-Link N150,and I have lower and unstable speed.

I tried  iwconfig

> 

user@user-AOA150:~$ iwconfig
wlx18d6c70d5f00  IEEE 802.11bgn  ESSID:"Vodafone-34344831"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 64:59:F8:E3:71:78   
          Bit Rate=65 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-37 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
[COLOR=#ff0000]          Tx excessive retries:275  Invalid misc:693   Missed beacon:0[/COLOR]


lo        no wireless extensions.


enp2s0    no wireless extensions.






The numbers,after Tx are changed.Why?

Thank you

---

### Post by chili555 on 2017-03-27
As I said previously, your speedtest results are all over the place with two different wireless devices and ethernet. I think it is time for you to consider that it is not Ubuntu at all, but that it is either the router, DSL or cable modem or your internet service provider that is at fault.

We have tried everything I know of or can Google to try. I haven't any further suggestions.

---

### Post by ubu112 on 2017-04-04
Sorry"chili555" if I'm disturbing you,but I'd need an opinion from an expert.If you remember,I told you that with 5 Ghz I can't cover all my 100 sq meters home.So, I'm 

investigating if my router's signal is too weak for my home(this,maybe,can affect the 2,4 Ghz signal).The router has been given to me from my ISP and it has 300 Mbps 

(wifi n)+ 1300 Mbps (wifi ac).The question is:

from your point of view is enough or I'd need a more powerfull router?I tried with a range extender but I didn't have improvements.What do you suggest to me 1)change the

 router(but unfortunately my router manage my phone too and I don't know if is allowed from my ISP) 2)add an access point 3)or,what else can you suggest to me.

Curiosity which router do you have?and how many channels do you have?I have 4 channels and I read that 5 Ghz has 19 channels.

Thank you

---

### Post by chili555 on 2017-04-05
> from your point of view is enough or I'd need a more powerfull router?It's impossible to know without seeing and troubleshooting your setup. Sometimes, you can make improvements by placement. What is between you and the router? Is it in a closet? Are there obstructions that you can move? Is there a better signal if the router is horizontal or vertical? Are there antennae that you can re-orient? Most of all, is there a setting in the router that changes the transmission power?

[https://www.howtogeek.com/wp-content/uploads/2011/03/tx-power.png](https://www.howtogeek.com/wp-content/uploads/2011/03/tx-power.png)

If you decide to increase the transmission power, please be cautious. Only increase it in small steps and stop when you get enough range to suit your needs. Running at full power for 24 hours a day and 7 days a week for year after year has the potential to overheat and damage the router.> change the router(but unfortunately my router manage my phone too and I don't know if is allowed from my ISP)I suggest that you inquire before proceeding further.> what else can you suggest to me.You could look into any of several mesh devices: [https://en.wikipedia.org/wiki/Wireless_mesh_network](https://en.wikipedia.org/wiki/Wireless_mesh_network) This is an example but not the only such device made. I haven't tested this or any others, but I hear good reports. [https://eero.com/](https://eero.com/)> Curiosity which router do you have?and how many channels do you have?I have 4 channels and I read that 5 Ghz has 19 channels.I have a TP Link Archer C7. I have a modem and router provided my my ISP that handles phone, as well. I turned off wireless in it and connected my TP Link to provide wireless. It was a bit tricky to set up but, once it was, works perfectly well. 

Setting up a router behind an ISP modem is far beyond the scope of this forum, so I won't go into it here.

I have eleven 2.4 Ghz channels available; 1-11. I have only nine 5 Ghz channels available and I did a survey of my neighborhood like this:```
sudo nmcli dev wifi list
```There is no-one near me on channel 149, so that is what I selected for 5 Ghz.

---

### Post by ubu112 on 2017-04-05
First of all,thank you,for your answer.I feel myself very lucky to have fund "chili555",because I have,always,great answers.I'm very grateful to you for all your help.

> [COLOR=#000000] Sometimes, you can make improvements by placement. What is between you and the router? Is it in a closet? Are there obstructions that you can move? Is there a better signal if the router is horizontal or vertical? Are there antennae that you can re-orient? Most of all, is there a setting in the router that changes the transmission power?[/COLOR]

When I changed ISP,at the end of the year,I tried to move my router at the center of my apartment (that should be the best position)but at the center I have a column.Between me and the router - walls.My 

router can stay just vertical and antennae are internal.I don't have setting to change transmission power.Have you settings like the picture you sent to me?Yes,because I took a look to the manual and I can just dream all these settings.TX power can be seen in other ways?

Maybe I'm wrong,mesh devices are range extender?Because I already tried one and I can't respect the right sequence router-extender-pc,because I like to move myself with my pc.

As I told you,I just have 4 channels and I made (with the code you give to me)a survey and I have about 35 at 2,4 Ghz,but no 5 Ghz.

Is it important transmission speed or not? For example my router has 1300 Mbps in Ac,you have the same and a more powerfull signal.

Today I talked with a Netgear agent and seem that with a wireless router with a transmission speed higher I can improve,what do you think ?is it correct?

So,my modem-router that handles just the phone,connected to a new wireless router that handles internet and wifi.How to exactly connect them and how to change settings, I don't know how to find the right one.

Do you think that,for example,with your wireless router can be made?do you know how change setting?

Do you think that this could be a problem for my ISP?

Do you see other solutions?

Are you ready for wireless ad?

Thank you

---

### Post by ubu112 on 2017-04-08
I started my pc wireless,I made an update and few speedtest.Then I decided to connect wired,unpluged Tp-Link,and I plugged the 

cable "surprise"no connection available.The network manager doesn't change in 2 arrows,but it's always the same.

Can you,please,help me to understand what's going on?

> user@user-AOA150:~$ ifconfig
lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:291 errors:0 dropped:0 overruns:0 frame:0
          TX packets:291 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1 
          Byte RX:21990 (21.9 KB)  Byte TX:21990 (21.9 KB)


wlx18d6c70d5f00 Link encap:Ethernet  IndirizzoHW 18:d6:c7:0d:5f:00  
          indirizzo inet:192.168.1.3  Bcast:192.168.1.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::a14:1087:2cbe:dc27/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:102 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
Byte RX:22924 (22.9 KB)  Byte TX:11495 (11.4 KB)



and


> user@user-AOA150:~$ dmesg | grep enpuser@user-AOA150:~$ lspci -nnk | grep 0200 -A2
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Acer Incorporated [ALI] RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [1025:015b]
    Kernel modules: r8169
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Foxconn International, Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [105b:e008]
    Kernel modules: ath5k
user@user-AOA150:~$ lsmod | grep r816
user@user-AOA150:~$ sudo dkms status
[sudo] password di user: 
r8168, 8.041.00, 4.4.0-67-generic, i686: installed
r8168, 8.041.00, 4.4.0-70-generic, i686: installed
r8168, 8.041.00, 4.4.0-71-generic, i686: installed
r8168, 8.041.00, 4.4.0-72-generic, i686: installed
user@user-AOA150:~$ sudo dpkg -s r8168-dkms
Package: r8168-dkms
Status: install ok installed
Priority: extra
Section: non-free/kernel
Installed-Size: 1083
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: r8168
Version: 8.041.00-1
Depends: dkms (>= 2.1.0.0)
Conffiles:
 /etc/modprobe.d/r8168-dkms.conf 5c1e04e15490158658d92fc6ddbd9d40
Description: dkms source for the r8168 network driver
 r8168 is the Linux device driver released for RealTek RTL8111B/RTL8168B,
 RTL8111/RTL8168, RTL8111C/RTL8111CP/RTL8111D(L), RTL8168C/RTL8111DP/RTL8111E,
 RTL8168E/RTL8111F/RTL8411, RTL8111G/RTL8111GUS/RTL8411B(N), RTL8118AS
 Gigabit Ethernet controllers with PCI-Express interface.
 .
 This driver should only be used for devices not yet supported by the
 in-kernel driver r8169. Please see the README.Debian for instructions how
 to report bugs against r8169 that made it necessary to use r8168-dkms.
 .
 Installation of the r8168-dkms package will disable the in-kernel r8169
 module. To re-enable r8169, the r8168-dkms package must be purged.
 .
 This package provides the dkms source code for the r8168 kernel modules.
 Kernel source or headers are required to compile these modules.
Original-Maintainer: Andreas Beckmann <anbe@debian.org>
Homepage: [https://github.com/mtorromeo/r8168](https://github.com/mtorromeo/r8168)
user@user-AOA150:~$ 




I tried gksudo gedit /etc/modprbe.d/r8168-dkms.conf,it's correct.


I don't know if these codes are helpful,please,let me know.

Thank you

---

### Post by chili555 on 2017-04-09
If your ethernet didn't start, there are only a very few things that can go wrong. First, did the required driver load? Find out the driver with:

```
lspci -nnk | grep 0200 -A3

```
The result will show some kernel module such as tg3, e1000e, r8169 or some other. Did it load?

```
lsmod | grep <driver_you_found>
```

If not, load it:

```
sudo modprobe <driver_you_found>
```

Are there errors or warnings? Did your ethernet start? Are there clues in the log?

```
dmesg | grep <driver_you_found>
```

Does it help to restart Network Manager?

```
sudo service network-manager restart
```

Is the cable good? Please try another known good cable.

Does it help to reboot the router?

---

### Post by ubu112 on 2017-04-09
Thank you for your reply.

Did you see the last changes I made to my post?because in the same time you answered I was making changes.

Few minutes and I'll send you the next results.

Thank you

---

### Post by ubu112 on 2017-04-09
I don't know if I'm doing right,I send all results.I'll use the last with cable.

[QUOTEuser@user-AOA150:~$ lspci -nnk | grep 0200 -A3
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Acer Incorporated [ALI] RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [1025:015b]
    Kernel modules: r8169
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Foxconn International, Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [105b:e008]
    Kernel modules: ath5k
user@user-AOA150:~$ lsmod | grep r8169
user@user-AOA150:~$ sudo modprobe r8169
[sudo] password di user: 
user@user-AOA150:~$ dmesg | grep r8169
[ 4369.772885] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[ 4369.772914] r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[ 4369.774017] r8169 0000:02:00.0 eth0: RTL8102e at 0xf858a000, 00:1e:68:fd:8b:6b, XID 04a00000 IRQ 29
[ 4372.323668] r8169 0000:02:00.0 enp2s0: renamed from eth0
[ 4373.321455] r8169 0000:02:00.0 enp2s0: link down
user@user-AOA150:~$ 


][/QUOTE]

In few minutes I'll say the result with cable.

Thank you

---

### Post by ubu112 on 2017-04-09
I made all what you said,with 2 cables,I rebooted the router,at the end to be sure the cable is good I connected my Windows pc and I made a speedtest: 290 Mbps.

When I tried "sudo service network-manager restart" I received a massage - you are now disconnected".

PLEASE, help me to get out of this problem.

Thank you

---

### Post by chili555 on 2017-04-09
Please try:```
sudo ethtool -s enp2s0 autoneg off speed 100
```Restart NM:```
sudo service network-manager restart
```Any improvement?

---

### Post by ubu112 on 2017-04-10
Nothing,here are results:


> user@user-AOA150:~$ sudo ethtool -s enp2s0 autoneg off speed 100[sudo] password di user: 
Cannot get current device settings: No such device
  not setting speed
  not setting autoneg
user@user-AOA150:~$ sudo ethtool -s enp2s0 autoneg off speed 100
Cannot get current device settings: No such device
  not setting speed
  not setting autoneg
user@user-AOA150:~$ sudo service network-manager restart
user@user-AOA150:~$ sudo ethtool -s enp2s0 autoneg off
Cannot get current device settings: No such device
  not setting autoneg
user@user-AOA150:~$ sudo ethtool enp2s0
Settings for enp2s0:
Cannot get device settings: No such device
Cannot get wake-on-lan settings: No such device
Cannot get message level: No such device
Cannot get link status: No such device
No data available
user@user-AOA150:~$ sudo gedit /etc/rc.local


** (gedit:3003): WARNING **: Set document metadata failed: Impostazione dell'attributo metadata::gedit-spell-enabled non supportata


** (gedit:3003): WARNING **: Set document metadata failed: Impostazione dell'attributo metadata::gedit-encoding non supportata


** (gedit:3003): WARNING **: Set document metadata failed: Impostazione dell'attributo metadata::gedit-position non supportata
user@user-AOA150:~$ sudo -s enp2s0 speed 100 autoneg off
/bin/bash: enp2s0: comando non trovato
user@user-AOA150:~$ 




As you can see,I tried with what we made in #25-#26 post and I checked the script that is like it was.

Where is r8168-dkms?

PLEASE,tell me what has to be done.

Thank you

---

### Post by chili555 on 2017-04-10
Well, you certainly had an enp2s0 earlier:>  r8169 0000:02:00.0 enp2s0: renamed from eth0Let's check a few things:```
sudo dkms status
ls /etc/modprobe.d
sudo modprobe r8168
dmesg | grep r816
```

---

### Post by ubu112 on 2017-04-10
Here I am:

> user@user-AOA150:~$ sudo dkms status[sudo] password di user: 
r8168, 8.041.00, 4.4.0-67-generic, i686: installed
r8168, 8.041.00, 4.4.0-70-generic, i686: installed
r8168, 8.041.00, 4.4.0-71-generic, i686: installed
r8168, 8.041.00, 4.4.0-72-generic, i686: installed
user@user-AOA150:~$ ls /etc/modprobe.d
alsa-base.conf              blacklist-oss.conf              iwlwifi.conf
blacklist-ath_pci.conf      blacklist-rare-network.conf     mlx4.conf
blacklist.conf              blacklist-watchdog.conf         r8168-dkms.conf
blacklist-firewire.conf     dkms.conf                       vmwgfx-fbdev.conf
blacklist-framebuffer.conf  fbdev-blacklist.conf
blacklist-modem.conf        intel-microcode-blacklist.conf
user@user-AOA150:~$ sudo modprobe r8168
user@user-AOA150:~$ dmesg | grep r816
[  441.107178] r8168: module verification failed: signature and/or required key missing - tainting kernel
user@user-AOA150:~$ 




Is it correct to work with so many kernel? and many blacklist.My system is all blacklisted?

Is it correct "i686" with my pc at 32 bit?

Are you used to clean,sometimes,your system?with "Ubuntu Tweak" for example.

Please,Tp-Link is working well,be so kind, make my Ethernet work like is working wireless.


Thank you

---

### Post by chili555 on 2017-04-11
> user@user-AOA150:~$ sudo modprobe r8168
user@user-AOA150:~$ dmesg | grep r816
[ 441.107178] r8168: module verification failed: signature and/or required key missing - tainting kernel

Let's get the module to load automatically on boot:

```
sudo -i
echo r8168 >>  /etc/modules
exit
```

Reboot and let us see: dmesg | grep r816


> Is it correct to work with so many kernel? and many blacklist.My system is all blacklisted?

It is entirely reasonable to have a kernel or two on hand in case an update doesn't work correctly. Then, you can boot into an earlier kernel at the GRUB menu and try to fix what's wrong. It appears that you have four installed.  They don't take up much room, but if you wish, you could autoremove all but two; the current running kernel and the last backup:

```
sudo apt-get autoremove
```

There are a lot of things blacklisted; in fact, many modules are blacklisted that don't exist and haven't existed for many years. I guess you will be all set if you decide to install a 2.4.1 kernel from 2001! Again, these files take up very little room and it's not productive or useful to do the research and remove 10-12 characters from a file that doesn't help or hurt you anyway.

> Is it correct "i686" with my pc at 32 bit?

Exactly correct. 64-bit systems will show x86_64.

> Are you used to clean,sometimes,your system?with "Ubuntu Tweak" for example.

Never.

> Please,Tp-Link is working well,be so kind, make my Ethernet work like is working wireless.

I'll try.

---

### Post by ubu112 on 2017-04-11
Here the result:


> user@user-AOA150:~$ dmesg | grep r816[   10.436868] r8168: module verification failed: signature and/or required key missing - tainting kernel
user@user-AOA150:~$ 




Like before,please,tell me what to do.

Thank you

---

### Post by chili555 on 2017-04-11
Let's have a look at:```
modinfo r8168 | grep 8136 
```I am beginning to wonder if the much-loved r8168 even drives your device!

---

### Post by ubu112 on 2017-04-11
Here,the result:

> user@user-AOA150:~$ modinfo r8168 | grep 8136

user@user-AOA150:~$ 




Tell me,what do you think?

Let me ask,even if I don't understand nothing,is the case to insist with this driver?

You are,the expert,PLEASE,tell me what to do to make my Ethernet work.

Thank you

---

### Post by chili555 on 2017-04-12
I thought that I suggested from the outset that it was possibly helpful and possibly not:> Note to searchers and my many colleagues: This package is often suggested as a fix for flaky performance from this device and, I admit, sometimes, it seems to help. However, the notes say:
[QUOTE]This driver should only be used for devices not yet supported by the
in-kernel driver r8169. Please see the README.Debian for instructions how
to report bugs against r8169 that made it necessary to use r8168-dkms.

Installation of the r8168-dkms package will disable the in-kernel r8169
module. To re-enable r8169, the r8168-dkms package must be purged.

This package provides the dkms source code for the r8168 kernel modules.
Kernel source or headers are required to compile these modules.
In short, this shouldn't help but often seems to be beneficial. It costs nothing to try it, so let's do so. Reboot.
[/QUOTE]Just because it isn't helpful for you doesn't mean that it isn't helpful for anyone.

Since we now know that it doesn't even cover your device, let's remove it and revert to r8169:```
sudo apt-get purge r8168-dkms
sudo apt-get purge dkms
sudo gedit /etc/modules
```Change the last line from:```
r8168
```To read:```
r8169
```Proofread carefully, save and close the text editor. Reboot.

---

### Post by ubu112 on 2017-04-12
First of all,sorry if I said something wrong,I really didn't want to offend you.

> [COLOR=#000000]I thought that I suggested from the outset that it was possibly helpful and possibly not[/COLOR]

That is absolutely true.

> [COLOR=#000000]Just because it isn't helpful for you doesn't mean that it isn't helpful for anyone[/COLOR]

I did not mean something like that,simply because I don't have your  expirence  and knowledge.

From your point of view:

> [COLOR=#000000]Let me ask,even if I don't understand nothing,is the case to insist with this driver?[/COLOR]

This question is wrong? I mean come back to the old driver (r8169) is correct?or there could be other ways?are you convinced?is it the right choice?

I'll wait your OK,to come back or not.

If you will say revert,I'll send to you few speedtest saying "now my speed is too slow",please,I want to come back to 70-80 Mbps.

Thank you

---

### Post by chili555 on 2017-04-12
> Let me ask,even if I don't understand nothing,is the case to insist with this driver?
This question is wrong?No, the question is not wrong. I proposed trying the r8168 driver because it sometimes helps some people. The only way I know of to tell if it helps you is to install it and try it.> I mean come back to the old driver (r8169) is correct?or there could be other ways?are you convinced?is it the right choice?I am never convinced until I receive a reply to a post that reports that the problem is solved and the original poster is happy.

There are all sorts of internet service providers out there. There are all sorts of ISP-provided modems. There are all sorts of routers. There are all sorts of setups within the router and within the modem. Some of the hardware; modem, router and network card, is new and in great condition and working perfectly. Some has fully updated firmware. Some others do not.

Because of this, it is somewhat of a guessing game to try to diagnose and fix a problem, often in another country and in another language, by only forum posts. As much as I appreciate your respect for my somewhat limited experience, if you have followed my posts here and elsewhere for enough years, you will have noticed that I can't always fix every last problem. There are too many variables over which I have no control, as I stated above. I regret the 20% or so that I can't ever fix but I am very proud of the 80% or so that I do.

r8168 has no chance to work for your network card. r8169 does. I suggest that you revert.

---

### Post by ubu112 on 2017-04-12
As I told you:

> 
user@user-AOA150:~$ iwconfig
wlx18d6c70d5f00  IEEE 802.11bgn  ESSID:"Vodafone-34344831"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 64:59:F8:E3:71:78   
          Bit Rate=52 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-35 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:420   Missed beacon:0


lo        no wireless extensions.


enp2s0    no wireless extensions.


user@user-AOA150:~$ ./speedtest-cli
Retrieving speedtest.net configuration...
Testing from Vodafone (2.32.41.159)...
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by Vodafone [6.99 km]: 24.513 ms
Testing download speed................................................................................
Download: 22.33 Mbit/s
Testing upload speed....................................................................................................
Upload: 17.80 Mbit/s
user@user-AOA150:~$ ./speedtest-cli
Retrieving speedtest.net configuration...
Testing from Vodafone (2.32.41.159)...
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by Fastweb  [6.99 km]: 24.556 ms
Testing download speed................................................................................
Download: 32.92 Mbit/s
Testing upload speed....................................................................................................
Upload: 18.75 Mbit/s
user@user-AOA150:~$ ifconfig
enp2s0    Link encap:Ethernet  IndirizzoHW 00:1e:68:fd:8b:6b  
          indirizzo inet:192.168.1.5  Bcast:192.168.1.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::f9bc:b7f4:c5c1:9dbf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:21 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:2488 (2.4 KB)  Byte TX:6199 (6.1 KB)


lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2204 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2204 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1 
          Byte RX:189734 (189.7 KB)  Byte TX:189734 (189.7 KB)


user@user-AOA150:~$ ./speedtest-cli
Retrieving speedtest.net configuration...
Testing from Vodafone 
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by Telecom  [6.99 km]: 29.916 ms
Testing download speed................................................................................
Download: 47.30 Mbit/s
Testing upload speed....................................................................................................
Upload: 19.00 Mbit/s
user@user-AOA150:~$ ./speedtest-cli
Retrieving speedtest.net configuration...
Testing from Vodafone 
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by Telecom  [6.99 km]: 30.519 ms
Testing download speed................................................................................
Download: 86.12 Mbit/s
Testing upload speed....................................................................................................
Upload: 18.80 Mbit/s
user@user-AOA150:~$ 




What do you think?I think,it's always unstable,but it can't be better.I mean I can't pretend more from this pc.Do you agree with me?

Let me reveal a "secret",I made this experiment just because it came from "chili555",for the person and his experience.

How many do you know that can solve more than 80%?with this,not easy,OS.Which OS did you use before Ubuntu?and why did you choose Ubuntu?

I have a question,regarding wireless,from what depend "Bit Rate"?am I wrong or it was 72 Mb/s and Tx-Power is the same you can 

read on your router?if I can't change it from the router setting,can be made in other ways?

Thank you very much

---

### Post by chili555 on 2017-04-13
> Testing download speed............................................. ...................................
Download: 86.12 Mbit/s
Testing upload speed............................................. .................................................. .....
Upload: 18.80 Mbit/sPerfect! I think that's about what we expect from a 100 Mbps network card.> I have a question,regarding wireless,from what depend "Bit Rate"?am I wrong or it was 72 Mb/s and Tx-Power is the same you can 

read on your router?if I can't change it from the router setting,can be made in other ways?
When you run:```
iwconfig
```...and you see 72 Mbps or 54 Mbps or some other, that is a reflection of what the wireless device is capable of doing in a perfect laboratory setting. Whether it is 54 or 72 or 144 or some other depends on the chip and the antenna or antennas. I am unaware of any USB wireless that has multiple input and output antennae. [https://en.wikipedia.org/wiki/MIMO](https://en.wikipedia.org/wiki/MIMO)

If there is such a device, I am sure it isn't available for US$13. Our TP Links are inexpensive because they use just one antenna and a well-developed (fortunately working well in Ubuntu!) chipset. I am unaware of any way to get this or any device to exceed the laws of physics and go faster than science and technology allow.

I replaced the card in my laptop but it cost me a bit more than $13. The card and my laptop have two antennae. Now, I get this:```
wlp3s0    IEEE 802.11  ESSID:"GBR5"  
          Mode:Managed  Frequency:5.745 GHz  Access Point: xx:2B:B0:DC:45:xx   
          [COLOR="#FF0000"]Bit Rate=866.7 Mb/s [/COLOR]  Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:287   Missed beacon:0

```You already rejected changing the internal card.

---

### Post by ubu112 on 2017-04-30
Chili555,I'd like to have your opinion about changing my Ubuntu to Xubuntu,always 16.04 LTS.Maybe with  my Acer Aspire One that has only 1 Gb of RAM,I can improve my system speed.I don't know if it can 

improve my connection speed (wired and wireless)too.What do you think?

Thank you

---

### Post by chili555 on 2017-04-30
As I have said before, much of your issues depend on your internet service provider, your modem, your router, your environment and your wireless device and driver. Because of this, it is difficult for me to say with certainty that xubuntu will help. 

It is, however, easy to find out. Download the iso, create a USB or DVD and try it for a few days. It it helps, after a thorough backup, install it. If not, you have spent almost nothing to know for sure.

---

### Post by ubu112 on 2017-04-30
I tried Xubuntu 16.04 LTS,wired is pretty fast 60-65+(made with speedtest with Firefox),but I can't connect wireless.

The question is: we blacklisted the internal card in Ubuntu,but now,in Xubuntu, I should use the internal card,not the Tp-Link,am I wrong?

I tried both,but I can't connect it,to compare Ubuntu vs Xubuntu speed.

Can you,please,explain to me what's wrong?

Thank you

---

### Post by chili555 on 2017-05-01
>  I should use the internal card,not the Tp-Link,am I wrong?

I tried both,but I can't connect it,to compare Ubuntu vs Xubuntu speed.

Can you,please,explain to me what's wrong?Please detach the USB and let's try the internal. Does it try and fail to connect? What does this tell us?```
dmesg | grep ath
```How about:```
cat /var/log/syslog | grep etwork | tail -n20
```Please conduct your test with the ethernet detached because Network Manager will generally default to the usually faster and more secure ethernet.

---

### Post by ubu112 on 2017-05-01
Sorry,if I disturbed you,no private messages anymore.

I tried without USB and cable,it ask me the password and nothing happend.

Now,the results:

```
xubuntu@xubuntu:~$ dmesg | grep ath
[   62.663294] ath5k 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   62.663449] ath5k 0000:03:00.0: registered as 'phy0'
[   64.733129] ath: EEPROM regdomain: 0x65
[   64.733140] ath: EEPROM indicates we should expect a direct regpair map
[   64.733151] ath: Country alpha2 being used: 00
[   64.733157] ath: Regpair used: 0x65
[   64.904664] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   64.929480] ath5k 0000:03:00.0 wlp3s0: renamed from wlan0
xubuntu@xubuntu:~$ cat /var/log/syslog | grep etwork | tail -n20
May  1 13:54:38 xubuntu NetworkManager[1156]: <info>  [1493646878.6059]   plen 24 (255.255.255.0)
May  1 13:54:38 xubuntu NetworkManager[1156]: <info>  [1493646878.6060]   gateway 192.168.1.1
May  1 13:54:38 xubuntu NetworkManager[1156]: <info>  [1493646878.6061]   server identifier 192.168.1.1
May  1 13:54:38 xubuntu NetworkManager[1156]: <info>  [1493646878.6061]   lease time 3600
May  1 13:54:38 xubuntu NetworkManager[1156]: <info>  [1493646878.6063]   hostname 'xubuntu'
May  1 13:54:38 xubuntu NetworkManager[1156]: <info>  [1493646878.6064]   nameserver '192.168.1.1'
May  1 13:54:38 xubuntu NetworkManager[1156]: <info>  [1493646878.6065]   domain name 'station'
May  1 13:54:38 xubuntu NetworkManager[1156]: <info>  [1493646878.6109] dhcp4 (enp2s0): state changed bound -> bound
May  1 13:54:38 xubuntu systemd[1]: Starting Network Manager Script Dispatcher Service...
May  1 13:54:38 xubuntu systemd[1]: Started Network Manager Script Dispatcher Service.
May  1 13:55:23 xubuntu NetworkManager[1156]: <info>  [1493646923.9366] device (enp2s0): link disconnected (deferring action for 4 seconds)
May  1 13:55:28 xubuntu NetworkManager[1156]: <info>  [1493646928.6375] device (enp2s0): link disconnected (calling deferred action)
May  1 13:55:28 xubuntu NetworkManager[1156]: <info>  [1493646928.6446] device (enp2s0): state change: activated -> unavailable (reason 'carrier-changed') [100 20 40]
May  1 13:55:28 xubuntu NetworkManager[1156]: <info>  [1493646928.6617] dhcp4 (enp2s0): canceled DHCP transaction, DHCP client pid 3763
May  1 13:55:28 xubuntu NetworkManager[1156]: <info>  [1493646928.6618] dhcp4 (enp2s0): state changed bound -> done
May  1 13:55:28 xubuntu NetworkManager[1156]: <info>  [1493646928.6755] dns-mgr: Writing DNS information to /sbin/resolvconf
May  1 13:55:28 xubuntu NetworkManager[1156]: <info>  [1493646928.8130] manager: NetworkManager state is now CONNECTED_LOCAL
May  1 13:55:28 xubuntu NetworkManager[1156]: <info>  [1493646928.8149] manager: NetworkManager state is now DISCONNECTED
May  1 13:55:28 xubuntu systemd[1]: Starting Network Manager Script Dispatcher Service...
May  1 13:55:28 xubuntu systemd[1]: Started Network Manager Script Dispatcher Service.
xubuntu@xubuntu:~$ 

```



I have always made my wireless tests without cable.

Thank you

---

### Post by chili555 on 2017-05-01
The only thing we see in syslog is cable. Let's dig deeper:```
cat /var/log/syslog | grep wlp
dmesg | grep wlp
```> [ 64.733140] ath: EEPROM indicates we should expect a direct regpair map
[ 64.733151] ath: Country alpha2 being used: 00What do these tell us?```
cat /etc/default/crda | tail -n1
sudo iw reg get
```

---

### Post by ubu112 on 2017-05-01
The results,without cable:

```
xubuntu@xubuntu:~$ cat /var/log/syslog | grep wlp
May  1 14:56:22 xubuntu kernel: [   63.117890] ath5k 0000:03:00.0 wlp3s0: renamed from wlan0
May  1 14:56:22 xubuntu NetworkManager[1167]: <info>  [1493650582.7922] device (wlan0): interface index 3 renamed iface from 'wlan0' to 'wlp3s0'
May  1 14:56:22 xubuntu NetworkManager[1167]: <info>  [1493650582.9812] devices added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/net/wlp3s0, iface: wlp3s0)
May  1 14:56:22 xubuntu NetworkManager[1167]: <info>  [1493650582.9813] device added (path: /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/net/wlp3s0, iface: wlp3s0): no ifupdown configuration found.
May  1 14:56:22 xubuntu NetworkManager[1167]: <info>  [1493650582.9828] device (wlp3s0): state change: unmanaged -> unavailable (reason 'managed') [10 20 2]
May  1 14:56:22 xubuntu kernel: [   63.352130] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
May  1 14:56:23 xubuntu kernel: [   63.379748] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
May  1 14:56:24 xubuntu NetworkManager[1167]: <info>  [1493650584.7207] device (wlp3s0): supplicant interface state: init -> starting
May  1 14:56:24 xubuntu NetworkManager[1167]: <info>  [1493650584.8287] device (wlp3s0): supplicant interface state: starting -> ready
May  1 14:56:24 xubuntu NetworkManager[1167]: <info>  [1493650584.8325] device (wlp3s0): state change: unavailable -> disconnected (reason 'supplicant-available') [20 30 42]
May  1 14:56:24 xubuntu kernel: [   65.203407] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
May  1 14:56:25 xubuntu wpa_supplicant[1432]: wlp3s0: CTRL-EVENT-REGDOM-CHANGE init=BEACON_HINT type=UNKNOWN
May  1 14:56:25 xubuntu NetworkManager[1167]: <info>  [1493650585.8872] device (wlp3s0): supplicant interface state: ready -> inactive
xubuntu@xubuntu:~$ dmesg | grep wlp
[   63.117890] ath5k 0000:03:00.0 wlp3s0: renamed from wlan0
[   63.352130] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   63.379748] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[   65.203407] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
xubuntu@xubuntu:~$ cat /etc/default/crda | tail -n1
REGDOMAIN=
xubuntu@xubuntu:~$ sudo iw reg get
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)
xubuntu@xubuntu:~$ 

```

As usual I don't  understand nothing,maybe REGDOMAIN? Yestarday when I tried to fix the hour I introduced my country,but the hour is still 

wrong.You are the expert,plaese,help me.

Thank you

---

### Post by ubu112 on 2017-05-01
Unbelievably,I fund the way to connect myself wireless.Unfortunately with the internal card is slow and I can't use the Tp-Link.Instead with cable it seems to be fast.

With this lighter OS,the system seems to be faster(working with a live USB),more RAM available,that with Ubuntu I don't have.

Now I'll try it for few days.What do you,as experienced Ubuntu user, think about this?have you some advices to give me?

A question:if I say install it,it will erase everything,I mean it's like a fresh install?

Thank you,very much,chili555 and sorry if I disturbed you

---

### Post by chili555 on 2017-05-02
> .Unfortunately with the internal card is slow and I can't use the Tp-LinkWhy can't you use the TP Link? Did you try blacklisting the driver for the internal as I described above? After blacklisting and rebooting, doesn't the TP Link work as expected?> A question:if I say install it,it will erase everything,I mean it's like a fresh install?I'm not sure. You should probably ask here: [https://ubuntuforums.org/forumdisplay.php?f=333](https://ubuntuforums.org/forumdisplay.php?f=333) In any event, you can never go wrong if you have a good backup.

---

### Post by ubu112 on 2017-05-06
Sorry chili555,if I'm disturbing you,but you are the wireless expert.

I'm making experiments with few distros.

I don't understand why Ubuntu 16.04.2 use kernel 4.4..and Xubuntu,Lubuntu use kernel 4.8.

In this case,with kernel 4.8,can I always use the same commands for Tp-Link,I mean to blacklist the internal card,and to use ./speedtest-cli?

In iwconfig the bitrate is very low,it depends because I'm using a live USB?

Thank you

---

### Post by chili555 on 2017-05-07
> In this case,with kernel 4.8,can I always use the same commands for Tp-Link,I mean to blacklist the internal card,and to use ./speedtest-cli?
Yes.> In iwconfig the bitrate is very low,it depends because I'm using a live USB?
I wouldn't think so. Does it get higher as you walk a bit closer to the router or is it always low? The TP-Link ought to show 72.2 Mbps if you are relatively close to the router; I'd think 10 meters or so.

---

### Post by ubu112 on 2017-05-15
From your last post,I have always this doubt.But now I blacklisted and I'm using our beautiful Tp-Link,and I have almost always a bitrate 72,2 Mbps

First of all,I make all my test always about 2 meters from my router,the question is low bitrate what does it means?because when I'll decide which distro to use I'll have to use one of them.In other 

words,is it better to check if the bitrate is always low,before installing a distro?

Second,but important for me,I'm testing Xubuntu and Lubuntu 16.04.2 LTS,from my point of view the system is faster with both,connection speed is about 40 wireless(with Tp-Link,because with the internal 

was 15/16) and wired 60,sometimes 65 and I'm happy,do you agree?it's true that Lubuntu is lighter than Xubuntu,because it has less stuffs.

Now I'd like to have your opinion,someone had suggested to me to use the core version,but,from my point of view,it'd be fine for you or them,because you are expert.In my hands,it can create many 

problems.Can you,please,tell me which would be your choice for an inexperienced like me?

Thank you

---

### Post by vasa1 on 2017-05-16
> **ubu112 said:**
> ... someone had suggested to me to use the core version,but,from my point of view,it'd be fine for you or them,because you are expert...
Stay with the full version of whatever you choose for now. That's the safer route.

Once you feel more confident, you can try out core, minimal, and whatever else.

---

### Post by ubu112 on 2017-05-16
First of all,thank you "vasa1"for your kind answer.

But,you said:

> [COLOR=#000000]Once you feel more confident, you can try out core, minimal, and whatever else[/COLOR]

Am I wrong or the "core/minimal" version can't be tried from a live USB?I mean I can just install it?

What do you think about low bitrate?This was a question made from "chili555".

Thank you

---

### Post by chili555 on 2017-05-17
> the question is low bitrate what does it meansThe 72.2 Mbps reported in iwconfig is the rate that the device, the TP Link, in your case, is capable of in absolute laboratory conditions. The device sitting an inch or so from the perfect, finely-tuned router and with no interference on any other channel anywhere. We will almost never achieve that. In my case, with other wifi networks nearby, light dimmers, microwave ovens, remote controls, etc., and sitting about 9.5 meters from the router, I get about half of the rate shown in iwconfig.> connection speed is about 40 wireless(with Tp-Link,because with the internal was 15/16) and wired 60,sometimes 65 and I'm happy,do you agree?I agree. I'd be happy, too.> it's true that Lubuntu is lighter than Xubuntu,because it has less stuffs.
True. But that is only important if the computer you install on has a slow CPU, low memory, slow graphics, etc. that therefore compete with networking for resources.> Am I wrong or the "core/minimal" version can't be tried from a live USB?I mean I can just install it?The minimal version requires that you download packages as you install. It doesn't even work with every wireless device. I tried to find a list at one time, but could not. I agree that you should stick with the full version of either xubuntu or lubuntu, whichever you like best.

---

### Post by ubu112 on 2017-05-18
First of all,thank you for your kind answer that,as you know,is always important for me.

About low bitrate,I have to apologize with you,because I made a question in a wrong way.Now I try to explain myself better.

When I said low bitrate,I meant that,before blacklisting to use Tp-Link,I made iwconfig with Xubuntu and Lubuntu and one gave to me a bitrate of 1 Mb,and the other distro

11 Mb.It's true that I'll use Tp-Link,but I'd like to know if these low bitrate are important or not.

> [COLOR=#000000] But that is only important if the computer you install on has a slow CPU, low memory, slow graphics, etc[/COLOR]

I have Intel Atom N270 1,6 Ghz and  1 Gb of RAM,then I'd think that the better choice is to install Lubuntu.Do you agree with me?

But,to  be honest I don't see a big difference between Xubuntu and Lubuntu.I made a thread to understand how much memory is  used,but it doesn't seems to be easy.

Have you  advices to give to me,to make the right choice? 

Thank you

---

### Post by chili555 on 2017-05-18
> But,to be honest I don't see a big difference between Xubuntu and Lubuntu.I agree. They are both ideal for computers with limited processing power, video capability and low memory. Your Atom with 1 Gb of RAM is exactly that. I suggest that you install whichever you like the best from the standpoint of look and feel, menus, user interface, etc.>  I'd like to know if these low bitrate are important or not.I suspect that they are not important. However, it is easy to check and confirm. Run each in a live session and check here a few times with each and note the result: [http://beta.speedtest.net/](http://beta.speedtest.net/)    I doubt that you will see any significant difference.

---

### Post by ubu112 on 2017-05-18
Thank you again,for your answer.

> [COLOR=#000000] I suggest that you install whichever you like the best from the standpoint of look and feel, menus, user interface, etc.[/COLOR]

This mean that is Xubuntu 16.04.2 LTS.

> [COLOR=#000000]I doubt that you will see any significant difference.[/COLOR]

This is true,because I'm trying both distros with Tp-Link and I'm just using my ISP server or an other one.If the server is choosen from speedtest.net or ./speedtest-cli according to the ping test,I always 
 
have ups and down,like I had previuosly.But,this doesn't have nothing to do with the "low bitrate"I saw with iwconfig when I tried both distros with the internal card.

I have 2 questions:1)when I'll install the distro,can I leave it blacklisted? 2)Now I have just Firefox,that,as I said,is faster.Now,with the new distro, I'd like to install an other browser.Between Chromium or

the lightweight,like Midori or Xombrero etc.,which is the best?

Thank you

---

### Post by chili555 on 2017-05-18
> when I'll install the distro,can I leave it blacklisted? If you mean leave the driver for the internal device blacklisted, then yes, please.> I'd like to install an other browser.Between Chromium or the lightweight,like Midori or Xombrero etc.,which is the best?I have only tried Chromium and have no opinion as to the others. I do think Chromium is faster than Firefox.

---

### Post by ubu112 on 2017-06-14
After many text I choose the lightweight Lubuntu 16.04.

Usually I have about 40 Mbs wireless and 60+ wired.

Tonight I made few texts with Tp-Link and the speed was 15/16 Mbs.

It seems is working with the internal and not with Tp-Link.

How can I check if the internal is still blacklisted?

Thank you

---

### Post by chili555 on 2017-06-14
> How can I check if the internal is still blacklisted?Did the module load?```
lsmod | grep ath
```

---

### Post by ubu112 on 2017-06-15
> user@AOA150:~$ lsmod | grep ath
ath9k_htc              69632  0
ath9k_common           36864  1 ath9k_htc
ath9k_hw              462848  2 ath9k_htc,ath9k_common
ath5k                 139264  0
ath                    24576  4 ath9k_htc,ath9k_hw,ath5k,ath9k_common
mac80211              679936  2 ath9k_htc,ath5k
cfg80211              512000  5 ath9k_htc,mac80211,ath,ath5k,ath9k_common


Thank you

---

### Post by chili555 on 2017-06-15
> user@AOA150:~$ lsmod | grep ath
ath9k_htc 69632 0
ath9k_common 36864 1 ath9k_htc
ath9k_hw 462848 2 ath9k_htc,ath9k_common
[COLOR="#FF0000"]ath5k[/COLOR] 139264 0
ath 24576 4 ath9k_htc,ath9k_hw,ath5k,ath9k_common
mac80211 679936 2 ath9k_htc,ath5k
cfg80211 512000 5 ath9k_htc,mac80211,ath,ath5k,ath9k_commonSo, no, it isn't blacklisted. You will probably have better performance by using the internal or the USB but not both. If you want to use the USB, you will need to blacklist ath5k as I explained above.

---

### Post by ubu112 on 2017-06-15
Is this the right one to blacklist it again?

```

[COLOR=#000000][FONT=&amp]sudo -i[/FONT][/COLOR]
echo "blacklist ath5k"  >>  /etc/modprobe.d/blacklist.conf 
exit

```[COLOR=#000000][FONT=&amp]
[/FONT][/COLOR]
Why I suddenly lost "the blacklist"?

Thank you

---

### Post by chili555 on 2017-06-15
> Is this the right one to blacklist it again?

Code:
sudo -i
echo "blacklist ath5k"  >>  /etc/modprobe.d/blacklist.conf 
exitYes, exactly.> Why I suddenly lost "the blacklist"?
I assume that you reinstalled, no??> After many text I choose the lightweight Lubuntu 16.04.


---

### Post by ubu112 on 2017-06-15
No,I'm using Lubuntu at least by 2/3 weeks and,as I said,It worked perfectly.

Now I'm always around 40 Mbs with each server choosed by "beta.speedtest.net",just sometimes I have ups and down like before.

I'd like to know what do you think about: now when I use Firefox with beta.speedtest.net,is faster than Chromium.

The reason is that with Chromium it loads ads,with Firefox no.I was thinking to use "adblock" but honestly I don't like "extention".

Do you agree with me?

Thank you,very much,chili 555

---

### Post by chili555 on 2017-06-15
I believe both load ads. I haven't any explanation as I said way back in post #8. > As I said, I don't understand it either. I assume it has to do with flash vs. HTML5. In my case, Chromium is faster and more stable and so I use it. I don't have the time or patience to take Firefox apart to see what is wrong with it. My strong suspicion is that flash is most of what's wrong with it.Obviously, use whichever one you prefer.

---

### Post by ubu112 on 2018-05-19
@chili555,Hi,sorry if I'm disturbing you again.

I changed the OS and now I need to blacklist the internal and work only with the TP-LINK N150

```
user@AOA150:~$ iwconfig
enp2s0    no wireless extensions.

wlx18d6c70d5f00  IEEE 802.11  ESSID:"Vodafone-34344831"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 64:59:F8:E3:71:78   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:36   Missed beacon:0

wlp3s0    IEEE 802.11  ESSID:"Vodafone-34344831"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 64:59:F8:E3:71:78   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=44/70  Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:5  Invalid misc:38   Missed beacon:0

lo        no wireless extensions.

```

Can you,please,help me because I don't want to make mistakes.

Have I to do this?

```
[COLOR=#000000][FONT=&amp]sudo -i[/FONT][/COLOR]

echo "blacklist wlp3s0"  >>  /etc/modprobe.d/blacklist.conf 

exit
```
Thank you

---

### Post by chili555 on 2018-05-19
> Have I to do this?

Code:
sudo -i

echo "blacklist wlp3s0"  >>  /etc/modprobe.d/blacklist.conf 

exitNo, that's incorrect.

Please see post #100 above.

---

### Post by ubu112 on 2018-05-19
@chili555,have I to write always "blacklist ath5k"?

```
[COLOR=#000000][FONT=&amp]sudo -i[/FONT][/COLOR]

echo "blacklist ath5k"  >>  /etc/modprobe.d/blacklist.conf 
exit
```

Is this correct?

I was making a mistake,because in "iwconfig" I read wlp3s0.

I was right to ask to the expert.

Thank you

---

### Post by chili555 on 2018-05-19
blacklist.conf expects to see the driver of the device; not the interface created by the marriage of the physical device and the driver. In fact, the file itself says, in part:

```
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.
```Is the driver for your internal device still ath5k? Check:```
sudo lshw -C network
```What does 'driver=  ' report for the internal wireless?

Post back if you still have any concerns.

---

### Post by ubu112 on 2018-05-19
@chili555,unfortunately,I already blacklisted and now I have:

```
r@AOA150:~$ iwconfig
enp2s0    no wireless extensions.

wlx18d6c70d5f00  IEEE 802.11  ESSID:"Vodafone-34344831"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 64:59:F8:E3:71:78   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:367   Missed beacon:0

lo        no wireless extensions.


```
Does that mean it was the same?

Is this correct? or,have I to do something else?

Thank you

---

### Post by chili555 on 2018-05-19
Looks like you are all set!

---

### Post by ubu112 on 2018-05-28
@chilli555,thank you for you help,now everything seems working well.

Now,I read this: [https://wiki.ubuntu.com/BasicSecurity/Firewall](https://wiki.ubuntu.com/BasicSecurity/Firewall) and much more about security.

I'd like to have your opinion,considering I'm using an old and weak computer, if it's the case to enable or install a firewall.That I've never used.

If,yes, will a firewall  slow down my connection speed that is only 40+ (wireless)?

Which of the three solutions,described in the link above,would your recommend to me?

Thank you

---

### Post by chili555 on 2018-05-29
> **ubu112 said:**
> @chilli555,thank you for you help,now everything seems working well.

Now,I read this: [https://wiki.ubuntu.com/BasicSecurity/Firewall](https://wiki.ubuntu.com/BasicSecurity/Firewall) and much more about security.

I'd like to have your opinion,considering I'm using an old and weak computer, if it's the case to enable or install a firewall.That I've never used.

If,yes, will a firewall  slow down my connection speed that is only 40+ (wireless)?

Which of the three solutions,described in the link above,would your recommend to me?

Thank youThese are great questions for the experts over on General: [https://ubuntuforums.org/forumdisplay.php?f=331](https://ubuntuforums.org/forumdisplay.php?f=331) I am familiar with networking and, especially wireless, and not much else. 

I'm sure they will be able to help.

---

