---
title: "2 part: help with my wireless card being ridiculous"
date: 2008-04-14
forum: Networking &amp; Wireless
---

### Post by takaelar on 2008-04-14
I have a BCM 4312 wireless card on a Dell 1501 Inspiron, AMD 64, Gutsy. Initially, I could not get my wireless card to physically turn on (it has no physicalswitch, just a Fn+F2 hotkey.) .  I downloaded the firmware for it using ndiswrapper, and it worked fine, unitl of course I restarted my computer. The result is that the light for wireless is off, but Restricted Device Manager says that the firmware is installed. Disabling and then re-enabling it solves this, but only for about half an hour, when it arbitrarily decides that it needs to turn off. And it does so, leaving me with no internet. My wired internet works most of the time, but sometimes i have to restart my computer with the live ethernet cable still inserted. Then i get great internet. I am using Wicd alongside Network Manager.

Update: that fix no longer has any effect. I have no wifi. Help plz. I am wiling to be drastic with my fix (reinstall Ubuntu if necessary), but I NEED help because it's finals time at University and there is info online that I need to access at school, on their wifi.

---

### Post by pytheas22 on 2008-04-14
Are you using ndiswrapper or the bcm43xx driver?  You mention ndiswrapper but the Restricted Drivers Manager would mean that you're using the bcm43xx, I think.

If you aren't sure, what is the output of

```
modprobe -l | grep ndiswrapper
```

and

```
modprobe -l | grep bcm43
```

---

### Post by tl3000 on 2008-04-14
> **takaelar said:**
> ...  I am using Wicd alongside Network Manager.  ...

I believe you cannot do this... it is one or the other.  I had to remove NM completely when I used WICD on Fiesty.

---

### Post by takaelar on 2008-04-16
josiah@Takaelar:~$ sudo modprobe -l | grep ndiswrapper
[sudo] password for josiah:
/lib/modules/2.6.22-14-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko

josiah@Takaelar:~$ sudo modprobe -l | grep bcm43
/lib/modules/2.6.22-14-generic/kernel/drivers/net/wireless/bcm43xx/bcm43xx.ko


As to tl3000, I removed Wicd. I will restart and see waht happens.

---

### Post by takaelar on 2008-04-16
ok, I uninstalled wicd with synaptics... I still have wired internet (hence my talking....) but i have no idea what is the deal with my wireless. I am going to try to do what was working before: reinstall the firmware. Also, I keep posting after every step because I want to see at what point I screw up. Now, I am lookig at my restricted driver list and it says that the firware is in use for bcm43xx. but the light is off, and NM does not recognize a wireless card. neither, i might add, does iwconfig. when entered it says no such device for eth1, my wireless card. eth0 is working and connected, and the internal loop works fine. ok, reinstalling the firmware worked. the light is on, but i cannot "see" any networks. This is preposterous, because I am in range of at least 11 known routers.

---

### Post by tl3000 on 2008-04-16
[http://ubuntuforums.org/showpost.php?p=4717531&postcount=5](http://ubuntuforums.org/showpost.php?p=4717531&postcount=5)

HTH

---

### Post by takaelar on 2008-04-16
Thank you so much. That certainly helps a lot, as i am on wireless right now, but i cannot detect any networks, i only know my ESSID and password and so typed them  in. I used to see them with the drop-down menu on network manager under select network, but I see none. also, when i restart my computer, my wifi card turns off. is there a coded killswitch that i can disable? I read about it somewhere, but i can;t seem to find info on it anymore.

---

### Post by takaelar on 2008-04-16
Alright, it would seem that I took two steps forward and one backwards. I restarted and now my wireless card is physically off. this has been a problem from day one... I would appreciate any insight as to the source of this problem and /or a fix

---

### Post by pytheas22 on 2008-04-16
> Alright, it would seem that I took two steps forward and one backwards. I restarted and now my wireless card is physically off. this has been a problem from day one... I would appreciate any insight as to the source of this problem and /or a fix

Make sure the device is up.  It's possible that for some reason it is not being brought after when the computer reboots:

```
sudo ifconfig eth1 up
```

If this doesn' t work, what is the output of the commands:

```
ifconfig -a
iwconfig
```

---

### Post by Bosk22 on 2008-04-16
Try this 

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch13_:_Linux_Wireless_Networking)

It sorted my wireless problems may be it will sort yours to

Good luck 

Bosk

---

### Post by tl3000 on 2008-04-16
> **takaelar said:**
> ... I restarted and now my wireless card is physically off. this has been a problem from day one... I would appreciate any insight as to the source of this problem and /or a fix

Try this poster's solution:

[http://ubuntuforums.org/showpost.php?p=4729570&postcount=5](http://ubuntuforums.org/showpost.php?p=4729570&postcount=5)

HTH

---

### Post by takaelar on 2008-04-25
josiah@Takaelar:~$ sudo ifconfig a
a: error fetching interface information: Device not found
josiah@Takaelar:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

I am very sure that my problem is as you are describing, because when I restart, the light turns off for the wifi card. I read somewhere that there is a built-in software "killswitch" that needs to be deactivated. I will repost with that as the title. thanks to all for your help!
Takaelar

---

