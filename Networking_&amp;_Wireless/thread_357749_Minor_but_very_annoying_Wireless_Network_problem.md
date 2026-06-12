---
title: "Minor but very annoying Wireless Network problem"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by tylersticka on 2007-02-10
Greetings!

I am not by any means a seasoned Linux user, and this is my first permanent installation in an attempt to salvage an out-of-date laptop from the clutches of obsolescence.

I'm using Xubuntu so I could get the economic resource usage in tandem with the usability and progressiveness of the Ubuntu installation. I'm using 6.10 (Edgey Eft).

The wireless card is a 3com A/B/G (3CRPAG175), and I have the latest version of madwifi-ng installed.

Here's the problem... I got the wireless network configured and installed, and everything looks great. I can talk to the network and internet normally through all applications, including Firefox, Package Manager and the Terminal.

However, upon reboot things go a little odd. The wireless network will read as "connected," but I can't talk to the network until I open up "Networking," uncheck the Wireless option and check it again. Once it reconnects, I can talk to the internet fine.

Even though I'm 95% of the way there, it still feels odd having to open Networking and turn off and on the wireless network any time I want to get online.

This is my first time posting, but from other messages I looked at here is some information that may be of use to you...

The contents of \etc\network\interfaces:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface

iface eth0 inet dhcp

iface ath0 inet dhcp
wireless-essid spamlives
address 192.168.1.109
netmask 255.255.255.0
gateway 192.168.1.1

auto ath0
```

ifconfig *BEFORE* network is turned off and on:
```

ath0      Link encap:Ethernet  HWaddr 00:0D:54:99:1E:2E  
          inet6 addr: fe80::20d:54ff:fe99:1e2e/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6215 (6.0 KiB)  TX bytes:1780 (1.7 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 b)  TX bytes:300 (300.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-0D-54-99-1E-2E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5730 errors:0 dropped:0 overruns:0 frame:225
          TX packets:97 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:434759 (424.5 KiB)  TX bytes:5961 (5.8 KiB)
          Interrupt:11 

```

ifconfig *AFTER* network is turned off and on (and is working):
```

ath0      Link encap:Ethernet  HWaddr 00:0D:54:99:1E:2E  
          inet addr:192.168.1.109  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20d:54ff:fe99:1e2e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1360 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1442 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1115524 (1.0 MiB)  TX bytes:263622 (257.4 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:300 (300.0 b)  TX bytes:300 (300.0 b)

wifi0     Link encap:UNSPEC  HWaddr 00-0D-54-99-1E-2E-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10669 errors:0 dropped:0 overruns:0 frame:339
          TX packets:1549 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:199 
          RX bytes:1845891 (1.7 MiB)  TX bytes:300474 (293.4 KiB)
          Interrupt:11 

```

iwconfig *BEFORE* network is turned off and on:
```

lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"spamlives"  Nickname:"spamlives"
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   Tx-Power:31 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/94  Signal level=-47 dBm  Noise level=-94 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```


iwconfig *AFTER* network is turned off and on (and is working):
```

lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"spamlives"  Nickname:"spamlives"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66:4E:A8:89   
          Bit Rate:11 Mb/s   Tx-Power:31 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=50/94  Signal level=-46 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

If you need any other information from me, please don't hesitate to request it and I will get it to you as promptly as possible. I would like to solve this without using a non-default Xubuntu app like Knetwork because I really enjoy the Xubuntu interfaces.

I appreciate any help you all could volunteer, thank you very much in advance!

---

### Post by gradedcheese on 2007-02-10
Hmm... that all looks good.  Can you try this: boot up (so that it's not working) and run:

sudo /etc/init.d/networking restart

...does that 'solve' it?   If it does, a stupid hack would be to have that execute on bootup ;)  However we'll hopefully figure out the real problem and solve it intelligently.

---

### Post by tylersticka on 2007-02-10
> **gradedcheese said:**
> Hmm... that all looks good.  Can you try this: boot up (so that it's not working) and run:

sudo /etc/init.d/networking restart

...does that 'solve' it?   If it does, a stupid hack would be to have that execute on bootup ;)  However we'll hopefully figure out the real problem and solve it intelligently.

It almost works!

So I restarted, opened Firefox and confirmed that the internet was not working, ran the command you provided, and restarted Firefox, and it worked!

Unfortunately, after I entered the command to "Auto-started Applications" and restarted, there is no apparent change... so I still have to manually restart for it to work correctly.

I apologize if this is a newbie-ish suggestion, but I notice that the "Access Point" that iwconfig gives before it works is "Not-Associated," and after it works is "00:0F:66:4E:A8:89". Could this mean anything?

---

### Post by gradedcheese on 2007-02-10
"not associated" means just that, but that set of numbers is your access point's MAC address, which is provided once you associate.  So that's normal.  Unfortunately, the command I had you run is basically the shell way of doing what you did before: bring down the WiFi and bring it back up (but you were doing it via checkboxes and the like).  If you're ok with this 'fix', there are a number of ways to have it run automatically on bootup, but it is an ugly hack.

The reason that adding it to the 'startup programs' doesn't work is probably because sudo needs your password and it can't ask for it in that context (not that you'd want it to do that each time).

---

### Post by tylersticka on 2007-02-10
> **gradedcheese said:**
> "not associated" means just that, but that set of numbers is your access point's MAC address, which is provided once you associate.  So that's normal.  Unfortunately, the command I had you run is basically the shell way of doing what you did before: bring down the WiFi and bring it back up (but you were doing it via checkboxes and the like).  If you're ok with this 'fix', there are a number of ways to have it run automatically on bootup, but it is an ugly hack.

The reason that adding it to the 'startup programs' doesn't work is probably because sudo needs your password and it can't ask for it in that context (not that you'd want it to do that each time).

I'm up for it, lay it on me or shoot me the relevant link. :-)

---

### Post by gradedcheese on 2007-02-10
It would be better if we could fix the real problem -- does anyone else out there know why he would need to bring that interface down and then back up to have it work?  Is it a known problem that anyone else had?

As far as the ugly hack: we'd need a place to run it where the script in question still runs with root privileges but not so early that it runs before networking is actually started.  The init stuff changed a little in 6.10 but I am looking at the init scripts to see where we could put it if you go that route.  Unfortunately I can't think very clearly right now, so I might have to get back to you on this tomorrow (or perhaps someone will chime in with a better idea by then :)), but it can be done. 

If you're ok with having sudo not ask for a password (it can be configured that way), then it's pretty trivial.  Some people don't like to do that, whereas I usually run that way.  The idea is that if you have shell/physical access to my laptop, then by that point my password is irrelevant anyhow ;)  Anyhow, if you wanted to do that, very carefully edit /etc/sudoers ("sudo gedit /etc/sudoers") and change the line "%admin ALL=(ALL) ALL" to instead read "%admin ALL= (ALL) NOPASSWD: ALL" and then save and exit.  Make sure you don't mess that up, otherwise you won't be able to use sudo until you fix it via the recovery boot ;)  Alright, someone can now yell at me for offering this solutiion.

---

### Post by tylersticka on 2007-02-10
> **gradedcheese said:**
> If you're ok with having sudo not ask for a password (it can be configured that way), then it's pretty trivial.  Some people don't like to do that, whereas I usually run that way.  The idea is that if you have shell/physical access to my laptop, then by that point my password is irrelevant anyhow ;)  Anyhow, if you wanted to do that, very carefully edit /etc/sudoers ("sudo gedit /etc/sudoers") and change the line "%admin ALL=(ALL) ALL" to instead read "%admin ALL= (ALL) NOPASSWD: ALL" and then save and exit.  Make sure you don't mess that up, otherwise you won't be able to use sudo until you fix it via the recovery boot ;)  Alright, someone can now yell at me for offering this solutiion.

That makes sense, but I would like to retain the security of having a password required as this laptop may be used frequently at work... you just can't trust those co-workers. ;-)

In the meantime, I'll create a little "Refresh Network" button for myself so I can turn it into a one-click process. Thanks so much for your help. :-)

Any other solutions offered would be appreciated!

---

### Post by citizenofnowhere on 2007-02-13
Wow I actually found someone else who has the exact same problem! I thought I had messed up configurations somehow...

I'm running Ubuntu/Gnome so I guess it's not a Desktop Environment thing. I even had the problem booting up in E17. Funny thing is once the network works and I'm on-line if I logout and log back in everything works fine.

AND to top it all off, when I go to my boyfriend's place and bootup it automatically connects to HIS wireless like it ought to (same modem/router/ISP).

So I'm :confused: ...

What I do know is that for one reason or another, when I tried to get the new gnome network manager thing working (the one that supports WPA) I had to edit my /etc/network/interfaces and basically blank it out. Then I put my details back in like so at which point it started acting funny:

```

auto lo
iface lo inet loopback


iface eth0 inet dhcp


iface eth1 inet dhcp
wireless-essid [network name here]
wireless-key [hex hey here]

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

```

---

### Post by tylersticka on 2007-02-13
I was never able to truly solve this problem, but I managed to streamline the process a bit.

First, I created icons in Xfce's panel for Network Manager, Wifi-Radar, and a "Refresh Network" button I made. The "Refresh Network" button executes the following command when clicked (and your password is entered):

```
sudo /etc/init.d/networking restart
```

So if I want to connect to the internet in one of my trusted networks, I switch to in Network Manager and then click my "Restart Network" button.

Then, I used Network Manager to create locations for my most commonly-used networks. With this setup, I only use Wifi-Radar for networks I do not use on a regular basis.

It's not an ideal setup by any means, and I can't seem to figure out how I can use Wifi-Radar to connect rather than a hodge-podge of Network Manager and Wifi-Radar. Wifi-Radar won't connect by itself unless no essid is specified in Network Manager, but if I don't specify an essid on my first attempt to connect to anything, it won't connect at all until I enter one.

This results in a rather functionally-neutered wifi-radar, but at least I can grab essid's I need for Network Manager with it.

Attached is a screenshot showing my location of the buttons I created. May or may not be relevant as you are using Gnome and I'm using Xfce...

---

### Post by citizenofnowhere on 2007-02-13
Thanks a lot! I'll probably do the same.

I'm in the process of recompiling the kernel - will post back if that solves (or doesn't solve anything). 

And I know I had wifi-radar managing my networks for me before, I just can't remember how I did it. Will go look it up and again if I find anything will post back.

Thanks!!

---

### Post by citizenofnowhere on 2007-02-13
Found it!

Here is the wifi-radar homepage, which has brief details on usage: [http://wifi-radar.systemimager.org/](http://wifi-radar.systemimager.org/) 

You can run it without a gui, to automatically scan and connect to a preconfigured network. 

Technically, it *should * run on start-up if it is installed. If you have a wifi-radar script to start it at launch, you can use the following code to enable it (I typed this in and it told me I already had wifi-radar on bootup - yay):

```
update-rc.d wifi-radar defaults
```

There's also a set of instructions for better GNOME integration, but I'm gonna try get rid of everything in my configuration file and see if wifi-radar will take over.

If it doesn't, I'll probably just add the non-gui command to my session startup.

---

### Post by tylersticka on 2007-02-14
Thanks for the link but unfortunately when I attempt to use the GUI-less command that scans and connects automatically, I get the error "device does not support scanning" for my card.

---

### Post by tylersticka on 2007-06-13
FYI, all my wireless problems are currently solved. I thought I'd post this message to explain how I got to my idea wireless networking setup. I did so by ditching wifi-radar completely and instead adopting wicd, which you can get from [here]("http://wicd.sourceforge.net/").

I should note that the problem outlined in this thread occurred primarily in Xubuntu 6.10 Edgy Eft, but largely persisted after upgrading to Feisty. This tutorial was successful under Xubuntu Feisty Fawn.

[LIST=1]
[*]Uninstalled wifi-radar
[*]Enabled the "Wireless" connection in the Xubuntu Network Manager, but left the network name blank. Note that this is Xubuntu only, it is not the same Network Manager as Gnome. After enabling but leaving the name blank, the white box to the left of the wireless connection should be a dash instead of a check.
[*]Installed wicd, following [these instructions]("http://wicd.sourceforge.net/wiki/doku.php?id=faq") to install the application
[*]Opened the wicd GUI (see above link), connected to my network successfully.
[*]Clicked the arrow next to my network in the UI, and checked "Automatically connect to this network."
[*]Added the wicd tray to the start-up scripts(see above link).
[/LIST]

Sweet success! The network connects at startup automatically, flawlessly. wicd runs on Python and is super light on resources. Also includes a cool tray icon which shows the strength of your signal.

---

