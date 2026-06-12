---
title: "apt-get update caused wireless to not work"
date: 2008-10-22
forum: Networking &amp; Wireless
---

### Post by amup on 2008-10-22
I finally got the wireless to work.  I am able to see my router.  I typed in my wep keys etc.  And I got in!!

So the first thing I did was type:

sudo apt-get update

It started to work then I got line after line of ndiswrapper error messages.  They wouldn't stop.  I finally had to shutdown to make them stop.  

Now I can not connect to the router again.  I've tried:

sudo /etc/init.d/networking restart

I've tried reentering my ssid and passkey

sudo iwconfig essid wlan0 myroutersname
sudo iwconfig wlan0 key  xx-xx-xx and so on
sudo ifconfig wlan0 up 
sudo dhclient wlan0

It gets no offers now.  It tries the old lease from the one time I did connect and that doesnt't work either.  

What should I do?

---

### Post by amup on 2008-10-22
For some reason it appears I have to enter those commands while I am in the root directory.  So now I have renewed.  How to I put those 4 commands in a file or something so I don't have to type them every time I start the computer?

---

### Post by melojo on 2008-10-22
> **amup said:**
> For some reason it appears I have to enter those commands while I am in the root directory.  So now I have renewed.  How to I put those 4 commands in a file or something so I don't have to type them every time I start the computer?

You can put it in /etc/rc.local file
make sure its permission is set to executable

---

### Post by amup on 2008-10-22
thanks

---

