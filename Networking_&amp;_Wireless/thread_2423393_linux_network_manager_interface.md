---
title: "linux network manager interface"
date: 2019-07-22
forum: Networking &amp; Wireless
---

### Post by jgw on 2019-07-22
I use a PIA vpn.  I have had some minor problems and have contacted them for help.  They came back and told me to access "linux network manager interface".  I replied that I had no idea what, exactly, that was.  The inference was that there was a gui for "linux network manager interface".  They never responded.  This is not critical but I was wondering, what are they referencing?  The specific problem, in this case, is that they have two systems to install their product.  One is to using the terminal for about 4 commands which installs, and runs the pia vpn.  The other involves downloading pia and then running the download.  The difference between the two is that the first installs their system that is recognized by ubuntu 18.04 and the second which is not recogized by Ubuntu 18.04.  Both work.  Oh, the first also has an icon reflecting whether it is connected or not.  The second doesn't but there is a gnome extension which will tell the user if the vpn is up or not (actually says; "VPN is up!" (or down).

The PIA tech inferred that one can goto the "linux network manager interface" and tell the system which to use.  Right now all I know is that the vpn is working.

Anyway..............

Thank you..........

---

### Post by TheFu on 2019-07-22
PIA uses standard openVPN, so you can use any OpenVPN client that you want.  I've never used their downloads besides their specific client ovpn files for the 45 different exit nodes they provide and I modified my client settings to use AES-256-CBC, instead of the defaults.  To use the AES-256 encryption, you need two extra files normally not included.
ca.rsa.4096.crt  crl.rsa.4096.pem

As for using some GUI to start, stop, or control the VPN connection, I don't do it that way.  In most Ubuntu installs, the little network icon in the panel **is** network manager and has been for about a decade.  There are a few different network-manager interfaces. I don't use any of them, so cannot help with that.

However, assuming you download their ZIP file with the ovpn client files, put them into /etc/openvpn/AES-256/ modify them to use AES-256, place thoseca.rsa.4096.crt  crl.rsa.4096.pem files in the same directory, then you can make a connection to Japan using the japan.ovpn client file with
```
$ sudo openvpn ./japan.ovpn &
```
easy, peasy.
When you want to shutdown the VPN, just kill the openvpn process however you prefer.

Here are the diffs between the 128-bit encryption and 256-bit encryption files:
```
# diff India.ovpn ../India.ovpn 
4c4
< remote in.privateinternetaccess.com 1197
---
> remote in.privateinternetaccess.com 1198
9,10c9,10
< cipher aes-256-cbc
< auth sha256
---
> cipher aes-128-cbc
> auth sha1
17,18c17,18
< crl-verify crl.rsa.4096.pem
< ca ca.rsa.4096.crt
---
> crl-verify crl.rsa.2048.pem
> ca ca.rsa.2048.crt
19a20
> 

```

Hope this all helps.  I've been with PIA for a few years now.

---

### Post by jgw on 2019-07-23
Thank you for the reply, and the info!

Actually I have pia running fine.  Been using them for over 5 years now.  I am currently using the download version but have the other installed.  I was, however, trying to find out about the "linux network manager interface" which, as far as I can tell, really doesn't exist, unless they are talking about the icon dropdown.  My problem (not really a problem), is that it screws up my network icons and the system never really recognizes the vpn even though the gnome vpn thing runs just fine.  If I want the system to recognize it I can use the other installation from the command line.  They are just different - they both do the job.  I have been programming these things for a very long time and these kinds of problems are due to sloppy programing so I hassle the  every now and then onprinciple (retired and its something to do I guess)

Again - thanks for the reply........  (will mark this solved)

---

