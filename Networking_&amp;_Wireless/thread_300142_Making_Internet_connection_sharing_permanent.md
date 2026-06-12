---
title: "Making Internet connection sharing permanent"
date: 2006-11-15
forum: Networking &amp; Wireless
---

### Post by Glutexo on 2006-11-15
Hello.

I have wanted to share the Internet connection from my Ubuntu box to my other PC, so I have found and followed this guide ([https://help.ubuntu.com/community/InternetConnectionSharing)](https://help.ubuntu.com/community/InternetConnectionSharing)), but using the ifconfig command doesn't seem to set this sharing permanently and I have to run it every time I boot up my Ubuntu box.

Thus I would like to ask how to make the Internet connection sharing permanent.

Thank you.

---

### Post by saiman on 2006-11-15
write your command in a script file somewhere in /etc/init.d
make it executable

run: 

update-rc.d your_script_name defaults

probably there's a smarter way, but i know that works.

---

### Post by Glutexo on 2006-11-17
I followed these steps and it works. :) Thank you, saiman!

If someone in the future would like to share his wisdom and tell how to configure the network this way without making the init scripts, I'd appreciate it, but I consider myself satisfied for now as the internet sharing works this way too. ^^

---

### Post by Xirowei on 2008-06-03
Follow guide at there, it is very simple.

[http://visio159.com/2008/04/20/internet-connection-sharing-ics-in-ubuntudebian/]("http://visio159.com/2008/04/20/internet-connection-sharing-ics-in-ubuntudebian/")

---

