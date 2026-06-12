---
title: "SecurID Dialup Connection"
date: 2007-09-05
forum: Networking &amp; Wireless
---

### Post by Tardus on 2007-09-05
HOWTO:- Set up a dialup connection to a private network that requires a SecurID one-shot password generator.

Took me a while to solve this one, and I could not find anything on the web.
My employer's dialup remote access uses a "SecurID" one-shot password gadget. It displays a new 6 digit password each minute.

The usual diialup ppp tools expect a fixed password, so don't work.

I tried WVDIAL and it was so simple.
Briefly, 

as root run **wvdialconf**

edit the **/etc/wvdial.conf** file to put in your remote username and phone number, but do not enter anything for a password. Comment out any password line.

then, still as root, run **wvdial password=nnnnnn** where the nnnnnn is the number on the SecurID. That's it. Note: best to wait till a new number appears, then type in the nnnnnn and press enter. This gives wvdial the max. time to connect and pass the password through before it changes. 

I'm using it on Xubuntu on an old laptop, with 128MB RAM and the built-in modem (Laptop is an IBM Thinkpad A22m).

Full details at my website [http://tardus.co.nr](http://tardus.co.nr) under the "Computers" link

---

