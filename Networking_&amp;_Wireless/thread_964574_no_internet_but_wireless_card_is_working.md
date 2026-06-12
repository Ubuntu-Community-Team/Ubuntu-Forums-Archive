---
title: "no internet but wireless card is working"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by hosk on 2008-10-31
Hey,

My wireless card is supported out of the box now, with the at76 driver. The upgrade went a little sketchy, and i'm booted into 8.10 but internet doesn't work at all. 

Here's the catch. ifconfig shows eth0(wired--not plugged in) and wlan0(wireless) as both up, and here's a bigger mystery to me, the iwconfig/ifconfig shows wlan0 as BEHAVING NORMALLY. 

I have a link strength and signal level of 76/100 +/- 15, yet I can't ping google, or the gateway address.

Pinging the gateway address gives me
"From 169.254.5.96 icmp_seq=1 Destination Host Unreachable"
and it repeats where icmp_seq goes up until ctrl+C

a routing issue?

---

### Post by hosk on 2008-10-31
in dmesg i see "wlan0: no IPv6 routers present"

also, in dmesg everything looks totally normal with the at76_usb driver until i see 2 lines
"at76_usb: 2515: assertion dev->istate == INIT failed"
"at76_usb: 1777: assertion dev->curr_bss==NULL failed"

---

### Post by hosk on 2008-10-31
and just to clear up any of the easy possibilities, I can use linux on the router fine with 8.04 on my wireless laptop, and the router sees my desktop computer and assigned it an IP.

---

### Post by hosk on 2008-10-31
bump, this has to be an easy fix.

---

### Post by sygard on 2008-10-31
I had the same problem, and it seems to be linked with network manager not automatically asking the dhcp server for a new address. This can though be forced through dhclient.

```

sudo dhclient ethX

```

/sygard.

---

### Post by hosk on 2008-10-31
I feel like this is getting closer to the problem. DHCLIENT doesn't recieve any offers and I can't figure out why.

---

### Post by sygard on 2008-10-31
that's not good... :(

I have tried this with my setup on several (both secure and unsecured) wireless networks, and it always seem to work after I run dhclient.

On my desktop computer though, I completely removed network manager and all it's startup calls, so I don't need to worry about it wrecking my network connection. But I need it on my laptop, as configuring wlans' is a drag whithout it...

---

### Post by hosk on 2008-10-31
I appreciate all your help though, I've resolved to go elsewhere, either back to 8.04.1 or to a new OS/distro completely after this miserably failed upgrade. Lucky for me I have a blank hard drive I need to put to use anyway.

---

### Post by Zack McCool on 2008-10-31
first, try sudo dhclient wlan0 instead of eth0...

Also, if network manager is giving you problems, try installing wicd instead.  It is a much better interface for wireless.

---

### Post by hosk on 2008-10-31
dhclient doesn't get any offers with wlan0

after killing NetworkManager, ifconfig down/up wlan0 and dhclient wlan0, still no offers.

i had everything working flawlessly in hardy, should've stayed there.

---

### Post by hosk on 2008-10-31
i see "wlan0: no IPv6 routers present" in my dmesg, so i blacklisted IPv6 in my modprobe.d/blacklist file , and i continue to get that message, and still no offers.

---

### Post by hosk on 2008-10-31
I guess I'll mark this thread as solved. A complete reinstall of 8.04.1 LTS alternate solved my internet woes. Also, I noticed that 8.04 alt did a very good job of HW detection and allowing me to configure my wireless adapter before installation. Is it only LTS distros that are this good? Or should I get used to the inability to do that for future releases(8.10 desktop/alternate did not provide necessary hardware support for my wireless card)

---

### Post by Jeff Seager on 2008-10-31
I had the same problem today after upgrading from Hardy to Intrepid, and at the moment I can't find the forum post that gave me the solution. After entering all needed information in NetworkManager, the wireless still was not working and I had to log into another computer to get on this forum. The answer turned out to be UNINSTALLING NetworkManager. Someone offered this command-line solution for that:

sudo update-rc.d -f NetworkManager remove

In my case, because I had already entered all the necessary info (SSID, WEP password and such), no further configuration was needed after rebooting (but you must reboot). If you have not tried all that I tried first, you can click on the green Globe icon at the top right of your Gnome desktop after rebooting, and configure manually.

I recall having similar problems in the upgrade from Gutsy to Hardy, so I think this is a flaw worth noting in NetworkManager.

I hope this helps somebody!

---

### Post by hosk on 2008-11-01
I marked this thread as unsolved again, I tried doing your command line solution and I STILL don't get a dhcp offer.

---

