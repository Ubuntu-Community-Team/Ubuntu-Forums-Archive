---
title: "WIFI driver help please :)"
date: 2016-05-27
forum: Networking &amp; Wireless
---

### Post by thomas110 on 2016-05-27
Hello. I am running the latest version of Ubuntu in VMware Workstation 12. I have a USB wifi card that operates on the RTL8821AU chipset. I have the driver (I think) but when I go into the terminal, and navigate to the driver directory, I put in this command "sudo make install" and I get "No rule to make target 'install'. Stop" I also get this when I try to do the "load" or "unload" command with sudo. I am new to Ubuntu and I would appreciate some help please. Please help me with a step by step guide in as much detail as you can. Thank you all so much. If you need any other information from me, please just advise :)

---

### Post by jeremy31 on 2016-05-28
Where did you get the driver from?  Have you installed build-essential and linux-headers-generic?

---

### Post by thomas110 on 2016-05-28
I have not installed build-essential and linux-headers-generic, and I got the driver from: [https://github.com/ulli-kroll/rtl8821au](https://github.com/ulli-kroll/rtl8821au)

---

### Post by thomas110 on 2016-05-28
UPDATE: Okay. I installed the 2 packages above and here is what I got from the terminal: [https://thomaskal.gyazo.com/043da20f957adc7baf1c1ba6d71764df](https://thomaskal.gyazo.com/043da20f957adc7baf1c1ba6d71764df)

---

### Post by jeremy31 on 2016-05-28
The terminal says to run ```
apt-get -f install
``` to fix the problems and it may install another driver that should work

---

### Post by thomas110 on 2016-05-28
It installed, then I rebooted but the wifi still is not showing up in the top right, Thanks for your help though :)   [https://thomaskal.gyazo.com/ebec3259270b16752f0bec5a7bc051c3](https://thomaskal.gyazo.com/ebec3259270b16752f0bec5a7bc051c3)

---

### Post by jeremy31 on 2016-05-28
See the wireless script link in my signature and post your results

---

### Post by thomas110 on 2016-05-28
Okay. It will be a few mins. It is taking a while to update

---

### Post by thomas110 on 2016-05-28
Here it is: [http://pastebin.com/4wG7FgXj](http://pastebin.com/4wG7FgXj)

---

### Post by jeremy31 on 2016-05-28
What happens if you ```
sudo modprobe -v rtl8821au
```

---

### Post by thomas110 on 2016-05-28
FATAL: Module rtl8821au not found in directory /lib/modules/4.4.0-22-generic

---

### Post by jeremy31 on 2016-05-28
How about ```
sudo modprobe -v rtl8812au
```

---

### Post by thomas110 on 2016-05-28
Still: modprobe: FATAL: Module rtl8812au not found in directory /lib/modules/4.4.0-22-generic

---

### Post by jeremy31 on 2016-05-28
Is secure boot enabled?  If it is the module will not be allowed to load.  I just built the rtl8812au-dkms on my computer and loaded it
```
[614657.287926] 8812au: module verification failed: signature and/or required key missing - tainting kernel
[614657.291653] RTL871X: module init start
[614657.291660] RTL871X: rtl8812au v4.3.8_12175.20140902
[614657.291663] RTL871X: build time: May 28 2016 10:54:41
[614657.291747] usbcore: registered new interface driver rtl8812au
```

You may have to try ```
sudo modprobe -v 8812au
```

---

### Post by thomas110 on 2016-05-28
So how would I disable secureboot on Vmware if you know?

---

### Post by jeremy31 on 2016-05-28
This might do the trick for vmware install
```
sudo apt install mokutil
sudo mokutil --disable-validation
```

This was found at [http://askubuntu.com/a/762255/300665](http://askubuntu.com/a/762255/300665)

---

### Post by thomas110 on 2016-05-28
The second command yields:  EFI variables are not supported on this system

---

### Post by jeremy31 on 2016-05-28
Is there any response from ```
sudo modprobe -v 8812au
```

Might as well add results for ```
dkms status
```

---

### Post by thomas110 on 2016-05-28
For sudo modprobe -v 8812au, when i hit enter it just goes to the next line. No error.

[COLOR=#000000][/COLOR]Fir dkms status gives me some hope: rtl8812au, 4.3.8.12175.20140902+dfsg, 4.4.0-22-generic, x86_64: installed

---

### Post by thomas110 on 2016-05-28
But still nothing comes up in iwconfig or ifconfig for wlan0 or anything like that.

---

### Post by jeremy31 on 2016-05-28
For iwconfig, you will likely not see any wlan with the new naming, it might be wlx??????????? any result from ```
dmesg | grep 8812
```

---

### Post by thomas110 on 2016-05-28
Okay. So. I tracked down the 1st party driver from Realtek and here it is along with all the documentation for Linux: [https://www.dropbox.com/s/es6h2pyd0e75xe4/linux.zip?dl=0](https://www.dropbox.com/s/es6h2pyd0e75xe4/linux.zip?dl=0) (UPDATED LINK)

---

### Post by thomas110 on 2016-05-28
No result from dmesg | grep 8812Just goes to the next line

---

### Post by jeremy31 on 2016-05-28
Does the wifi work in the host?  It may have to be disconnected from the host to be used in the guest.  The module installed works on normal installs.  I am downloading a new ISO to try on vmware to see if my USB wireless card works

---

### Post by thomas110 on 2016-05-28
Thank you. Yes It works on the host, but it is connected to the VM. It even shows up in Ubuntus USB list. Another thing I noticed when I "cd" into the driver folder, I try to run the command "sudo make install" to install the driver, but I get this error: install: cannot stat '8821au.ko': No such file or directory

---

### Post by thomas110 on 2016-05-28
And that is the driver that came with the usb adapter for Linux. Sudo make load or unload brings up "no rule to make target 'load'. Stop" also. Is it something wrong with the VM or the driver you think?

---

### Post by jeremy31 on 2016-05-28
```
sudo apt-get remove rtl8812au-dkms
```
That driver was missing the alias for your wifi
```
git clone https://github.com/ulli-kroll/rtl8821au.git
```
Ignore if it says something about a non-empty directory, already exists
```
cd rtl8821au
make
 sudo make install
```
Then restart the guest

---

### Post by thomas110 on 2016-05-28
The very last command "sudo make install" I get "make: *** No rule to make target 'install'.  Stop."  

But everything ellse works fine

---

### Post by thomas110 on 2016-05-28
is this an error with the Makefile?

---

### Post by jeremy31 on 2016-05-28
It is not a normal makefile for some reason, lets try a different way
```
sudo cp rtl8821au.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless
sudo depmod -a
```

Restart guest

---

### Post by thomas110 on 2016-05-28
cp: cannot stat 'rtl8821au.ko': No such file or directory

For the first command

---

### Post by jeremy31 on 2016-05-28
Probably weren't in the correct directory
```
cd rtl8821au
sudo cp rtl8821au.ko /lib/modules/$(uname -r)/kernel/drivers/net/wireless
sudo depmod -a
```

Then restart guest

---

### Post by thomas110 on 2016-05-28
Done. It just skips to the next line. The command goes through but still no wifi

---

### Post by thomas110 on 2016-05-28
The first way we tried it: [COLOR=#000000][FONT=Ubuntu Mono]cd rtl8821au[/FONT][/COLOR]make
 sudo make install   

That worked up untill the last command when it gave me the error. I read that it could be the Makefile. But it was so close.

---

### Post by jeremy31 on 2016-05-28
Post ```
lsmod | grep 8821
```

The makefile doesn't contain the normal install header so it won't work

---

### Post by jeremy31 on 2016-05-28
Post ```
lsmod | grep 8821
```

The makefile doesn't contain the normal install header so it won't work

---

### Post by thomas110 on 2016-05-28
[https://thomaskal.gyazo.com/744c9a5b1d435abfd2411356e09cede3](https://thomaskal.gyazo.com/744c9a5b1d435abfd2411356e09cede3)

---

### Post by jeremy31 on 2016-05-28
Run the wireless script again, the module is loaded

---

### Post by thomas110 on 2016-05-28
ok

---

### Post by thomas110 on 2016-05-28
[http://pastebin.com/pnjqntcL](http://pastebin.com/pnjqntcL)

---

### Post by jeremy31 on 2016-05-28
Try ```
systemctl restart NetworkManager.service
```
It shows it being renamed to enx from wlan0, so it could be the network manager bug

---

### Post by thomas110 on 2016-05-28
You legend.

---

### Post by thomas110 on 2016-05-28
It worked. Thank you so much.

---

### Post by thomas110 on 2016-05-28
So now, when I restarted. Its gone again!!!

---

### Post by jeremy31 on 2016-05-28
If it works, use the thread tools to mark as solved, I hope that bug is fixed soon

A note to anyone who may come across this thread from a search, please use [https://github.com/abperiasamy/rtl8812AU_8821AU_linux](https://github.com/abperiasamy/rtl8812AU_8821AU_linux) 
```
sudo apt-get install git dkms build-essential linux-headers-generic
git clone https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git
sudo dkms add ./rtl8812AU_8821AU_linux
sudo dkms build -m 8812au -v 1.0
sudo dkms install -m 8812au -v 1.0
```

---

### Post by thomas110 on 2016-05-28
Good news: It has detected the wifi adapter and I can see my networks, but I can barely connect to them. And the connection is very slow

---

### Post by thomas110 on 2016-05-28
Thank you very much again for your help. I couldnt have done it without you :)

---

### Post by jeremy31 on 2016-05-28
It may be worth trying the alternative I posted, I know chili555 has posted answers using it.  

Gone after a restart, did you not have this set as persistant
[img]https://www.vmware.com/support/ws3/doc/img/ws32_disksa5_t.gif[/img]

---

### Post by thomas110 on 2016-05-28
I did. For some reason I have to unplug and re-plug the adapter in then it detects it, and I am able to connect to a network but load minimal things. Almost like the adapter is running at like 5% power

---

