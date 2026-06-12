---
title: "network issues"
date: 2010-08-12
forum: New to Ubuntu
---

### Post by nnamdi on 2010-08-12
in my office i use the LAN here and it is on dhcp too, but still i cant surf the internet but other windows computers can surf the internet on my network dont really know what is wrong here. i can ping the router but cant ping external addresses like eg. [www.google.com](www.google.com), [www.yahoo.com](www.yahoo.com) what can i do please...

---

### Post by Peter09 on 2010-08-12
Sounds like a dns issue. Can you post the output of the command
 
```
route
```

---

### Post by nnamdi on 2010-08-12
```

pradeep@pradeep-laptop:~$ route

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
pradeep@pradeep-laptop:~$ 
 
```

that is my result...

---

### Post by Peter09 on 2010-08-12
Mmmm.. not default gateway defined in there. Are you sure that you are connected properly to the internet, what is your IP address. Can you provide the output to
 
```
ifconfig
```

---

### Post by nnamdi on 2010-08-12
i can ping my gateway which is 192.168.0.250 and i get a reply besides am on dchp in my office

```

 pradeep@pradeep-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr a4:ba:db:94:b3:ca  
          inet addr:192.168.0.25  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::a6ba:dbff:fe94:b3ca/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2003 errors:0 dropped:0 overruns:0 frame:0
          TX packets:267 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:203591 (203.5 KB)  TX bytes:36480 (36.4 KB)
          Interrupt:29 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:73 errors:0 dropped:0 overruns:0 frame:0
          TX packets:73 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6944 (6.9 KB)  TX bytes:6944 (6.9 KB)

pradeep@pradeep-laptop:~$ 


```

thank you for your response

---

### Post by Peter09 on 2010-08-12
As an experiment do this command and see if you get internet access
 
```
 
route add default gw <your gateway ip>

```
 
It is only temporary and will not survive a reboot.

---

### Post by nnamdi on 2010-08-12
but i use this computer on thiese same network all the time why should be happening?

---

### Post by Peter09 on 2010-08-12
> but i use this computer on thiese same network all the time why should be happening?
 
If we new we would not need to try to find the problem.

---

### Post by nnamdi on 2010-08-12
peter thank you so much it worked 

```

route add default gw 192.168.0.250

```

but you mention that if i reboot it will go back to the normal"which is not working" way it was. do you have a clue on what i can do to make it stop or a fix..

---

### Post by Peter09 on 2010-08-12
Here is a link on how to make a static route permanent.
 
[http://www.ubuntugeek.com/howto-add-permanent-static-routes-in-ubuntu.html](http://www.ubuntugeek.com/howto-add-permanent-static-routes-in-ubuntu.html)
 
You may find that when you open the file you find an invalid gateway address in there - if so delete it and restart networking. See if things work then.

---

### Post by nnamdi on 2010-08-12
does it mean that i cant use my computer elsewhere only in my office huh ???

---

### Post by Peter09 on 2010-08-12
Yes - that is true, if so then first check the /etc/networks file - it should not have a default gateway specified. We need to see where this default gateway address is coming from. Also does your computer work on other networks?

---

### Post by Peter09 on 2010-08-12
Sorry, talking rubbish - I am also talking to someone with an invalid gateway - not No gateway.. :D
 
Putting a fixed route into your machine will cause problems. Wondering why you are not seeing the gateway on your office network.
 
I wonder if its because the gateway is a windows machine .....
try installing winbind ..
 
```
sudo apt-get install winbind
```
 
which helps in address resolution on a windows network.

---

### Post by nnamdi on 2010-08-12
yes i use my 3g dongle to surf at home too.. then other wireless networks around

---

### Post by Peter09 on 2010-08-12
OK - try the winbind install

---

### Post by nnamdi on 2010-08-12
it is already installed winbind before now.

---

### Post by Elmer Fudd on 2010-08-12
Rigt-click the  Network manager.
Select "edit connections"
Go to "Wireless" tab.
Select the wireless connection in question.
Select "Edit"
select "iPv4 Settings" (I am assuming iPv4 is in use)
Select the "Routes" button.

I believe that you can address your problem location (192.168.0.250)  there without messing up your other locations that are working properly

Let us know.

---

### Post by nnamdi on 2010-08-13
that did not work for me tried adding the route like you via network manager but did not work...

---

### Post by Peter09 on 2010-08-13
You will need to restart to get it to work, at least log of the network, and re-login. Safer to try a reboot.

Check the route command afterwards

---

### Post by Elmer Fudd on 2010-08-13
> **nnamdi said:**
> that did not work for me tried adding the route like you via network manager but did not work...

Please confirm that when you got to the "Editing iPv4 Routes.." dialog that you clicked the "Gateway" Tab before adding the 192.168.0.250 route.
You should check the first check box below as well.

---

