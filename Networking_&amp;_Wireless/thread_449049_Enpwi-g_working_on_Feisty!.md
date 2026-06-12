---
title: "Enpwi-g working on Feisty!"
date: 2007-05-19
forum: Networking &amp; Wireless
---

### Post by macabro22 on 2007-05-19
Alright fellow Ubuntuers!

I finally got my Encore electronics ENPWI-G PCMIA wi-fi card working!

After upgrading from Edgy-Eft I couldn't connect anylonger. So I installed ndiswrapper and loaded the windows driver found at the manufacturer's web site:

```
ndiswrapper -i mrv8000c.inf
modprobe ndiswrapper
ndiswrapper -m
```

The card's LED's lit up and I was happy. I then could detect available networks but not connect to them. :P

The solution found was to input the following at terminal:

```
iwlist wlan0 scan
```

Then I got two wireless networks in range:

```
Cell 01 - Address: 00:11:95:53:63:4F
                    ESSID:"caifora"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:28/100  Signal level:-78 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
          Cell 02 - Address: 00:17:9A:69:E3:A9
                    ESSID:"default"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:6/100  Signal level:-92 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

```

'caifora' is the name of the networtk my router is broadcasting which for some obscure I couldn't connect to.

From there I got the address 00:11:95:53:63:4F. 

If somehow I could make my card associate with it...

So I issued:

```
sudo iwconfig wlan0 ap 00:11:95:53:63:4F
```

Bingo! Anyone can do the same by inputing HIS router address in place of mine.

---

### Post by printarg on 2007-06-19
I tried that and got no error message but I cannot ping anything including my router!!

iwconfig says:

wlan0     IEEE 802.11b  ESSID:Off/any 
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated  
          Bit Rate=1 Mb/s   Sensitivity=-200 dBm 
          RTS thr=2346 B   Fragment thr=2346 B  
          Power Management:Off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

What do I do now??

---

### Post by macabro22 on 2007-07-01
whats the output of

```
iwlist wlan0 scan
```?

---

### Post by LuiFer on 2007-07-19
Hi!!

I'm using Ubuntu 7.04, installed on a Compaq EVO N610c (1024MB RAM, 40GB HDD and so on). I have an Encore ENPWI-G card, and I try to make it work following this post.

However, the only think I'm able to do is install the driver. i can't go further. When I run the command: iwlist wlan0 scan, I get the follow message:

luifer@luifer-u:~/ENPWI-G/V1.10/DRIVER/Windows XP$ iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

Even more, when I run the command modprobe, I don't get any message.

Any idea?

Thanks in advance

---

### Post by LuiFer on 2007-07-20
Hi, all

Just to let you know: it's working. All I need to do is a true reset (shutdown, then turn on), and thats all. Now I'm working in the air =)

Regards,

---

### Post by u-blunt-2 on 2008-01-16
ANyone get this chipset working on 64-bit distro ?

---

