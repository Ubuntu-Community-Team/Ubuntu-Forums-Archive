---
title: "Wireless connection is not detected"
date: 2008-08-25
forum: Networking &amp; Wireless
---

### Post by evillan on 2008-08-25
Hi,

I'm a linux newbie and the wireless internet card does not seem to work. I've tried [this guide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide#check").

This is what I've done:
1) Checked the wireless connection with the network-admin. There's only a wired connection and a point to point connection.
2) Checked lscpi which outputs
```

01:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
        Subsystem: Intel Corporation PRO/Wireless 3945ABG Network Connection
        Flags: bus master, fast devsel, latency 0, IRQ 219
        Memory at da000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

07:08.0 Ethernet controller: Intel Corporation PRO/100 VE Network Connection (rev 02)
        Subsystem: Fujitsu Siemens Computers Unknown device 10ad
        Flags: bus master, medium devsel, latency 64, IRQ 21
        Memory at dc000000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at 5000 [size=64]
        Capabilities: <access denied>

```
3) Tried  "sudo pccardctl ident" with no output. My laptop is relatively new so I don't think an old card is the problem.

How  do I activate the card?

---

### Post by qstraza on 2008-08-25
my lspci says that we have the same card. Mine worked out of the box.

What does ```
iwconfig
``` say?

---

### Post by evillan on 2008-08-25
iwconfig outputs
```

xxx~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


```

---

### Post by qstraza on 2008-08-25
try running ```
sudo modprobe -r iwl3945
sudo modprobe iwl3945
```

what does it say?

---

### Post by david sousa on 2008-08-25
You can install ndiswrapper

---

### Post by qstraza on 2008-08-25
> **david sousa said:**
> You can install ndiswrapper
lol

---

### Post by evillan on 2008-08-25
> **qstraza said:**
> try running ```
sudo modprobe -r iwl3945
sudo modprobe iwl3945
```

what does it say?

Nothing...?

```

xxx:~$ sudo modprobe -r iwl3945
xxx:~$ sudo modprobe iwl3945
xxx:~$ 

```

---

### Post by qstraza on 2008-08-25
> **evillan said:**
> Nothing...?

```

xxx:~$ sudo modprobe -r iwl3945
xxx:~$ sudo modprobe iwl3945
xxx:~$ 

```
and still nothing from iwconfig?

---

### Post by evillan on 2008-08-25
> **qstraza said:**
> and still nothing from iwconfig?

Nope.

---

### Post by qstraza on 2008-08-25
does dmesg mention your wireless driver?

```
dmesg | grep Wireless
```

it should look something like this:
```
[   40.500598] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[   40.500792] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection

```

---

### Post by evillan on 2008-08-25
Yes:

```
xxx:~$ dmesg | grep Wireless
[ 1187.640744] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[ 1187.640974] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection

```

---

### Post by qstraza on 2008-08-25
i found this on our forum:
```
 sudo apt-get install linux-backports-modules-hardy-generic
```

let us know if it works (run modprobe iwl3945 afterwars and iwconfig)

---

### Post by evillan on 2008-08-25
Hmm, it does not work

```

xxx:~$ modprobe iwl3945
xxx:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

```

---

### Post by qstraza on 2008-08-25
i kinda ran out of ideas.

---

### Post by evillan on 2008-08-25
Let's hope somebody else can help me, then :)

---

### Post by qstraza on 2008-08-25
well i just dont get this... it should work... did you reboot after installing those thingies? But i think it wont help. Try searching the forum

EDIT: Did you turn bluetooth/wlan switch on, on your laptop? Does your LED light lights blue?
This have to be enabled in order to work

---

### Post by evillan on 2008-08-25
> **qstraza said:**
> well i just dont get this... it should work... did you reboot after installing those thingies? But i think it wont help. Try searching the forum

EDIT: Did you turn bluetooth/wlan switch on, on your laptop? Does your LED light lights blue?
This have to be enabled in order to work

Ah! You're right. I just checked the manual of the laptop and I have to turn on the bluetooth manually. I'm sorry for wasting your time.

```

xxx:~$ modprobe iwl3945
xxx:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11a  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

As you can see, "modprobe iwl3945" still doesn't do anything. Is that a problem?

---

### Post by qstraza on 2008-08-25
owned.

iwl3945 is a driver for your wireless.
So if you do 
```
modprobe iwl3945
```
you run the driver, but it is allready running.
with ```
modprobe -r iwl3945
``` you remove it, so it will stop working. Try it.
The driver is runned automaticly since ubuntu knows that you need it;)

---

### Post by evillan on 2008-08-25
Yes, it's working now. Thank you so much for your help.

---

### Post by qstraza on 2008-08-25
np man, feel free to seek help here:p
and you owe me a beer ;)

---

