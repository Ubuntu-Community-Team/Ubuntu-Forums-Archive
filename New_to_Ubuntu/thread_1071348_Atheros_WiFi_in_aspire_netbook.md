---
title: "Atheros WiFi in aspire netbook"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by tysonh on 2009-02-16
I just bought this netbook and installed ubuntu.  After a little forum searching I was able to get the wifi card up and running without problems.  However, I just downloaded a lot of updates and restarted the netbook only to notice my wifi connection was lost.  

Any idea's how to revert from a update?

---

### Post by binbash on 2009-02-16
I had atheros wifi also.You have to re-install it everytime you updated the kernel.Did you update the kernel lately?

Also at grub menu there should be the old kernel there and it should work, you can edit the grub menu and make the old one default

---

### Post by tysonh on 2009-02-16
thanks for the response bin.  How to edit the grub menu?

---

### Post by 3rdalbum on 2009-02-16
This depends on how you installed the wireless driver in the first place.

If you compiled the "madwifi" driver from source like the Ubuntu Wiki now tells you to, then you will need to recompile the driver whenever the kernel changes. (not every time, but most new kernel versions require the outside drivers to be recompiled).

If you enabled the "ath5k" driver from the Intrepid Backports repository, then I don't know what is wrong. You could press Escape when GRUB is counting down to get into the GRUB menu, and then select the earlier kernel to boot into.

The other update that I can remember that might have caused problems is the HAL update. In Synaptic Package Manager you can select the HAL packages and "Force Version" to the older version. This will probably require you to hook into your Ethernet connection so you can download the old package.

I'm also reminded of one time when HAL wasn't loading on startup, and this was causing the wireless network to not work. Try going into a terminal and typing "sudo hald --daemon=yes".

---

### Post by tysonh on 2009-02-16
I did the madwifi compile.  So I have to do it again and every time I update?

---

### Post by binbash on 2009-02-16
3rdalbum is right, it depends on the installation type.I installed ath5k from external source(i removed the backports etc).So even you installed the driver with madwifi or ath5k i had to re-install it.

Please link to the guide or forum topic which helped you to installing the driver so we can see which method you used and then we can help better



PS : 
for editing grub menu : 

sudo nano -w /boot/grub/menu.lst

---

### Post by binbash on 2009-02-16
> **tysonh said:**
> I did the madwifi compile.  So I have to do it again and every time I update?

yes but ONLY if you update the kernel.go to the madwifi directory : 

sudo make uninstall
sudo make clean
make
sudo make install

---

### Post by tysonh on 2009-02-16
here are the instructions that I followed:

```

sudo apt-get install build-essential linux-headers-$(uname -r)
```

Navigate to the madwifi directory

```
cd madwifi-hal-0.10.5.6*/
```

Compile

```
make
```
```

sudo make install
```

Load the driver

```
sudo modprobe ath_pci
```

Make it load every time


```
gksudo gedit /etc/modules
```

put a # in front of ath5k

Add this line to the end of the file

Code:

```
ath_pci
```[/QUOTE]

---

### Post by binbash on 2009-02-16
go to this directory : cd madwifi-hal-0.10.5.6*/

and gave the commands i wrote that is all(reboot the pc after all)

---

### Post by tysonh on 2009-02-16
Thanks!  I followed the code you gave me and it worked great.  Saved me a lot of back tracking after getting to work in the first place.  Thanks again.

---

### Post by 3rdalbum on 2009-02-16
Not all kernel updates cause my desktop wireless (which is an unofficial one I compiled) to break. If the changelog for the kernel update says "ABI bump" then you'll be required to recompile the module. If it's just a security patch you'll probably be alright.

---

