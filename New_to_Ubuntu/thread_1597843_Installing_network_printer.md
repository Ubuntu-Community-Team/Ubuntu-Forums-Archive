---
title: "Installing network printer"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by Sunfist on 2010-10-15
I have a Canon network printer which works fine in Windows, how do I install this in Ubuntu (10.4). I go to printers/add and click on find printer, was wondering what, if anything, goes in the box labeled Host. I do know the IP address of the printer if thats a help, but it just says no printers located.

---

### Post by khelben1979 on 2010-10-16
What is the model number of this Canon printer?

Also, do you have [CUPS]("http://en.wikipedia.org/wiki/Cups") installed?

---

### Post by Sunfist on 2010-10-16
Yes CUPS is installed and the model is a MX860, I did a search and Ubuntu didn't locate any drivers specific to this model.

---

### Post by khelben1979 on 2010-10-16
I just found [this thread]("http://forums.linux-foundation.org/read.php?25,9006"). Check it out!

---

### Post by Mark Phelps on 2010-10-16
Open CUPS in a browser by entering localhost:631.

Click the Administration tab, then Add New Printer.

You should then have three headings:
-- Local Printers
-- Discovered Network Printers
-- Other Network Printers

The printer you want should be under the second heading.

This has worked for me with networked printers since Ubuntu 10.04.  Before that, I had to add them manually.

---

### Post by cariboo on 2010-10-16
It would be handy if you knew the ip address, in case you have to do printer administration. To find out what the ip address is, open an Application->Accessories->Terminal, next type:

```
ifconfig
```


the output will look something like this:

```
ifconfig
eth0      Link encap:Ethernet  HWaddr 18:a9:05:d4:c2:22  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 

eth1      Link encap:Ethernet  HWaddr 90:4c:e5:41:e4:2f  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::924c:e5ff:fe41:e42f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:676928 errors:0 dropped:0 overruns:0 frame:2631586
          TX packets:350100 errors:64 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:945577862 (945.5 MB)  TX bytes:31631792 (31.6 MB)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2478 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2478 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:102314 (102.3 KB)  TX bytes:102314 (102.3 KB)
```

If you look at eth1 you will see that my ip address is 192.168.1.104. now that you know your ip address, you can search the network for your printer in the same terminal type:

```
sudo nmap -sP 192.168.1.0/24
```

The above command will list the ip addresses of all the devices on your local network. One thing to note, is if you don't have nmap installed, Ubuntu will give you instruction on how to install it.  Once you have run the nmap command, if it found your printer, the output will look similar to this:

```
Nmap scan report for 192.168.1.230
Host is up (0.054s latency)
MAC Address: 00:80:77:89:A3:29 (Brother Industries)
```

As you can see from the above output, I have a Brother printer, and it's ip address is 192.168.1.230.

---

### Post by Jerry N on 2010-10-16
First, can you see your Windows computer from your Ubuntu computer, ie is your network working correctly?  
Second, have you activated printer sharing in Windows?

When you are ready to set up the network printer, under "Printing" select "Add Print" but I assume you have already been there and done that.  Then you select "Network Printer".  Then select "Windows Printer Via Samba".  Then "Browse" for the Windows server to which the printer is connected.  In my case I get to "WORKGROUP", which surprisingly enough is the name of my workgroup, and from there to ATOM330, the name of my Windows print server.  When I select the server, I see the connected printers and go from there.  I never have to resort to fiddling with CUPS or //localhost:631 on an Ubuntu or Mint system.  As usual, if you have been through all these steps, just forget my blather.

Jerry

Actually, I did try to mess with CUPS and //localhost:631 on Xubuntu 6.06LTS.  Never did get that sucker to print!

---

