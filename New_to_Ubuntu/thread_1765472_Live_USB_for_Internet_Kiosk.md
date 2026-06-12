---
title: "Live USB for Internet Kiosk"
date: 2011-05-23
forum: New to Ubuntu
---

### Post by Marthinusjvv on 2011-05-23
Good day to all! 

I need to create a Live USB for a Internet Kiosk Terminal. The machine will thus run its OS from the RAM once it its been booted from the USB. This is easy to accomplish, but there are a few customization issues with which i have been struggling. 

First - Once the user has logged on to the system (there can only be one account) firefox should automatically run. 

Second - The user may not have access to ANY files or filesystems or applications apart from firefox. There is an additional USB port available for the user if he chooses to download to his own USB. 

Third - The user must not be able to boot from his own USB. In other words only the USB with my OS should be available to boot from. 

Fourth - The OS needs a specific Wi-fi driver for a USB dongle(Wi fi adaptor) to enable wireless access tothe internet. 


Any and all help will be deeply appreciated. 

THX

---

### Post by grahammechanical on 2011-05-23
I am not qualified to answer all your questions but I suggest that you test everything out before you let clients loose on your machines. I expect you already intend to do this. 

So, for number 1. Try putting Firefox as a Startup Application. On Ubuntu 11.04 this is in System Settings>Startup Applications.

Number 2. Make the Live USB a very minimal installation. When the install is finished remove all unnecessary programs. If the programs are not there they cannot be used. Also try using the Users and Groups utility to restrict what programs are available to these users. You do not want them running the Software Centre and adding other programs. Severely limit what this type of user can do. Also consider if you need a specialist Internet Kiosk program. Check out Lock Down Editor in the Ubuntu Software Centre. It might be useful.

Number 3. Deny the user access to the base unit. Provide access to the USB ports by USB extension cables (if such things exist). If users cannot switch the machine off and on then they cannot boot their own USB OS.

Number 4. I suggest that if you follow the standard procedures for setting up wireless on a USB stick installation. You need a USB stick for each machine. If the machines have different wireless adapters then you will need to make sure that each USB stick is only used on the machine that it is set up for.

Regards.

P.S. another thought has occured to me. If the motherboard has internal USB connectors that are not connected to a USB port, then it is possible to use a cable to connect the USB stick to one of these connectors and fix the USB stick inside the machine so that it cannot be removed and the machine rebooted from another USB stick. It might be worth a try.

---

### Post by psrdotcom on 2011-09-15
I am trying to have a similar kind of theme .. 

I have found this thread .. see this also 

[*http://ubuntuforums.org/showthread.php?t=1765472&highlight=firefox+kiosk*]("http://ubuntuforums.org/showthread.php?t=1765472&highlight=firefox+kiosk")

---

### Post by haqking on 2011-09-15
Kiosking

[http://www.instructables.com/id/Sett...Web-Appliance/]("http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/")

[http://www.ianatkinson.net/computing/operakiosk.htm](http://www.ianatkinson.net/computing/operakiosk.htm)

[http://ubuntuforums.org/showthread.php?t=338980](http://ubuntuforums.org/showthread.php?t=338980)


Flash Drive Linux

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
[http://www.pendrivelinux.com/put-ubu...using-windows/]("http://www.pendrivelinux.com/put-ubuntu-10-04-on-flash-drive-using-windows/")

Adapt the first to suit the install on the latter ;-)

---

### Post by psrdotcom on 2011-09-16
Thanks for sharing the links.

I will try and if I am facing any issues, then I will post in this thread.

---

### Post by zkissane on 2011-09-16
> **grahammechanical said:**
> 
P.S. another thought has occured to me. If the motherboard has internal USB connectors that are not connected to a USB port, then it is possible to use a cable to connect the USB stick to one of these connectors and fix the USB stick inside the machine so that it cannot be removed and the machine rebooted from another USB stick. It might be worth a try.

Depending on how you solve the keyboard/mouse/wireless/boot stick problem, putting epoxy in the excess USB ports works surprisingly well.

---

