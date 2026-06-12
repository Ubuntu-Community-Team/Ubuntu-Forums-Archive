---
title: "Wireless not working (WG311) and more things slowly crashing!"
date: 2006-09-30
forum: Networking &amp; Wireless
---

### Post by kkram13 on 2006-09-30
Well... it was probably a bad idea to begin with but here goes. 

For a number of reasons I'm wanting to set up my desktop with a wireless card: Netgear WG311 v2 (a homeless freebie from work). Plugged the card in, booted, could see it in the System>Administration>Networking bit. Told it to connect to, ah, er, a neighbour's connection that's not secure. SSID was 'default'. Told it to make wlan0 the default connection. This did not work: it will not connect to the network. 
Clearly the settings are wrong. An added problem is that I cannot now access Networking: if I click on anything in System>Administration it mulls it over and then does nothing. I am still a member of the sudo group, so that's not it. Typing a command using sudo in a terminal window works, but first gives an error message "unable to look up (none) via gethostbyname()". Later it wouldn't execute whatever the command was but that's now okay. To top it all off, when I reboot it cannot start basic networking.

I'm now afraid to do anything else before the whole thing falls over! I have installed ndiswrapper using the HOWTO and that works, but still doesn't give me an internet connection.

Two more bits: no, I cannot for the time being connect in a wired fashion. And later on today I will have access to an internet connection for which I will know the details, like service provider etc. Actually make that three: I used to have a speedtouch modem which worked but I never uninstalled the various bits. I did deactivate the modem in networking when I still had access to that, but I know that pppoa or something is still active (I think).

Oh and no, I don't have another wired internet connection so installing is tricky! I can, however, reboot into Win2000 which gives me internet access and download .deb files.

Last bits, in case they are useful:
mark@(none):~$ iwconfig:
lo        no wireless extensions.

wlan0     IEEE 802.11b+/g+  ESSID:"STABB0BEE"  Nickname:"acx v0.3.21"
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr: off
          Encryption key: off
          Power Management: off
          Link Quality=35/100  Signal level=9/100  Noise level=0/100
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

**Note it gives me a link quality and signal level! Yet Firefox cannot load anything...

mark@(none):~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:104 errors:0 dropped:0 overruns:0 frame:0
          TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:7056 (6.8 KiB)  TX bytes:7056 (6.8 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:09:5B:BB:0B:EE
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:185


/etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto wlan0

iface wlan0 inet dhcp

wireless-scan


---
If anyone has any ideas on what to do/try, I would be very very grateful. So far I've managed to get everything working under Linux but this one is beyond me.

Taa very muchly!

Mark

---

### Post by eltorodeoro on 2006-09-30
Network Manager is a useful tool for this sort of thing.  It's designed to manage multiple connections - wired and wireless.  Try removing (commenting out) the lines in /etc/network/interfaces that have to do with wlan0.  Then reboot.  See if that gets your wired port back.  Of course, if you can't sudo, you may be up a creek there.

If it happens that you're able to boot up normally, go to synaptic (or apt-get) and load network-manager-gnome.  That should fix you right up.

jc

---

### Post by kkram13 on 2006-09-30
Cheers eltorodeoro - the problem is that at the moment I do *not* have a straight connection to the net from ubuntu. I can reboot my computer to windows and it picks up the card and network no problem. I also have a (windows) laptop and so I can download files, copy them across and install stuff.

For the past few hours I've been trying to install NetworkManager - I get stuck when it tells me that 
package requirements (dbus-glib-1 >= 0.60) were not met
I cannot find this package and seem unable to get it to accept dbus0.60 from ubuntu. Ugh. It's at times like this -much as I hate saying it- that Windows works sooooooo much easier!

Mark

---

### Post by eltorodeoro on 2006-10-01
That's why it's so aptly called dependency hell.  The error you're getting is indeed strange, as that particular package on the Debian site is only listed at 0.23.4.  This is why package managers are so great.

Did manually editing /etc/network/interfaces not work?  Also, I compared your file with my own, and I noticed that you're missing **auto eth0** before the **iface eth0 inet dhcp** line.  Not exactly sure what the auto tells it - maybe duplex/speed?  Maybe try inserting that...

(longshot) Is it possible that whatever is providing DHCP is no longer working?  Have you tried statically addressing your eth0?

jc

---

### Post by bdann on 2006-10-05
kkram13, I am wondering if you ever made any progress on this issue?  I'm having the same problem with the same wireless card.

---

### Post by kkram13 on 2006-10-06
Apologies, I was away getting my headwounds treated - hitting your head against a wall repeatedly ](*,)  just isn't good for it ;) 

And no, no progress. As far as I can tell, the card is recognised, the drivers are present, I give it the right settings. Iwconfig/ifconfig even give me the impression I'm connected - but I get nothing.

Further complication is that I don't have access to the router at the moment, so I cannot easily turn off WEP to try with a non-secure connection. In a month's time, that's all set to change when the router comes back into my flat. I will then connect through a network cable. I'm giving up, life's too short.

It's depressing. I really like Linux, I like what it stands for, and so far I've been able to solve all the problems I've had, but this one has me stumped. Normally I would just try to get another wireless card, but as this is only a stop-gap measure, it's not worth it. Never mind.

Good luck, and let me know if you do get it to work...

Mark

|\/|<

---

### Post by ruleboy on 2006-10-07
I had a problem like this, basically everything was "running" but there was no network traffic.

The problem turned out to be this; 

I had configured my wireless router to assign a specific IP address to my computer AND in the computer I had set the wireless interface to use that same specific IP address (Static IP).

Why this did not work is beyond me, the solution was to set the wireless interface to use DHCP after which the router would assign it the IP address I wanted and everything worked.

---

### Post by apoth on 2006-10-08
Try something like ```
options acx firmware_ver=1.2.0.30
``` in /etc/modprobe.d/options

---

