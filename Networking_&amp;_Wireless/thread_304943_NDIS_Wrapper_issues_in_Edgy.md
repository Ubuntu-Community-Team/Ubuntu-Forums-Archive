---
title: "NDIS Wrapper issues in Edgy"
date: 2006-11-22
forum: Networking &amp; Wireless
---

### Post by N'Jal on 2006-11-22
Hi, i am wanting to set up a wireless adapter with ubuntu, and while i have ndiswrapper installed and the hardware installed and working, I can't seem to make a connection, i DID have an error loading ndiswrapper with modprobe but that seems to have cleared up. However I canno't make the connection, i have a belkin F5D7050 and APPEARS to use the rt73 driver. If anyone could show me where i am going wrong i would be very happy.

Thanks.

---

### Post by IntuitiveNipple on 2006-11-22
What kind of problems are you seeing? Does **iwlist <if> scan** see the W.A.P. ?

---

### Post by N'Jal on 2006-11-22
For some odd reason i have both wlan0 and wmaster0.

iwlist wlan0 scan
wlan0     No scan results

iwlist wmaster0 scan
wmaster0     Failed to read scan data: Operation not permitted.

---

### Post by Doug11 on 2006-11-22
I just went through sort of the same thing. I don't know if it will work for you but I had to disable wired connection before my wireless would work. My wireless light would be on but I couldnt get any kind of connection. It took about 4 days before I figured this about. Hope it helps.

---

### Post by trubblemaker on 2006-11-22
Check your dmesg for bcm43xx



```
dmesg | grep bcm43xx
```
or 
```
lspci | grep Broadcom 
```

**if it comes up blank skip the rest of this post.** if it lists output 

```
echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
```

and reboot all should be well, why I say this is I think that their may be a native driver for your card, but I don't know for sure, it might be bcm43xx so it's worth a shot.

---

### Post by N'Jal on 2006-11-22
There is no wired connection on the machine at the moment, and there is no broadcom driver running on the system. However i was aware it MIGHT have been a problem, but not at the moment. I also did check the NDISWrapper list and my card does appear to be listed in there.

---

### Post by FrodoB on 2006-11-22
Check you lsmod output for anything that refers to rt2500, rt2570, rt73 or   something similar and black list it. If you give up on ndiswrapper I can refer you to instructions for rt73 native drivers that will work with WEP.

---

### Post by trubblemaker on 2006-11-22
To be be thurrow, you check'd dmesg? alternatively if you believe that it uses rt73 driver try unloading it:

```
sudo rmmod rt73
```

I"m thinking that it is a driver conflict issue. If that works then blacklist that driver instead.

---

### Post by trubblemaker on 2006-11-22
And as Usual I agree with FrodoB, he's the man

---

### Post by N'Jal on 2006-11-22
If there is a native way to install the drivers with WEP i imagine that would be better, right?

Since the machine i am trying to get online is not this one i just took a screen dump after running this command 

Also lsmod | grep rt 

and moved it via usb stick.

---

### Post by trubblemaker on 2006-11-22
K so its your decision time as I can see both rt*usb and ndis*usb inth output  so **either** 

follow the howto from FrodoB, 

or 

blacklist rt73usb and reboot.

Both will work fine for  edgy,  I think that the native driver might be better in a long run situation, but it look like you 1 step away from finshing ndiswrapper, your decision.

---

### Post by FrodoB on 2006-11-22
You can take a look at these. If the machine that you are installing to has no internet access through a wired connection, it may be difficult to follow the instructions:

[https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29](https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29)

Back to ndiswrapper, you need to blacklist anything that has rt73 in the name to try it. If you go to the native driver you will have to blacklist ndiswrapper or remove it. You may want to get it a few last tries especially if the machine has no wired connection to the net.

If you cannot get the machine on the internet  and you still want to try native drivers, you can insert the install disk into a running system and then in Synaptic go to edit -> Add CD Rom and then add the build essential packages. Get the rt73 driver downloaded on windows and then try to follow the instructions.

---

### Post by N'Jal on 2006-11-22
Gonna attempt the native instructions first, I would rather not have to use ndiswrapper if at all possible, so will follow the instructions native first and let you know.

Thanks for your help so far. It's really appreciated!

---

### Post by N'Jal on 2006-11-22
Working natively now, thanks very much guys. YOU ALL ROCK!!!

---

### Post by FrodoB on 2006-11-22
Thanks for letting us know that it worked. Do I need to make any changes or improvements to the instructions?

---

### Post by N'Jal on 2006-11-22
Nope, any problems i had were my own typo's. And that was setting up the DHCP in /etc/network/interfaces and simply making the changes in the GUI fixed it. It's fantastic.

Again I thank you.

---

### Post by N'Jal on 2006-12-02
I have had to reinstall and followed the wiki and now my card will not activate on boot, it will work if i boot without the card inserted and then plug it in at the desktop, but only then, if i booted with it plugged in and remove and re-insert it, it does not work.

---

