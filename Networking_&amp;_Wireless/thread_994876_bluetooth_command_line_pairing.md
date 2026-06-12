---
title: "bluetooth command line pairing"
date: 2008-11-27
forum: Networking &amp; Wireless
---

### Post by deadlinx on 2008-11-27
Hi,

I rarely use bluetooth, anyway, 
in the past, I've used it, successfully, 
via command-line.

How can I do the pairing, via command line, 
on a Kubuntu Intrepid Ibex?

In the past I did the pairing with:
passkey-agent --default /etc/bluetooth/bluepin

Nowaday it is not possible to act in this way yet.


I read here: 
[https://help.ubuntu.com/community/BluetoothDialup](https://help.ubuntu.com/community/BluetoothDialup)

In this tutorial the new procedure seems to be the following:

sudo hcitool cc your-phone-mac-address

then:

sudo hcitool cc your-phone-mac-address

Unfortunately the first command seems to be successfull 
(gives no output), but the second command told me the device is not connected


So how can I do the pairing, via command line, 
on a Kubuntu Intrepid Ibex?


If I had more RAM I could use kbluetooth or some GUI, 
but unfortunately I need to do the pairing via command line,
because of the low RAM machine I'm on now, that is the reason,
I've to use a light WM like Fluxbox.


Please help,


deadlinx

---

### Post by deadlinx on 2008-11-28
JUuuuuuuuuuuh,

is there anybody reading?

Don't say me there's nobody pairing bluetooth,
via command line in Intrepid Ibex, 

so, please, help.


deadlinx

---

### Post by deadlinx on 2008-11-28
Don't say me everybody uses only GUI tools,
I can't belive it,

so please, give an idea and so on,


deadlinx

---

### Post by HRH_H_Crab on 2009-04-02
You aren't the only one that doesn't use gui tools.
I am also suffering from the total lack of consideration that the bluez devs seem to have for anyone that might dare to not use a full gui.

Can anyone help? All I want to do is pair my damn phone!

---

### Post by gertmul on 2009-05-16
Same need here!

I found that once devices are paired, the key/pin is stored in a file called /var/lib/bluetooth/xx : xx : xx : xx : xx : xx /linkkeys as:
yy:yy:yy:yy:yy:yy XYZ32HEXNUMBERSYADAYADA456789012 0 4

x: is your local Bluetooth device's "MAC?" address and y is the one you are connecting to.

There are some more files pertaining to your remote devices like "classes", "features", "manufacturers", "names", "profiles" and "sdp" in that same folder.

so maybe there is a way to add your external device info to those files...but the 32 bit encrypted key in "linkkeys" might be tricky?

Anyone any ideas?

---

### Post by gertmul on 2009-05-16
This might be useful if you have only one device:

[http://www.spinics.net/lists/linux-bluetooth/msg02190.html](http://www.spinics.net/lists/linux-bluetooth/msg02190.html)

---

