---
title: "kbluetoothd Gone in Gutsy?"
date: 2007-09-25
forum: Networking &amp; Wireless
---

### Post by sog on 2007-09-25
hi there - trying to follow the directions here [https://help.ubuntu.com/community/BluetoothSkype]("https://help.ubuntu.com/community/BluetoothSkype") to get my Jawbone connected to Ubuntu, but the recommended kbluetoothd package seems absent in Gutsy. 

if i run kbluetoothd, i get the following: 

```
The program 'kbluetoothd' is currently not installed.  You can install it by typing:
sudo apt-get install kdebluetooth
bash: kbluetoothd: command not found

``` 

which would be great and helpful - except that kdebluetooth is already installed. searching through Synaptic i don't see the package referred to anywhere. 

has it been deprecated in favor of a different package? if so, which one?

---

### Post by Bagheera06 on 2007-09-25
I have the same issue. 

It's very annoying as it's the first time I have needed to use it, and typically it appears to have "just gone" :(

---

### Post by daka on 2007-10-24
Me too... no bluetooth working.... no kbluetoothd anywhere to be found????!!!

All in all Gutsy is Great!!!! fixed many other problems for me.... this is the first glitch!

Daka

---

### Post by daka on 2007-10-24
MAYBE installing KDE will solve this?.....

I seem to remember installing KDE and being surprised that bluetooth worked... that kbluetoothd was automatically installed within KDE.

I have a very slow connection so I will try it but it may take some time to get KDE installed

Daka

---

### Post by daka on 2007-10-24
KDE did not completely solve the bluetooth problem... now I can send from laptop to phone but not from phone to laptop.  This problem was solved previously by kbluetoothd... seems like it consumnated the marriage somehow.  Now that it's not available in or out off KDE I am back to waiting for a guru to manifest.

So the problem is that I can send from laptop to phone but not vice versa... even when I eventually figure out how to pair the two... which is not very intuitive.... I bumped into it by accident.

Waiting for Godot

Daka

---

### Post by vhof on 2007-10-27
Ahhh... you lucky all....
And I get more worse, the following:
```
bash: kbluetoothd: command not found
```
Weird,,, on Feisty it was ok.

---

### Post by plasticM on 2007-10-31
Bump - 

This is a real pain! - my bluetooth remote worked fine with kbluetoothd under 7.04.  Does anyone know how to get kbluetoothd working in Gutsy?

Tim

---

### Post by plasticM on 2007-11-01
OK, It seems to work just using "kbluetooth" instead of "kbluetoothd" but it still doesn't make my SE phone bluetooth remote work and I'm sure that was what did it in Feisty. :(

Tim

---

