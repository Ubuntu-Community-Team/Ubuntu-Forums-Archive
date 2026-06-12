---
title: "Wireless Problems, help please"
date: 2008-01-28
forum: Networking &amp; Wireless
---

### Post by KyyubiDX on 2008-01-28
so here's the thing:

I have an Acer Aspire 5520 with ubuntu 7.10 and its up and running for most part...
for the wifi drivers i used: [http://ubuntuforums.org/showthread.php?t=512828]("http://ubuntuforums.org/showthread.php?t=512828") and i THINK its working but i can't be sure and here's why:
I am able to connect (it says connected) to my home network but when i open firefox it stucks on looking up and then eventually says it can't open the site

also: i think i may have screwed up somthing related to the boot because everytime i boot linux the X server doesn't work properly and i have to re-install the NVIDIA drivers everytime for it to work properly... any ideas?

thanks in advance

---

### Post by YoungJim on 2008-01-28
Hi.  I've an Aspire 5100 for comparison.  Have you tried a wired connection to your router?  For comparison.  If you're using network manager, I'd suggest turfing it and getting wicd ([http://wicd.sourceforge.net]("http://wicd.sourceforge.net")) as it is a lot easi er to use.

     If it says connected, but you're not getting anywhere, then that sounds like you're not getting an ip address from your router.  Try System -> Administration -> Network Tools; try pinging your router to see if you can a response.  

     Anyway, try it with wicd first, let us know how it goes.  Jim

---

### Post by kevdog on 2008-01-28
Your going to have to provide more details about your wireless before anyone can really help you.  If you could provide

lshw -C network
iwlist scan

That would be helpful.

---

### Post by KyyubiDX on 2008-01-29
ok more details...

My wireless LAN is a Windows XP, ASUS SOFT AP (which turns your wireless card into an access point)... The main PC's IP is 192.168.0.1 with a wub net mask of 255.255.255.0
my PSP can connect to it with no problem but the laptop with ubuntu does one of two things:

1. If I don't use a Static IP ith custom subnet mask and DNS it never obtains an IP adress when connecting
2. If i do insert an Static ip (192.168.0.2), a custom subnet mask (255.255.255.0), gateway (192.168.0.1) and DNS 1,2,3 (192.168.0.1), it says it connects but when I try and ping the main PC it says destination host unreachable... this enough?

EDIT: i just found out that: "sometimes it happens that ndiswrapper fails to assign a MAC address to the
wifi card, to fix that do the following
sudo nano -w /etc/network/interfaces
add the line
pre-up /sbin/ifconfig wlan0 hw ether XX:XX:XX:XX:XX:XX
where XX:XX:XX:XX:XX:XX is the MAC address of the card."

how do i know the mac address of the card?

---

