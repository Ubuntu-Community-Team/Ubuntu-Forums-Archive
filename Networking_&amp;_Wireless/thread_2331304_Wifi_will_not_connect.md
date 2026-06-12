---
title: "Wifi will not connect"
date: 2016-07-20
forum: Networking &amp; Wireless
---

### Post by 4kh3RAm on 2016-07-20
I installed Ubuntu-Mate to a laptop. (HP G60)

But I can not connect to internet using WiFi.

I used the correct connection and password.

---

### Post by deadflowr on 2016-07-20
Moved to **Networking and Wireless**

Sorry, but you will need to post more information in order for anyone to help you with the issue at hand.
See:
[https://ubuntuforums.org/showthread.php?t=370108]("https://ubuntuforums.org/showthread.php?t=370108")

---

### Post by 4kh3RAm on 2016-07-20
More info attached.

---

### Post by jeremy31 on 2016-07-20
Lets set the country code and hope the power output will increase
```

sudo iw reg set US
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda

```

If you can change the wifi router settings put it on channel 9 and change encryption to WPA2-AES, WPA2-PSK, or WPA2 only without TKIP
If this doesn't help run the wireless script again and post the new results

---

### Post by wildmanne39 on 2016-07-20
You may want to try the following commands to raise your tx=power.
```
sudo /etc/init.d/network-manager stop

sudo iwconfig wls1 power off

sudo iwconfig wls1 rate 18

sudo /etc/init.d/network-manager start
```

---

### Post by 4kh3RAm on 2016-07-20
> **jeremy31 said:**
> Lets set the country code and hope the power output will increase
```

sudo iw reg set US
sudo sed -i 's/^REG.*=$/&US/' /etc/default/crda

```

If you can change the wifi router settings put it on channel 9 and change encryption to WPA2-AES, WPA2-PSK, or WPA2 only without TKIP
If this doesn't help run the wireless script again and post the new results

No change.

Will try WildMan ideas next.

> **Wild Man said:**
> You may want to try the following commands to raise your tx=power.
```
sudo /etc/init.d/network-manager stop

sudo iwconfig wls1 power off

sudo iwconfig wls1 rate 18

sudo /etc/init.d/network-manager start
```

```
andy@7:~$ sudo iwconfig wls1 rate 18
Error for wireless request "Set Bit Rate" (8B20) :
    SET failed on device wls1 ; Network is down.
```

Had to do a 
```
sudo /etc/init.d/network-manager stop
```
to get my wired network to work again. :-)

---

### Post by jeremy31 on 2016-07-20
Lets try a variation of Wild Man's commands
```
sudo /etc/init.d/network-manager stop

sudo iwconfig wls1 power off

sudo iwconfig wls1 txpower 18

sudo /etc/init.d/network-manager start
```

Then see if ```
iwconfig
``` shows a Tx-Power setting higher than 3 dbm

---

### Post by 4kh3RAm on 2016-07-20
> **jeremy31 said:**
> Lets try a variation of Wild Man's commands
```
sudo /etc/init.d/network-manager stop

sudo iwconfig wls1 power off

sudo iwconfig wls1 txpower 18

sudo /etc/init.d/network-manager start
```

Then see if ```
iwconfig
``` shows a Tx-Power setting higher than 3 dbm

```
andy@7:~$ sudo iwconfig wls1 power off
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wls1 ; Operation not supported.


```

---

### Post by jeremy31 on 2016-07-21
```
sudo ifconfig wls1 down
sudo iwconfig wls1 txpower 18
sudo ifconfig wls1 up
sudo iwconfig wls1 txpower 18
```

See if that works to raise the transmist power

---

### Post by 4kh3RAm on 2016-07-21
Got error with 2nd command.

```
andy@7:~$ sudo ifconfig wls1 txpower 18
txpower: Unknown host
ifconfig: `--help' gives usage information.

```

---

### Post by jeremy31 on 2016-07-21
Copy and paste the commands into terminal, you used ```
sudo ifconfig wls1 txpower 18
```
The code I posted was ```
sudo iwconfig wls1 txpower 18
```
ifconfig and iwconfig are not the same

---

### Post by 4kh3RAm on 2016-07-21
Still no connection.

I know wifi is good because it works with Slacko Puppy.

```
andy@7:~$ iwconfig
lo        no wireless extensions.

enp1s0    no wireless extensions.

wls1      IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=16 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

Does not look like Ubuntu can get my wifi going.

I guess I will have to stick with Linux Slacko on my laptop.

But I do appreciate the effort.

I will try another distro of Ubuntu and see if wifi works with it.

Does not look like Ubuntu can get my wifi going.

I guess I will have to stick with Linux Slacko on my laptop.

But I do appreciate the effort.

I will try another distro of Ubuntu and see if wifi works with it.

That command has made more problems.

Now I can NOT make programs using wine.

I hope I do not have to do a re-install. :-(

It's gotten awful quiet. :-)

I would still like to **_undo_** those 2 chown "experiments" that I ran.

---

### Post by wildmanne39 on 2016-07-23
If you be patient I am almost sure one of the wireless experts can help you fix it. All ubuntu's and many other distributions will be the same. This may be the network manager bug. 

I am on my cell and I am traveling today so I am of no help.

---

### Post by 4kh3RAm on 2016-07-23
O.k.

---

### Post by jeremy31 on 2016-07-23
Run the wireless script again so we can see if things changed correctly

---

### Post by 4kh3RAm on 2016-07-23
Jeremy31,

I installed ubuntu-15.04-desktop-amd64 and it had no problem connecting using wifi.

I just realized that my former version that I installed on laptop was for AMD.

I am now downloading the Intel version for it.

---

