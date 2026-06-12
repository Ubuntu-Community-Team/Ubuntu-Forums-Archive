---
title: "install Canon MX870 wireless printer"
date: 2018-02-10
forum: Networking &amp; Wireless
---

### Post by s9032g@comcast.net on 2018-02-10
Using Ubuntu 17.10 64 bit on Dell E7240.

 Canon says it has no driver for this. Is there any way to set up to use the printer as wireless (wired works fine).

Thanks

---

### Post by chili555 on 2018-02-10
If it works perfectly wired; that is, by USB I assume, it stands to reason that there is a functioning Linux driver for the printer on your system. It is certainly available and selectable on my 17.10 system.

How are you wanting to use it wirelessly? Connected by USB to your router? Connected by ethernet to your router? Connected by USB to some other computer in your network? If another computer, is it Ubuntu or Windows or MacOS or ... ?

---

### Post by s9032g@comcast.net on 2018-02-11
Yes there is a functioning Linux driver; however it does not work for wireless.
 I want to connect via wifi directly to my printer, no usb, no lan. Also the printer is not connected to the modem/router. There is a windows 10 laptop in the same room that has no problem connecting with the printer this way.

---

### Post by chili555 on 2018-02-11
No LAN? Doesn't the printer get its IP address from your wireless router? What is it? Can you get some details from the Windows machine?> Yes there is a functioning Linux driver; however *it does not work for wireless*.I shall be very surprised if this is the case.

---

### Post by s9032g@comcast.net on 2018-02-11
I agree that there is probably a solution; however I note that others have the same problem.

I have three laptops in the same room. One is connected to the printer by usb, another is connected wirelessly, the third is the Linux unit which, as of now, will only work via usb. The printer itself is connected wireless (no cable) to the modem/router. The laptop that connects to the printer with usb is connected by lan to the modem/router. The other two laptops are strictly wireless.

I looked at the windows 10 laptop that works fine via wireless with the printer. I see a DESKTOP code, an ip address, a mac address, and a serial number. I tried putting the ip address into the setup on the Ubuntu laptop. It just says it is waiting for "available" and nothing ever happens. The laptop is only a few feet from the printer.

No doubt I am missing something here. That's why I am seeking help.

Thanks

---

### Post by chili555 on 2018-02-11
> I have three laptops in the same room. One is connected to the printer by usb, another is connected wirelessly, the third is the Linux unit which, as of now, will only work via usb. The printer itself is connected wireless (no cable) to the modem/router. The laptop that connects to the printer with usb is connected by lan to the modem/router. The other two laptops are strictly wireless.The implication here is that the printer is connected *both* by USB to one of the computers and wirelessly to the modem/router. I think this is unlikely.

What I think is more likely is that the computer that is connected to the printer by USB is set to share the printer so that it is operating as a simple print server. Thereby, any computer on the same network can see it and print to it. Here is how you can test. At some convenient time, late at night perhaps, shut down completely, not suspend, the computer to which the printer is attached by USB. Now can the other computers print to it?

To be accessible to all the computers on the network, including Ubuntu, the printer needs an IP address which it gets from the modem/router. Can you log on to the administration pages of the modem/router and see the DHCP client list and see the printer as an attached device? Or only the three computers? If you do see the printer, what is its IP address? [https://i.stack.imgur.com/1YMVC.png](https://i.stack.imgur.com/1YMVC.png)

Again, what is the operating system of the computer that is connected to the printer by USB?> I tried putting the ip address into the setup on the Ubuntu laptop. It just says it is waiting for "available" and nothing ever happens. The laptop is only a few feet from the printer.
How and where? Here? [https://i.stack.imgur.com/VDu6u.png](https://i.stack.imgur.com/VDu6u.png) In your case, I suspect the URI would be more like ipp://<some_IP_address>:631/lpr or similar.

---

### Post by s9032g@comcast.net on 2018-02-12
Again, what is the operating system of the computer that is connected to the printer by USB?

Windows 7

---

### Post by s9032g@comcast.net on 2018-02-12
chili555,

Apparently I am not a very good student despite using Ubuntu since 8.04. I am used to Ubuntu "just working".

Things are now worse. I can't even print via usb. Print settings are:
Description: Generic CUPS-BRF Printer
Location: Office
Device URI: cups-brf:/
Make&Model: Canon mx870 series -CUPS + GUTENPRINT
State: Idle

Everything is plugged in and I did some restarts.

---

### Post by s9032g@comcast.net on 2018-02-12
Forget it. Too much trouble. Ok again with usb,

---

