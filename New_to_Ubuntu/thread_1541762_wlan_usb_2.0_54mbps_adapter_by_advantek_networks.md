---
title: "wlan usb 2.0 54mbps adapter by advantek networks"
date: 2010-07-29
forum: New to Ubuntu
---

### Post by The Real Pelana on 2010-07-29
Hello everyone!

Im back. After successfully installed my 10.4 netbook distro (still having some trouble with skype, cant use the mic) Im ready to give it the shot in the oldie desktop at my office.

I did already have my usb pendrive with Ubuntu Desktop distro, however I couldnt connect to the wireless modem at the office. I have this wlan usb 2.0 54mbps adapter by advantek networks and I would appreciate any help from you guys.

Thank you again and believe me when I say that Im really happy with Ubuntu :-)

---

### Post by The Real Pelana on 2010-07-30
> **The Real Pelana said:**
> Hello everyone!

Im back. After successfully installed my 10.4 netbook distro (still having some trouble with skype, cant use the mic) Im ready to give it the shot in the oldie desktop at my office.

I did already have my usb pendrive with Ubuntu Desktop distro, however I couldnt connect to the wireless modem at the office. I have this wlan usb 2.0 54mbps adapter by advantek networks and I would appreciate any help from you guys.

Thank you again and believe me when I say that Im really happy with Ubuntu :-)




heeeEEEeeelp!!! please...

---

### Post by soldier1st on 2010-08-03
is the office set up to allow remote connections?also what os is the office running?

---

### Post by The Real Pelana on 2010-08-03
Actually we dont have a LAN here. The desktop an lap computers are connected independently to the IPs modem.

This wlan usb works fine with xp and whenever i run Ubuntu from the pendrive it doesnt recognizes my wlan adapter...

---

### Post by gordintoronto on 2010-08-03
At this web pages:
[http://advanteknetworks.com/products/wireless/awnusb54s.html](http://advanteknetworks.com/products/wireless/awnusb54s.html) 
there is a link called "driver linux." That's probably a good starting point.

By the way, that wireless adapter only supports WEP encryption, which takes a few minutes to break...

---

### Post by The Real Pelana on 2010-08-03
> **gordintoronto said:**
> At this web pages:
[http://advanteknetworks.com/products/wireless/awnusb54s.html](http://advanteknetworks.com/products/wireless/awnusb54s.html) 
there is a link called "driver linux." That's probably a good starting point.

By the way, that wireless adapter only supports WEP encryption, which takes a few minutes to break...




Aight, im on it...

---

### Post by The Real Pelana on 2010-08-04
Let's see. Today I've already tried to import the drivers that actually works fine on xp. However and after locating them in the system32\drivers\sis163u.sys the Network Manager says that it doesn't have the same .PPTP extension.

I have a .ZIP file with the drivers I did download from the manufacturer's website, however, as soon as I extract the files I have no idea which folder I have to add'em.

Any new hint please?

Thanx a lot.

---

### Post by Peter09 on 2010-08-04
Hi,
after an install it is really good practice to get an internet connection and do an update so that it  can download the updated drivers etc. Often the system will work after that.

  can you post the output of

```
ifconfig
```and
```
lshw -C network
```and also check ins System->applications->hardware

and see if there is a driver waiting to be enabled.

---

### Post by Peter09 on 2010-08-04
Also

```
lsusb
```

Do all with your usb network adapter plugged in.

---

### Post by mojo risin on 2010-08-04
hm I also had this problem that my usb stick did not work, but when I extracted the dirver from my usb key(i did it via windows and put it onto my portable harddrive to get it over to my ubuntu laptop) and created an inf file and loaded this into the front end ndiswrapper, and i restarted the laptop and it worked :).

---

### Post by Peter09 on 2010-08-04
Many of these sticks are re-badged from standard hardware - this one could be using the ralink hardware - but really need confirmation of that from the output of the commands. There again it may need a windows driver as you say. Its difficult to tell until we get the information.

---

### Post by The Real Pelana on 2010-08-05
**ifconfig**
orthoimplants@orthoimplants-desktop:~$ ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:19:db:76:fd:64  
          Direc. inet:192.168.1.74  Difus.:192.168.1.255  Másc:255.255.255.0
          Dirección inet6: fe80::219:dbff:fe76:fd64/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1500  Métrica:1
          Paquetes RX:134708 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:70885 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:198599457 (198.5 MB)  TX bytes:5191120 (5.1 MB)
          Interrupción:23 Dirección base: 0x8000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:12 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:12 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:720 (720.0 B)  TX bytes:720 (720.0 B)

orthoimplants@orthoimplants-desktop:~$ 

**lshw -c network**
orthoimplants@orthoimplants-desktop:~$ lshw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: VT6102 [Rhine-II]
       vendor: VIA Technologies, Inc.
       physical id: 12
       bus info: pci@0000:00:12.0
       logical name: eth0
       version: 78
       serial: 00:19:db:76:fd:64
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 ip=192.168.1.74 latency=64 maxlatency=8 mingnt=3 multicast=yes
       resources: irq:23 ioport:cc00(size=256) memory:fdffe000-fdffe0ff
orthoimplants@orthoimplants-desktop:~$ 

**lsusb**
orthoimplants@orthoimplants-desktop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0457:0163 Silicon Integrated Systems Corp. 802.11 Wireless LAN Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by The Real Pelana on 2010-08-05
And connected with ethernet wire and upgrading drivers as the system prompted me...

---

### Post by Peter09 on 2010-08-05
if you still have no connection the the following is a quote from a thread that made it work. You need to get sis163.inf from the manufacturers site.

> 
     Code:
     cd ~/
ndiswrapper -i sis163u.inf 
   If no error where shown run:

     Code:
     depmod -a 
   Again If no error where shown (load ndiswrapper as a module):

     Code:
     modprobe ndiswrapper 
  Them check if the driver is being used by device. Plug in the device and run:

     Code:
     ndiswrapper -l 
  The result should be:

     Quote:
                                                 sis163u : driver installed
        device (0457:0163) present                                 




note that ndiswrapper is in the repositories

---

### Post by The Real Pelana on 2010-08-05
I did install the ndiswrapper and got the sis163u.inf file however  ndiswrapper says that it is already installed. I got some drivers for  linux but have no idea how to install them. Theyre compressed in zip  files and after following the directions on the readme file included I  realized that I cannot copy and paste in the etc\wap_supplicant  folder... got stuck again :-(

---

### Post by Peter09 on 2010-08-05
did you do the other commands in the sequence?

---

### Post by The Real Pelana on 2010-08-06
I actually did run the commands as I was told...

---

### Post by Peter09 on 2010-08-06
What is the output of 
```

ndiswrapper -l
```

---

### Post by The Real Pelana on 2010-08-06
> **Peter09 said:**
> What is the output of 
```

ndiswrapper -l
```


ndiswrapper -l
sis163u not a valid driver!

and by the way Pete, i do appreciate your time for guiding me through this darkness :-)

---

### Post by Peter09 on 2010-08-06
Can you start from the top with this command ```
ndiswrapper -i sis163u.inf
```  and look for any error messages, post them here (with the command you used).

---

### Post by The Real Pelana on 2010-08-06
that is:

ndiswrapper -i sis163u.inf
driver sis163u.inf is already installed

---

### Post by Peter09 on 2010-08-06
OK so lets start again
do
```
ndiswrapper -e sis163u.inf
``` 
which should remove the driver, then go back and start the process again. If you have any error message on a command stop and post the output here. I know this may be tedious but the process should work. The chances are that early on in your attempts to get things working you did something that is stopping things working. We need to reset and try again.

---

