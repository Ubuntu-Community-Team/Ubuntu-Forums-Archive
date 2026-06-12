---
title: "WPA, TKIP, PEAP, RADIUS, etc."
date: 2005-05-24
forum: Networking &amp; Wireless
---

### Post by valnar on 2005-05-24
If you know what those acronyms are, then hopefully you clicked on my topic to help me!   :smile: 

I run Windows XP & Ubuntu on an IBM T41 laptop and connect to my Corporate network.  Windows XP works fine.  We run Cisco Aironet access points and they are configured to use WPA/TKIP and PEAP or LEAP for authentication.  PEAP is preferred, and requires a client root certificate from Verisign, which is easy to do in Windows especially since Microsoft includes all the major root certs.  I also need to authenticate against the Radius server, which in turn authenticates against ADS, something the "Wireless Zero Configuration" service does for you quite easily in XP.

I would like to get WPA-PSK working for my home Linksys router too, which doesn't require RADIUS authentication - still TKIP though.

So what is the equivalent to this functionality in Linux?  I am a newbie (you've been warned) and installed the WPA Supplicant, but don't know what to do next.  Is it all text editing from here on out, or is there a GUI front end?

-Robert

---

### Post by luca_linux on 2005-05-24
You have to install "wpa_supplicant".
Just follow the second part of this howto: [http://www.ubuntuforums.org/showthread.php?t=26623](http://www.ubuntuforums.org/showthread.php?t=26623)
Obviously you should read the readme file to know the driver you need for your wireless card if you don't have ipw.

And if I remember well, maybe you also need a CISCO client...try just wpa_supplicant and report your experience...if you don't manage to get it working, maybe you need this client.

---

### Post by anders.ostling on 2005-05-25
I have succeeded with the combination Ubuntu + modified ipw2100 (for proper WPA support) and xsupplicant. We are using Cisco AP's with a central ACS for administration. The ACS is connected to our AD domain controller. So I have to specify AD domain + userid + hardcoded password in the xsupplicant config file. Works just fine with LEAP pre-authentication. Have not tried PEAP or other means of auth.

Anders

PS Dont forget to specify the -W command line parameter to xsupplicant. Without it, authentication was successful but no WEP key exchange was done.

---

### Post by Kitty on 2005-07-26
[QUOTE=anders.ostling]I have succeeded with the combination Ubuntu + modified ipw2100 (for proper WPA support) and xsupplicant. We are using Cisco AP's with a central ACS for administration. The ACS is connected to our AD domain controller. So I have to specify AD domain + userid + hardcoded password in the xsupplicant config file. Works just fine with LEAP pre-authentication. Have not tried PEAP or other means of auth.

Anders

PS Dont forget to specify the -W command line parameter to xsupplicant. Without it, authentication was successful but no WEP key exchange was done.[/QUOTE]
 Can you tell us :
- which version of ipw2100 you are using (with which patch)
- are xsupplicant and wpa_supplicant installed with apt-get ? or compiled from source ? which version ?

I used many versions of ipw2100, with many patches, with many version of wpa_supplicant and xsupplicant, and nothing works... :(

---

### Post by Kitty on 2005-07-28
Finally, I got ipw2100 and xsupplicant working.

I installed :
- ieee80211 v 1.0.3
- ipw2100 v 1.1.2 + patch for compilation with ieee80211 v 1.0.3
- xsupplicant 1.0.1

The problem was in my xsupplicant.conf.
I added the line :
first_auth_command = <BEGIN_COMMAND> echo "I am connected"<END_COMMAND>

Yes, this line does nothing !
But without it, xsupplicant stops after authentication. With it, xsupplicant stays running (xsupplicant -i eth1 &). After that, I just have to enter "dhclient eth1".

Hope it could help someone.

---

