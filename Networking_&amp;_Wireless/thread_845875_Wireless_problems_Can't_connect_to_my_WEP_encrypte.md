---
title: "Wireless problems: Can't connect to my WEP encrypted network"
date: 2008-07-01
forum: Networking &amp; Wireless
---

### Post by ayzwah on 2008-07-01
Hello, I just installed Ubuntu, and also finally configured ndiswrapper with my WUSB11v4 to work correctly after days of frustration. 

Now, I can't seem to connect to my home network, which is encrypted by a WEP key. I did some trial-and-error tests and when I add "iface wlan0 inet dhcp" to /etc/network/interfaces, the wireless networks don't show when you click the networks icon on the taskbar. 
The only thing that I see when clicking the network icon when I add that line is Wired network and Manual Configuration. 
Does anyone have any tips to fix this? Specifically, how should my interfaces file look? I'm not sure about all of this dhcp, static ip stuff, but does it have something to do with that?

Also, I AM ABLE to connect to other networks that are NOT encrypted by a WEP key.

---

### Post by ayzwah on 2008-07-01
Bump, any help is appreciated

---

### Post by ayzwah on 2008-07-02
Bump. Someone PLEASE help, 
Thank you.

---

### Post by untermensch on 2008-07-02
What wireless card do you have? 

can you show the output of iwconfig ?

---

### Post by untermensch on 2008-07-02
Are you sure you got the password right? also when you go to connect to the AP are you sure the encryption is right ? it will give you several options and sometimes the default is not correct.

---

### Post by ayzwah on 2008-07-02
My wireless card is a Linksys WUSB11 version 4

Output of iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:off/any  Nickname:""
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan1_rename  IEEE 802.11b  ESSID:"network"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:14:BF:32:B1:B0   
          Bit Rate=11 Mb/s   
          RTS thr=2432 B   Fragment thr=2432 B   
          Power Management:off
          Link Quality:40/100  Signal level:-70 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
Not sure what wlan1_rename is??? Before, I'm pretty sure it was connecting through wlan0. Hmm..interesting

Yes I'm pretty sure the WEP key is correct. 
And, by the encryption do you mean the options it gives that include: DHCP, Zero configuration, Static IP, etc etc? Sorry, i'm a newbie don't really understand all the terms. If so, I tried all of them in interface and none of them work. 

Also, as I mentioned in the first post. The thing that is weird is that when I edit the /etc/network/interfaces file to include ""iface wlan0 inet dhcp", the wireless networks do not show up when i click the network icon, but reappear when i delete that line.

---

### Post by untermensch on 2008-07-02
If it is encrypted than when you try to connect to the wireless network a window will pop up asking for the key. above where you put the key you will see a scroll down bar of types of encryption, if that isn't set right it not work correctly.

---

### Post by untermensch on 2008-07-02
> **ayzwah said:**
> 
  
Also, as I mentioned in the first post. The thing that is weird is that when I edit the /etc/network/interfaces file to include ""iface wlan0 inet dhcp", the wireless networks do not show up when i click the network icon, but reappear when i delete that line.

Then I would recommend leaving that line out =p

---

### Post by rlzyoner on 2008-07-02
You could try connecting manually.
Open a terminal and type the following

sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "ESSID_HERE"
sudo iwconfig wlan0 key HEX_KEY 
sudo iwconfig wlan0 key open  
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

Follow exactly where there are and aren't quotes

I'm assuming wlan0 is the name of your wireless adaptor, change if necessary

---

### Post by ayzwah on 2008-07-02
```
Then I would recommend leaving that line out =p 
```
:) Yes, but after reading about wireless on linux, everywhere it says to add that line to connect to networks, so I thought it was kind of weird. 
> **untermensch said:**
> If it is encrypted than when you try to connect to the wireless network a window will pop up asking for the key. above where you put the key you will see a scroll down bar of types of encryption, if that isn't set right it not work correctly.

Yes, is there any way to verify which option I need to choose? But, I tried each one of them, and none of them work. Also, I am sure that the WEP key I am using is correct.

When I connect to my network, sometimes it shows when i mouse the network icon the percent of the connection. So, it appears that it is connected, but when I try to go to websites it does not work (Firefox is in online mode, not offline), and when I do the ping tests in network manager, it also DOES NOT work. 

Thanks for the help.

---

### Post by untermensch on 2008-07-02
So you are connected to the network, just not receiving packets?

---

### Post by ayzwah on 2008-07-03
> **untermensch said:**
> So you are connected to the network, just not receiving packets?
Correct.

---

### Post by untermensch on 2008-07-03
unplug your modem, then unplug your router. leave them both off for twenty seconds. if that doesn't work unplug them both and hold down the restart button for twenty seconds.

---

### Post by ayzwah on 2008-07-04
Actually, when it asks for my encryption type, it does not have an option for WEP 64 bit encryption which is what mine is. It only has WEP 128 bit, LEAP, WEP 64/128 bit HEX and WEP 64/128 bit ASCII. Is there any way to fix that?

---

### Post by chili555 on 2008-07-04
> WEP 64 bit encryption which is what mine is.It wants your key in WEP 64/128 bit HEX if it's a 10-character key.

---

### Post by ayzwah on 2008-07-04
> **chili555 said:**
> It wants your key in WEP 64/128 bit HEX if it's a 10-character key.

Oh, Ok, that's what I was trying. Strange that its not working.

---

