---
title: "Connecting to the internet with the Belkin F5D6050"
date: 2006-12-08
forum: Networking &amp; Wireless
---

### Post by JSnake on 2006-12-08
I seem to have trouble connecting with the above wireless adapter. I have it connected to a Linksys router (I'm not sure of the model...). I set up the IP address and everything, but then I forgot the drivers. I tried googling for the drivers, but I didn't find anything.

Could someone help me?

---

### Post by FrodoB on 2006-12-08
If you are referring to the NDIS drivers for use with ndiswrapper then see:

[http://web.belkin.com/support/download/download.asp?download=F5D6050&lang=1&mode=](http://web.belkin.com/support/download/download.asp?download=F5D6050&lang=1&mode=)

otherwise please elaborate.

---

### Post by FrodoB on 2006-12-08
Also have you just inserted the device and ran iwconfig to see if it is recognized?

Publish the output of lsusb please.

---

### Post by JSnake on 2006-12-08
> **FrodoB said:**
> Also have you just inserted the device and ran iwconfig to see if it is recognized?

Publish the output of lsusb please.

Do I just type "iwconfig" in the terminal? I'm a Linux newbie.:-#

---

### Post by FrodoB on 2006-12-08
Sorry, you just need to type both commands into a terminal:

lsusb


iwconfig

---

### Post by JSnake on 2006-12-08
> **FrodoB said:**
> Sorry, you just need to type both commands into a terminal:

lsusb


iwconfig

How would I go about pasting the output if I need to keep booting back and forth?

---

### Post by FrodoB on 2006-12-08
Sorry, I guess you cannot.  the important thing is do you see something similar to this from iwconfig: wlan, or eth1, or some other device name

wlan0     IEEE 802.11b  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00   
          Bit Rate:11 Mb/s   Sensitivity=-200 dBm  
          RTS thr:2346 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:60/100  Signal level:-57 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


And what is a an output of lsusb for a different Belkin device:

Bus 001 Device 021: ID 050d:705c Belkin Components 

Write down the number just after ID:

 050d:705c

That will help to determine what kind of wireless chipset you device actually has.

---

### Post by JSnake on 2006-12-08
> **FrodoB said:**
> Sorry, I guess you cannot.  the important thing is do you see something similar to this from iwconfig: wlan, or eth1, or some other device name

wlan0     IEEE 802.11b  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00   
          Bit Rate:11 Mb/s   Sensitivity=-200 dBm  
          RTS thr:2346 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:60/100  Signal level:-57 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


And what is a an output of lsusb for a different Belkin device:

Bus 001 Device 021: ID 050d:705c Belkin Components 

Write down the number just after ID:

 050d:705c

That will help to determine what kind of wireless chipset you device actually has.

1) Yes.
2) My adapter has the Atmel at76c503 chipset.

---

### Post by FrodoB on 2006-12-08
You are a lucky person, that card is supported in Dapper and Edgy without adding anything.  Just configure it in the GUI tool:

See these instructions which were made for Dapper, Edgy is similar:
[https://help.ubuntu.com/community/WifiDocs/WirelessNetworking](https://help.ubuntu.com/community/WifiDocs/WirelessNetworking)

Setting up WEP is easy, if you want WPA then you can search the forum for instructions.

---

### Post by JSnake on 2006-12-08
> **FrodoB said:**
> You are a lucky person, that card is supported in Dapper and Edgy without adding anything.  Just configure it in the GUI tool:

See these instructions which were made for Dapper, Edgy is similar:
[https://help.ubuntu.com/community/WifiDocs/WirelessNetworking](https://help.ubuntu.com/community/WifiDocs/WirelessNetworking)

Setting up WEP is easy, if you want WPA then you can search the forum for instructions.

Yeah, I already have it set up like that. Not working.

---

### Post by FrodoB on 2006-12-08
Well it is hard to say without details, but the WEP key is usually the issue at this point. What do you have in your /etc/interfaces file? Can you get a copy of it on a floppy, usb drive or something to present it here on line?

---

### Post by JSnake on 2006-12-08
> **FrodoB said:**
> Well it is hard to say without details, but the WEP key is usually the issue at this point. What do you have in your /etc/interfaces file? Can you get a copy of it on a floppy, usb drive or something to present it here on line?

I never use WEP.

And no, since I don't have either of those.

---

### Post by FrodoB on 2006-12-08
So are you going to say if you use WPA-PSK, or nothing, or any further details?

---

### Post by JSnake on 2006-12-08
> **FrodoB said:**
> So are you going to say if you use WPA-PSK, or nothing, or any further details?

I don't use any encryption. 
I'm sorry. I've never used Linux before, so I don't know what kinda details to give. :(

---

### Post by FrodoB on 2006-12-08
So did you output from iwconfig look somewhat similar to mine?

Your interfaces file (/etc/network/interfaces) should look kind if like this:

iface wlan0 inet dhcp
wireless-essid MY_NETWORK
auto wlan0

Take a look at iwlist, which should show your network access point:

user@Edgy:~$ iwlist wlan0 scanning
wlan0     Scan completed :
          Cell 01 - Address: 00:12:19:B1:3E:4D
                    ESSID:"MY_NETWORK"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:53/100  Signal level:-62 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


You are using Ubuntu 6.10 Edgy Eft, correct?

---

### Post by JSnake on 2006-12-08
> **FrodoB said:**
> So did you output from iwconfig look somewhat similar to mine?

Your interfaces file (/etc/network/interfaces) should look kind if like this:

iface wlan0 inet dhcp
wireless-essid MY_NETWORK
auto wlan0

Take a look at iwlist, which should show your network access point:

user@Edgy:~$ iwlist wlan0 scanning
wlan0     Scan completed :
          Cell 01 - Address: 00:12:19:B1:3E:4D
                    ESSID:"MY_NETWORK"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:53/100  Signal level:-62 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0


You are using Ubuntu 6.10 Edgy Eft, correct?

Yes, everything looks as you say. And I am using 6.10.

---

### Post by FrodoB on 2006-12-08
At a command prompt type:

sudo iwconfig wlan0 essid my_network

This examples assumes that:

wlan0 - is your wireless device

my_network - is you access point's network name

then type iwconfig and see if your access points MAC address is listed in the output of iwconfig, if so you are connected.

then type netstat -rn to see if you have a path out of your local network.

---

