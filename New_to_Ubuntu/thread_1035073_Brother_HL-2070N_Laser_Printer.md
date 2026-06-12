---
title: "Brother HL-2070N Laser Printer"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by DforVendetta on 2009-01-09
I'm using a usb HL2070N Brother laser printer. A Google search seems to identify the printer as easy to install and set up but I am having difficulty. Synaptic says CUPS is installed but I am not sure if I have it running correctly. I searched synaptic and installed just about everything related to my printer but I am still unable to find it in printer list.

d@dan-desktop:~$ lsusb
Bus 003 Device 002: ID 04f9:0029 Brother Industries, Ltd Printer
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 005: ID 413c:3012 Dell Computer Corp. 
Bus 002 Device 004: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by RobsterUK on 2009-01-09
It looks like your system knows the printer exists at least, did anything happen when you connected the printer to your USB port?

Have you tried adding it via System > Administration > Printing ?

---

### Post by avtolle on 2009-01-09
Asking perhaps the obvious question, which likely you did, but did you select "New printer" after selecting "Printing" under System-->Administration to add the printer?

---

### Post by DforVendetta on 2009-01-09
"It looks like your system knows the printer exists at least, did anything happen when you connected the printer to your USB port?"

Nothing happened when I connected the printer and turned it on.

"Have you tried adding it via System > Administration > Printing ?"

I tried adding it. There is nothing in the listbox and "Refresh" yields nothing.

"New" is grayed out and if I choose "Connect" from the dropdown field I get a dialog box that I don't really understand.

"Asking perhaps the obvious question, which likely you did, but did you select "New printer" after selecting "Printing" under System-->Administration to add the printer?"

Don't over-estimate me, I'm new :). I tried doing what you said but the "New" icon is grayed out.

---

### Post by hyper_ch on 2009-01-09
[http://solutions.brother.com/linux/en_us/download_prn.html#HL-2070N](http://solutions.brother.com/linux/en_us/download_prn.html#HL-2070N)

---

### Post by DforVendetta on 2009-01-09
> **hyper_ch said:**
> [http://solutions.brother.com/linux/en_us/download_prn.html#HL-2070N](http://solutions.brother.com/linux/en_us/download_prn.html#HL-2070N)

I installed the drivers using their instructions and still no luck

---

### Post by hyper_ch on 2009-01-09
lpr and cupsdriver?

---

### Post by DforVendetta on 2009-01-09
I still cannot add the printer under admin > Printing but I went to print this webpage in Opera browser and my printer is listed now, but I still cannot print the page

---

### Post by DforVendetta on 2009-01-09
> **hyper_ch said:**
> lpr and cupsdriver?

Yes. I installed both drivers, however I do see an unusual usb device connected now:

d@dan-desktop:~$ lsusb
Bus 008 Device 002: ID 045e:0710 Microsoft Corp. 
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04f9:0029 Brother Industries, Ltd Printer
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 005: ID 413c:3012 Dell Computer Corp. 
Bus 002 Device 004: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Wonder what "Microsoft Corp." is?

*update*

Nevermind, I had plugged in my Zune for charging. Duh

---

### Post by hyper_ch on 2009-01-09
and yuo did follow the install instructions that were provided just beneath the downloadable .deb files?

---

### Post by DforVendetta on 2009-01-09
> **hyper_ch said:**
> and yuo did follow the install instructions that were provided just beneath the downloadable .deb files?

Yes, I followed the instructions exactly. I had to use the terminal anyways because I'm 64 bit. Is there any way I can tell if cups is running?

---

### Post by wykedengel on 2009-01-09
stupid question, but are you using the printer on a windows network?

---

### Post by hyper_ch on 2009-01-09
post the output of:

```

sudo apt-get install ia32-libs

```
```

sudo dpkg -l | grep Brother

```
```

cat /etc/printcap

```

run
```

sudo aa-complain cupsd
sudo mkdir /usr/share/cups/model

```
before the lpr driver installation

Check if the printer is there:  [http://localhost:631/printers](http://localhost:631/printers)
Or add it then.

---

### Post by DforVendetta on 2009-01-09
> **wykedengel said:**
> stupid question, but are you using the printer on a windows network?

I'm not sure what you mean. I do not have a home network set up yet, I am rather new to Linux and taking things one step at a time. Just for shits and giggles I botted to my Windows and it set up the printer upon boot with no problems. I have firestarter running, are there are ports which should be open?

---

### Post by hyper_ch on 2009-01-09
why do you run firestarter?

---

### Post by DforVendetta on 2009-01-09
d@dan-desktop:~$ sudo apt-get install ia32-libs
[sudo] password for d: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
ia32-libs set to manually installed.
The following packages were automatically installed and are no longer required:
  libqca2 libgeoip1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

d@dan-desktop:~$ sudo dpkg -l | grep Brother
ii  brhl2070nlpr                              2.0.1-1                                 Brother HL-2070N LPR driver
ii  cupswrapperhl2070n                        2.0.1-2                                 Brother HL2070N CUPS wrapper driver

d@dan-desktop:~$ cat /etc/printcap
HL2070N:\
        :mx=0:\
        :sd=/var/spool/lpd/HL2070N:\
        :sh:\
        :lp=/dev/usb/lp0:\
        :if=/usr/local/Brother/lpd/filterHL2070N:

2



When I try to connect to "http://localhost:631/printers" via web browser I get the common "Cannot connect to remote server"

---

### Post by DforVendetta on 2009-01-09
> **hyper_ch said:**
> why do you run firestarter?

I run it because I use p2p often.

---

