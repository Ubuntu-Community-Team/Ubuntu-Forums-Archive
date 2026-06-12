---
title: "No wireless HELP!"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by benjamonk on 2009-12-02
Hello

I have just installed Ubuntu for the first time on an ageing Sony Vaio laptop (PCG-QR20). I did this because windows was just so and clunky on it.

Problem is I now can't connect to my wireless network - Wireless Card is a Belkin F507010 network card. Worked on windows but now the power led indicator doesn't even illuminate.

Never used ubuntu before, searched these forums and found some tech stuff to do with wireless cards which seemed a bit beyonf me at this stage! 

Any pointers?

Many thanks,

B

---

### Post by fooman on 2009-12-02
not sure what chipset is in that wireless adapter...open a terminal (applications > accessories > terminal) and type the following:

```
lspci
```then press enter.  post the output back here and we will see how to help you.

also post the output of this command as well:

```
 iwconfig
```

---

### Post by benjamonk on 2009-12-02
[QUOTE=fooman;8426245]not sure what chipset is in that wireless adapter...open a terminal (applications > accessories > terminal) and type the following:

OK - The first problem I have is that when I open a terminal, I just get a blank white screen!????

---

### Post by benjamonk on 2009-12-02
> **fooman said:**
> not sure what chipset is in that wireless adapter...open a terminal (applications > accessories > terminal) and type the following:

```
lspci
```then press enter.  post the output back here and we will see how to help you.

also post the output of this command as well:

```
 iwconfig
```

OK fixed my white screen issue by fiddling with display effects.

lspci outputs:
ben@Ubuntu-Bag:~$ lspci
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 11)
00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 11)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 Controller (rev 03)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 03)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 03)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 03)
01:00.0 FireWire (IEEE 1394): Texas Instruments TSB43AA22 IEEE-1394 Controller (PHY/Link Integrated) (rev 02)
01:02.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)
01:02.1 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 80)
01:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
02:00.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
ben@Ubuntu-Bag:~$ 

and iwconfig outputs:
ben@Ubuntu-Bag:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Thanks for offering to help!!

---

### Post by bkratz on 2009-12-02
since your card uses the B43 drivers, this will probably work for you.

[http://ubuntuforums.org/showpost.php?p=8399211&postcount=31](http://ubuntuforums.org/showpost.php?p=8399211&postcount=31)

Good Luck

---

### Post by ukripper on 2009-12-02
If you are using ubuntu 9.10, follow this :

**[SIZE="3"]Method 1[/SIZE]** try this:

```
sudo apt-get install bcmwl-kernel-source
```

unplug any wired ethernet cable so you can use wireless.

Reboot and see if it comes up. If it doesn't work then follow method 2



**_Method2:_**
in terminal :

```
sudo apt-get install linux-backports-modules-karmic b43-fwcutter
```

3. Blacklist the ssb module.
```
echo "blacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist-ssb.conf
```

4. Blacklist the wl module.
```
echo "blacklist wl" | sudo tee -a /etc/modprobe.d/blacklist-wl.conf
```
5. Reboot and unplug any wired ethernet cable so you can use wireless.

Now after login see if your wireless comes up

---

### Post by benjamonk on 2009-12-02
> **ukripper said:**
> If you are using ubuntu 9.10, follow this :

**[SIZE="3"]Method 1[/SIZE]** try this:

```
sudo apt-get install bcmwl-kernel-source
```

unplug any wired ethernet cable so you can use wireless.

Reboot and see if it comes up. If it doesn't work then follow method 2



**_Method2:_**
in terminal :

```
sudo apt-get install linux-backports-modules-karmic b43-fwcutter
```

3. Blacklist the ssb module.
```
echo "blacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist-ssb.conf
```

4. Blacklist the wl module.
```
echo "blacklist wl" | sudo tee -a /etc/modprobe.d/blacklist-wl.conf
```
5. Reboot and unplug any wired ethernet cable so you can use wireless.

Now after login see if your wireless comes up

I tried both methods - still no joy i'm afraid :-(

---

### Post by halitech on 2009-12-02
> **benjamonk said:**
> 
ben@Ubuntu-Bag:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

Thanks for offering to help!!

this looks to me like its already seeing the card but just not connecting. Do you have broadcasting SSID turned off? Try
```
sudo iwlist scan
```

---

### Post by linux6994 on 2009-12-02
I was so frustrated with Karmic that I installed Linux Mint which is Karmic based and all is fine.The b43-fwcutter is working well in it.

---

