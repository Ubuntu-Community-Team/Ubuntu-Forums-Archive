---
title: "Winmodem troubles"
date: 2005-06-22
forum: Networking &amp; Wireless
---

### Post by Aragorn992 on 2005-06-22
Ive been trying to install this and have run into problems when its dialing up.

I modprobe'd lt_modem and lt_serial as a guide said and got the modem all working at /dev/ttLTM0.

My problem is connecting.

I KNOW the username and password are correct. It dialsup, goes through all the buzz's and hiss's but when its authenticating the username/password I get the following problem:

-> The system has a partial freeze, I can click something, but anything I click becomes unresponsive to future actions. The mouse still moves fine and alt-tab works fine but apps are unresponsive in general.

-> Eventually the modem has the disconect sound and tries to connect again, once this happens this system is responsive as usual.

Two questions really:

1. Why is it doing this? I.e. how do I fix it?
2. Where can I see the error report for this?

---

### Post by az on 2005-06-22
In one terminal do
sudo pppconfig
Enter all you information (name the connection provider for now...) and do not forget to save.

do
sudo tail -f /var/log/messages

in the terminal and open another terminal

In the new terminal type
sudo pon

and post the output of the first terminal here...

---

### Post by Aragorn992 on 2005-06-22
Ok this is what I get:

[I]localhost kernel: PPP generic driver 2.4.2
...
localhost chat: ...
...
localhost kernel: ...
...
localhost chat[9220]: alarm
localhost chat[9220]: Failed
localhost pppd[9227]: Exit.[/I]

I didnt list it all as the machine froze so I couldnt copy the text to a file, so I wrote down what I thought was needed, is this adequate?

Any ideas?

---

### Post by az on 2005-06-22
Maybe you need a more recent version of the driver?

Download this:
[http://www.sfu.ca/~cth/ltmodem/ltmodem-8.31a10.tar.gz](http://www.sfu.ca/~cth/ltmodem/ltmodem-8.31a10.tar.gz)

and find a way to access it from ubuntu (usb drive or mount your windows partition)

copy it to a folder in your Ubuntu home folder

In ubuntu, remove linux-restricted-modules (from synaptic and install build-essential and linux-headers-2.6.10-5-386)

In a terminal cd into the folder and unpack it:

cd Desktop
cd folder
tar xvzf ltmodem*
cd ltmodem*
sudo ./build_deb
...and then install the deb that it makes for you.

sudo dpkg -i (package.deb)

I have not tested this in Hoary.  It should work fine.  If it does not, install it by hand:

I have never done this, I have always just built the deb.
cd Desktop
cd folder
tar xvzf ltmodem*
cd ltmodem*
sudo ./build_module 
sudo ./ltinst2 
sudo ./autoload

Good luck!

---

### Post by Aragorn992 on 2005-06-23
Yeah tried it and still the same problem unfortunately, any other ideas?

Thanks for your help so far :)

Would really love to use Ubuntu next semester but I need modem support ah :/

---

