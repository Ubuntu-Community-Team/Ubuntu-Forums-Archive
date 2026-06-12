---
title: "Help please, no internet at all (wifi + ethernet)"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by dummiebeginner on 2009-04-25
Hi,

I recently installed Jaunty and my ethernet connection (sis191) worked well but my classic-pain-in-the-*** atheros wifi card ar5007eg didn't.

So I tried -once more- to try to make the wifi connection work. I had tried lots of times before with Hardy and Intrepid driving me crazy. As usual I followed some instructions given by someone somewhere in the different Ubuntu forums in different languages.

Well, not only it didn't work but now my ethernet connection is also dead and I am writing this from Windows.

Can somebody help me please? I die if I have to reinstall after hundreds of hours of working in configuring my Ubuntu.

Thanks in advance

PS: By the way. Another problem I have is that I have installed some programs via .deb file and now I can't uninstall them. They are installed, I can even run them, but they don't show up in Synaptic or install/uninstall. They are popular programs like Frostwire or Rainlendar (which works awful in Linux). Thanks again.

---

### Post by Peter09 on 2009-04-25
Can you post the output of the terminal commands

```
ifconfig
```

```
lshw -C network
```

Note that if you have no internet connection you can push the output to a file by using the command like this

```
ifconfig > 'a file name'
```

this directs the out put to a file rather than the screen.(no quotes)

---

### Post by johnjb on 2009-04-25
Hi
I am assuming you upgraded to Jaunty not a fresh install if so go to System, Administration, Hardware Driver's and reactivate your WiFi your drivers will be there without having to download them.Worked on both my machines.
As for your other little problem I don't know enough to help you hope this helps you a little

johnjb

---

### Post by dummiebeginner on 2009-04-25
Thanks a lot for you help.

Back in Ubuntu the wire connection works for unknown reasons. I had restarted twice and didn't work.

It is a fresh install, I was using Mandriva before because it is the only one that recognizes my wifi and graphic card out of the box. But I was tired of so many bugs and problems and wanted to try Ubuntu once again.

This is the "tutorial" I followed before the crash: [http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-get-atheros-ar5007eg-or-ar242x-wireless-cards-may-be-other-models-working-in-ubuntu-810-intrepid-ibex.html)

And this is the answer to what you ask me to do. Sorry in advance if I do annoying mistakes:

yo@portatil:~$ ifconfig
eth0      Link encap:Ethernet  direcciónHW 00:1e:33:04:98:4b  
          inet dirección:192.168.0.193  Difusión:192.168.0.255  Máscara:255.255.255.0
          dirección inet6: fe80::21e:33ff:fe04:984b/64 Alcance:Vínculo
          ARRIBA DIFUSIÓN CORRIENDO MULTICAST  MTU:1500  Métrica:1
          RX packets:1318 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1366 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:1000 
          RX bytes:1429488 (1.4 MB)  TX bytes:236283 (236.2 KB)
          Interrupción:19 Dirección base: 0xdead 

lo        Link encap:Bucle local  
          inet dirección:127.0.0.1  Máscara:255.0.0.0
          dirección inet6: ::1/128 Alcance:Anfitrión
          ARRIBA LOOPBACK CORRIENDO  MTU:16436  Métrica:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          colisiones:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

yo@portatil:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 191 Gigabit Ethernet Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 4
       bus info: pci@0000:00:04.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:04:98:4b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sis190 driverversion=1.2 ip=192.168.0.193 latency=0 module=sis190 multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 22:00:8e:e6:58:ea
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
yo@portatil:~$ ifconfig > madwifi-nr-r3366+ar5007.tar.gz
yo@portatil:~$ screenshot.png
bash: screenshot.png: orden no encontrada
yo@portatil:~$ 

That's it. Thanks guys!

---

