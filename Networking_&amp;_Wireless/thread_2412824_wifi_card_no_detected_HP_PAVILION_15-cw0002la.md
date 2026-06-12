---
title: "wifi card no detected HP PAVILION 15-cw0002la"
date: 2019-02-17
forum: Networking &amp; Wireless
---

### Post by daniel53194 on 2019-02-17
Hi there, i'm new with Linux Ubuntu and i'm trying to know why my HP PAVILION 15-cw0002la the wifi card is no detected just in linux because in Windows it works perfectly, and i tried a lot of things and did't work. my laptop has a Realtek RTL8821CE 802.11ac PCIe Wireless Network Adapter. and is not working and the jack it's. so can some one help me? I need linux for college. thank u. 


Alright i was able to make it work just if you have a  Realtek RTL8821CE 802.11ac PCIe Wireless Network Adapter. follow the code or go to [https://askubuntu.com/questions/990378/wi-fi-not-working-on-lenovo-thinkpad-e570-realtek-rtl8821ce](https://askubuntu.com/questions/990378/wi-fi-not-working-on-lenovo-thinkpad-e570-realtek-rtl8821ce). Is the 5th one. just make sure that the secure boot is completely disable. if you can not make sure of it then you can go to the BIOS and change it. In my case to have directly access it was F10 and the disable it. The it will work :)

Open up a terminal and type the following lines (You can cut and paste if you prefer):
  sudo apt-get install --reinstall git dkms build-essential linux-headers-$(uname -r)
git clone [https://github.com/tomaspinho/rtl8821ce](https://github.com/tomaspinho/rtl8821ce)
cd rtl8821ce
chmod +x dkms-install.sh
chmod +x dkms-remove.sh
sudo ./dkms-install.sh
  After this is completed successfully, you should reboot and find that your Wifi is working. 
  *You also want to make sure **SecureBoot** is **Disabled** in the BIOS settings or it won't let you load the unsigned self-complied kernel module.*

---

