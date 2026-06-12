---
title: "HP-NC6000 wifi configuration"
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by maurizio73 on 2006-10-29
Hi All,
I've a laptop HP nc600 whit wifi card embadded it's "HP WLAN 802.11 b/g W400" and on windows it uses ar5211.sys driver.

I'm trying to configure this card with ubunt 6.06 but It' doesn't work. 

From networking setting panel I'm able to see the wifi card and I configured it but nothing works.

From command line, whit the utility iwconfig I get this output:

"[COLOR="Red"]maurizio@maurizio:~$ iwconfig
lo        no wireless extensions.

ath0      IEEE 802.11g  ESSID:"23maurizio73"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:66:37:40:31
          Bit Rate:54 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/94  Signal level=-44 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.[/COLOR]
"

It seems to be configured and active but It doesn't work.

Any ideas about the issue?

Thanks in advance,
Maurizio

---

### Post by maxdevis on 2006-10-30
i had the same problem in dapper
but in edgy everything works fine

---

### Post by maurizio73 on 2006-11-05
I installed edgy and the last version of network-manager but wifi connection doesn't work yet. It requires the wep key, I wrote it but wifi card doesn't get the IP address.
I tryed to modify my network settings, I deleted all security (wep, hiden SID and mach filtering) but the wifi network card gets an IP address like 169.*.*.*, that doesn't belong to router defined range.

Any suggestion?

Thanks
Maurizio

---

### Post by spaztech on 2006-11-08
This works for me.

[http://spaztech.wordpress.com/ubuntu-wireless-hp-nc6000/](http://spaztech.wordpress.com/ubuntu-wireless-hp-nc6000/)


Ubuntu wireless & nc6000

How to get wireless working on an HP nc6000 with Ubuntu using ndiswrapper.

   1. Download the [Atheros 5211 Drivers from HP]("http://h18007.www1.hp.com/support/files/hpcpqnk/us/download/23550.html")
   2. Extract them to /Desktop/drivers. #the file you need is net5211.inf
   3. Open a terminal console and CD to the /Desktop/drivers directory. #or wherever you saved the files to
   4. sudo ndiswrapper -i net5211.inf #this installs the driver
   5. sudo ndiswrapper -l #this will list your installed driver
   6. sudo modprobe ndiswrapper #tells the kernel to use ndiswrapper as a module
   7. sudo ndiswrapper -m #adds this to your startup
   8. Go to System> Administration >Networking and check your configuration #I use DHCP but set yours accordingly.
   9. Enjoy!

-spaztech

---

### Post by stavinski on 2008-06-23
Looks like the page this links to has moved. Anyone know if this should still work with the new link... trying it.

---

