---
title: "CD and Wifi Drivers"
date: 2010-09-16
forum: New to Ubuntu
---

### Post by Moose2000 on 2010-09-16
Hey there I am brand new to the world of Ubuntu and everything was running fine but I want to upgrade my PCI card with a Wireless N USB Long range dongle. I have drivers for Linux on said disc BTW its an RTL818S, but I cannot seem to find a way to install these anywhere.

Anyone either have another set of drivers or some code I can copy and paste into terminal. Please be gentle because as soon as I see Kernel and things like that I don't have a clue.

---

### Post by 3rdalbum on 2010-09-16
Install these packages:

linux-headers-generic
build-essential

Extract the archive containing the driver source code onto your hard disk. Open a terminal.

Type 'cd' and then a space, and then drag the folder containing the driver's source code from the hard disk into the terminal. Switch back to the terminal and then press Enter. Your terminal is now inside the correct directory.

Type these commands:

```
make
sudo make install
```

The first one compiles the driver, the second one installs it.

After every kernel update you'll need to do this procedure again (you might need to run "make clean" before running "make").

Hopefully before too long there will be native support for this device in the kernel.

If anyone knows of a PPA with the driver, then go right ahead and post it (or post any improvements to my instructions).

---

### Post by Moose2000 on 2010-09-16
I took your advice and

Building wpa_supplicant requires a configuration file
(.config). See README for more instructions. You can
run "cp defconfig .config" to create an example
configuration.
make: *** [verify_config] Error 1
janice@rachel-desktop:~/Desktop/RTL8188SU_Driver/Linux/linux_2.6.0003.0825.2009/wpa_supplicant-0.5.10$"

Was my response to that. Making progress though. I glanced at the readme and couldn't make sense. Its uploaded if anyone wants to have a crack. 
[http://www.mediafire.com/?b6az57ngswdqecz](http://www.mediafire.com/?b6az57ngswdqecz) - ReadMe file

---

### Post by Moose2000 on 2010-09-17
Anyone know what I need to do?

---

### Post by chili555 on 2010-09-17
For me, the download link for README hangs at "Your download is starting..." but it never actually downloads.

I believe wpa-supplicant is already on your system; you shouldn't have to re-invent the wheel. I believe you can skip that portion altogether.

Can you please attach the README to your reply? Just use that little paperclip at the top of the reply box. You may have to rename the file as README.txt.> linux_2.6.0003.0[COLOR="Red"]825[/COLOR].[COLOR="Red"]2009[/COLOR]I have a little skepticism that a year old package will build correctly, but who knows, we'll see.

---

### Post by Moose2000 on 2010-09-17
Think I added it, try that

---

### Post by chili555 on 2010-09-17
Not there yet; please try again.

---

### Post by Moose2000 on 2010-09-17
[http://www.youshare.com/Guest/a85632/DisplaySimple](http://www.youshare.com/Guest/a85632/DisplaySimple) tried using the Forums but it says its too big try this

---

### Post by chili555 on 2010-09-17
Here is what I see. Can you right-click it, select Encrypt and save it as README.txt.zip? The limit for zip files is quite a bit larger.

---

### Post by Moose2000 on 2010-09-17
There that seems to have sorted it

---

### Post by migs73 on 2010-09-17
I read your readme and it states that you have to manually write a .config file (the one that was missing when you tried earlier). It doesn't look too hard ( I am still a noob myself) but you need to know what functions you require. There I am at a loss.
I opened the file in Wordpad (I am on my works XP machine) which made the file unreadable (one long text string) but if imported to Word was fine, just incase any one is having bother with it (that was the download not your new zip file).

---

### Post by chili555 on 2010-09-17
That seems to be a README that explains wpa-supplicant which is, as I explained, already built in. What you want to do is build the driver itself. Instead of running 'make' in the wpa-supplicant folder, try this:```
cd /Desktop/RTL8188SU_Driver/Linux/linux_2.6.0003.0825.2009
ls
```Isn't there a Makefile there for the driver itself? If so, do:```
sudo su
make
make install
exit
```Report any errors or warnings.

---

### Post by Moose2000 on 2010-09-20
> janice@rachel-desktop:~$ '/home/janice/Desktop/RTL8188SU_Driver/Linux/linux_2.6.0003.0825.2009/wpa_supplicant-0.5.10/Makefile' 
/home/janice/Desktop/RTL8188SU_Driver/Linux/linux_2.6.0003.0825.2009/wpa_supplicant-0.5.10/Makefile:  line 1: ifndef: command not found
/home/janice/Desktop/RTL8188SU_Driver/Linux/linux_2.6.0003.0825.2009/wpa_supplicant-0.5.10/Makefile:  line 3: endif: command not found
/home/janice/Desktop/RTL8188SU_Driver/Linux/linux_2.6.0003.0825.2009/wpa_supplicant-0.5.10/Makefile:  line 5: ifndef: command not found
/home/janice/Desktop/RTL8188SU_Driver/Linux/linux_2.6.0003.0825.2009/wpa_supplicant-0.5.10/Makefile:  line 6: CFLAGS: command not found
/home/janice/Desktop/RTL8188SU_Driver/Linux/linux_2.6.0003.0825.2009/wpa_supplicant-0.5.10/Makefile:  line 7: endif: command not found
/home/janice/Desktop/RTL8188SU_Driver/Linux/linux_2.6.0003.0825.2009/wpa_supplicant-0.5.10/Makefile:  line 10: CFLAGS: command not found
# reading passphrase from stdin


Thats what I get when I drag the makefile into a terminal, tried the other ways without success

---

### Post by chili555 on 2010-09-20
Please let me see:```
ls Desktop/RTL8188SU_Driver/Linux/linux_2.6.0003.0825.2009
ls Desktop/RTL8188SU_Driver/Linux/
ls Desktop/RTL8188SU_Driver/
```You do not drag the Makefile into the terminal; instead, in the directory containing the Makefile, you simply issue the command, 'make.'

I notice that you are still incorrectly in the wpa_supplicant-0.5.10 directory.

Thanks.

---

### Post by Moose2000 on 2010-09-20
> janice@rachel-desktop:~$ ls Desktop/RTL8188SU_Driver/Linux/linux_2.6.0003.0825.2009
firmware       readme.txt                   wlan0up
HAL            release_note                 wpa1.conf
ieee80211      runwpa                       wpa_supplicant-0.5.10
ifcfg-wlan0    wireless-rtl-ac-dc-power.sh  wpa_supplicant-0.5.10.tar.gz
Makefile       wlan0dhcp
RadioPower.sh  wlan0down
janice@rachel-desktop:~$ 

janice@rachel-desktop:~$ ls Desktop/RTL8188SU_Driver/Linux/
linux_2.6.0003.0825.2009
janice@rachel-desktop:~$ 

janice@rachel-desktop:~$ ls Desktop/RTL8188SU_Driver/
Linux  Mac  Windows


There we go

---

### Post by chili555 on 2010-09-20
Please do:```
cd Desktop/RTL8188SU_Driver/Linux/linux_2.6.0003.0825.2009
sudo su
make
make install
exit
```Please report any errors.

---

