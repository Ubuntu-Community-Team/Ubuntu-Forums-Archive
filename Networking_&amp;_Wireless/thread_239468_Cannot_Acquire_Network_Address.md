---
title: "Cannot Acquire Network Address"
date: 2006-08-19
forum: Networking &amp; Wireless
---

### Post by infocom on 2006-08-19
Hi all

I've been having huge problems connecting to the internet using wireless, like so many others.

I have now got the furthest I ever have been, it is in my grasp I am sure.

First I abandoned my Level One and Belkin wireless and bought a LinkSys WUSB11V4 because I thought it was compatable. I may have got the versions wrong though as Ubuntu did recognise it. But I managed to get it to work using ndiswrapper and the Windows driver. So the card is now recognised and configured, but it would not connect. So I decided to use Wifi Radar.

Now, I can see ALL the wireless networks in range! They report strength, if they are encrypted etc. So that means my card is working surely?? But using Wifi Radar I get a "Could not acquire IP address". I have used the correct password and I get the error if I try to connect to my neighbours non-secure wireless connection.

So does anyone know why I am not being assigned an IP Address???

I also tried using static and this does not work.

Thanks

Laurie

---

### Post by infocom on 2006-08-19
P.S. I can't ping my router or any other address. I have the default settings if the profile in Wifi Radar and also tried it by entering correct settings still no joy.

Running iwconfig shows ESSID as off/any and Access Point as Not-Associated. Maybe something to do with this?

---

### Post by infocom on 2006-08-20
Hi

Can anone help?

Laurie

---

### Post by lupine_nickt on 2006-08-20
try running sudo iwconfig <interface> ap <MAC address of router>

The MAC address shows up as 'Address' in the iwlist <interface> scan list.

Also, make sure that you're running in Managed, as opposed to (say) Master or Ad-Hoc mode. 

iw

xF,

...Nick

---

### Post by infocom on 2006-08-20
Hi, thanks.

At first it looked like it assigned the ESSID. But I accidentally copied the wrong one (my neighbours). So I did the command again and it did not change. I notice encryption was off on it anyway, so I ran "iwconfig wlan0 enc s:mypassword" to encrypt and assign password, but ESSID went back to off/any. So I ran your command again using the right Mac address and it doesn't change at all now. So its back to ESSID off/any and your command no longer working.

---

### Post by infocom on 2006-08-20
Alss, for info...

When I run a "dhclient" command I get:

Listening on LPF/wlan0/00:12:17:98:14:5d 
Sending on LPF/wlan0/00:12:17:98:14:5d 

But this is not the MAc address of wlan0 which shows up using the  "iwlist wlan0 scan", and is not any MAc address on this list (for eth0 etc).

And I also get:
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
(this shows a few times)
No DHCPOFFERS received
No working leases in persistent database - seeping

For info, my router is setup for subnet 255.255.255.0

---

### Post by infocom on 2006-08-20
SUCCESS (sort of :( ) If I disable ny security on my router, it connects, I get an IP address and can connect!!! So therefoe it must be the WPA-PSK security I was using?? I need to have this security enabled on the router, so the next step is getting Ubuntu LinkSys WUSB11v4 to work with WPA-PSK security (pass phrase). I did enter a password, but did not work as you know.

Anyone know how?

---

### Post by infocom on 2006-08-20
I have decided to install Network Manager as it looks like this will manage my WPA-PSK password and allow me to connect apparently. 

I installed Network Manager, the icon is in my tray, but it has a Warning sybol. I click on it and "Enable Networking" but Netowrking is not enbabled. I still see the warning. I go to enable it again and it it still says "Enable Network" for me to choose in the drop down, but the tick next ot the choice is gone. I click it, and next time the tick is back and it still says Enable Networking. Hovering the mouse over it says "Networking Disabled".

So anyone know a straightforward guide to allow you to connect to WPA-PSK secure connection??? I mean, thats got to be one of the most common connections, to allow to use a password, right??

P.S. I htink evgeryitme I try it my router kicks off my windws PC ?? Or is this just a bizarre cioncidence?

---

### Post by Y4CcduyctJL3 on 2006-10-24
i'm in exactly the same boat, except with 48 bit wep hex key.  i have the driver working, and it'll even see the router out there.  i put the info in (that i know is correct because it works on my other systems) and can't get dhcp to work. ](*,)  is there some trick i'm missing for getting ndiswrapper to work with dhcp and wep?

---

### Post by Y4CcduyctJL3 on 2006-11-13
so now i'm able to get on the internet, but it's sort of a backwards way.  after startup i can use iwconfig and connect manually, but what does that indicate isn't working?

---

