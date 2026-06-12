---
title: "How do i obtain the windows driver for my system?"
date: 2008-08-07
forum: Networking &amp; Wireless
---

### Post by iseekins on 2008-08-07
I just installed ndisgtk, but i don't know how to obtain my windows driver to make my wireless work.

---

### Post by mjavorek on 2008-08-07
At first you must know, which card you have. Then you can search for win driver.

---

### Post by iseekins on 2008-08-07
im in vista right now and it says i have a Dell Wireless 1390 WLAN Mini-Card. how do i use that information and install the driver in ubuntu?

---

### Post by dje on 2008-08-07
> **iseekins said:**
> im in vista right now and it says i have a Dell Wireless 1390 WLAN Mini-Card. how do i use that information and install the driver in ubuntu?

i have that card, do the following:
open up a terminal (applications >> accessories >> terminal) and type the following:
```
sudo apt-get install b43-fwcutter
```
answer yes when it asks to download the firmware

hope that helps,
dje

---

### Post by Ayuthia on 2008-08-07
If you don't know how to check, you can open up the Terminal and type:
```
lspci -nn
```and look for something that says Network Controller or Ethernet Controller.  You can also look at:
```
lshw -C network
```That will list out your network cards.  

If you need more help, just post the results of lspci -nn and we will try to help point you in the right direction.

---

### Post by iseekins on 2008-08-07
ok thanks guys:)

---

### Post by iseekins on 2008-08-07
ok it works!!!! Thanks guys for all the help

---

### Post by iseekins on 2008-08-07
Uh-oh Now I can see the wireless networks but it wont let me connect. it just keeps trying to connect and than stops after several minutes. Im on a college campus and I was in my room and it connected for me and I moved to a different building and I can see the networks to connect to but it wont let me connect.

---

### Post by Locutus_of_Borg on 2008-08-07
i have a laptop with that wireless card

in order to connect i had to manually turn wireless off through the hardware button then back on, otherwise it would just endlessly try to connect

if that doesnt work try it through the terminal:
```

ifconfig wlan0 down && dhclient -r wlan0 && ifconfig wlan0 up && iwconfig wlan0 essid NAME_OF_YOUR_NETWORK_ESSID && iwconfig wlan0 mode Managed && dhclient wlan0

```
change wlan0 to your interface, and input your own ESSID

---

### Post by iseekins on 2008-08-07
> **Locutus_of_Borg said:**
> i have a laptop with that wireless card

in order to connect i had to manually turn wireless off through the hardware button then back on, otherwise it would just endlessly try to connect

if that doesnt work try it through the terminal:
```

ifconfig wlan0 down && dhclient -r wlan0 && ifconfig wlan0 up && iwconfig wlan0 essid NAME_OF_YOUR_NETWORK_ESSID && iwconfig wlan0 mode Managed && dhclient wlan0

```
change wlan0 to your interface, and input your own ESSID

Sorry im really new to this...how do i know my interface and what is my own ESSID?

---

### Post by Locutus_of_Borg on 2008-08-07
open up a terminal then:
```
 sudo -i
iwconfig
```
this will list your interfaces, the one that does not say "no wireless extensions" is your wireless interface, so substitute that for wlan0 in the previous command (it will probably be either eth0 or wlan0)

now back in that same terminal, enter ```
iwlist [INTERFACE] scan
``` use the same interface from the last step (dont use brackets) 
this will list all the available wireless networks you can connect to including the ESSID and whether it is unsecure or encrypted (you an also just click on the network manager icon to get a list of available wireless network names/essid's) put the name of the network into the previous post's command where it says "NAME_OF_YOUR_NETWORK_ESSID"

then just press enter, wait a moment, and you should get a message saying dhcp has binded you to some address, now you should be connected

---

