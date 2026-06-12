---
title: "A message for those with slow FTP"
date: 2007-06-22
forum: Networking &amp; Wireless
---

### Post by Jordanwb on 2007-06-22
I figured out why my FTP was slow and I figured that I should help other who are having the same problem.

Here's what I did:

Installed Proftpd (sudo apt-get install proftpd)

Go into Proftpd's config file (sudo nano /etc/proftpd/proftpd.conf)

Set IPv6 to off and save

After that you do not need to do any more configuration.

load your FTP program (I use ALFTP)

for FTP address: [ftp://x.x.x.x](ftp://x.x.x.x) (x.x.x.x being static IP address)
Username: The username you use to login
Password: The password you use to login

Do not turn of Passive FTP and voila fast FTP

****** Edit #1

Just a note added if you're using LAMP and using the computer as a server use putty to manually set the www/ folder to 777:

cd /var
sudo chmod 777 www/
now you can upload to the www folder through FTP

******* Edit #2

WTH it's slow now!

---

### Post by ktrnka on 2007-07-24
I had the same problem and what worked was to change UseReverseDNS to off.

---

