---
title: "Upgraded from Ubuntu 16.04 to 18.04 - wifi no longer working"
date: 2018-12-23
forum: Networking &amp; Wireless
---

### Post by fourducks on 2018-12-23
Hi

Very inexperienced non technical Linux user here.

I recently upgraded to Ubuntu 18.04, which has resulted in me now being unable to connect to wifi.

My computer can see the various wifi networks available, but is unable to connect to any of them. 

I have been googling around for the past 6 hours, and tried multiple things I've read, but with no luck.

Any help would be much appreciated ..i am running an old Toshiba machine. this is my main laptop and this recent Ubuntu upgrade and associated difficulties has made me consider switching to a Mac instead for productivity reasons. The lack of internet on the laptop is making it particularly difficult to troubleshoot .

Many thanks in advance for any help that can be offered.

Thanks!

---

### Post by praseodym on 2018-12-23
Please run the wireless script from the sticky thread and show the outputs

---

### Post by fourducks on 2018-12-23
> **praseodym said:**
> Please run the wireless script from the sticky thread and show the outputs


Hi 

Many thanks for your help... a much appreciated Christmas present! 

Attaching the output of the code below. Hope this helps.


>>> [https://paste.ubuntu.com/p/kz5h7b4snW/](https://paste.ubuntu.com/p/kz5h7b4snW/)

Please do let me know if anything further I can provide to help diagnose the issue further.

Thanks!

---

### Post by praseodym on 2018-12-23
Try changing the encryption mode in your router to WPA2 only, not mixed mode WPA/WPA. Additionally you can try
```

echo "options rtl8821ae msi=0 swenc=1 swlps=0 fwlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl88821ae_options.conf
sudo modprobe -rfv rtl8821ae
sudo modprobe -v rtl8821ae
```

---

### Post by fourducks on 2018-12-23
Hi
 
Thanks for the guidance.
 
Regarding the WPA2 guidance, I don’t unfortunately have a “WPA2 only” in the network option. The options I have are only:

[LIST]
[*]None
[*]WEP 40/128-bit Key (Hex or ASCII)
[*]WEP 128-bit Passphrase
[*]LEAP
[*]Dynamic WEP (802.1x)
[*]WPA & WPA2 Personal
[*]WPA & WPA2 Enterprise
[/LIST]
 
Currently, the security settings are on “WPA & WPA2 Personal”. I have also separately tried connecting to other wifi networks, but have also been unsuccessful here.
 
Finally, I’ve tried entering the commands given, but these have not fixed the issue. This is true also after a reboot.
 
I’ve re-run the script in the sticky, and attach the log ouput below in case helps with any further guidance.
[https://paste.ubuntu.com/p/Q6gjHDXS9b/](https://paste.ubuntu.com/p/Q6gjHDXS9b/)
 
Many thanks in advance! Really hoping I can resolve this somehow. :)

---

### Post by praseodym on 2018-12-23
You need to change the encryption mode in your router interface. Check its manual

---

### Post by fourducks on 2018-12-23
I've tried connecting from the laptop through 2 different internet networks - one being my home internet connection, and the other trying to tether from a Vodafone mobile phone connection.

Neither of the above have worked, so not sure changing any settings on the router will have much impact? Furthermore, there are several computers which are successfully connected to the home internet connection, which suggests the issue is with "my" laptop vs the internet connection itself.

As my laptop running ubuntu is 5+ years old, I don't have any of the manuals etc.

Do you have any other suggestions?

Thanks!:)

Hi

I should say also that on the mobile phone network that I have tried tethering a connection from, I also tried to remove all passwords from the internet connection.

Unfortunately my ubuntu laptop was still unable to connect....suggesting a more fundamental issue than security settings alone. I'm not sure?

Hope this information helps some more.

Thanks

---

### Post by praseodym on 2018-12-23
Just seen that your /etc/network/interfaces shows a configuration for LAN. Revert it to default via
```

echo -e "auto lo\niface lo inet loopback" | sudo tee /etc/network/interfaces
```
and reboot

---

### Post by fourducks on 2018-12-23
Hi
 
Latest script output is below.
[https://paste.ubuntu.com/p/CNf4skCD6D/](https://paste.ubuntu.com/p/CNf4skCD6D/)
 
Unfortunately still having the same issue after having trying the command.
 
I tried your suggestion with “ech” however this seemed to prompt an error, so I then also tried with “echo”…so that the full line became:
 
```
echo -e "auto lo\niface lo inet loopback" | sudo tee /etc/network/interfaces


``` 

I then rebooted, but same issue after this.
 
I’ve tried this line multiple times again, each with a reboot, to see if issue was fixed, but same issue occurring.
 
Any other thoughts as to what could be the issue?
 
Thanks

---

### Post by praseodym on 2018-12-23
> ```
[   77.260463] [UFW BLOCK] IN=wlan0 OUT= MAC= SRC=fe80:0000:0000:0000:<IP6 'wlan0' [IF2]> DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=862345 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
[   77.260531] [UFW BLOCK] IN=wlan0 OUT= MAC= SRC=fe80:0000:0000:0000:<IP6 'wlan0' [IF2]> DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=177207 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
[   77.270735] [UFW BLOCK] IN=wlan0 OUT= MAC= SRC=fe80:0000:0000:0000:<IP6 'wlan0' [IF2]> DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=862345 PROTO=UDP SPT=8612 DPT=8612 LEN=24 
[   77.270827] [UFW BLOCK] IN=wlan0 OUT= MAC= SRC=fe80:0000:0000:0000:<IP6 'wlan0' [IF2]> DST=ff02:0000:0000:0000:0000:0000:0000:0001 LEN=64 TC=0 HOPLIMIT=1 FLOWLBL=177207 PROTO=UDP SPT=8612 DPT=8610 LEN=24 
```

The firewall blocks. Deactivate it

```
sudo apt-get remove --purge ufw gufw
sudo iptables -t filter -n -L -v
sudo iptables -F
sudo iptables -X
```

---

### Post by fourducks on 2018-12-23
Hi

Thanks - tried running those code lines in the terminal, and rebooted...still no luck unfortunately.

Same issue as before where I'm not able to connect to the internet wifi.

Updated log output is:
[https://paste.ubuntu.com/p/2vvQH3fsRF/](https://paste.ubuntu.com/p/2vvQH3fsRF/)

Anything else I could do?

Thanks

---

### Post by praseodym on 2018-12-24
You dont get an IPv4 address. Lets check
```

sudo dpkg-reconfigure resolvconf
```

---

### Post by fourducks on 2018-12-24
Hi

Thanks. I ran that code...after clicking the subsequent 2 dialog boxes, I then received the following output in the terminal:

```
resolvconf-pull-resolved.service is a disabled or a static unit, not starting it.

```

The updated sticky script log output also pasted below:
[https://paste.ubuntu.com/p/nxsqvcgrkS/](https://paste.ubuntu.com/p/nxsqvcgrkS/)

Issue still unresolved unfortunately - I can't connect to the internet.

Appreciate your continued support here!

Thanks

---

### Post by praseodym on 2018-12-24
Ok, lets run

```
sudo rm /etc/resolv.conf
sudo ln -s /var/run/resolvconf/resolv.conf /etc/resolv.conf
sudo service network-manager restart
```

---

### Post by fourducks on 2018-12-24
Hi

I've run these commands and rebooted, but same issue as before. 

Pasted the latest script output below:
[https://paste.ubuntu.com/p/j4nzgvDKFf/](https://paste.ubuntu.com/p/j4nzgvDKFf/)

Thanks for your continued help.

---

### Post by praseodym on 2018-12-24
Change the encryption mode in your router to WPA2-AES (CCMP) only. The router should have a sticker with login/PW for that (not confusing with ESSID and PW!). There should also be an IP address for connecting in your browser, type that in and login

---

### Post by fourducks on 2018-12-24
Hi

Okay thanks - I will look into this, but just to clarify first of all..other laptops in the house are able to connect to the internet fine, and I have also tried tethering from phone's network (with a password and then also without password), with no luck.

Given the above, is it likely to be the case that the issue is with my router's setting vs some configuration on my laptop ?

Thanks

For example, all other devices in the house (including the laptop that I am currently typing from) are able to connect to the internet network fine..which suggests to me that the issue is not with the router itself but the settings of the laptop running ubuntu?

Hope that clarifies.

Thanks

---

### Post by praseodym on 2018-12-24
Check if the MAC address filter is turned on in the router. If yes, turn it off

---

### Post by fourducks on 2018-12-24
Hi 

Just checked and it's not on on the router...and also tried again tethering from my phone which I was also unsuccessful in connecting to.

Any further thoughts, or proving too difficult to try to solve this?

Thanks

---

### Post by praseodym on 2018-12-25
Please show
```

ip -4 neighbor
```

---

### Post by fourducks on 2018-12-25
Hi

Thanks

I entered the code into terminal...the issue still there with not being able to connect to internet.

Updated log output pasted below:

[https://paste.ubuntu.com/p/7dV7zRs7zg/](https://paste.ubuntu.com/p/7dV7zRs7zg/)

Thanks!

---

### Post by jeremy31 on 2018-12-25
Try ```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
echo "options rtl8723ae ips=N" | sudo tee /etc/modprobe.d/rtl8723ae.conf
```
Reboot

Can you change the encryption used on that wifi to WPA2 only, no TKIP

---

### Post by fourducks on 2018-12-25
Hi 

Tried the lines but no luck....I've tried connecting to 2 other wifi networks as well (one which is an open network without any password/security).

Do you think this issue is beyond repair? I'm not sure what else I can do - I don't have the understanding unfortunately to effectively troubleshoot myself.

Log output pasted below.

[https://paste.ubuntu.com/p/gH4Swqqp2d/](https://paste.ubuntu.com/p/gH4Swqqp2d/)

Seasons greetings!

Thanks

---

### Post by praseodym on 2018-12-25
Please show these outputs
```

ip -4 neighbor
route -n
```

Edit: You may want to try updating the drivers

```
sudo apt-get install git build-essential 
git clone https://github.com/lwfinger/rtlwifi_new 
cd rtlwifi_new
make
sudo make install
sudo depmod -a
sudo update-initramfs -u
```
and reboot

---

### Post by fourducks on 2018-12-25
Ok thanks.

The output of the first 2 lines of code is:

```
Kernel IP Routing Table
Destination    Gateway    Genmask    Flags Metric Ref    Use Iface
```

How could I update my drivers given that I can't get internet on that laptop?

I have a usb stick and another laptop with internet (running windows 10), but don't know how to download drivers from github onto a usb stick.

Do you have any links with a tutorial for this?

Thanks

---

### Post by praseodym on 2018-12-25
Go to

[https://github.com/lwfinger/rtlwifi_new](https://github.com/lwfinger/rtlwifi_new) 

Click on the green button "clone or download" and "Download ZIP". Unpack it to your home folder and run

```
cd rtlwifi_new-master
make
sudo make install
sudo depmod -a
sudo update-initramfs -u
```

---

### Post by fourducks on 2018-12-25
Great thanks - I updated using that, still no luck..

Updated log:
[https://paste.ubuntu.com/p/nQfqQ45Tsp/](https://paste.ubuntu.com/p/nQfqQ45Tsp/)


Beginning to think I should give up on linux! 

Thanks for the continued support

---

### Post by praseodym on 2018-12-25
Lets try
```

sudo apt-get purge resolvconf
echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee /etc/resolv.conf
```
Reboot

---

### Post by fourducks on 2018-12-25
Just tried but  still no luck

Latest log output below

[https://paste.ubuntu.com/p/Nj9YZVqStm/](https://paste.ubuntu.com/p/Nj9YZVqStm/)

Thanks!

---

