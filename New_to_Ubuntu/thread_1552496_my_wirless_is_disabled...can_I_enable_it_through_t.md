---
title: "my wirless is disabled...can I enable it through the terminal?"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by audit on 2010-08-13
Can I enable my wireless through the terminal? 

when i entered this command: ```
lspci | grep Wireless
```
this was my reply: ```
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
```

The icon tells me my "wireless is disabled", and it will not let me select "enable wireless".

additional note: I can use my wireless on a another computer so I know that it is working.

---

### Post by wojox on 2010-08-13
Did you install the driver for it?

---

### Post by jtarin on 2010-08-13
To see if it will enable from the terminal issue the command ```
sudo '/sbin/service NetworkManager start
```

You might want to have a look at [WIFI Radar]("http://www.ubuntugeek.com/wifi-radar-simple-tool-to-manage-wireless-profiles.html").

---

### Post by audit on 2010-08-13
no--where would I find the driver, and how would I install it. I assume that the drivers are still there because it worked 10 hours ago.

because I had a similar problem so months ago I entered this code:
```
sudo apt-get install linux-backports-modules-wireless-lucid-generic

```

because it had been suggested before--but it had no effect. 

Sometimes when I reboot the icon tells me that my wireless is enabled, but I still cannot connect and the icon always changes back to where it will not let me "enable" it if I reboot again. 
The wireless button is always lit and blue--I have pushed but it seems to have no effect--because when I push it it does not go orange. The button is orange briefly each time I reboot, but it always turns blue.

---

### Post by jtarin on 2010-08-13
See post above about WIFI Radar.

---

### Post by wojox on 2010-08-13
> **audit said:**
>  I assume that the drivers are still there because it worked 10 hours ago.

Drivers should be installed if that's the case. I'd check out jtarin's WIFI Radar.

---

### Post by audit on 2010-08-13
I tried:
```
sudo NetworkManager start

```

and got this response

```
** (NetworkManager:2054): WARNING **: NetworkManager is already running (pid 775)

```

and I am still unable to "enable" my wireless...any other suggestions?

---

### Post by audit on 2010-08-13
I went to the NetworkManager man page and read this quote:

> NetworkManager  will  connect  any network  device  when  a  connection for that device becomes available, unless that behavior is  disabled.

My question is how do I enable my wireless card from the terminal?

---

### Post by wojox on 2010-08-13
What does 

```
iwconfig
```

Return?

---

### Post by admiralspark on 2010-08-13
do two things:
```
 iwconfig 
``` to see what your wireless card is called (I assume it is wlan0 for the rest of this, but it can be eth0, eth1, wlan1, anything).
```
sudo ifconfig wlan0 up
``` will turn the device on, assuming it's called wlan0.

---

### Post by jonnywombat on 2010-08-13
Just a thought... are you dual booting??

If so did you boot into windows before you got the problem? I have had this problem where using the button to turn wireless off in windows will mean ubuntu cannot access the wireless device, with exactly the symptoms you describe.

If this is the case the fix is to simply boot back into windows, turn on the wireless and then reboot back into ubuntu.


hth

jonny

---

### Post by audit on 2010-08-13
I entered: ```
iwconfig
```

this was the replY:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```          
then i entered this:
```
sudo ifconfig wlan0 up
```
and this was the reply:
```
SIOCSIFFLAGS: Unknown error 132

```

additional note: I am not dual booting.

---

### Post by wojox on 2010-08-13
Check out this [Bug Report]("http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1813445.html")

---

### Post by audit on 2010-08-13
I attached a usb wireless card that use to "work with this machine" here is its name
```
Bus 002 Device 002: ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter

```
Then i ran this: ```
iwconfig
```
which gave me this reply:
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan1     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
```

seeing that I now had a wlan1 I ran this: ```
sudo ifconfig wlan1 up

```
which worked without error--but both wireless cards are still shown as disabled.

---

### Post by wojox on 2010-08-13
Did you try these commands from the report?

---

### Post by audit on 2010-08-13
i did run these commands from the report:
```
rmmod ath9k
rfkill block all
rfkill unblock all
modprobe ath9k
rfkill unblock all
ifconfig wlan0 up

```

here is the response:
```
gms@gms-laptop:~$ rmmod ath9k
ERROR: Module ath9k does not exist in /proc/modules
gms@gms-laptop:~$ rfkill block all
gms@gms-laptop:~$ rfkill unblock all
gms@gms-laptop:~$ modprobe ath9k
WARNING: Error inserting mac80211 (/lib/modules/2.6.32-24-generic/updates/cw/mac80211.ko): Operation not permitted
WARNING: Error inserting ath9k_common (/lib/modules/2.6.32-24-generic/updates/cw/ath9k_common.ko): Operation not permitted
FATAL: Error inserting ath9k (/lib/modules/2.6.32-24-generic/updates/cw/ath9k.ko): Operation not permitted
gms@gms-laptop:~$ rfkill unblock all
gms@gms-laptop:~$ ifconfig wlan0 up

```

since I cannot guess what my version of ath9k is I am not sure what to do?

Since I don't have any idea what to do I am thinking about reformatting the computer

---

### Post by audit on 2010-08-13
I have now connected with my usb wireless card. Works only sometimes. I did not reformat because I seemed to have the same problems with the live cd as I was having without.
Because of the inconsistency of the results I have no idea whether this is a hardware problem or a software problem. 
Any guesses would be appreciated--a long with suggestion of where I might look for information about this problem. 
Thanks for the help that was provided.

Additional note: the reason I stopped using the usb wireless card was  because the wireless card installed in this labtop started to work and the two of them running at the same time made my Internet very slow. If anyone knows how to ensure the installed wireless card is disabled I would appreciate it.

---

### Post by kroq-gar78 on 2010-08-13
assuming your installed wireless card is wlan0 (if it isn't, then replace with what it is):
```

sudo ifconfig wlan0 down

```

If you use the sleep mode (maybe hibernate too) and the network is disabled (no option to connect to anything), go back to sleep or hibernate and it should re-enable networking. You can do that though terminal:
If you don't have pmi (or whatever the package is called), install it using ```
apt-get install
``` pmi (i think). Otherwise:
```
pmi action suspend
```
Sorry if irrelevent; I didn't really read anything but the last post.

---

### Post by audit on 2010-08-13
kroq-gar78 it does seem as if all I needed to do was enter:

```
sudo ifconfig wlan0 down
```

then shut my computer down and when I turn it back on my wireless is up. a this point I was able to enter 

```
sudo ifconfig wlan0 up
```

and i receive no error.

thank you for the help.

---

### Post by a2020vision on 2010-08-13
> **audit said:**
> i did run these commands from the report:
```
rmmod ath9k
rfkill block all
rfkill unblock all
modprobe ath9k
rfkill unblock all
ifconfig wlan0 up

```

here is the response:
```
gms@gms-laptop:~$ rmmod ath9k
ERROR: Module ath9k does not exist in /proc/modules
gms@gms-laptop:~$ rfkill block all
gms@gms-laptop:~$ rfkill unblock all
gms@gms-laptop:~$ modprobe ath9k
WARNING: Error inserting mac80211 (/lib/modules/2.6.32-24-generic/updates/cw/mac80211.ko): Operation not permitted
WARNING: Error inserting ath9k_common (/lib/modules/2.6.32-24-generic/updates/cw/ath9k_common.ko): Operation not permitted
FATAL: Error inserting ath9k (/lib/modules/2.6.32-24-generic/updates/cw/ath9k.ko): Operation not permitted
gms@gms-laptop:~$ rfkill unblock all
gms@gms-laptop:~$ ifconfig wlan0 up

```

since I cannot guess what my version of ath9k is I am not sure what to do?

Since I don't have any idea what to do I am thinking about reformatting the computer

In the below post, it mentions that it's a AR5001 card; I suggest you worry more about the ath5k module than the ath9k one (I have ath5k cards in both my PC's).

Also, have you tried the GUI tools already (System -> Preferences -> Network Connections)? I know many linux-users go straight for the command line, but...


> **audit said:**
> Can I enable my wireless through the terminal? 

when i entered this command: ```
lspci | grep Wireless
```
this was my reply: ```
02:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
```

The icon tells me my "wireless is disabled", and it will not let me select "enable wireless".

additional note: I can use my wireless on a another computer so I know that it is working.

---

### Post by audit on 2010-08-13
I did try to use the gui first they allowed me to do nothing. You are right the driver that was causing me problems was "ath5k" 

It has caused me quite a bit of problems at first it did not work at all and I was forced to buy a usb wireless card. Then when it started to work with my wireless card it fought it usb wireless card. It took me a week before I realize that I had two wireless cards working at the same time and that was why my Internet was so slow. 

Maybe it is not the driver, maybe it is the wireless card this time, I don't care, Because I blacklisted that ath5k driver (my usb wireless works just fine.)

I find the guis are great when they work--but for problems they suck. The documentation is not as convenient as the man pages--and it is much easier to understand when someone says type this at the terminal then trying to figure out which pretty box they wish you to push.

---

