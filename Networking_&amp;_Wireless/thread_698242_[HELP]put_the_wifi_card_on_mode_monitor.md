---
title: "[HELP]put the wifi card on mode monitor"
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by arnoldo on 2008-02-16
I have got an acer 5100 but i don't try to understand witch kind of wireless card i have got.
So i don't be able to put my card on mode monitor.
In the shell of ubuntu i know that i write the command:

"sudo iwconfig wlan0 mode monitor"

but the shell write this error:

Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.

I have configured the driver card by ndiswrapper and the wireless works corretly.

But i need to put the card on mode monitor.I want use the kismet program.

[COLOR="Red"]The guide says it:[/COLOR]

STEP 1:open shell
STEP 2:sudo apt-get install kismet
STEP 3:After write this: .sudo gedit /etc/kismet/kismet.conf
STEP 4:Now modify the file:

    source=type,interface,name[,channel]

in:

    ipw3945,eth0,Wireless Card

STEP 5:To switch on the "server kismet" write:

    sudo iwconfig eth0 mode monitor

STEP 6:To start kismet write

    sudo kismet


Thanks every all for the help!!!:confused::confused::confused::confused:

---

### Post by arnoldo on 2008-02-16
up

---

### Post by arnoldo on 2008-02-18
up

---

