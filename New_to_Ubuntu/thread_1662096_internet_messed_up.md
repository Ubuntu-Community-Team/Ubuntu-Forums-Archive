---
title: "internet messed up"
date: 2011-01-07
forum: New to Ubuntu
---

### Post by libihero on 2011-01-07
for some reason today the network connections manager got messed up.  it shows up in the icon that no network is available and networking is disabled... even though the ethernet cable is connected and the internet is working fine.  its a real hassle with wireless though, since it shows no wireless networks and i cant connect to any of them

---

### Post by Hippytaff on 2011-01-07
I guess you tried enabling wireless?

what does ```
 iwconfig
```return?

---

### Post by libihero on 2011-01-07
```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

i am suspicious of the indicator-network applet i downloaded, since my problems started since i downloaded it.  but even when i uninstalled it, it still wouldnt let me turn on the wireless

---

### Post by Hippytaff on 2011-01-07
try
```

iwconfig up

```
you might need to use sudo :?

---

### Post by libihero on 2011-01-07
it says no such device :(

---

### Post by Hippytaff on 2011-01-07
haha...don't panick, I just tried it and I got the same response, I'm using wireless but it's on eth0 for some reason.

Anyway, are the drivers ok, does rebooting do anything?
do
```

lspci | grep -i netw

```search for the driver for the chipset you have on google, then
```

lsmod | grep -i *name of diver* 
```
to see if it is still loaded.

does the wireless work with windows?

---

### Post by Hippytaff on 2011-01-07
Just had a thought, now the possibly offending applet has been uninstalled have you tried getting rid of any cruft with

```

sudo apt-get autoclean

```

---

### Post by libihero on 2011-01-07
the first thing you gave me gave no results in terminal...
just a random question though, is it possible to remove just the network systray icon from the systray, cuz the indicator icon is randomly working now

---

### Post by linuxman94 on 2011-01-07
@Hippytaff He has a problem with network manager, not the connection.  

OP: Have you rebooted since you had he problem?  Sometimes the applet doesn't load correctly.

---

### Post by libihero on 2011-01-07
i tried rebooting this morning in a wifi hotspot and it didnt work with or without both the indicator applet network manager and the one in the systray both loaded.  i got rid of the indicator applet, rebooted, and it wouldnt allow me to enable networking.  right now though with both loaded, the indicator applet network manager is letting me connect to wifi, but for some reason the one in the systray still shows "networking enabled" grayed out

---

### Post by linuxman94 on 2011-01-09
Try this command in the terminal:

```
sudo ifconfig wlan0 up
```

---

