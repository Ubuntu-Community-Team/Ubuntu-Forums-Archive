---
title: "Netgear WG311V3 Wireless: How?"
date: 2006-12-08
forum: Networking &amp; Wireless
---

### Post by johann_p on 2006-12-08
I installed a Netgear WG311V3 wireless lan card in my computer (running WindowsXP/Ubuntu Edgy dual boot). Works fine in Windows, but nothing whatsoever happened in Ubuntu (until now that computer was attached to a ethernet cable, but since it needs to get moved, I need it to work over wireless). 

I was hoping that Ubuntu would tell me about new hardware or something but nothing happened. How can I get this to work??

---

### Post by endersshadow on 2006-12-08
According to [this thread](http://ubuntuforums.org/showthread.php?t=290798), you'll need to use ndiswrapper.  Luckily, that's not too hard.  Really, it's not!

[list=1]
[*] Download [this file](http://www.jimbo7.com/wiki/files/good_WG311v3-driver.tgz) and save it to your home directory.

[*] Open up a terminal and type:
```
mkdir drivers/
mv good_WG311v3-driver.tgz drivers/
cd drivers/
tar xzf good_WG311v3-driver.tgz
sudo apt-get install ndiswrapper-utils-1.8
sudo ndiswrapper-1.8 -i ~/drivers/WG311v3.INF
sudo ndiswrapper-1.8 -m
sudo modprobe ndiswrapper

```

[*] You should be all set, so it's now time to see your wireless card:
```
iwconfig
```
My iwconfig returns this (note, I'm wired right now):
```
eric@homesteadgrays:~/Desktop$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:16 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
Notice how my wireless card is eth1.  Yours may be eth1 or wlan0, depending.  Assuming that it's eth1...

[*] Time to point your card to the right access point:
```
sudo iwconfig eth1 essid "SSID goes here" key s:password
```
Note: If you know your key in hex digits, omit the s:--it's there to provide for an ASCII key.

[*] Next, we need to make your card active:
```
sudo ifup eth1
```

[*] If you don't have a connection, post back here with the results of iwconfig and ifconfig, as well as any error messages you received.  You may also try:
```
sudo dhclient
```
[/list]

---

### Post by johann_p on 2006-12-08
```
sudo modprobe ndiswrapper
```This produces: 
```
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

```

I ignored this since ndiswrapper seems to be loaded already.

I see an entry wlan with iwconfig:
```

wlan0     IEEE 802.11FH  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Sensitivity=-200 dBm  
          RTS thr:2346 B   Fragment thr:2346 B   
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
However, this does not work
```
iwconfig wlan0 essid "xxxx" key s:passphrase
```

It returns the following error: " SET failed on device wlan0 ; Invalid argument."

When I try which parameter is responsible, it seems I can set the essid, but not the key.
[FONT=monospace]
[/FONT]

---

### Post by endersshadow on 2006-12-08
What's the return of these commands?

```
sudo modinfo ndiswrapper
sudo modprobe -vn --first-time ndiswrapper
```

---

### Post by FrodoB on 2006-12-08
Check the output of lspci, I believe that this is a Marvell 88w8335 device:

user@ubuntu:~$ lspci

Your output from lspci should contain a line very much like this:  

0X:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 03)


if so use this instruction:

[https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29]("https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3aB1_%28ndiswrapper%29?highlight=%28WifiDocs%2FDevice%29")

---

### Post by johann_p on 2006-12-08
I have done everything except the manual compile of ndiswrapper. Is this really necessary (the one that is installed now is version 1.22).

When I run "ifup wlan0" I get:
```

Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Invalid argument.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Invalid argument.

```

---

### Post by FrodoB on 2006-12-08
Yes, I suspect that that will resolve your issue.  But make sure that you get all of the existing copies of ndiswrapper removed before making the new one.

---

### Post by FrodoB on 2006-12-08
In fact if you do not have a lot of personal data on the machine, just reinstall and then follow the directions. You will need wired ethernet access to do the task.

---

### Post by johann_p on 2006-12-08
No luck so far.

Successfully installed ndiswrapper 1.31 but the same error as before -- cannot set a WPA passphrase.

---

### Post by endersshadow on 2006-12-08
Don't reinstall...there's a fix.  Just posting because I didn't want you to do anything drastic, but I'm gonna find you the solution, cause I know it exists. Bear with me.

---

### Post by FrodoB on 2006-12-08
DId you use the TRENDnet drivers recommended in the instruction rather than the ones that came with your device? If not use them instead. 

I don't recall your mentioning a problem that dealt with WPA.

---

### Post by endersshadow on 2006-12-08
Okay. iwconfig doesn't allow WPA passphrases, only WEP.  I couldn't remember how to set them up, so I had to look it up, which explains the delay.

Anyway, here's how you make WPA goodness:

```
sudo apt-get install wpa-supplicant
sudo gedit /etc/wpa_supplicant.conf
```

In that, post this (replacing necessary parts):

```
network={ 
	ssid="SSID_goes_here" 
	psk="password_goes_here" 
	priority=5 
	key_mgmt=WPA-PSK
	proto=WPA
}
```

Save and close.  In the terminal:

```
sudo chmod 600 /etc/wpa_supplicant.conf
sudo wpa_supplicant -i wlan0 -c /etc/wpa_supplicant.conf -Dndiswrapper
sudo ifup wlan1
```

You should now be assigned an IP on the network.

Good luck. [Source](http://www.jimbo7.com/wiki/index.php?title=WG311v3).

---

### Post by FrodoB on 2006-12-08
__endersshadow;

Very nice information, a lot of folks can use it.

---

### Post by johann_p on 2006-12-08
Getting closer, but still no luck: 
I created the /etc/wpa_supplicant.conf file with the information about ssid, passphrase etc.

Then the command "wpa_supplicant -Dndiswrapper -iwlan0 -c/etc/wpa_supplicant.conf" results in:
```

Trying to associate with 00:09:5b:c1:68:f8 (SSID='myssid' freq=2462 MHz)
Association request to the driver failed
Authentication with 00:00:00:00:00:00 timed out.
Trying to associate with 00:09:5b:c1:68:f8 (SSID='myssid' freq=2462 MHz)
Association request to the driver failed

```In the referenced wiki, they talk about using the wext driver. When I try this:
```

Trying to associate with 00:09:5b:c1:68:f8 (SSID='myssid' freq=2462 MHz)
Associated with 00:09:5b:c1:68:f8
WPA: 4-Way Handshake failed - pre-shared key may be incorrect
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Associated with 00:09:5b:c1:68:f8
WPA: 4-Way Handshake failed - pre-shared key may be incorrect
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys

```I tried this with the driver from good_WG311v3-driver.tgz and with the Windows2000 driver from TEW-421PC_b1\Driver\Utility_Driver_TEW-421PC_423PI_b1_2.00.zip and got the same results with both.

---

### Post by FrodoB on 2006-12-08
You may want to remove all security at this point just to prove to yourself that the card and ndiswrapper are working for you as you expect.

Then after it connects with no security start working on adding that in.

---

### Post by johann_p on 2006-12-08
Ugh. Somehow the version with driver wext seems to get a step further because it seems to associate with the correct wlan router. 

Removing security sounds like a real hassle and is not really an option since a lot of other computers (running WindowsXP and working fine with the WPA key) are on the same network. They would all have to be reconfigured ... not to speak of the security problem this would open up. 

:(

---

### Post by endersshadow on 2006-12-08
I don't know what type of WPA you're using, but [here are the variant configurations](http://www.die.net/doc/linux/man/man5/wpa_supplicant.conf.5.html) for wpa-supplicant.

I noticed something on that site. Try this config:

```
network={ 
	ssid="SSID_goes_here" 
	scan_ssid=1
	key_mgmt=WPA-PSK
	psk="password_goes_here" 
}
```

---

### Post by johann_p on 2006-12-08
I am using WPA-PSK
I have read the documentation about wpa_supplicant and tried practically all options. I have added "pairwise=TKIP" etc and I have specified the psk in hex using wpa_passphrase. I have checked the passphrase itself a dozen times. No luck.

My frustration is big enough to give up now, really. I'll probably go back to WindowsXP when I have to move the computer. Maybe I will at some point buy a new Wlan card that is sure to work without ndiswrapper (I do not like that concept at all) and that is sure to work with WPA-PSK.

---

### Post by endersshadow on 2006-12-08
As a last ditch effort, try using the Qt GUI for it:

```
sudo apt-get install wpagui
wpa_gui &
```

---

### Post by FrodoB on 2006-12-08
Don't give up so easily. WPA-PSK can work well in ndiswrapper. There have been several posts on this subject in the forum in the past week.

See:

[http://ubuntuforums.org/search.php?searchid=10894907](http://ubuntuforums.org/search.php?searchid=10894907)

---

### Post by FrodoB on 2006-12-08
This is the one that lots of folks seem to like:

[http://www.ubuntuforums.org/showthread.php?t=263136](http://www.ubuntuforums.org/showthread.php?t=263136)

---

### Post by johann_p on 2006-12-09
Thank you everyone for your kind and patient help! 

Do not take it personally, but after spending hours and hours trying to get this to run, I am just frustrated. I do not want this to somehow work after lots of tweaking and compiling. I want this to *just work* like much everything else. If it is necessary to change my hardware, I would be prepared to spend the money -- I would earn a lot more money in the time I waste to unsuccessfully get this card to work anyways. 

So I have created this thread: [http://ubuntuforums.org/showthread.php?t=315417](http://ubuntuforums.org/showthread.php?t=315417) in order to get suggestions of what I can put in my computer that *is guaranteed* to work. Without the hassle.

I'd like to buy some product that has a supported linux driver, so that I can go back to the store and give the card back if it does not work under Ubuntu. As nice it is to get the help of well-meaning individuals, I want a card where it is *my right*, not just a favor, to have it run under Linux. Where it does not depend on me, but on the manufaturer of the card and on the creators of Ubuntu whether it works or not.

So: what card would I have to buy for this?

---

### Post by bruble on 2007-08-16
All
Having spent a while with trying to sort this out thought my experience may assist.
I am using Feisty Fawn 7.04 on an old 686 machine.
I have a WG311v3 wireless card and tried to get WPA to work. Eventually I have had success.

I had to install NDISWRAPPER and used the latest NDISWRAPPER although the one NDISWRAPPER has tested with the WG311v3 is v 1.5 I am on the very latest version now.

I then had to install WPA supplicant and then spent a while trying to get it to work. I kept getting the 4 Way Handshake error.
I used WICD but while this would connect at boot (sometimes) it would only connect at boot sometimes and if not connected at boot could not be made to connect after so constant rebooting. 
Managed to find the PSK that is generated, /opt/wicd/data/wireless-config. (Only retrieve this PSK when WICD has established a link to your access point.

I then found that the wpa_supplicant generated psk is different to the one that WICD actually has as the PSK when it connects.
I swapped this in as the psk in the /etc/wpa_supplicant.conf and tried using the wireless tools iwconfig, ifconfig ifup and ifdown etc. This worked a treat.

The 4 way handshake error indicates your generated psk is incorrect. WICD will generate the correct one.

---

