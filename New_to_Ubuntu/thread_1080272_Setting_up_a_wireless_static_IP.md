---
title: "Setting up a wireless static IP"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by kunnie on 2009-02-25
Hi yall, I need your help: can you tell me how to set up a wireless IP address in ubuntu? 

Whenever I put my subnet mask in the gnome network manager, and I press ok, the system ignores it and puts 24 (instead of 255.255.255.0). All my other settings stay after I put "ok".

If you can tell me how to put [another network manager]("http://www.ubuntugeek.com/wicd-wired-and-wireless-network-manager-for-ubuntu.html") (without using internet in my Ubuntu machine), or just explain me another way to get wireless internet using a static IP, I will be pleased :lolflag:

---

### Post by llamabr on 2009-02-25
Hi.  This is probably pretty simple, but it's hardly an absolute beginner question.

If you don't get any response, try taking it to the appropriate forum.  Experts elsewhere will help you set up your system.

---

### Post by OffAxis on 2009-02-25
a value of 24 is shorthand for 255.255.255.0. Usually it's represented as something like
192.168.1.1/24
which would be an IP of
192.168.1.1
and a subnet mask of
255.255.255.0

if you open a terminal and type

```
ifconfig
```

you should be able to confirm the IP and subnet mask of the connection.


That article you referenced is out of date. wicd is now in the ubuntu repositories.

Just
```
sudo apt-get install wicd
```

---

### Post by abyssius on 2009-02-25
You don't have to install anything really. I recommend simply editing your interfaces file located in the /etc/network directory.

```
sudo gedit /etc/network/interfaces
```

Your existing interfaces file might look like this:
```

auto lo
iface lo inet loopback

```

You should add lines as shown in the example below - replacing the example parameters (in bold) with those that match your application:

```

auto lo
iface lo inet loopback

iface **wlan0** inet static
address **192.168.1.106**
netmask **255.255.255.0**
gateway **192.168.1.1**
wireless-essid **linksys**

auto **wlan0**

```

After you save the file, you can invoke the settings by issuing:
```

sudo /etc/init.d/networking restart

```

If you enter the correct parameters, you should be online.

---

### Post by kunnie on 2009-02-25
> **abyssius said:**
> You don't have to install anything really. I recommend simply editing your interfaces file located in the /etc/network directory.

```
sudo gedit /etc/network/interfaces
```

Your existing interfaces file might look like this:
```

auto lo
iface lo inet loopback

```

You should add lines as shown in the example below - replacing the example parameters (in bold) with those that match your application:

```

auto lo
iface lo inet loopback

iface **wlan0** inet static
address **192.168.1.106**
netmask **255.255.255.0**
gateway **192.168.1.1**
wireless-essid **linksys**

auto **wlan0**

```

After you save the file, you can invoke the settings by issuing:
```

sudo /etc/init.d/networking restart

```

If you enter the correct parameters, you should be online.

The problem is, whenever I try to edit my files, this comes up in the terminal:

** (gedit:6758): WARNING **: Could not write gedit state file: there has been an error while trying to create the file <</root/.gnome2/gedit-2.Q0BTPU>>: No suc file or directory

I/O error: No such file or directory
I/O error: No such file or directory

---

### Post by Reiger on 2009-02-25
Directly editing /etc/network/interfaces may not work as well when you use wpa_supplicant (and that's what both network manager and for instance wicd use). If you just want a static IP on your network because you want to be able to access your device from some other device, it is as simple as simply configuring the router properly and binding a static IP address to the MAC (hardware) address of your WLAN card/dongle. You can get the hardware address by examining the output of ```
ifconfig
```.

---

### Post by sgosnell on 2009-02-25
If you just want to keep the same IP address for a computer, do it in the router settings.  If you're trying to do something else, please explain it more clearly.

---

