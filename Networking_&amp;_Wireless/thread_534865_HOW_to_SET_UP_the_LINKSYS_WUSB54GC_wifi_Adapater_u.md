---
title: "HOW to SET UP the LINKSYS WUSB54GC wifi Adapater using ndiswrapper"
date: 2007-08-25
forum: Networking &amp; Wireless
---

### Post by boem on 2007-08-25
Hi all,

[SIZE="2"]Here are the steps I followed successfully to make the wusb54gc wifi adapter work using ndiswrapper.
[/SIZE]

just to point out that I've read unsuccessfully many posts for setting this adapter.

I have Ubuntu Feisty Fawn. WPA security and static IP.


**1. ****download **the latest windows driver at the linksys site.
**2. ****login as root** and copy the 2 files (rt73.inf and rt73.sys) in /root/Desktop
**3. ****open a terminal** and go to /root/Desktop

**4. **> lsmod|grep rt73
this should show you rt73usb, the default driver. remove it by typing:

**5. **> rmmod rt73usb

**6. **> ndiswrapper -l
this should give you no result. otherwise, you should remove any existing driver using ndiswrapper -r 

**7. **> ndiswrapper -i rt73.inf

**8. **> ndiswrapper -m

**9.**>  modprobe ndiswrapper

**10. **> iwconfig
at this stage, you should have your adapter recognized as wlan0. the output should look like this:

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.467 GHz  Access Point: 00:07:CB:52:A8:0F   
          Bit Rate=54 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm  
          RTS thr=2347 B   Fragment thr=2346 B   
          Encryption key:on
          Power Management:off
          Link Quality:68/100  Signal level:-52 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

If you don't have wlan0, go back to the previous steps. check your version of ndiswrapper.

**11. **we will now enter the wifi as well as the TCP/IP settings. Open the file **/[SIZE="2"]etc/network/interfaces[/SIZE]** and add the following:
 
> auto wlan0
iface wlan0 inet static
address 192.168.0.1
netmask 255.255.255.0
gateway 192.168.0.254
dns-nameserver 212.27.39.135 212.27.39.134
wpa-driver wext
wpa-ssid your_ssid
wpa-proto WPA
wpa-pairwise TKIP
wpa-key-mgmt WPA-PSK
wpa-psk your_key

IT'S IMPORTANT TO NOT USE NetworkManager for all these steps. you should adapt according to your IP , gateway IP, dns nameservers, essid, wpa_key. Also check for your encryption type (I use TKIP). change wpa-pairwise and wpa-key-mgmt according to your router configuration.

save the file.

**12. **> /etc/init.d/networking restart
It would be also a good idea to remove the adapter from it's slot and replace it again in order to have it initialized correctly.

**13. **> iwconfig
you should see now your essid and key in the output of iwconfig. if not, go back to the previous steps.

**14. **> ping your_gateway_ip
replace with your gateway IP. if the ping is ok, go forward. if not, check the previous steps starting at step 11.

**15. **open the file **[SIZE="2"]/etc.resolv.conf[/SIZE]** and add your dns servers, this way:
> nameserver 212.27.39.135
nameserver 212.27.39.134

**16. **> ping google.com
this should be ok and Internet is YOURS.

NOW IT'S TIME TO MAKE ALL THIS STUFF PERSISTANT if the previsous steps are ok for you.

**17. **add to the file **[SIZE="2"]/etc/modprobe.d/blacklist[/SIZE]** the line:
> blacklist rt73usb

**18. **add to the file **[SIZE="2"]/etc/modules[/SIZE]** the following:
> ndiswrapper

**19. **add to **[SIZE="2"]/etc/init.d/bootmisc.sh[/SIZE]**, the following at the end of the do_start() procedure:
> 	ifdown wlan0
	ifup wlan0

without step 19, I was forced after reboot to type : /etc/init.d/networking restart

good luck

---

### Post by SKi on 2007-08-28
Looks good, but where do you get RT73.ini and RT73.sys.. Linksys only gives *.exe files.

Thanks, SKi :popcorn:

---

### Post by boem on 2007-08-29
here a link in the french linksys site:

[http://www-fr.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=FR%2FLayout&cid=1175231402335&packedargs=sku%3DWUSB54GC&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=0233502335B01&displaypage=download#versiondetail]("http://www-fr.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=FR%2FLayout&cid=1175231402335&packedargs=sku%3DWUSB54GC&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=0233502335B01&displaypage=download#versiondetail")

In the column "N° de version du périphérique", specify Version 1.0, Enter.

go then to "Pilote" section, download a zip file, unzip it, go to DRIVERS folder and there you'll find the 2 files : rt73.inf and rt73.sys.

---

### Post by SKi on 2007-08-29
> **boem said:**
> here a link in the french linksys site:

[http://www-fr.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=FR%2FLayout&cid=1175231402335&packedargs=sku%3DWUSB54GC&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=0233502335B01&displaypage=download#versiondetail]("http://www-fr.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=FR%2FLayout&cid=1175231402335&packedargs=sku%3DWUSB54GC&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=0233502335B01&displaypage=download#versiondetail")

In the column "N° de version du périphérique", specify Version 1.0, Enter.

go then to "Pilote" section, download a zip file, unzip it, go to DRIVERS folder and there you'll find the 2 files : rt73.inf and rt73.sys.

Nicely done! thanks for the info Boem.

Thanks, SKi :guitar:

---

### Post by nicatron on 2007-09-03
you can also download the .exe and use WINE to open and extract it...
will this work on WPA-PSK2 ?

---

### Post by vhunterd on 2007-09-03
I have to say thank you! I've been trying to figure out for an hour why, I can't blacklist rt73usb! Everytime I do, it causes major problems with my system, gnome doesn't work, my keyboard/mouse are not recognized anymore (so I can't log in), and I get a massive amount of error messages when booting (it went by fast but I think it said something about the HAL damon...or something similar). Anyway just removing the fing module fixed my problem and I am now online. THANKS!

---

### Post by nicatron on 2007-09-03
would u say this is correct?

auto wlan0
iface wlan0 inet static
address 192.168.0.1
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameserver 68.87.85.98 68.87.89.146
wpa-driver wext
wpa-ssid myssid
wpa-proto WPA
wpa-pairwise TKIP
wpa-key-mgmt WPA-PSK2
wpa-psk2 mykey

i havent been able to ping anything,

---

### Post by TestDummy! on 2007-09-04
@nicatron: Did you try changing the computer's IP  to the next free one in 192.168.1.* (perhaps 192.168.1.2) instead of 192.168.0.1, like it is now?

I don't know if it'd make a difference, but it seems like it would to me.

---

### Post by boem on 2007-09-05
nicatron, I understand that your wifi connection is ok and that the ping is not ok, i.e. it's a matter of TCP/IP setting. Is that right ?

---

