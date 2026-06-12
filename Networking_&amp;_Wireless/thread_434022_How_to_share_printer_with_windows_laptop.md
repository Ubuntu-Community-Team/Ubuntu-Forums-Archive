---
title: "How to share printer with windows laptop?"
date: 2007-05-05
forum: Networking &amp; Wireless
---

### Post by danny71 on 2007-05-05
Hello

My printer is connected to the desktop computer working with Ubuntu.

I want to share the printer with the laptop.

How can I do it?

---

### Post by Floppyjoe on 2007-05-05
On the machine that you want to print with that is not directly connected to the printer add a network printer with the address:
```
http://PrinterHostipGoesHere:631/printers/PrinterNameGoesHere
```

---

### Post by dbott67 on 2007-05-05
Here's a step-by-step of what Floppyjoe suggests:

[http://ubuntuforums.org/showthread.php?p=2413840#post2413840](http://ubuntuforums.org/showthread.php?p=2413840#post2413840)

-Dave

---

### Post by danny71 on 2007-05-05
Thank you very much for your quick reply, but still my laptop doesn't detect the printer.

1. What is the printer's name?

2. The system has detected the printer as local printer. Is it OK?

---

### Post by dbott67 on 2007-05-05
[B][U]This is what I did to get it working:

[/U][/B][COLOR=Red][I]Obviously, you'll need to modify the printer settings & IP addresses to suit your situation.  My Ubuntu computer is 192.168.1.106; replace it with whatever yours is.

[/I][COLOR=Black]_**On your Ubuntu Computer**_[/COLOR][/COLOR] 

1. Click **SYSTEM > ADMINISTRATION > PRINTING** and add the printer using the "New Printer" wizard [COLOR=Blue]*(if your locally-attached printer is already working in Ubuntu, then skip this step)*[/COLOR].
2. Next, under **Printers > Global Settings** select '**Detect LAN Printers**'
3. Dapper Instructions: Edit **/etc/cups/cups.d/ports.conf file** (Edgy/Feisty edit the **/etc/cups/cupsd.conf** file instead):
```
dbott@thedrake:~$ sudo nano /etc/cups/cups.d/ports.conf
Listen localhost:631
Listen /var/run/cups/cups.sock
[COLOR=Red]**Listen 192.168.1.106  ***[COLOR=Blue]<-- my Ubuntu IP address[/COLOR]*[/COLOR]

```4. Restart the CUPS daemon:
```
sudo /etc/init.d/cupsys restart
```_**From Windows XP:**_

5. On **Windows XP computer**,  browse to [http://192.168.1.106:631/printers/](http://192.168.1.106:631/printers/) (see screenshot below).  [COLOR=Red]Make note of the printer name.[/COLOR]
6. In the Windows 'Add Printer Wizard' I used the following URL:
```
http://192.168.1.106:631/printers/PhotoSmart-P1315
```For the record, here are my specs:

1. Router: D-Link DI-614+
2. Desktop PC: **Ubuntu **6.06 LTS, Wired Connection, IP: **192.168.1.106**
3. Laptop: **XP Pro**, Wireless, IP:**192.168.1.105**
4. Printer: HP PhotoSmart 1315 (Parallel) connected via HP JetDirect. JetDirect connected via ethernet cable 192.168.1.10 port 9100.

Here's the HOWTO I followed:
[https://help.ubuntu.com/community/NetworkPrintingWithUbuntu](https://help.ubuntu.com/community/NetworkPrintingWithUbuntu)

---

### Post by danny71 on 2007-05-05
I cannot print even from the desktop computer after installation of the printer as network printer. It works only as local printer

---

### Post by Floppyjoe on 2007-05-05
> **danny71 said:**
> I cannot print even from the desktop computer after installation of the printer as network printer. It works only as local printer

The desktop printer is a local printer.
The laptop printer should be network.

---

### Post by dbott67 on 2007-05-05
> **danny71 said:**
> I cannot print even from the desktop computer after installation of the printer as network printer. It works only as local printer

Please re-read my post from above (#5) and follow the steps very carefully.

If you still have troubles, post the following info:
```
dbott@feisty:~$ **ifconfig -a**
eth0      Link encap:Ethernet  HWaddr 00:50:BA:C0:A7:55  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:baff:fec0:a755/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1367781 errors:0 dropped:0 overruns:0 frame:0
          TX packets:950416 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1131487074 (1.0 GiB)  TX bytes:127920935 (121.9 MiB)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:528119 errors:0 dropped:0 overruns:0 frame:0
          TX packets:528119 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:86962914 (82.9 MiB)  TX bytes:86962914 (82.9 MiB)

``````
dbott@feisty:~$** sudo cat /etc/cups/printers.conf **
# Printer configuration file for CUPS v1.2.8
# Written by cupsd on 2007-05-05 16:42
<Printer PhotoSmart-P1315>
Info 
Location 
DeviceURI socket://192.168.1.110:9100
State Idle
StateTime 1178397734
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>

```-Dave

---

### Post by danny71 on 2007-05-06
I did all the above, but still the laptop doesn't recognize the printer.

Also, I've installed Samba, so the laptop can recognize the desktop computer on the network.

Maybe the IP adress is wrong? how can I know what is the right IP?

---

### Post by dbott67 on 2007-05-06
Post the output of the above 2 commands from your Ubuntu computer:
```
ifconfig -a
``````
sudo cat /etc/cups/printers.conf
```And the following from your XP computer:
```
ipconfig /all
```Copy the information from a terminal and paste it here.

---

### Post by l1oyd on 2007-05-10
hi

Having some trouble and still very new with the whole Linux thing...

I have followed the instructions but am not able to get my XP machine to see the printer, is there anything I could be missing.

Cheers

---

### Post by Slave5Tom on 2007-05-21
I'm not sure if this thread is still active.  I am also having trouble printing from a wireless notebook running Windows-XP to my Ubuntu-Feisty desktop.  I can see the printer in the notebook computer by browsing to [http://192.168.0.101:631/printers/Photosmart_C3100](http://192.168.0.101:631/printers/Photosmart_C3100) (address of the ubuntu machine) and I can print a test page from here, however the XP notebook hangs when I use the wizard to install the printer as a network printer.  I noticed a different line in my printer.conf file in the DeviceURI:

# Printer configuration file for CUPS v1.2.8
# Written by cupsd on 2007-05-14 18:15
<DefaultPrinter Photosmart_C3100>
Info Photosmart C3180 all-in-one
Location Jacob's room
[COLOR="Red"]DeviceURI hp:/usb/Photosmart_C3100_series?serial=CN6AOC213Y04KV[/COLOR]
State Idle
StateTime 1175601015
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>
keith@keith-desktop:~$

I also looked on the MS website and they said to install the printer as a local printer but this did not work either.  see [http://www.microsoft.com/windowsxp/using/setup/expert/russel_october22.mspx](http://www.microsoft.com/windowsxp/using/setup/expert/russel_october22.mspx)
Any ideas?

---

