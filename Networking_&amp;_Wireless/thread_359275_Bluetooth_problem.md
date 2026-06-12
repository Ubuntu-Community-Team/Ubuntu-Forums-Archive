---
title: "Bluetooth problem"
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by stinkball on 2007-02-11
I'm trying to setup my Belkin f8t012 bluetooth dongle in ubuntu.  after following the guide [here]("https://help.ubuntu.com/community/BluetoothSetup"), i found out that it isn't supported, but wondered if anyone has it working.  Ubuntu won't even start when i have it plugged in, so when i start up my pc i have to remove it before i can boot.

any suggestions?

---

### Post by dghenke on 2007-06-28
I encountered the same problem with the F8T012, both under the Ubuntu-supplied 2.6.20-16-generic, and with a 2.6.21.5 I built myself. I noticed some kernel message output about the device being claimed by a "Pegasus" driver, which didn't sound right. I blacklisted that (by putting a line with "blacklist pegasus" in my /etc/modprobe.d/blacklist file). That seemed to do the trick; the system will at least boot now. Off to try some actual bluetooth devices...

---

### Post by bennyj on 2007-06-29
> **dghenke said:**
> I encountered the same problem with the F8T012, both under the Ubuntu-supplied 2.6.20-16-generic, and with a 2.6.21.5 I built myself. I noticed some kernel message output about the device being claimed by a "Pegasus" driver, which didn't sound right. I blacklisted that (by putting a line with "blacklist pegasus" in my /etc/modprobe.d/blacklist file). That seemed to do the trick; the system will at least boot now. Off to try some actual bluetooth devices...

This worked for me..I was able to connect after entering the above into the blacklist...thank you!

---

### Post by VON_CAPO on 2007-07-10
> **bennyj said:**
> This worked for me..I was able to connect after entering the above into the blacklist...thank you!
I blacklisted the "pegasus" driver. 

I installed the following packages:
    - bluez-btsco (1:0.50-0ubuntu2)
    - bridge-utils (1.2-1build1)
    - btscanner (2.1-3)
    - dhcp3-server (3.0.4-12ubuntu4)
    - grml-btnet (0.04)
    - grml-shlib (1.02.11ubuntu3)
    - ipcalc (0.41-1)
    - python-bluez (0.9.1-1)
    - python-libbtctl (0.8.2-0ubuntu6)
    - ussp-push (0.9-2)

I restarted X pressing Alt-Ctrl-Backspace

Next, I plugged my Belkin FT8012 dongle, and the "Bluetooth Applet" icon showed up.

I tried to connect using using the function "Find me" of my Motorola Razr V3, but it was a failure. :(

My question is: How did you connect it?

Should I install any additional driver?  :confused:

---

### Post by VON_CAPO on 2007-07-10
**_Update:_**

Installed the following packages:
gnome-phone-manager (0.8-0ubuntu3)
libgnokii3 (0.6.14-3)

Now I have in Applications/Accessories an icon of "Phone Manager"
If this menu does not appears, just open the terminal and type: " sudo gnome-phone-manager ". The menu should show up, also an icon on the system panel too.

Using this Phone Manager I would be able to discover my phone, but I am still without success :(

Additionally, I found a bluetooth tutorial, specific for Ubuntu, but in French :(:(:(
The address is ---> [http://doc.ubuntu-fr.org/materiel/bluetooth](http://doc.ubuntu-fr.org/materiel/bluetooth)

---

### Post by Nanoboy on 2007-07-10
Just installed gnome-phone-manager now (installed absolutely everything else previously), and still won't work.  My built-in bluetooth card is detected, but can never found any device from scanning, or being found by my phone.   :(  I'm using a Dell Inspiron laptop, so the card would be one of those Dell ones.

---

### Post by Lgndryhr on 2007-07-13
i did some of the things listed here as well as what i found [here](http://www.linuxquestions.org/questions/showthread.php?t=185978). I got as far as them paring the first time on my samsung a727 then my cell said it couldn't find the processes or something. Now my cell can't connect. They see each other but just wont connect now. Any ideas?

EDIT: Upon running Bluetooth File Sharing 0.8.0 my cell connected and says browsing files... and my dongle is blinking which means it is talking/sending info to the cell.
It conintued to blink and my cell continued to say the same thing for 10 mins but nothing happened so I stopped it,

EDIT: Upon reading [here](http://ubuntuforums.org/showthread.php?t=75978) I was able to get it to connect to my computer and pair but my cell is trying to send files and it just sits there and says browsing files while my computer awaits a transfer.

---

