---
title: "WG111v3 - Working (Gutsy)"
date: 2008-01-19
forum: Networking &amp; Wireless
---

### Post by halucinations on 2008-01-19
Ok i have been struggling with getting this adapter working for about a week now!  Basically i read everything that i could find and applied what i learned.  First of all ndsiwrapper is needed.  

First off i got ndisgtk.
Then i got the wg111v3 drivers by following jonathanpeter post here. ([http://ubuntuforums.org/showthread.php?t=615471&highlight=wg111v3](http://ubuntuforums.org/showthread.php?t=615471&highlight=wg111v3)).
**Not all of the previous steps are needed i dont think, just the part to get the driver files (.inf and .sys)**
Then opened the windows wireless drivers (System->Administration->Windows wireless drivers). 
Next i loaded in the wg111v3.inf file, should be under Places->Home->WG111 if you followed the steps posted by jonathanpeter.

This is where it got tricky.  I had the same problem as everyone with WEP and internet connection.  So i turned off WEP and under no wireless security it worked like a charm.  But i dont like having no security so i tried WPA shared-key (i believe).  And it still works with WPA and its not continuously asking for the password!

For a disclaimer:  I am a Linux newbie.  So feel free to tweak my steps if you feel they are not right.

The bottom line is, try WPA security, it is working for me.

Thanks

Brad

---

### Post by madsmaddad on 2008-01-19
Well Done. 

It has taken me months to get my Wireless USB adapter working perfectly, But in short bursts when I had time. 

Thanks for posting . it could help someone else.

madsmaddad

---

### Post by wightghost on 2008-01-19
I've got the same Netgear adapter and I also have a Netgear DG834G wireless modem/router.  I had little trouble getting it to work with Windows Wireless Drivers just like you, Brad, but i cannot, no matter what I do, get WPA working.  The wireless works perfectly fine with no encryption ( but I have MAC filtering on and have disabled SSID broadcast).  AS soon as I enable WPA it all goes pear-shaped and nothing works.  In fact if I enable WPA then reboot, Ubuntu will hang about half way into the boot process.  When I unplug the USB adapter, Ubuntu then continues to boot!:mad:
I love Ubuntu otherwise but this is a nagging problem.

Brad (a different one)

---

### Post by halucinations on 2008-01-19
Well it seems that another problem raised its ugly head.  After my post last night i turned off my computer and went to sleep.  This morning there was no wireless.  It was not that difficult to get it working again, but it is a pain none the less.

What i did was:

sudo su -
ndiswrapper -l
ndiswrapper -i WG111v3.inf
ndiswrapper -l
modprobe ndiswrapper
iwconfig
ifconfig -a
dhclient wlan0

The driver should already be installed with what you have done previously with ndiswrapper.  

Wightghost - Try using WPA only, without MAC address filtering and enable the broadcast of ESSID.  Do you really need that secure of a network?  It is worth a try ya know.

Anyone else have any ideas on how to make the wireless settings more permanent?  When i started the computer there was not even a wireless tab under network configuration!  Any help is appreciated.

Brad

---

### Post by Hightide on 2008-01-20
> **halucinations said:**
> Wightghost - Try using WPA only, without MAC address filtering and enable the broadcast of ESSID.  Do you really need that secure of a network?  It is worth a try ya know.
Brad

I agree with above as I had some trouble setting up wireless with Netgear router/modem.

I have No mac address. Just broadcast ESSID and your WPA should work

Sorry Halucinations about your further problem as i have no idea

:)

---

### Post by wightghost on 2008-01-20
After seriously considering my network situation I've decided I don't *really* need WPA.  I live on acerage and the houses around here are spaced a reasonable distance away from each other.  So I've decided to hide the SSID and keep MAC filtering.  That should keep it fairly secure and the wireless works fine with that setup.  

Now if there was an open source driver for my Canon i350 printer I could ditch Windoze completely.  :)

Brad

---

### Post by halucinations on 2008-01-21
I just ditched the wg111v3.  I returned it and bought a Linksys WUSB54GC and it worked right out of the box.

---

### Post by msrk on 2008-01-21
I have a Netgear WG311v3 card working great.  Well almost. It only works in roaming mode and only starts once I log into my desktop.  I have read lots of forum threads and posts and cannot seem to get it to start on boot.  If my computer goes down while I am away it can restart itself but I cannot get the network to start on its own.

The router I connect to is set up for 64 bit WEP dhcp.  I have tried many combinations of static and not-static configurations in /etc/network/interface.

I did add ndiswrapper to /etc/modules which makes it possible to for the wireless net to start on login.  Does anyone know how to get it to start on boot?

Thank you,
Marc

---

### Post by stooshbunutu on 2008-04-10
I have found that configuring manually via network manager (disable roaming) will stop it dropping out whether encrypted or not, my router is hidden and encrypted and I have no troubles.

---

