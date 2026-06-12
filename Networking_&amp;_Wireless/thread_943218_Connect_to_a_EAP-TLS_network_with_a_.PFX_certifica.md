---
title: "Connect to a EAP-TLS network with a .PFX certificate"
date: 2008-10-10
forum: Networking &amp; Wireless
---

### Post by jcm1979 on 2008-10-10
I'm a Linux newbie using Hardy 8.04 with kernel 2.6.24-21-generic and am having an issue connecting to my companies secured Wi-Fi network.  I can connect to my personal network using WPA-Personal, and have no problems connecting to various WEP encrypted networks.

 I have read a great deal about the subject and still can't seem to resolve the issue.  My company provides a .PFX file that is used to gain access to the network.  I believe my problem lies in converting the file to .PEM.  Can someone point me in the right direction?  I'm not entirely certain I understand the method in changing the .PFX file into the 3 different certificates that WPA Supplicant and other programs use to connect.

Thanks for your help
Floyd

---

### Post by Hoshnasi on 2008-10-15
I have a Dell Mini 9 and would REALLY like to know how to do this.  I have an exported .pfx file and have no idea how to get on the network.

---

### Post by Hoshnasi on 2008-10-22
So no one has any info on this?  I'm having the worst time trying to figure it out.

---

### Post by jcm1979 on 2008-10-29
I seem to be getting closer to a solution.  When I get it working 100% I'll pass along any info I have

---

### Post by ibbers on 2008-12-20
jcm, did you have any luck with this?

---

### Post by jcm1979 on 2008-12-21
I haven't had any luck so far.:(

---

### Post by ]SiB[ on 2010-06-14
openssl pkcs12 -in file.pfx -cacerts -nokeys -out wifi/ca.crt
openssl pkcs12 -in file.pfx -clcerts -nokeys -out wifi/cl.crt
openssl pkcs12 -in file.pfx -clcerts -out wifi/prv.pem
mcedit prv.pem (delete all after line with: -----END RSA PRIVATE KEY-----)
Try connect to your WiFi.
My WiFi working fine.

---

