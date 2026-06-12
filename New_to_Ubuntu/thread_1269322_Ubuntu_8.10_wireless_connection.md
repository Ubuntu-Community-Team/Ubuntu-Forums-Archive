---
title: "Ubuntu 8.10 wireless connection"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by garrydog on 2009-09-18
Hi
I am having dificulty connecting to my wireless network,I am on Sky broadband and have been on to the pouter settings page for the settings 192.168.0.1.Now in network connections-and editing auto,can someone tell me what setting that I should put in the boxes eg,
CONNECTION NAME
SSID
MODE
BSSID
MAC ADRRESS
MTU.
The laptop is picking up my network and is trying to connect but failing to do so.
Thanks .

---

### Post by mapes12 on 2009-09-18
> **garrydog said:**
> Hi
I am having dificulty connecting to my wireless network,I am on Sky broadband and have been on to the pouter settings page for the settings 192.168.0.1.Now in network connections-and editing auto,can someone tell me what setting that I should put in the boxes eg,
CONNECTION NAME
SSID
MODE
BSSID
MAC ADRRESS
MTU.
The laptop is picking up my network and is trying to connect but failing to do so.
Thanks .Any settings like that will need to be provided to you by the documentation with your Sky router. If you haven't got them then their tech desk should be able to help.

---

### Post by garrydog on 2009-09-18
Hi
Thanks for the reply,I have got the MAC address ,but I don't know what to put in the box marked BSSID,according to the pop up it should look something like a MAC address.

---

### Post by garrydog on 2009-09-18
I now have put the Mac address into the box on the edit pannel,but it will not allow me to OK the pannel.

---

### Post by garrydog on 2009-09-18
Hi
I now have the laptop working wired,AUTO eth0.It is still detecting my wireless network but it will not connect.I have tried all ways in the edit box to try an fix the problem but it is still the same.

---

### Post by nickpaton on 2009-09-18
Regarding MTU etc, I assume you're asking what they're supposed to be on the router.
 
I also assume from the IP address that you're using a Netgear router, so I suggest pressing the recessed reset button on the back of the router to get the default sky settings and then starting again.

I've found [**this useful page**]("http://www.skyuser.co.uk/forum/view-router.html") which goes through the Netgear router settings (ignore the Windows stuff).

What I also suggest is to first of all set up the router with an SSID but NO encryption - ie an open connection.  Make sure you always click the router screen "Apply" button to save the settings.
Log out of the router and test the whole setup using a wired Ethernet connection to make sure you can access the Internet etc. from the Ubuntu machine.

Then move to Ubuntu wireless setup and enter the SSID and as per the router but with no encryption.
Disconnect the wired connector and see if you can now access the Internet wirelessly.

If you can go back into the router and apply the appropriate encryption and mirror the settings on the laptop.

By building up your wireless connection this way you hopefully will get connected as you want having checked each stage at a time.

Good Luck!

---

### Post by garrydog on 2009-09-19
Hi
Thanks for the reply,progress at last,the password on my router is set to WPA-PSK(WI FI protected accsess pre-shared key)on the router setup i disabled this ,and the laptop connected wirelessly.
So my problem must be something to do with the security password on the laptop.

The options on the router are,

Security Options
Disable
WEP (Wired Equivalent Privacy)
WPA-PSK (Wi-Fi Protected Access Pre-Shared Key)
WPA-802.1x

the options on the linux laptop are,
WEP4/128-BIT KEY
WEP128-128-BIT PASSPHRASE
LEAP
DYNAMIC WEP(802.1X)
WPA & WPA2 PERSONAL
WPA & WPA2 ENTERPRISE.

So what setting do I need to put on the linux laptop to enable the laptop to connect .

---

