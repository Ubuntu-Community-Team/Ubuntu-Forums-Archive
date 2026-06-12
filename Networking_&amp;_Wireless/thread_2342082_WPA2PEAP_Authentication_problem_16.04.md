---
title: "WPA2/PEAP Authentication problem 16.04"
date: 2016-11-03
forum: Networking &amp; Wireless
---

### Post by bbellster on 2016-11-03
I am not able to connect to our corporate wireless network using an Ubuntu 16.04 machine. On Windows 7 everything works fine. It tries to connect, but keeps asking for a password. As I said, this username/password combination works fine in Windows. Also, I can connect fine from my Android phone.

Details of the connection gleaned from my windows machine:
Security type: WPA2-Enterprise
Encryption type: AES
Authentication method: PEAP
Authentication mode: Computer authentication
no certificate in use

I also had a look at the file in /etc/NetworkManager/system-connections/SNI and saw that my identity and password were shown correctly.
I ran the wifi test script and attached the file. The network I am trying to connect to is called SNI. Several channels are shown available in the report.
What can I do to fix this?

---

### Post by bbellster on 2016-11-03
Just tried setting the password to "ask every time" and the NetworkManager client (nm-applet) crashed. I have noticed that this crashes a lot when I try to connect. Sometimes it continually asks for a password, sometimes it crashes.

---

