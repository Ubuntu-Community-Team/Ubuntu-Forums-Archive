---
title: "WUSB54GC Trouble"
date: 2008-02-07
forum: Networking &amp; Wireless
---

### Post by ZekeSword on 2008-02-07
So I just purchased the WUSB54GC by Linksys today and tried it out on my other computer which runs Ubuntu 7.10, what happens is the light flashes on and off a few times but never connects. I know the key is right, but I don't know what my problem is.

---

### Post by pytheas22 on 2008-02-08
I am not positive (I only did a quick search on Google) but it looks like that card has an rt73 chipset.  Ubuntu ships with a driver for that card that still isn't stable in some cases, which would explain why it only half works for you.  You can try installing the legacy rt73 driver from [http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads](http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads) ...this is what I have to use to get my rt73 USB stick to work properly in Ubuntu; otherwise I get a similar problem where it lights up but can't actually connect.  Note that you will have to blacklist the unstable default driver, called rt73usb, for the new one to kick in.  To do that, in a terminal type
```

sudo gedit /etc/modprobe.d/blacklist
```

and add the line "blacklist rt73usb" to the file that appears.

If you need help compiling and installing the legacy rt73 driver, post.

---

### Post by ZekeSword on 2008-02-08
I downloaded the driver, but I'm a total newbie to Linux. Any help with how to install it would be wonderful.

---

### Post by pytheas22 on 2008-02-08
It's pretty simple to install.

First you have to install a compiler and other essential packages to build things.  In a terminal type:

```
sudo apt-get install build-essential
```

then download the rt73 driver from [http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt73-cvs-daily.tar.gz) .  Save it to your desktop.

Right click on the icon for the rt73 driver and select "Extract Here."

Then in a terminal:
```

cd ~/Desktop/rt*
cd Module
make
sudo make install
```

This will compile and install the driver.  It might at some point give you a warning about the "module being much too big;" you can ignore it.

to finish up, blacklist the unstable default driver by typing
```

sudo gedit /etc/modprobe.d/blacklist
```

and adding the line "blacklist rt73usb" to the end of that file.

Finally, activate your new driver and bring the interface up:
```

sudo depmod -a
sudo modprobe rt73
sudo ifconfig wlan0 up
```

Then you should be able to connect normally using Network Manager.  If you have any trouble, post.

---

