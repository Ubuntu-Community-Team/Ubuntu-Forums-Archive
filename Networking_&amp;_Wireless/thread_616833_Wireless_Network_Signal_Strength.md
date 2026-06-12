---
title: "Wireless Network Signal Strength"
date: 2007-11-18
forum: Networking &amp; Wireless
---

### Post by davers007 on 2007-11-18
I am using a brand new install of Gutsy on an IBM Thinkpad x60. lspci gives the following info about the wireless card:
```
03:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
```
My wireless card worked out of the box, and the signal strength meter also works correctly. My question regards the signal strength compared to that in Windows.

In my current living situation, the desk in my bedroom has about two walls, a door, and me between it and the wireless router. In Windows, I routinely get two or three out of five bars for signal strength but generally get 200-300kb/s download speed on a good connection no matter if I am in my room or right next to the router.

In Ubuntu, however, I get about 300kb/s when I put the laptop directly next to the router and essentially no signal (one bar, if that) when in my bedroom. Ubuntu seems to be _very_ sensitive to the computer's location relative to the router, but Windows does not share this sensitivity. This leads me to believe that the computer is capable of getting a better signal strength when in my room and running Ubuntu if I can change something.

Has anyone seen this phenomenon before or have ideas about how to achieve the same signal strength as in Windows? Thanks for your time.

David

---

### Post by nosh on 2007-11-18
Huh, I had the opposite effect when I installed xubuntu on my laptop:  suddenly my wireless card could pick up stronger signals than when on windows.  I have no idea what causes it but I have an HP pavilion dv1000.  weeiiiiirrrrd.

---

### Post by moe_syzlak on 2007-11-18
Do you also have the signal up technology, where the antenna is wired through your monitor (for better reception)?

---

### Post by Strangerdave on 2007-11-18
I too have this problem.  In windows I get five bars, but in Ubuntu I only get two.  Download speeds range, but the router is located directly below me, in the basement, with only wood separating me and the wireless router.  

I have used both network manager and wcid and the same thing occurred.  It seems that bars highlighted do not represent actual connection speeds and strength.

I have just ignored it since I get good download speeds.

-SD-

---

### Post by davers007 on 2007-11-19
My bars _do_ represent correct signal quality both in Windows and Ubuntu, but the degradation of download speed with distance from the router and interfering objects is faster in Ubuntu.

For example: if I am next to the router I get 5 bars in Windows and Ubuntu with 300kb/s download speed. If I move into my room, the Windows signal drops to 2-3 bars and about 150-200kb/s. The Ubuntu signal drops to 0-2 bars and about 30kb/s, if I can connect at all. It would be a non-issue for me if it showed 0-2 bars but I got the same download speed as in Windows.

As for SignalUp technology with the antenna through the monitor, I have only heard or seen of that in Acer's computers. I do have a little black thing on the top right side of my monitor, but I assumed that was for the built-in Sierra Wireless 1xEV-DO Network Adapter for connecting to Verizon's wireless network, which I obviously don't use since I live in Germany.

---

### Post by Arrakiv on 2007-11-22
I have the same issue as well. I'm actually running windows at the moment simply because I don't trust my connection to be stable enough in the room I'm currently in with my laptop under linux.

I have noticed in wifi-radar that the signal strength for the router tends to go up and down quite a bit as well. From 0 - 3 bars rather sporadically.

---

### Post by Whiffle on 2007-11-22
My thinkpad t43 has the antennas (there are two), in the screen, one mounted horizontally and one vertically.  Good reception says I. 

Anyway, you're not quite comparing apples to apples here.  there are different power and sensitivity settings that may be set differently in the two os's.  Try doing:

iwconfig

and post the results here.  It will show us what you've got for your sensitivity and txpower settings.  I was having trouble connecting where I am right now to an ap way far away, I upped the txpower and the sensitivity and now have a much better connection.

---

### Post by davers007 on 2007-11-22
Hello everyone, thanks for the responses. Here's my iwconfig:
```
ath0      IEEE 802.11g  ESSID:"Lothlorien"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:11:6B:26:74:7A   
          Bit Rate:6 Mb/s   Tx-Power:8 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=38/70  Signal level=-60 dBm  Noise level=-98 dBm
          Rx invalid nwid:3730  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

---

### Post by Arrakiv on 2007-11-22
Just an update for me...

I disabled the Network Manager as a Startup Program under System-> Preferences-> Sessions after I noticed the possible fix in another thread. After this, I tried using wifi-radar to connect instead. I've noticed my download speed seems to have picked up and I'm seeing more bars than I was before.

I'm a bit surprised that managed to fix anything, but hopefully it can help some others as well.

---

### Post by str8line on 2007-11-30
Question for you, the 200-300 kbps is that a computer to computer transfer or a download from the internet?

The reason that I ask is that currently the standard for most broadband internet connections in North America is far lower than the 54Mbps advertised by 802.11 network cards.  Typical downloads on a 3Meg connection from broadband providers such as Verizon and Comcast would translate to 2-300 Kbps.

---

### Post by davers007 on 2007-11-30
200-300 is a download from the Internet. I'm also not in North America, I'm in Germany. I don't know if that changes anything. Regardless, the signal strength is still too weak in my room when using Ubuntu, but works great with Windows.

---

