---
title: "Wi-fi is not working inUbuntu 18.04.02 in Dell Inspiron"
date: 2019-06-05
forum: Networking &amp; Wireless
---

### Post by vishalraj232 on 2019-06-05
Hey everyone, I just instaled Ubuntu 18.04.02 inital but my wi-fi  is not working. I try last 2 days and try almost all method that given in ubuntu forum and youtube.

But still not working for me. Could any one hep me out or i have to re-install ubuntu.

I already followed some of these steps: 

git clone [https://github.com/lwfinger/rtlwifi_new.git](https://github.com/lwfinger/rtlwifi_new.git)
Checkout to the extended branch


git checkout extended
Enter to the cloned folder


cd rtlwifi_new
Start installation


sudo make install
sudo modprobe -r rtl8723de
sudo modprobe rtl8723de

sudo apt purge bcmwl-kernel-source
sudo sed -i '/blacklist bcma/ d' /etc/modprobe.d/blacklist.conf
sudo sed -i '/blacklist brcmsmac/ d' /etc/modprobe.d/blacklist.conf
Reboot if wifi does not come on do:


sudo modprobe -v brcmsmac
sudo modprobe -v bcma

---------------------------------

 sudo apt updatesudo apt install build-essential git


git clone [https://git.kernel.org/pub/scm/linux/kernel/git/iwlwifi/backport-iwlwifi.git](https://git.kernel.org/pub/scm/linux/kernel/git/iwlwifi/backport-iwlwifi.git)
cd backport-iwlwifi
sudo make
sudo make install


The ‘make’ step takes a few moments; please be patient.


Now, we’ll write a conf file:


sudo -i
echo “options iwlwifi disable_msix=1”  >>  /etc/modprobe.d/iwlwifi.conf

cd backport-iwlwifi
sudo make clean
sudo make
sudo make install
Reboot.


Please retain the files and these instructions for that time.

---------------------------------------
[https://ubuntuforums.org/showthread.php?t=2319457](https://ubuntuforums.org/showthread.php?t=2319457)

and amny more even i folowed youtube videos also but still not fixed.




Thanks.

---

### Post by kc1di on 2019-06-05
Please go to a terminal and enter this command and post the output here: ```
lspci | grep -i network
```

also this command : ```
rfkill list
```

---

### Post by vishalraj232 on 2019-06-05
Hey for first command

lspci | grep -i network 

Output is: 
01:00.0 Network controller: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter (rev 31)

and for sencond command 

rfkill list

Output is giving this:

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

---

### Post by vishalraj232 on 2019-06-05
[COLOR=#000000]Hey for first command[/COLOR]

[COLOR=#000000]lspci | grep -i network [/COLOR]

[COLOR=#000000]Output is: [/COLOR]
[COLOR=#000000]01:00.0 Network controller: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter (rev 31)[/COLOR]

[COLOR=#000000]and for sencond command [/COLOR]

[COLOR=#000000]rfkill list[/COLOR]

[COLOR=#000000]Output is giving this:[/COLOR]

[COLOR=#000000]0: hci0: Bluetooth[/COLOR]
[COLOR=#000000]Soft blocked: no[/COLOR]
[COLOR=#000000]Hard blocked: no[/COLOR]

---

### Post by jeremy31 on 2019-06-05
```
cd backport-iwlwifi
sudo make uninstall
```
Reboot and run kc1di's commands again

---

### Post by vishalraj232 on 2019-06-05
sorry but i am new here in ubuntu. What does mean of [COLOR=#000000] "kc1di's commands" and where i'll find it?[/COLOR]

---

### Post by vishalraj232 on 2019-06-05
hey,

i run the above command and reboot system and again run kcidi's command now i am getting this:

lspci | grep -i network


01:00.0 Network controller: Qualcomm Atheros QCA9377 802.11ac Wireless Network Adapter (rev 31)

rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

Now what should i do?

---

### Post by jeremy31 on 2019-06-05
I would do ```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
Reboot and if it still doesn't work, see the wireless script link in my signature and post results

---

