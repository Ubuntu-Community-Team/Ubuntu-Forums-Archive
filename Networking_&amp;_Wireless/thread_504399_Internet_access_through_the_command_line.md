---
title: "Internet access through the command line"
date: 2007-07-19
forum: Networking &amp; Wireless
---

### Post by macijuana on 2007-07-19
Ok here is my situation. I just got through installing the command line os version of xubuntu, because the host computer is old and low end to begin with. I now want to be able to access the internet wirelessly, which I WAS able to do during the low memory mode installation process. It's my only option.The fact that I could connect during the install leads me to believe that the drivers are already preinstalled? Of course I had to select the appropriate modules to use from a list, but it still all worked from within the installer. So basically, right now I'm looking at a command line with no idea what step to take next. I'm sure it's quite simple. It looks like I may just have to enter one or two commands... (and the wireless router is WEP encrypted)

This is what I get when I enter 'iwconfig':
lo           no wireless extensions

rausb1   RT2500USB WLAN ESSID:""  Nickname:""
              Mode:Managed Frequency=2.412 GHz
              RTS thr: off   Fragment thr: off
              Link Quality=0/100  Signal level:-120 dBm  Noise level:-256 dBm
              Rx invalid nwid:0   Rx invalid crypt:0   Rx invalid frag:0
             Tx excessive retries:0   Invalid misc:0   Missed beacon:0

---

### Post by macijuana on 2007-07-19
Oh and the wireless adaptor is a Linksys Wireless G USB Adaptor

---

### Post by psyburn on 2007-07-19
If you not roaming outside your network, then this is simple...

Mind you it has been a good while since I setup wireless this way, so this is completely out of memory...
So any one who can correct this, please do...

you'll need to edit /etc/network/interfaces
```
sudo nano /etc/network/interfaces
```
or subsitute "nano" for "vim" if you prefer that like I do.

NOTE:
All things in code past here are to be appended not overwritten.
=Also=
change the following to whatever you know it should be instead:
```
rausb1
YOUR_SSID_GOES_HERE
YOUR_WEP_Key_GOES_HERE
XXX.XXX.XXX.XXX
```

Enter this in nano or vim if you have DHCP:
```
iface rausb1 inet dhcp
wireless-essid YOUR_SSID_GOES_HERE
wireless-key YOUR_WEP_Key_GOES_HERE

```


or enter this in nano or vim if you use static IP:
```
iface rausb1 inet static
address XXX.XXX.XXX.XXX
netmask XXX.XXX.XXX.XXX
gateway XXX.XXX.XXX.XXX
wireless-essid YOUR_SSID_GOES_HERE
wireless-key YOUR_WEP_Key_GOES_HERE

```

Sometimes dhcp times out so try static if you're having trouble.

Usually a valid home "static" setup is:
```
iface rausb1 inet static
address 192.168.1.50
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid YOUR_SSID_GOES_HERE
wireless-key YOUR_WEP_Key_GOES_HERE

```

Then just run:
```
sudo ifup -vv rausb1
```

to take it down to switch between Access Points use:
```
sudo ifdown -vv rausb1
```

I use the -vv to see if dhcp times out or not

FINAL CONSIDERATIONS:

In all of this I've had one problem with USB adaptors.
Some times the adapter name may change from boot-up to boot-up
rausb1 -> rausb0 or rausb2

an easy way to get around that is to make a duplicate entry for the adapters.

also If you do intend to roam about, setting "wireless-essid any" without the quotes allows it to connect to the strongest signal. caveat: it will connect to to the strongest signal

Edit: misinterpretable grammar fixed

EDIT2: source I used to refresh my memory was: [http://ubuntuforums.org/showpost.php?p=216745&postcount=3](http://ubuntuforums.org/showpost.php?p=216745&postcount=3)

EDIT3: clairification

---

### Post by macijuana on 2007-07-19
well everything looks good... but it says that that 'etc/network/interfaces' isn't a file or directory. And if it's dhcp, do i only enter that one code, or the one above it as well?

---

### Post by psyburn on 2007-07-19
I'll edit the above a tad to make it a bit more clear...

Clarifying 
```
/etc/network/interfaces
=NOT=
etc/network/interfaces
```

```
sudo nano /etc/network/interfaces
```

EDIT: Now my above should be a little clearer

---

### Post by macijuana on 2007-07-19
Oh wait a minute. I tried vim as you prefer and I am now viewing the file that 'describes the network interfaces available on your system and how to activate them. It seems like the installer carried over the wireless settings, because it already has the ip and wep key. should the ip be the local one (192.168.0.x) or the external? Silly question, but I certainly don't know the answers to them. I'll tinker with it for a little while longer. Thanks for all the help.

---

### Post by psyburn on 2007-07-19
preference for vim is just the geek in me, however I'm not the one to teach you vim if you don't know how to use it.... :(
Be careful

EDIT: Should be the internal one

---

### Post by macijuana on 2007-07-19
Under the hostname it reads '# wireless-* options are implemented by the wireless-tools package', and then the rest has the mode, essid, and key. Is that typical? or should I be using the wireless tools.

---

### Post by psyburn on 2007-07-19
The hash means they are commented out, but I don't see why you can't uncomment them for now and try to get it up through "ifup".

---

### Post by macijuana on 2007-07-19
Alright I'm just going to type exactly what I see when I enter sudo nano /etc/network/interfaces

# This file describes the netork interfaces available on your system and how to activate them. For more information, see interfaces (5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto rausb0
iface rausb0 inet dhcp
            hostname 192.168.0.1
            #wireless-* options are implemented by the wireless-tools package
            wireless-mode managed
            wireless-essid raymond
            wireless-key1 xxxxxxxxxxxxxxxxxxxxxxxxxx

So should I take out the hash marks for now?

---

### Post by psyburn on 2007-07-19
No nevermind those are notes

I would hash/comment-out the hostname and the wireless-mode unless you really think they need to be there.

Remember you can always comment out but deletion can be forever.

It looks fine to me.
Does it work or what is the failure?
===========================
**I see it!**

type in this at the bottom:
```
auto rausb1
iface rausb1 inet dhcp
wireless-essid raymond
wireless-key1 xxxxxxxxxxxxxxxxxxxxxxxxxx
```
but do put in the right WEP key instead of x's

---

### Post by macijuana on 2007-07-19
So I commented out the hostname and wireless mode.
And, should I leave the name as rausb0 or change it to rausb1 as you did?
AND, when I entered the ifup command it said it couldn't read /etc/network/interfaces. It didn't do that before so I must have changed something it didn't like.

---

### Post by psyburn on 2007-07-19
Make /etc/network/interfaces look like this:
```
# This file describes the netork interfaces available on your system and how to activate them. For more information, see interfaces (5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto rausb0
iface rausb0 inet dhcp
hostname 192.168.0.1
#wireless-* options are implemented by the wireless-tools package
wireless-mode managed
wireless-essid raymond
wireless-key1 xxxxxxxxxxxxxxxxxxxxxxxxxx

# sometimes the WUSB54Gv4 shows up as somthing else
auto rausb1
iface rausb1 inet dhcp
wireless-essid raymond
wireless-key1 xxxxxxxxxxxxxxxxxxxxxxxxxx
```
Save and use these commands:
```
sudo ifdown -vv rausb1
```
```
sudo ifup -vv rausb1
```

Did you mess with the permissions of the file?
also give the results of ```
ifconfig -a
```

---

### Post by macijuana on 2007-07-19
I set up /etc/network/interfaces exactly as you typed it.

Response to
sudo ifdown -vv rausb1
and
sudo ifup -vv rausb1
and
sudo ifdown -vv rausb0
and
sudo ifup -vv rausb0
is:

/etc/network/interfaces:2: misplaced option
if(up or down): couldn't read interfaces file "/etc/network/interfaces"

Response to
ifconfig-a
is:

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0b) TX bytes:0 (0.0b)

rausb1 Link encap:Ethernet Hwaddr 00:00:00:00:00:00
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:0 (0.0b) TX bytes:0 (0.0b)

---

### Post by psyburn on 2007-07-19
gimme a
```
ls -l /etc/network
```

---

### Post by macijuana on 2007-07-19
response to
ls -1 /etc/network
is:
[COLOR="Blue"]if-down.d
if-post-down.d
if-pre-up.d
if-up.d[/COLOR]
interfaces

---

### Post by psyburn on 2007-07-19
```
drwxr-xr-x 2 root root 4096 2007-04-15 04:55 if-down.d
drwxr-xr-x 2 root root 4096 2007-04-15 04:52 if-post-down.d
drwxr-xr-x 2 root root 4096 2007-04-15 04:49 if-pre-up.d
drwxr-xr-x 2 root root 4096 2007-04-15 04:55 if-up.d
-rw-r--r-- 1 root root  184 2007-07-15 04:41 interfaces
```
Is this the same as what you got?

---

### Post by macijuana on 2007-07-19
No I didn't get anything to the right of the ifs and interfaces. Just:
if-down.d
if-post-down.d
if-pre-up.d
if-up.d
interfaces

---

### Post by psyburn on 2007-07-19
LS -L /ETC/NETWORK

in lowercase

---

### Post by macijuana on 2007-07-19
Oh haha sorry:
total 20
drwxr-xr-x 2 root root 4096 Jul 18 17:58 [COLOR="Blue"]if-down.d[/COLOR]
drwxr-xr-x 2 root root 4096 Jul 18 17:58 [COLOR="Blue"]if-post-down.d[/COLOR]
drwxr-xr-x 2 root root 4096 Jul 18 17:58 [COLOR="Blue"]if-pre-up.d[/COLOR]
drwxr-xr-x 2 root root 4096 Jul 18 17:59 [COLOR="Blue"]if-up.d[/COLOR]
-rw-r--r-- 1 root root 602 Jul 19 05:53 interfaces

---

### Post by psyburn on 2007-07-19
I saw this when looking over the errors
back to
```
sudo nano /etc/network/interfaces
```

```
wireless-key[COLOR="Red"]1[/COLOR] xxxxxxxxxxxxxxxxxxxxxxxxxx
```

should be in both places:
```
wireless-key xxxxxxxxxxxxxxxxxxxxxxxxxx
```

---

### Post by macijuana on 2007-07-19
Still no luck. I'm going to reinstall the command line OS so I can start from a clean slate now that I have more of an I idea what I'm doing. So in a few hours we shall see if I can get it to work. If not, I'll post any problems here. Thanks for all of your desperately needed help thus far!

---

### Post by psyburn on 2007-07-19
good luck with that
Can't wait to hear back...:popcorn:

---

