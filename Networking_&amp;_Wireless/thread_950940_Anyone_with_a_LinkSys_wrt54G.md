---
title: "Anyone with a LinkSys wrt54G?"
date: 2008-10-17
forum: Networking &amp; Wireless
---

### Post by legolas_w on 2008-10-17
Hi
Thank you for reading my post.
I get a Linksys WRT54G and now I am thinking that it is not OK.
First I can not connect to its administration console on 192.168.1.1 or 192.168.1.100. 
Secondly when I turn it on, all of its lan ports' LEDS blink for few minutes and then it stop blinking, after it stop blinking my computer can acquire an IP address like:

and finally, its power button always blinks instead of being ON.


Are these OK for a WRT54G or my device is defected?

Thanks.

---

### Post by Ub1476 on 2008-10-17
My wrt54g:

Power: Always green
DMZ: Off
Wlan: flashing
Internet: flashes quickly. 

And I'm running the Tomato firmware, open-source and simply awesome compared to what came with the device.

I'm no router smartguy but your might be defect in some way I guess.. And it's probably the power since it's flashing.

---

### Post by cariboo on 2008-10-17
You may have a defective router, on mine the power light is always green, not being able to access the management interface may be another clue.

Jim

---

### Post by klange on 2008-10-17
Sounds like it's bricked. Be that the case, there are ways to fix it such as [reflashing the firmware](http://oasis-games.com/article.php?id=131) via tftp.
My WRT runs dd-wrt at the moment. Tried out OpenWRT a while ago, and that didn't work very well, ended up bricking it and having to fix it, then I was back on the regular firmware for a while.

---

### Post by pacrep on 2008-10-17
Mine is the same as above Wrt54g Ver 2.2 using DD-Wrt also Open Source. I Recommend A hard reset, Hold the reset button for 30sec.

If you are on wireless I suggest trying use the ethernet port
If already on ethernet port and still have to wait for IP Addess then somethings wrong.

---

### Post by Viranh on 2008-10-17
I have several of these routers. I seem to remember that it is normal for them to blink when they come on. Are you trying to connect to it wirelessly? They need to be configured plugged in to one of the LAN ports. You should get a login dialogue at 192.168.1.1 by default. If you don't, try powercycling then if that doesn't work, reset it using the pin in the back and try again. It really should allow you to login if you are plugged in to it. However, I do have one machine that has trouble logging in wirelessly some days. I have found that manually assigning an IP, setting the default gateway to 192.168.1.1 and setting the subnet mask. I only have to do this wirelessly though,so I'm not sure this helps at all. I've never had trouble connecting via Ethernet. Is your Ethernet card well supported in Linux? Do you have another computer to test the router with? If you dual boot, check it in both OS's. What does ifconfig (Linux) or ipconfig (Windows) output when you are plugged in to the router? Have you tried different cords? Different ports on the router? If none of this helps, I'd probably call it defective. I haven't ever had that kind of trouble with them out of the box. I'm no expert though.

---

### Post by legolas_w on 2008-10-17
Thank you all,
My computer can acquire an IP after some time something like:
```

eth0:avahi Link encap:Ethernet  HWaddr 00:50:8d:ca:1f:7b  
          inet addr:169.254.6.172  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:20 Base address:0x4c00 

```

Is that ok?
But the power led blink even when it gave me an IP.

I dont know what i did but a web page shown onece when i was playing with the  router and its power supply plug and reset button, the page was titled "Management Mode" and it had some places to upload a new ROM.

how much it takes for the router to upload the new ROM from my hard disk?

Thanks

---

### Post by pp. on 2008-10-17
> **legolas_w said:**
> 
          inet addr:169.254.6.172

Is that a computer running Windows?
What IP address does it acquire when the wrt54g is powered off?
When the wrt54G is powered on and connected to the LAN, does the browser find a page at [http://169.254.6.1](http://169.254.6.1) ?

Have you tried resetting the device for about 30 seconds?

---

### Post by Viranh on 2008-10-17
upgrading the firmware is a good idea. I hadn't thought about that. Your IP is not what I would have expected. When I plug a computer into port 1 on my router, I get something like the following:
IP: 192.168.1.101
Default Gateway: 192.168.1.1
Subnet mask: 255.255.255.0

I actually might try manually setting these. You can do this from network manager in Ubuntu. If you need instructions for Windows, I need to go home and check because I can't remember specifically where the settings are.

---

### Post by legolas_w on 2008-10-17
Hi
I am using ubuntu and network interface get this IP address automatically.

It acquire no IP address when I unplug it from the wrt45g or turn that off.

No it does not open [http://169.254.6.1/](http://169.254.6.1/) and it does not opens 192.168.1.1


When unplugged from WRT45G it shows:

```


eth0      Link encap:Ethernet  HWaddr 00:50:8d:ca:1f:7b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:9145895 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10117938 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3646530382 (3.3 GB)  TX bytes:1257222433 (1.1 GB)
          Interrupt:20 Base address:0x4c00 


```

Thanks

---

### Post by Viranh on 2008-10-17
Google tells me that a 169 ip address means that your computer cannot find a DHCP server. Anyone care to interpret this? I thought that the router was the DHCP server.

---

### Post by K.Mandla on 2008-10-17
Moved to Networking and Wireless.

---

### Post by smartboyathome on 2008-10-17
My WRT54G router recently quit, and it was in a similar shape to yours. I would say you might have to just go out and buy a new router. I got a new WRT54G2, it works perfectly for what I need. Only problem is there is no alternative firmware yet. :(

---

### Post by pp. on 2008-10-18
> **Viranh said:**
> Google tells me that a 169 ip address means that your computer cannot find a DHCP server. Anyone care to interpret this? I thought that the router was the DHCP server.

The device is not working.

It does 'operate' the NIC. The DHCP server does not respond. The flashing power on light indicates that the firmware does not start properly when the device is turned on.

Not finding the built-in web server does not contribute anything to the analyses because it could use an unexpected IP address. You could try and run an IP scanner, but I do not think that it would find anything.

I didn't know that Linux also uses 169.x.x.x when there is no working DHCP. Also, I didn't take into consideration that the DHCP client does not look for a DHCP server when the NIC is not connected to a live node.

As other people already have suggested:
[LIST]
[*]Do a hard reset (paper clip into "reset" hole for at least ten seconds).
[*]Try to restore the firmware.
[*]Buy another one.
[/LIST]

---

### Post by tubbygweilo on 2008-10-27
I am have been running a Linksys AG241 router as address [http://192.168.2.1/Status_DSL.asp](http://192.168.2.1/Status_DSL.asp) and have been running a WRT54GL as address [http://192.168.1.1/](http://192.168.1.1/). 

It took a little while to realise that I needed to change the router address from 192.168.1.1 to the new value of 192.168.2.1.

---

### Post by seannon on 2008-10-27
I have used a couple of different versions of the wrt54"x" routers for several years now... 

Here is a microsoft article explaining the 169.254.X.X address.
[http://support.microsoft.com/kb/220874](http://support.microsoft.com/kb/220874)

As for the lights flashing on the router, it sounds like a firmware problem... there is more information on DD-WRT.com here [http://dd-wrt.com/wiki/index.php/Main_Page](http://dd-wrt.com/wiki/index.php/Main_Page) you can go into the installation section, and check on info on your particular version...

---

### Post by Staphman on 2008-12-28
My Linksys WRT54G packed in over Xmas and I found that the power supply has gone (without warning). When I opened it up I found that two wires had broken on the transormer, which isn't fixed down very well. So, intermiittent flashing of this model at least, could be to do with poor contact inside the power supply. There is a well known problem with the power supply for this router. 
Cheers
Don

---

