---
title: "[SOLVED] OpenVPN 181: Status: not found / Cannot load CA certificate"
date: 2008-08-31
forum: Networking &amp; Wireless
---

### Post by Piraja on 2008-08-31
Dear all,

I have been using OpenVPN for quite a while to connect to my university network. Everything has worked perfectly until a moment ago, and even though everything (including the CA certificate file) seems to be in place, I get the following errors:

```
pprasane@ubuntu-laptop:~$ sudo /etc/init.d/openvpn start
 * Starting virtual private network daemon.  
/etc/init.d/openvpn: 181: STATUS: not found
pprasane@ubuntu-laptop:~$ sudo openvpn --config /etc/openvpn/openvpn.conf
Sun Aug 31 12:14:10 2008 OpenVPN 2.1_rc7 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] built on Jun 11 2008
Enter Auth Username:pprasane
Enter Auth Password:
Sun Aug 31 12:14:20 2008 mlockall call succeeded
Sun Aug 31 12:14:20 2008 Cannot load CA certificate file liteca.crt path (null) (SSL_CTX_load_verify_locations): error:02001002:system library:fopen:No such file or directory: error:2006D080:BIO routines:BIO_new_file:no such file: error:0B084002:x509 certificate routines:X509_load_cert_crl_file:system lib
Sun Aug 31 12:14:20 2008 Exiting
pprasane@ubuntu-laptop:~$ 

```

Any suggestions anyone?

---

### Post by Piraja on 2008-08-31
I solved the issue [edit: or maybe I should say "I got OpenVPN started" after all] by installing Firestarter (I have used it previously, but, for some reason, had uninstalled it at some point) and choosing "VPN tunnel (tap0)" as the Internet connection device in the "Preferences" tab. However, I still don't see why the VPN connection had suddenly stopped working. Well, I suppose I'm just content that it does work now.

EDIT: Actually it seems that changing between window managers (I have Gnome and Fluxbox and also gave XFCE4 another try a moment ago) and opening OpenVPN in the different desktop environments might cause the error "181: Status not found"...? Even though the "reload" command did not work in Gnome (while the change in Firestarter preferences did), I could get OpenVPN started in Fluxbox by using "sudo /etc/init.d/openvpn reload" and then "sudo /etc/init.d/openvpn restart". So, even though I'm not sure why certain procedures worked, it seems that if you get "181: Status not found", you might try to first reload and then restart OpenVPN &#8212; and/or change the firewall settings...

---

