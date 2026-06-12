---
title: "connecting to HP printer on wireless network"
date: 2020-12-07
forum: Networking &amp; Wireless
---

### Post by dshock on 2020-12-07
I have a hp officejet 8610 multifunction printer that will not print from ubuntu 20.04 on my wireless network.. Ubuntu shows the job going to the printer and  when the job is done but the printer does not print. The printer shows it is connected to the wireless network, but does not print the file.Is there a way to connect the printer to the computer via usb and keep the computer on the wireless network? Thank you for your  help.

---

### Post by morrownr on 2020-12-08
I have an 8600. Recommend the following to get started:

Install the hplip-gui to help troubleshoot:

```
$ sudo apt install hplip-gui
```

Run the gui once installed and let's see what it says.

Also, I set the printer on a fixed ip address: 192.168.1.86

---

### Post by Autodave on 2020-12-08
Yes, you can have both wireless and wired at the same time.

You do need to go into the panel on the printer and set that up for wireless use.  Check your manual for how to navigate to that.

---

### Post by dshock on 2020-12-09
I have the latest version of hplip installed (3.20.3). How do I start it to troubleshoot?  I have 2 computers using the one printer. Can the printer receive wirelessly fron one computer and by usb from the other? Would OI need a hub or router for the usb?

---

