---
title: "[SOLVED] Bluesoleil bluetooth adapter doesnt work on feisty"
date: 2007-09-09
forum: Networking &amp; Wireless
---

### Post by manoj_nair on 2007-09-09
**This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/ubuntu/+question/12670/](https://answers.launchpad.net/ubuntu/+question/12670/) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hello everyone,
I have been using ubuntu for quite some time now on my laptop without any problems. One of the things i like about it is the large pool of devices it supports.

Recently, I bought a bluetooth adapter which works in windows using a software called "BlueSoleil".

However, i was unable to get it working on my laptop. I believe i have all the required packages.  I have followed the instructions here with no success > [https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

Has someone with the same adapter got it working? Is there anything  that i can do? Any help is appreciated.

lsusb gives me the foll. output:
manoj@ubuntu:~$ lsusb
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 1131:1001 Integrated System Solution Corp. KY-BT100 Bluetooth Adapter
Bus 001 Device 001: ID 0000:0000

However, hcitool returns empty:
manoj@ubuntu:~$ hcitool dev
Devices:

manoj@ubuntu:~$ hcitool scan
Device is not available: No such device

i have also tried updating ubuntu using the update manager, but the problem persists.
 Thanks for reading :)

---

### Post by err_ok on 2007-09-10
I have a similar problem with that adapter, however when scanning i can find devices. When i try and send something to the PC however it the Connection is refused/fails.

Have you got it working yet ?

---

### Post by manoj_nair on 2007-09-13
Thanks to er_ok, i am able to get my bluetooth working to some extent. Here's what i did.

First i removed all bluetooth related libraries and packages. I switched off multiverse, universe and all other third party sources from synaptics settings > repositories menu. 

Then i installed the following packages:
bluetooth
bluez-gnome
bluez-pin
bluez-utils

Later i enabled universe and installed obexpushd, obex ftp, and gnome-bluetooth.
I am now able to send files from my laptop to my cell phone from withing nautiluis. What i do is, rightclick the file to be sent and open with > other app > custom command > gnome-obex-send. (i installed nautilus-sendto package and now i can directly send files by right clicking the file and selecting sendto option)

However, i am unable to pair the cell with my cell, because, i am not prompted for the pin on my laptop when pairing. I will try pairing from my laptop instead later in the evening.

---

### Post by manoj_nair on 2007-09-13
My bluetooth is working perfectly now. All i had to do was restart. After restart, i got a bluetooth icon in my panel. Rightclicking this icon gives me options that i can set for my adapter. 

Now i can also pair my cell phones with the computer. I initiate the pairing from my cellphone, where i enter a pin, and the bluetooth icon in my laptop prompts me for the pin. 

However if i want to send files from my cell to my computer, i need to have "bluetooth file sharing" applet running. This can be done from > main menu > accessories > bluetooth file sharing.

So now i am able to send as well as receive files from my computer as well as the cell phone. :)

---

### Post by err_ok on 2007-09-13
Sorted. Good good.

I suppose we should get this adapter added to the compatible adapters then. Glad you got it working.

---

### Post by manoj_nair on 2007-09-13
I have even got multisync+evolution working with my cell phone(Ericsson W550i). It syncs everything(contacts, tasks, calendar, events) perfectly!

---

### Post by manoj_nair on 2007-09-14
Guys, i did a small write up on my blog describing the whole procedure. I hope it is helpfull to someone. The entry can be found here > 
[http://nairmanoj.com/2007/09/14/bluesoleil-with-ubuntu/](http://nairmanoj.com/2007/09/14/bluesoleil-with-ubuntu/) (URL updated...)

Let me know if i missed out on something. :)

P.S: Will also try to do a write up on using multisync using the bluesoleil bluetooth adaptor.

---

### Post by Diabolis on 2007-10-13
If I'm done using the bluetooth adapter should I just unplug it or is there a correct way to do it? I think that if I just unplug it abruptly, after a while it will stop working just like usb flash drives.

---

### Post by manoj_nair on 2008-02-18
> **Diabolis said:**
> If I'm done using the bluetooth adapter should I just unplug it or is there a correct way to do it? I think that if I just unplug it abruptly, after a while it will stop working just like usb flash drives. I dont think it will affect the device if you pull it out, because unlike usb drives, they do not store any data on themselves...

---

### Post by Diabolis on 2008-02-19
As far as I know every usb device establishes communication with the pc. The usb and the pc keeps sending info to each other so they'll be ready whenever you need them. Even if a device doesn't store information, it will have to communicate with the pc.

---

