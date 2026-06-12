---
title: "[SOLVED] strange poor wireless reception problem"
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by evencoil on 2008-09-10
I have a 2WIRE 2701HG-B router that is 8 feet away from my desktop in perfect line of sight. My desktop is running Kubuntu Hardy. I first had a TrendNet TEW443PI PCI wireless adapter and I got about 60% reception. I figured maybe the adapter was junk or defective so I bought an Edimax EW-7128G PCI card and put that in and now I get 50% but it fluctuates up to around 70% on occasion. With the TrendNet, third party hardware drivers were installed automatically for me, and when I put in the Edimax and booted, they were gone but wireless worked right off the bat. (Do I need to change drivers? If so, how?)

Now the strange part in my mind is that my laptop will get close to 100% reception sitting right next to my desktop on either Kubuntu Hardy or Windows 2000.

I only have one PCI slot (small form factor computer), otherwise my first instinct would be to switch PCI slots. What do you all think?

Also: I should add that I live in an apartment building in a dense urban area and there are tons of wireless signals all around me. I have tried changing my router to every channel that it can go on and still get the same result.

---

### Post by evencoil on 2008-09-14
If anyone has this problem in the future, here's a hint: don't pay any attention to KNetworkManager. It lies! When I run iwconfig in the terminal I get Bit Rate = 54 KB/s and Link Quality = 92 EVEN AS KNetworkManager says my signal strength is 50. Furthermore, KnetworkManager will fluctuate (as I mentioned before) even when there is no change under iwconfig.

---

### Post by Crafty Kisses on 2008-09-14
You may diagnose these network settings by activating and deactivating the wireless network interface from the Terminal, which shows some diagnostic messages:
```
sudo ifdown wlan0
sudo ifup wlan0
```
You may diagnose the network adapter status with commands:
```
ifconfig
iwconfig
dmesg
tail /etc/var/messages
```
I also want to see the results of this command:
```
lshw -C network
```
I'm thinking it could also be packet loss, it certainly sounds like it.

Packet loss can be caused by a number of factors, including signal degradation over the network medium, oversaturated network links, corrupted packets rejected in-transit, faulty networking hardware, maligned system drivers or network applications, or normal routing routines.

Some network transport protocols such as TCP provide for reliable delivery of packets. In the event of packet loss, the receiver asks for retransmission or the sender automatically resends any segments that have not been acknowledged.

You might want to check if there is any interference with like a phone or a microwave or even possibly a lamp. I know it sounds stupid but my lamp for some reason was causing some interference with my router, that can all lead to packet loss.

---

### Post by evencoil on 2008-09-14
Oops, I forgot to flag this as fixed (see my second post). The problem appears to have been only that KNetworkManager has some sort of display bug for signal strength. Here is the output of iwconfig:

```

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11  ESSID:"someagainstmany"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1F:B3:CF:DE:01
          Bit Rate=54 Mb/s   Tx-Power=12 dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B
          Link Quality=91/100  Signal level=-46 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

At the very same time that KNetworkManager shows signal strength of 52 and bandwidth of 62Mb/s (which would be curious for 802.11g, no...?).

---

