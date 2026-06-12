---
title: "EAP-TTLS university wireless on eee 1000h"
date: 2008-10-07
forum: Networking &amp; Wireless
---

### Post by mrsudo on 2008-10-07
im at the university of manitoba, just loaded my new eee 1000h up with ubuntu eee 8.04.  works great, only thing is it wont connect to the secure network at my school.  its 802.1X EAP-TTLS.  

i've tried following [this]("http://avocet.cs.umanitoba.ca/~tliu/um_secure_linux_wifi.html") guide, with no success.

i also have tried using both network-manager and wicd....

anyone at uofm got secure wireless on linux?

---

### Post by mrsudo on 2008-10-07
i forgot to add that i use the following script to automate wpa_supplicant:

```
#!/bin/bash

iwconfig ra0 essid uofm-secure
wpa_supplicant -c /etc/wpa_supplicant.conf -i ra0 -D Rt2860STA
dhclient ra0
```

---

### Post by willca on 2008-10-08
Did you create this file?

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=2
fast_reauth=1

network={
        ssid="uofm-auth"
        key_mgmt=IEEE8021X
        eap=TTLS
	anonymous_identity="anonymous"
	identity="[UMNETID]"
	password="[PASSWORD]"
	priority=2
        phase2="auth=PAP"
}

Before trying to run your command to execute wpa?

---

### Post by mrsudo on 2008-10-09
i have that exact wpa_supplicant file, i start my script and it told me the RT2860STA is an invalid driver.  i put wext in its place, and it seemed to take away all the errors i was recieving except it will try and authorize, but just time out instead.

Do i have to use a script to connect using DHCP or can i use a networking manager?

sorry, i can't post my terminal output seeing im not using my eee, i will try asap

---

### Post by harvey69 on 2008-10-13
Hi,

I followed the same [guide]("http://avocet.cs.umanitoba.ca/~tliu/um_secure_linux_wifi.html") as you without any results. 

Just a quick note regarding the wpa_supplicant.conf file, according to the most recent update of the guide in the you must comment out (or delete): "ctrl_interface_group = 0" (no longer needed with the newest wpa_supplicant), and "ap_scan=2"(because the SSID is now broadcast). And since the guide was made i think the SSID of the secure University of Manitoba network changed from "uofm-auth" to "uofm-secure".

So my unsuccessful wpa_supplicant.conf file looked like:

[B]ctrl_interface=/var/run/wpa_supplicant
eapol_version=1
fast_reauth=1
network={
        ssid="uofm-secure"
        key_mgmt=IEEE8021X
        eap=TTLS
	anonymous_identity="anonymous"
	identity="[UMNETID]"
	password="[PASSWORD]"
	priority=2
        phase2="auth=PAP"
}[/B]


But I'm pretty sure you already new that. Please let me know if you somehow manage to get this working. I've been trying for hours without any results and I am slowly going insane.

Thank you,
Harvey

---

### Post by mrsudo on 2008-10-31
i've mainly been tweaking that short script i wrote, is there any way to use wpa_supplicant or xsupplicant alongside a network manager?

i also seem to have trouble using the unsecured network as well, when on campus.  i've only been able to connect maybe 3 or 4 times out of the 200 i've tried.  Everytime it was in EITC, which luckily for me is where i spend most of my time :)

hope you have better luck than me, Harvey. let me know if you do

so anything anyone anyone can help with would be much appreciated..

---

### Post by chris.pappas on 2008-11-03
Nice work on this Bruce... so did you actually get it working?

I'm going to try setting up Ubuntu on the EEE 701 pc and see if I can get it working :)

Chris

---

### Post by CodeAlias on 2008-11-09
Hi,

This is a [guide on EAP-TTLS with wpa_supplcant  ]("http://www.codealias.info/technotes/wireless_security_wpa/wap2_with_eap-ttls_using_wpa_supplicant_and_client_ssl_certificates_linux_setup")

Hope it helps.

---

### Post by mrsudo on 2008-11-14
i just went to visit to the computer support desk and a helpful guy told me they dont "officially" support linux but a coworker of his had got it working.  he sent me an email with instructions on how to set up uofm-auth with intrepid. 

unfortunately i have hardy installed on my laptop, but i will still give it a shot.  i have not brought my laptop today so will have to wait until monday to see if everything works out.  

the .pem CA certificate file is attatched to this post.
i think this may be the only thing i am missing considering my wpa_supplicant file is exactly the same as others with working wireless.

I will post again next week letting you know if i am successful.  :)

e-mail is as follows:

-----------------------------------------------------------------------------

After downloading the lastest version of Ubuntu. (something-or-other Ibex) it looks like secure wireless workless effortlessly now. Looks like the key components in making this work (as far as I can tell are nm-applet 0.70 and the 2.26-27 kernel (at least on iw3965 chipsets) for those of you using other distros).

Since this isn't an LTS distro, instructions on enabling the upgrade can  be found here:
[http://www.ubuntu.com/getubuntu/upgrading#Network%20Upgrade%20for%20Ubuntu%20Desktops%20(Recommended](http://www.ubuntu.com/getubuntu/upgrading#Network%20Upgrade%20for%20Ubuntu%20Desktops%20(Recommended))

Anyways, once that's all taken care of, start off by right clicking on the nm-applet icon on the task bar and select edit connections.

Pick the wireless tab as shown below and click the add button.

You'll be presented with the following. Enter the fields as shown below.

Next click on the 'wireless security' tab and fill out as shown below.

I've attached the uofm.pem file to this email.

No need to worry about the IPv4 settings. Save all of this and it should
connect without any hassle.

Have Fun.
Bruce


-----BEGIN CERTIFICATE-----
MIID3DCCA0WgAwIBAgIBADANBgkqhkiG9w0BAQQFADCBqzELMAkGA1UEBhMCVVMx
CzAJBgNVBAgTAk1JMRIwEAYDVQQHEwlBbm4gQXJib3IxITAfBgNVBAoTGEludGVy
bGluayBOZXR3b3JrcywgSW5jLjEUMBIGA1UECxMLc2FtcGxlIHVuaXQxHTAbBgNV
BAMUFGNhQHNhbXBsZWNvbXBhbnkuY29tMSMwIQYJKoZIhvcNAQkBFhRjYUBzYW1w
bGVjb21wYW55LmNvbTAeFw0wMzAzMDcxMzI0NTdaFw0xNjExMTMxMzI0NTdaMIGr
MQswCQYDVQQGEwJVUzELMAkGA1UECBMCTUkxEjAQBgNVBAcTCUFubiBBcmJvcjEh
MB8GA1UEChMYSW50ZXJsaW5rIE5ldHdvcmtzLCBJbmMuMRQwEgYDVQQLEwtzYW1w
bGUgdW5pdDEdMBsGA1UEAxQUY2FAc2FtcGxlY29tcGFueS5jb20xIzAhBgkqhkiG
9w0BCQEWFGNhQHNhbXBsZWNvbXBhbnkuY29tMIGfMA0GCSqGSIb3DQEBAQUAA4GN
ADCBiQKBgQDlChOB/eL+S/Jk8kDDtQnXaExl9f03XvO3DzGss1yPosVPWPaWQWdX
G+F436T3jAzMnNShvSs77jYPONk7Y2V7J5PMLgjIBP3dZgWAL9EeHVlDWgtjX+EP
zCZhu30ALsPiG75dxfMCFdlPEg2Bh3TC+ptIkm5gyU8toURrgGpXxQIDAQABo4IB
DDCCAQgwHQYDVR0OBBYEFDhmBP57DQcYnIMmVqiCvwyRUhpmMIHYBgNVHSMEgdAw
gc2AFDhmBP57DQcYnIMmVqiCvwyRUhpmoYGxpIGuMIGrMQswCQYDVQQGEwJVUzEL
MAkGA1UECBMCTUkxEjAQBgNVBAcTCUFubiBBcmJvcjEhMB8GA1UEChMYSW50ZXJs
aW5rIE5ldHdvcmtzLCBJbmMuMRQwEgYDVQQLEwtzYW1wbGUgdW5pdDEdMBsGA1UE
AxQUY2FAc2FtcGxlY29tcGFueS5jb20xIzAhBgkqhkiG9w0BCQEWFGNhQHNhbXBs
ZWNvbXBhbnkuY29tggEAMAwGA1UdEwQFMAMBAf8wDQYJKoZIhvcNAQEEBQADgYEA
2pGPR2ljCrIUTJ6W4GriFznqhUNO/Lk5vPoeJe1vjJF/HPGSHus4pg6ZzXNt5hU5
s4iK4SZ2C0VssbDZ3eo199HP0V+D+qYfHQw56XkvSv0ASFoiqTWsCs8tp9UJOxp8
0Z3sn2wc3MKWnGetNVyrDx9rGVs1nF+jK/vhHEJhFm4=
-----END CERTIFICATE-----

---

### Post by mrsudo on 2008-11-14
after just rereading the e-mail, he says he thinks nm -applet 0.70 is the key to connecting.  

i did some quick searching and found that there is only an official 0.6  package for hardy.  if your looking to upgrade to 0.70 (which looks like it works perfectly with ttls and pap) and keep your current installation then i advise you check out these threads:

[http://ubuntuforums.org/showthread.php?t=797059](http://ubuntuforums.org/showthread.php?t=797059)
[http://ubuntuforums.org/showpost.php?p=5305278&postcount=82](http://ubuntuforums.org/showpost.php?p=5305278&postcount=82)

everything seems to be working fine on my home network.  now comes the hardest part of waiting for monday so i can test uofm-auth....
im not quite eager enough to make the trip down to campus to test it out.  considering its an hour and a half bus ride there and back.  

i'll post the outcome asap!

---

### Post by mrsudo on 2008-12-11
I ended up just giving in and installing intrepid for the new NetworkManager applet.  it ended up pretty much breaking my wireless.  I haven't been able to totally figure out how to fix it.

NetworkManager shows me the wireless networks, although they appear to be much weaker than they actually are. My home network is barely visible even though it is a draft N router.  

I've been able to write myself a little script which will connect but it periodically disconnects and it's a real pain in the *** to keep restarting.  I still haven't been able to connect to the secure wireless. (im hardplugged in at a comp lab at school right now)

---

### Post by mrsudo on 2009-01-07
So I got a few things worked out, my wireless works with the new network manager.  works flawless with my network at home, and the unsecured at school.  

I still can't connect to uofm-secure!  the applet just shows one of the circles lit up and says it is connecting.... but just hangs there.

Also, the networks at school show a VERY weak signal when i know for a fact that they should not.  After connecting to the unsecured, it shows a signal strength of 95%.  

I am just using the default wireless drivers used in ubuntu eee 8.04.1

any ideas?

---

### Post by Favux on 2009-01-07
Hi mrsudo,

It's hard for me to tell, based on what you posted, but this work around may be of some use to you:

[http://ubuntuforums.org/showthread.php?t=1010650]("http://ubuntuforums.org/showthread.php?t=1010650")

I hope this useful.

---

### Post by mrsudo on 2010-01-20
it's been soo long and believe it or not i still haven't found a working solution....

i guess i haven't really put too much effort into it.  trying again.

---

### Post by oOarthurOo on 2010-06-16
UofM just changed their methods, until about October this should work, at which point you'll need to get their WPA2-Enterprise (ssid: uofm-wpa) working. Until then, in wicd, select TTLS-WEP, use your username, password and under auth write "PAP".

---

