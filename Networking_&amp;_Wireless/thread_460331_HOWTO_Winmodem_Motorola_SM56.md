---
title: "HOWTO: Winmodem Motorola SM56"
date: 2007-05-31
forum: Networking &amp; Wireless
---

### Post by linitrofe on 2007-05-31
**This HOWTO was written for the Motorola 1057:3052 device but maybe it would work with other winmodems**

Run the scanModem tool from [http://www.linmodems.org/]("http://www.linmodems.org/") to know exactly what device you have and get further information about it. Here are the instructions to get it working:
```
cd /tmp
wget http://132.68.73.235/linmodems/packages/scanModem.gz
gzip -d scanModem.gz
chmod 777 scanModem
./scanModem
grep 3052 Modem/ModemData.txt
```

If you get the following info (or similar) we are talking about the 3052 device
> 
 0000:03:0d.0   1057:3052       1057:3020       Modem: Motorola: Unknown device 3052 
   Class 0703: 1057:3052 Modem: Motorola: Unknown device 3052
      Primary PCI_id  1057:3052

If not, read carefully the ModemData.txt file to get more help on how to setup your winmodem.

To the 3052 owners: Lets install the smarlink driver.
Get the tools necessary to build the drivers
```

sudo apt-get install linux-headers-generic build-essential

```

Download the drivers
```

wget http://linmodems.technion.ac.il/packages/smartlink/ungrab-winmodem-20070505.tar.gz
wget http://linmodems.technion.ac.il/packages/smartlink/slmodem-2.9.11-20070505.tar.gz

```
Untar them
```

tar xzf slmodem-2.9.11-20070505.tar.gz
tar xzf ungrab-winmodem-20070505.tar.gz

```
Build and install
```

cd /tmp/slmodem-2.9.11-20070505/drivers/
make
sudo make install
cd /tmp/ungrab-winmodem-20070505/
make
sudo make install

```
Load the modules
```

sudo modprobe ungrab-winmodem
sudo modprobe slamr

```
Edit your /etc/modules
```

sudo gedit /etc/modules

```
and add the following lines (in the same order) at the tail of the file
```

ungrab-winmodem
slamr

```
Install the sl daemon
```

sudo apt-get install sl-modem-daemon

```
And start it
```

sudo /etc/init.d/sl-modem-daemon start

```

That's all. You must have now a /dev/ttySL0 device as your modem ;)

---

### Post by facildelembrar on 2007-07-05
The indicated smartlink driver doesn't supports x64 OSes.

---

### Post by mikeincal on 2008-02-17
The above method worked perfectly!! The linmodem website was being problematic, so I took the no guts, no glory approach, and assumed the modem was compatible with the above instructions. I was concerned at first, since Gnome PPP still would not detect my modem. A simple reboot brought everything in line. The driver becomes classified as "restricted", but it works. This worked on a Pentium 4 running Ubuntu 7.10.

Thank you very much for your efforts.

---

### Post by medya on 2008-07-10
hey I have no internet in ubuntu, how I can do APT-get ?...

---

