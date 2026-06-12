---
title: "Wrong Architecture i386"
date: 2010-06-23
forum: New to Ubuntu
---

### Post by D4matricks on 2010-06-23
Everytime i install deb files it gives me error.
i researched about it and apprently it is when you install 64bit in 32bit systems

I downloaded 32bit 10.04 ubuntu and used wubi to dual boot.
any help here?

---

### Post by Ozymandias_117 on 2010-06-23
What deb files are you trying to install?

---

### Post by sandyd on 2010-06-23
> **D4matricks said:**
> Everytime i install deb files it gives me error.
i researched about it and apprently it is when you install 64bit in 32bit systems

I downloaded 32bit 10.04 ubuntu and used wubi to dual boot.
any help here?
Theirs a weird thing going on with wubi at the moment for some users. Although you download the 32bit version of ubuntu, and then use wubi to install, it somehow installs the 64-bit version...
anyways, just download a 64-bit version of the deb and install that.

for more info, [https://wiki.ubuntu.com/WubiGuide#Can%20I%20force%20Wubi%20to%20download%20and%20install%20a%2032%20bit%20version%20of%20Ubuntu?](https://wiki.ubuntu.com/WubiGuide#Can%20I%20force%20Wubi%20to%20download%20and%20install%20a%2032%20bit%20version%20of%20Ubuntu?)

---

### Post by D4matricks on 2010-06-24
> **carlee said:**
> Theirs a weird thing going on with wubi at the moment for some users. Although you download the 32bit version of ubuntu, and then use wubi to install, it somehow installs the 64-bit version...
anyways, just download a 64-bit version of the deb and install that.

for more info, [https://wiki.ubuntu.com/WubiGuide#Can%20I%20force%20Wubi%20to%20download%20and%20install%20a%2032%20bit%20version%20of%20Ubuntu?](https://wiki.ubuntu.com/WubiGuide#Can%20I%20force%20Wubi%20to%20download%20and%20install%20a%2032%20bit%20version%20of%20Ubuntu?)

well my comp can only handles 32bit. 64 bit, wont work for me.
installed linux for better gaming...wolfenstein ET.
if i install 32bit with CD, it would work i guess right?

---

### Post by sandyd on 2010-06-24
> **D4matricks said:**
> well my comp can only handles 32bit. 64 bit, wont work for me.
installed linux for better gaming...wolfenstein ET.
if i install 32bit with CD, it would work i guess right?
wait. your saying that the Deb installer output the error "wrong architecture i386" right?
because thats not possible if you are running i386.

here, download this onto your desktop, and run the below...
[http://www.fileplanet.com/124801/download/Return-to-Castle-Wolfenstein:-Enemy-Territory-Client-v2.60-%5BLinux%5D](http://www.fileplanet.com/124801/download/Return-to-Castle-Wolfenstein:-Enemy-Territory-Client-v2.60-%5BLinux%5D)

```

cd ~/Desktop
chmod 777 [et-linux-2.60.x86.run]("http://www.fileplanet.com/files/120000/124801.shtml")
sudo sh ./[et-linux-2.60.x86.run]("http://www.fileplanet.com/files/120000/124801.shtml")

```
and follow the instructions in the installer

---

### Post by D4matricks on 2010-06-24
> **carlee said:**
> wait. your saying that the Deb installer output the error "wrong architecture i386" right?
because thats not possible if you are running i386.

here, download this onto your desktop, and run the below...
[http://www.fileplanet.com/124801/download/Return-to-Castle-Wolfenstein:-Enemy-Territory-Client-v2.60-%5BLinux%5D](http://www.fileplanet.com/124801/download/Return-to-Castle-Wolfenstein:-Enemy-Territory-Client-v2.60-%5BLinux%5D)

```

cd ~/Desktop
chmod 777 [et-linux-2.60.x86.run]("http://www.fileplanet.com/files/120000/124801.shtml")
sudo sh ./[et-linux-2.60.x86.run]("http://www.fileplanet.com/files/120000/124801.shtml")

```
and follow the instructions in the installer

problem is, i dont think im running it. 
currently on xp atm, deleted ubu since it gives me same probs, gonna try it with flashdrive, not wubi.

its not just ET files, like Flash Player Deb file doesnt work, i tried installing Gfire, which didnt work. 
just all deb files didnt work for me.

From my understanding, im running 64bit, strange since i put 32bit stuff with wubi.

---

### Post by sandyd on 2010-06-24
> **D4matricks said:**
> problem is, i dont think im running it. 
currently on xp atm, deleted ubu since it gives me same probs, gonna try it with flashdrive, not wubi.

its not just ET files, like Flash Player Deb file doesnt work, i tried installing Gfire, which didnt work. 
just all deb files didnt work for me.

From my understanding, im running 64bit, strange since i put 32bit stuff with wubi.
as said, thats a problem with wubi. It automatically detects your CPU and installs what it thinks is  appropriate.

You could use the wubi flags to force it to be 32bit (see above links), but try installing via flashdrive first.

---

### Post by D4matricks on 2010-06-24
> **carlee said:**
> as said, thats a problem with wubi. It automatically detects your CPU and installs what it thinks is  appropriate.

You could use the wubi flags to force it to be 32bit (see above links), but try installing via flashdrive first.

Gotcha, will do that, thanx for the help :D
if something goes on, i will write bout it

---

