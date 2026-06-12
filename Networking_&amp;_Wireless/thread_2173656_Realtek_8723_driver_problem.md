---
title: "Realtek 8723 driver problem"
date: 2013-09-10
forum: Networking &amp; Wireless
---

### Post by frede2 on 2013-09-10
Hey all.

I have a clevo 110er with Realtek 8723 wireless chip, running Ubuntu 12.04.2 LTS.

 After installing ubuntu i had no wireless. I followed the steps from some of the last pages of this thread [http://ubuntuforums.org/showthread.php?t=2017622&page=13](http://ubuntuforums.org/showthread.php?t=2017622&page=13) to get wireless running. This resulted in wireless networks showing up in the network manager. I can now connect to most wireless networks, but the connection is very unstable. It can sit right next to the accespoint, and the connection varies between full signal to almost no signal. If i am further from the accespoint it keeps connecting/disconnecting from the network. The speed of the internet inbetween disconnects is not bad at all, and runs smoothly, it just stalls everytime it reconnects. At my school this happen all the time. When booting up in windows there is no problems.

Any help is appreciated.

---

### Post by chili555 on 2013-09-10
I don't know which exact post on that thread you linked is the one you followed but the package linked in post #127 is strongly preferred. If that is not the version you installed, please do so.

---

### Post by frede2 on 2013-09-10
Thank you very much for answering :D

It is indeed the one in post #127 i have installed, unless several of the downloads have the exact same filename?

---

### Post by chili555 on 2013-09-10
> **frede2 said:**
> Thank you very much for answering :D

It is indeed the one in post #127 i have installed, unless several of the downloads have the exact same filename?[https://dl.dropboxusercontent.com/u/58267392/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012.tar.gz](https://dl.dropboxusercontent.com/u/58267392/rtl_92ce_92se_92de_8723ae_linux_mac80211_0007.0809.2012.tar.gz)

It should be the 00[COLOR="#FF0000"]07.0809[/COLOR].2012 version; or, as I call it, 7-8-9. Is that the one?

---

### Post by frede2 on 2013-09-11
that is the version i have used. Perhaps i can try to reinstall it, and see if it helps?

---

### Post by chili555 on 2013-09-11
You might try the even newer version mentioned here: [http://ubuntuforums.org/showthread.php?t=2169602&page=2&p=12770984#post12770984](http://ubuntuforums.org/showthread.php?t=2169602&page=2&p=12770984#post12770984)

Since you are using 12.04.2 and not 13.04, I suggest you try compiling first *without* these changes: > Now open the "pci.h" file from the extracted directory above, and add following lines...If it fails, do a 'make clean' and make the changes and try again. I do not currently have a 12.04.2 installation or I'd do a proof myself. 

Please try it and let us have your report.

---

### Post by frede2 on 2013-09-11
I tried to download the file, but all internet communication seems to stall every few seconds now. Perhaps it is not a wireless problem, as it now seems to happen when i connect through an ethernet cable aswell. I am writing this from a windows 7 installation on the same machine(dual boot), and there are no networking/wireless problems at all here. Should i still try the newer verison of the driver?

---

### Post by frede2 on 2013-09-11
I was worried that the hardware might be faulty, but the connection never drops from full signal in windows 7, and i can browse/download really fast.

---

### Post by frede2 on 2013-09-11
I have installed the new driver you linked now, but i must have messed up somewhere. Everytime i restart now, the device name of the wireless changes. By that i mean that if i run iwconfig, my wlan is now named wlan4, and the number increases by one for each restart,

 Also i have to add connections (wireless ssid/password). If i go to the newwork manager and press edit connections, i have a list of:
"nameofmywireless"
"nameofmywireless" 1
"nameofmywireless" 2
"nameofmywireless" 3

---

### Post by chili555 on 2013-09-11
> **frede2 said:**
> I have installed the new driver you linked now, but i must have messed up somewhere. Everytime i restart now, the device name of the wireless changes. By that i mean that if i run iwconfig, my wlan is now named wlan4, and the number increases by one for each restart,

 Also i have to add connections (wireless ssid/password). If i go to the newwork manager and press edit connections, i have a list of:
"nameofmywireless"
"nameofmywireless" 1
"nameofmywireless" 2
"nameofmywireless" 3When you ran 'make,' were there warnings? You can certainly compile again; something like:```
cd Desktop/rtl_files_or_whatever
make clean
make
sudo make install
```At the 'make' step, capture all the terminal output and paste it here and give us the link in your reply: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

---

### Post by frede2 on 2013-09-12
Here is the output from make:

[http://paste.ubuntu.com/6096307/](http://paste.ubuntu.com/6096307/)

When i booted the laptop at school just now, it is back to wlan0 for some reason. Now i get the "Wireless disasbled by hardware switch" each time i boot, and i have to press fn+f11 to turn it on. It disconnects from the schools wireless every few seconds, so it is near unuseable. The same wireless network works fine for the others students in class.

---

### Post by chili555 on 2013-09-12
You don't see that often; not a single warning and, of course, no errors! There is at least one driver parameter we can try:```
sudo modprobe -r rtl8723e
sudo modprobe rtl8723e swenc=1
```If it helps, we can write one quick file to make it persistent.

Since you have a custom driver, let's see what other parameters may be available:```
modinfo rtl8723e | grep parm
```

---

### Post by frede2 on 2013-09-12
Here is the output from modinfo rtl8723e | grep parm:
[http://paste.ubuntu.com/6097141/](http://paste.ubuntu.com/6097141/)

I tried to set swenc=1 , but i am no longer at school, so i can't check if it disconnects. On my home wifi it keeps the connection, but it falls to very low signal strength all the time. My friend is sitting right besides me with constant full signal on his mac. Also i have no problems here if i boot to windows.

---

### Post by chili555 on 2013-09-13
> On my home wifi it keeps the connection, but it falls to very low signal strength all the time. At home, let's see:```
dmesg | grep rtl
iwconfig
```Does it start out fine and then fall off? If so, we might look at power management.

---

### Post by frede2 on 2013-09-19
output from dmesg | grep rtl
[http://paste.ubuntu.com/6127382/](http://paste.ubuntu.com/6127382/)

---

### Post by frede2 on 2013-09-19
output from iwconfig:
[http://paste.ubuntu.com/6127388/](http://paste.ubuntu.com/6127388/)

---

### Post by frede2 on 2013-09-19
It sometimes seems like it works fine for the first minutes after boot, and then starts the dicsonnect/reconnect thing. But this might just be by chance.

---

### Post by varunendra on 2013-09-21
> **frede2 said:**
> It sometimes seems like it works fine for the first minutes after boot, and then starts the dicsonnect/reconnect thing. But this might just be by chance.

Please try -
```
sudo modprobe -rv rtl8723e
sudo modprobe -v rtl8723e swlps=N swenc=1 ips=0 fwlps=0
```
Post back if it returns any errors. If not, does it make the connection anymore stable?

As Dr. Chilli mentioned previously, it is a temporary change that will be lost at next boot. If it helps, we can try to strip it down to only those parameters that are actually helping, then make it permanent.

---

### Post by frede2 on 2013-09-21
Ouput:
[http://paste.ubuntu.com/6137125/](http://paste.ubuntu.com/6137125/)

It just disconnected again, so haven't helped so far.

---

### Post by varunendra on 2013-09-21
I think we've already seen almost all the interesting parts of your setup, but just for the kick of it, could you please post a detailed report created by a script?

Please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

I suggest you use the "alternate" version of the script (from the link at the bottom of the linked post) as it covers a bit more stuff in dmesg and lsmod.

---

