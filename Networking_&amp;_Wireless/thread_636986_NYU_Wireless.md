---
title: "NYU Wireless"
date: 2007-12-10
forum: Networking &amp; Wireless
---

### Post by juliansuddaby on 2007-12-10
==edited to be up-to-date==

Hello everyone,

It just took me an hour or so to figure out how to connect to my school's wireless network (NYU).  I thought I'd quickly relay the steps I went through to help others at NYU, or with similar school network setups.

The network manager (nm-app) can now do everything you need.  No messing around with config files (earlier versions of ubuntu needed this).

I'm assuming your wireless card connects to open unprotected networks just fine.

NYU got rid of their old system using a crappy Cisco VPN client (the NYURoam-XX ESSIDs) and now center on a new 'nyu' ESSID.  [http://www.nyu.edu/its/wireless/configure/nyu.html](http://www.nyu.edu/its/wireless/configure/nyu.html) contains instructions for Windows XP, Vista, and MacOS.  No Linux.  Bad NYU.

First off you'll need to get the Verisign Root CA certificate:

1. Go to [https://getca.verisign.com/](https://getca.verisign.com/) and download the current Root CA Certificate. It downloads for me as 'getrootcert.cer'.

2. Convert the .cer file to a .pem file:

> openssl x509 -in getrootcert.cer -inform d -out verisign.pem

Save verisign.pem wherever you want (/etc/ssl/certs would make sense).

3.  You need to go to the network manager (usually on the top bar) where you select wireless networks, click the left mouse button and select 'connect to other wireless network'.

Select 'WPA2 Enterprise' for a 'Wireless Security', and a whole bunch of new options will appear.

Network Name is 'nyu'
EAP Method is PEAP
Key Type: Automatic (or, I believe AES)
Phase2 Type is MSCHAPv2
Identity is you NYU NetID (eg. js123 -- don't include the @nyu.edu )
Password is your NetID password.

Anonymous Identity, Client Certificate File, Private Key File, and Private Key Password should be left blank.

For CA (Certifying Authority, I guess) Certificate file use the verisign.pem file.

It then worked fine.  If it does, do let NYU IT services know about it...

Thanks!

---

### Post by juliansuddaby on 2008-01-24
==removed because of obsolence==

---

### Post by soro2005 on 2008-02-10
Hey, just wanted to say thanks a bunch. I've kept connecting to NYU-ROAM2 and ROAM3 because I didn't figure out how to get the certificate. :guitar:

---

### Post by arphaus on 2008-04-27
Any advice if the settings don't work?

---

### Post by juliansuddaby on 2008-05-13
Settings still work for me, though sometimes the wireless access points are a little temperamental.

---

### Post by arphaus on 2008-05-13
thanks.  i'll keep at it and hope for the best.

---

