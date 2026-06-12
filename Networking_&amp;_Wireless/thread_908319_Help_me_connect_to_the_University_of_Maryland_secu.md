---
title: "Help me connect to the University of Maryland secure wireless! :)"
date: 2008-09-02
forum: Networking &amp; Wireless
---

### Post by _Atreides_ on 2008-09-02
Hello komrades! Today is the first day of classes at the UMD and  i cannot seem to connect to the secure wireless network! They have guides on how to connect with a mac and pc but not with linux :(. They did give a list of general parameters which can be found at [http://www.oit.umd.edu/units/nts/noc/wireless/generic_config_chart.html]("http://www.oit.umd.edu/units/nts/noc/wireless/generic_config_chart.html"), and I am not sure what to put into my network manager. If anyone can send a pic or tell me what to do it would be greatly appreciated thank you!

---

### Post by timcredible on 2008-09-02
you're going to need the wpa supplicant with certificates, that will either require adding those packages via synaptic or by hand, or i think the new network manager in ubuntu 8.10 supports wpa out of the box, that might be easier.  

however, you're paying to go to that school, so you're the customer, you should be able to contact the help desk at your school and force them to work with you to get connected.

EDIT:  i just looked at the school's front page for network access, and they say they have a second SSID of 'umd' that doesn't require wpa or certificates, but does a login web page - just use that, it'll work instantly.  don't even bother with the 'umd-secure' SSID.

---

### Post by dyzzy on 2008-11-11
Late reply, but if you still need it:

Security: WPA & WPA2 Enterprise
Authentication: TTLS (Tunneled TLS)
Anonymous Identity: anonymous
CA Certificate: [see below]
Inner Authentication: PAP
User Name: [your user name]
Password: [your password]

To get the certificate, download the file from [http://www.thawte.com/roots/](http://www.thawte.com/roots/) (you don't actually need to fill out anything, just click Accept), and extract it anywhere you want. The one you want is ThawtePremiumServerCA.cer in the Thawte Server Roots folder.

Note: this is using the latest version of nm-applet (0.7.0), the one that shipped in 8.10 (Intrepid). The fields might be different if you're using 8.04 (Hardy) or earlier. I know it did look different in 7.10 (Gutsy).

---

### Post by squirrelplayingtag on 2008-11-22
This thread should help.

[http://ubuntuforums.org/showthread.php?t=436035](http://ubuntuforums.org/showthread.php?t=436035)

---

### Post by _Atreides_ on 2009-01-30
Hey fellow University of Maryland ers, i have solved this prob for a year or more but i thought i would post the solution for you other guys

Security: WPA & WPA2 Enterprise
Authentication: TTLS (Tunneled TLS)
Anonymous Identity: yourusername
CA Certificate: go to /etc/ssl/certs and choose Thawthe Premium CA
Inner Authentication: PAP
User Name: [your user name]
Password: [your password]

---

