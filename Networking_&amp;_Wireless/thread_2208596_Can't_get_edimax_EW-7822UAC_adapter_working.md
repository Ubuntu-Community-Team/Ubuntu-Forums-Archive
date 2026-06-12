---
title: "Can't get edimax EW-7822UAC adapter working"
date: 2014-03-01
forum: Networking &amp; Wireless
---

### Post by oliwout on 2014-03-01
hi,

I cant get my wireless adapter working.

It's a edimax ew-7822uac adapter.

---

### Post by praseodym on 2014-03-01
Please show the terminal outputs of these commands:
```

lsusb
lsmod
iwconfig
cat /etc/resolv.conf
```

---

### Post by oliwout on 2014-03-02
Here are the screenshots with the code.

Sorry for the late response.


[ATTACH=CONFIG]250819[/ATTACH][ATTACH=CONFIG]250818[/ATTACH][ATTACH=CONFIG]250820[/ATTACH][ATTACH=CONFIG]250821[/ATTACH]

---

### Post by praseodym on 2014-03-02
You need this driver:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential
wget media.cdn.ubuntu-de.org/forum/attachments/29/51/6222752-rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100.tar.gz
tar xvf 6222752-rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100.tar.gz 
cd rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100
make
sudo make install 
sudo modprobe -v 8812au
```

Reinstallation after kernel upgrade:
```

cd rtl8812AU_8821AU_linux_v4.2.2_7502.20130517_AC6100
make clean
make
sudo make install 
```

---

### Post by oliwout on 2014-03-02
Hi
Thank you for the response but when i try "make" at the driver install i get this error:[IMG]http://gyazo.com/3fbb017e858c484936bb0daf3106e0bd.png[/IMG]

---

### Post by praseodym on 2014-03-02
Try
```

make clean
sudo make
sudo make install
```

---

### Post by praseodym on 2014-03-02
Sorry, for 13.10 you need another driver:
```

sudo apt-get install git
git clone https://github.com/abperiasamy/rtl8812AU_8821AU_linux
cd rtl8812AU_8821AU_linux
make
sudo make install 
```
Reinstallation after kernel upgrade via```

cd rtl8812AU_8821AU_linux
make clean
make
sudo make install 
```

---

### Post by oliwout on 2014-03-02
I did that and didn't find any errors. 
But i can't find networks.
ubuntu recognizes the adapter because when i plug it in I get this [http://gyazo.com/e5ef0c7230435c88e089aab1a3b4eeb2](http://gyazo.com/e5ef0c7230435c88e089aab1a3b4eeb2) and [http://gyazo.com/24e12899baedead7b5f4d1cd4ec7cc38](http://gyazo.com/24e12899baedead7b5f4d1cd4ec7cc38)

---

### Post by praseodym on 2014-03-02
Now open the network-manager and create a wireless profile with your ESSID and key.

---

### Post by oliwout on 2014-03-02
Can't it find the networks by itself?
with other adapters it just shows all the available networks
[http://gyazo.com/b0b982fdf66654249bc999800f8bf3b0](http://gyazo.com/b0b982fdf66654249bc999800f8bf3b0)

---

### Post by praseodym on 2014-03-02
Please check
```

lsmod
iwconfig
cat /etc/resolv.conf
iwlist chan
sudo iwlist scan
```
Which channel does the router send?

---

### Post by bbrown2 on 2014-07-27
I have 14.04 LTS installed. will this work for my computer also. Im fairly new to Ubuntu so installing stuff is almost like reading a foriegn language. I thank anyone for their help upfront.

---

### Post by brad-drew on 2014-08-10
The good news - it will work. [http://askubuntu.com/questions/368015/problem-with-building-compiling-a-driver-for-edimax-wireless-adapter-ew-7822uac](http://askubuntu.com/questions/368015/problem-with-building-compiling-a-driver-for-edimax-wireless-adapter-ew-7822uac)
The bad news - very poorly! [https://wikidevi.com/wiki/Edimax_EW-7822UAC](https://wikidevi.com/wiki/Edimax_EW-7822UAC)

---

### Post by ulisses2 on 2014-11-28
Thank you so much. I'm glad I came across this post. It worked. But the performance speed is extremely slow at 8MB for an AC dongle in an AC network.

---

### Post by praseodym on 2014-11-29
Try a later driver after uninstalling this one:
```

make clean
make
sudo make uninstall
```
New driver:

```
sudo apt-get install --reinstall linux-headers-generic build-essential git
git clone https://github.com/abperiasamy/rtl8812AU_8821AU_linux
cd rtl8812AU_8821AU_linux
make clean
make
sudo make install 
```
Reboot.

---

