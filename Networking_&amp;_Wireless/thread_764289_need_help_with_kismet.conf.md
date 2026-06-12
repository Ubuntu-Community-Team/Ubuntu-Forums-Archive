---
title: "need help with kismet.conf"
date: 2008-04-23
forum: Networking &amp; Wireless
---

### Post by atdhe on 2008-04-23
hi can who help me i have a asus wl 167g usb wirless card and i dont know how too config kismet... can who help me pls.

---

### Post by odin1965 on 2008-04-23
You need to know the interface and driver of your wireless card. Right click on Network manager and click on Connection Information. Your interface should be something like wlan0 or eth1 or whatever is in bracket after 802.11 Wifi
The driver name should be listed below that. Mine is iwl3945. Use that info below. The rest is from [http://www.linuxbasement.com/content/finuxs-kismet-gpsdrive-google-earth-howto-guide](http://www.linuxbasement.com/content/finuxs-kismet-gpsdrive-google-earth-howto-guide)


The next step is to configure kismet.conf file. I have used gedit to work with the kismet.conf file but you can use any text editor you feel happy with. In a terminal put the following command

sudo gedit /etc/kismet/kismet.conf

and locate the part of the file that says

suiduser=your_user_here, and replace it with your username, do not put root in here. Kismet starts with super user privileges then drops back into a normal user privileges. So in my case i changes so it read suiduser=arron.

Then we need to set the capture source, i looked for the line that reads source=none,none,addme. Now the layout of this line is source=interface,capture source, and ignore this bit. So when i edited the file for the interface i put eth1, but this maybe different in your case, it's whatever ifconfig tells you is your wireless device. The source for me was ipw3945, and i left the addme bit. so my line reads like this

source=ipw3945,eth1,eth1

To test that Kismet is working you run by issuing the following command

sudo kismet

---

### Post by atdhe on 2008-04-24
thank u very much///

---

### Post by atdhe on 2008-04-24
can u tell me does it works with rt73 usb drivers.

---

### Post by cactuska on 2009-07-22
Up, because, i would like to know it as well

Regards

---

### Post by brakeangrily on 2009-10-24
I just made the change in kismet.conf and tested the Ralink rt73 driver with the Hawking HWUG1 and all worked fine. 

sudo nano /etc/kismet/kismet.conf

source=rt73,mon1,ralink

#source=[driver],[adapter],[name]

---

