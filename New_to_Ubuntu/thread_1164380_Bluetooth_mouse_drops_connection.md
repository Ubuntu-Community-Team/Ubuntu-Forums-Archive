---
title: "Bluetooth mouse drops connection"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by Raziekiel on 2009-05-19
Every time my mouse idles for too long, it drops the bluetooth connection, and get it working again I have to delete and re-add the device everytime.
 I've searched all over and I can't find anything to fix this.
Any help would be appreciated :)

---

### Post by charliehorse55 on 2009-05-19
Have you tried to "Pair" the bluetooth connection?

This should remove this problem?

---

### Post by Raziekiel on 2009-05-19
I'm not sure what you mean by "pair" the connection. I've used the bluetooth wizard to add my mouse a million times, but everytime it idles I have to delete it and re-add it.

---

### Post by Raziekiel on 2009-05-21
/bump
Any ideas??

---

### Post by LowSky on 2009-05-21
What kind of Mouse? Does it use a PIN number?

I have a Razer ProClick and the thing works flawlessly, but only if it is paired correctly, and If i switch to Windows the Mouse wont connect. I have to reset the mouse.

---

### Post by pinoyboyf4i on 2009-05-21
My friend had success with getting his bluetooth mouse to stay connected on 8.10 by uninstalling bluez4 and installing bluez3.

[https://bugs.launchpad.net/ubuntu/+bug/289836](https://bugs.launchpad.net/ubuntu/+bug/289836)

add "deb [http://ppa.launchpad.net/blueman/ubuntu](http://ppa.launchpad.net/blueman/ubuntu) intrepid main" to sources list

get key: "sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 6B15AB91951DC1E2"

sudo apt-get update
sudo apt-get install blueman

This uninstalls bluez4 and installs bluez3.

After all that go into your menu and click on BLUETOOTH MANAGER

---

### Post by Raziekiel on 2009-05-21
Now bluetooth manager won't even start.

---

### Post by LowSky on 2009-05-21
What version of Ubuntu are you using?

---

### Post by Raziekiel on 2009-05-21
I"m running 9.04 64bit.

---

### Post by Raziekiel on 2009-05-23
/bump 
Still have to re-delete and add my bluetooth mouse everytime it goes to sleep.. Any help would be very appreciated :D

---

### Post by alibasho on 2009-06-21
hmm...

 4 weeks since the last post and no solution...

I installed my ubuntu 9.04 3 days ago and except this problem i have like yours (idle disconnection), my ubuntu ready for action:popcorn:..... i think...

---

