---
title: "Help with usb wifi needed"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by I Dunno on 2007-01-06
Ok i have a Netgear WG111T and I used ndiswrapper to get the drivers to work so the blue LED lights up, the  problem I am having now is that I cannot get the internet connection to work I have entered the SSID and the WPA-key in the networking options, I then tried a DCHP and a static ip connection and still nothing...

To get this far has took we quite a while so help will be extremely appreciated

---

### Post by teaker1s on 2007-01-06
save yourself a lot of agro, either with synaptic or apt-get install
[COLOR="Red"]network-manager-gnome[/COLOR]
make sure that interfaces in
[COLOR="Red"]system-administration-networking[/COLOR] are not configured.

reboot and on your panel network manager applet will appear and you can use this to easily control wireless

---

### Post by I Dunno on 2007-01-06
Thanks it worked! Im typing this through ubuntu :D 

now im sort of new to ubuntu so is there a virus scanner and firewall already included inside or would you recommend a anti-virus and firewall to download

---

### Post by teaker1s on 2007-01-06
viruses-nothing that is worth worrying about there are iptables, as an x windows user I prefer gui option

you may need to uncomment some of the sources in
[COLOR="Red"]gksudo gedit /etc/apt/sources.list[/COLOR]

[COLOR="Red"]gksudo synaptic[/COLOR]
in preferences select recommended as dependency
hit reload button;) 
set search box to description and name
search firewall

---

### Post by I Dunno on 2007-01-08
I have installed shorewall but cannot see it on the desktop is it supposed to be like this? Or is there a way to access it.

---

### Post by teaker1s on 2007-01-08
install
[COLOR="Red"]alacarte[/COLOR]

install
[COLOR="Red"]menu[/COLOR]

which makes gnome a lot more friendly to see installed programs

you will then see "menu layout" under preferences and it's tick boxes to select

synaptic select settings choose preferences and tick show properties in main window under general tab-this will show installed file location

which normally is
/usr/bin/nameofyourapp

---

### Post by I Dunno on 2007-01-08
"install
alacarte"

"install
menu"

I do know some things about ubuntu but i don't know what you mean there, do you mean that i have to type that in the terminal?

---

### Post by teaker1s on 2007-01-09
sorry should have said terminal

[COLOR="Red"]gksudo synaptic[/COLOR]

on synaptic select settings tab and preferences and set your synaptic as the attached screenshot-this will make sure you have no dependency issues.

now hit reload tab

search package name and discription-see screen shot

[COLOR="Red"]
alacarte[/COLOR]
and
[COLOR="Red"]menu[/COLOR]

now  on panel "menu layout" will appear under system _preferences_menu layout 
this allows you to select what you want to see on menu's

the "menu" package will give you debian menu's and should show all installed programs

---

