---
title: "Kubuntu 8.04 (KDE 4 Remix) ndiswrapper working - knetworkmanager not seeing wlan0"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by petersk on 2008-05-27
I "finally" got my Linksys wpc300n working on the laptop I'm using, but can't seem to get Knetworkmanager to see any devices.[http://ubuntuforums.org/showthread.php?t=766560&highlight=broadcom+wireless+setup+hardy](http://ubuntuforums.org/showthread.php?t=766560&highlight=broadcom+wireless+setup+hardy)

I used the lscmnd driver from linksys's website and ndiswrapper 1.9 (which I had to USB copy over since wireless is the only way that laptop can connect), and had to delete the extraneous *.sys files installed in the ndiswrapper directory to get wlan0 to show up (I also followed the various posts here on blacklisting, etc).
  Now, wlan0 shows up, and 'iwlist wlan0 scanning' shows the three available wireless networks available in my area.
  Unfortunately, I cannot connect to any of them through knetworkmanager (or any other means that I know of for that matter -- which doesn't mean that much).
  Does anyone have any clue how to get knetworkmanager to see the ndiswrapper hardware?
  I've tried 1) totally removing interfaces, 2) commenting out wlan0, and 3) adding: 
auto wlan0
iface wlan0 inet dhcp
    pre-up ifconfig wlan0 up
    pre-up iwpriv wlan0 set AuthMode=WPAPSK
    pre-up iwpriv wlan0 set EncrypType=TKIP
    pre-up iwpriv wlan0 set WPAPSK="YOUR_WPA_PSK_KEY"
    pre-up iwpriv wlan0 set SSID="YOUR_SSID"
    pre-up iwpriv wlan0 set NetworkType=Infra
to it.
  None have worked.  I thought about 'sudo aptitude purge network-manager', but that gives me some "dependency" problems and it then wants to remove kde-desktop (kde4).

Thanks in advance,
Kurt

---

### Post by petersk on 2008-05-28
Well, low-and-behold, I figured out my problem.  It seems that knetworkmanager has changed a little and responds to both left and right clicks now.  After getting no response here I figured I'd go back to the drawing board and try changing /etc/network/interfaces by removing everything again and rebooting.  
  I accidentally right clicked on knetworkmanager, and there was the "familiar" screen to select an SSID!
I have a connection now.
Kurt

---

