---
title: "Netgear MA101 USB wireless adaptor"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by Mousetrapreplica on 2010-05-12
I have installed Xubuntu 10.04 on an old spec PC that was running XP pro and connecting to the network via a Netgear MA101 USB wireless adaptor.
 
When I 'explored' Xubuntu using the Live CD, the adaptor was picked up and the only thing I found I had to do was enter the WEP key for the router. Firefox worked and I could browse the internet.
 
Now I have Xubuntu installed and Windows XP has gone I no longer have networking.
Is it possible that the live CD was piggybacking the Windows driver for the NIC?
 
Does anyone know if Xububtu supports this card and if so how do I go about enabling it?
 
On a different note but same subject, I tried to boot from the Live CD to see if the network still worked from there and whatever the boot sequence - with CD ROM first - it bypasses the CD ROM drive and boots from the hard drive straight into Xubuntu.
 
Any help would be greatly appreciated

---

### Post by cariboo on 2010-05-12
In order to help you, we need to know what chipset your device has. Make sure the device is connected, then open a terminal and type:

```
lsusb
```

the output should look something like this:

```
lsusb
Bus 002 Device 002: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 07d1:3c04 D-Link System WUA-1340
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

as you can see I have a D-link WUA-1340 connected. Look at the number next to your device, in my case:

```
07d1:3c04
```

do a search in Google for the number to see which driver your device needs. After you have the information, type:

```
lsmod | grep rt73
```

Substitute your driver for the one I used in the above example. The output of the above command should look something like this:

```
lsmod | grep rt73
rt73usb                24256  0 
crc_itu_t               1715  1 rt73usb
rt2x00usb              11260  1 rt73usb
rt2x00lib              32133  2 rt73usb,rt2x00usb
```

Again your output will be for a different driver. If the lsmod command does give you any output, you will need to manually load the driver with this command:

```
sudo modprobe <driver_name>
```

Once the driver has loaded type:

```
dmseg | tail -n10
```

the output should look something like this:

```
 dmesg | tail -n10
[18620.088078] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[18620.088081] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[18620.088083] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[18620.418412] phy0: Selected rate control algorithm 'minstrel'
[18620.419207] Registered led device: rt73usb-phy0::radio
[18620.419224] Registered led device: rt73usb-phy0::assoc
[18620.419241] Registered led device: rt73usb-phy0::quality
[18620.419741] usbcore: registered new interface driver rt73usb
[18620.484917] rt73usb 1-8:1.0: firmware: requesting rt73.bin
[18620.609140] ADDRCONF(NETDEV_UP): wlan0: link is ready
```

If everything works, you should now be able to setup your wireless connection.

---

### Post by Mousetrapreplica on 2010-05-13
Firstly thanks Cariboo907 for getting back to me with such a detailed reply.
 
I have followed your instruction - 
The id of the card is 0864:4100
Which, as far as i can find, seems to use driver at76_usb.
 
However, when I try the command lsmod | at76_usb it returns
 
at76_usb command not found
 
I get the same result if I try using modprobe at the root.
 
Is at76_usb a driver or am I using something completely wrong here?

---

### Post by ukripper on 2010-05-13
post output of this command:
```
lsmod
```

---

### Post by cariboo on 2010-05-13
There is an at76c50x-usb module in /lib/modules/<kernel_version> that may be the driver you need.

---

### Post by zerobytes2003 on 2010-05-14
I am also struggling with this card.  Here's some success I've found:

You can get the correct drivers here:
[http://drivers.softpedia.com/get/NETWORK-CARD/NETGEAR/NETGEAR-Network-Card-MA101-24.shtml](http://drivers.softpedia.com/get/NETWORK-CARD/NETGEAR/NETGEAR-Network-Card-MA101-24.shtml)

Once you have the drivers you can install them using ndiswrapper and ndisgtk which should be available in the package manager.  I've found that the netm101r driver works fine by itself (without netm101a) 

After installing the drivers try using lsusb again to see if you can see the device.  There is a great tut for ndiswrapper [here]("http://ubuntuforums.org/showthread.php?t=885847&highlight=ndiswrapper+sticky") if that doesn't work.

Let me know if that works...

---

### Post by Mousetrapreplica on 2010-05-17
Thanks again for the suggestions.
 
Ukripper - I ran lsmod, but I'm afraid i can't post the results here as none of my USB sticks are being recognised. However, I think I see where you are coming from which is to look for a similar driver which would be the at76c50x_usb that Cariboo907 suggested.
I tried this without success.
 
Zerobytes2003 - the same thing aplies with ndis wrapper in that I don't have the means to move data onto my Xubuntu PC.
 
But I don't give up that easily.
 
I should have explained that I am a total newbie to this, so all the commands you are using are all new to me. My only experience of unix was a one day introduction to it in 1998 which has long since been washed away.
However, I am an old DOSer so using the terminal doesn't phase me.
I have to admit when I first looked at Xubuntu using the live CD I didn't expect things to be quite so tricky, but I like a challenge as I believe it's the best way to learn.
 
Lastly, how do you get the Code: 'box' that you all use in the forums?

---

### Post by RedRat on 2010-05-17
Going back to your original post, you say that you cannot boot from the LiveCD. Have you checked your bios settings? It should make no difference if the bios is set to boot from the CD or first removable disk what other OSs are installed.

If indeed you cannot boot from the CD, then one of your installations must have reset the bios.

---

