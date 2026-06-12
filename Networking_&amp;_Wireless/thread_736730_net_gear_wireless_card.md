---
title: "net gear wireless card"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by Cap'n Skyler on 2008-03-26
ok,here is what i am into at the moment--and hello to all :)
small home network,one windows xp machine,and 2 linux ubuntu 7.10 comps,one is an old HP p4 which i had trouble getting to work with ndis(i found the driver and got the INF i needed) and finally got the card detected and installed and working with NDIS wrapper.
 now my other comp is an old athlon xp,and i have Ubuntu 7.10 on and all up to date,and have everything working i could want--
i did all the same things to get the wireless up and running here,and still no luck.i have my INF file where i can find it ,and the device  manager shows my card netgear wg311/
Marvell Technology Group Ltd.
88w8335 [Libertas] 802.11b/g Wireless
same as on my P4 comp.
 i see my INF is called the invalid driver on the wireless drivers tab and i assume this is because my wireless card is not showing up.
on my P4 once i saw the card ,i could easily install the driver and presto it was on like donkey kong!
but this athlon xp machine just wont do it.i am unsure what i did exactly to make the p4 show the wireless card.
 sudo lshw shows this for my card

 *-network:1 UNCLAIMED
                description: Ethernet controller
                product: 88w8335 [Libertas] 802.11b/g Wireless
                vendor: Marvell Technology Group Ltd.
                physical id: 8
                bus info: pci@0000:01:08.0
                version: 03
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list
                configuration: latency=32

thanks for the help...i am unsure where to go from here.i did play with PCLinuxOS live dvd and got both computers working with wireless fully functioning.but i like ubuntu :) and want to make it work like it should .
and thanks to the ubuntu makers-- you are getting it so much more right every new release!! great job!

scott

---

### Post by Cap'n Skyler on 2008-03-27
small update here.
re started the p4 machine,and lost my settings.so re did everything,and got it back and saved (duh! LOL) my settings.
on the athlon machine,i changed the driver INF from the XP driver,to the win 98 (no idea if any difference between the two) and now it shows the driver is right and the hardware is installed. 
  *-network:1 UNCLAIMED
                description: Ethernet controller
                product: 88w8335 [Libertas] 802.11b/g Wireless
                vendor: Marvell Technology Group Ltd.
                physical id: 8
                bus info: pci@0000:01:08.0
                version: 03
                width: 32 bits
                clock: 66MHz
                capabilities: pm bus_master cap_list
                configuration: latency=32
           *-storage
still unclaimed.can some one explain what this means?

ok, and my wireless network diver tab says the hardware is installed
and it let me install the driver as well,but it is not coming up for the Wlan to be activated.
i think i am still a few clicks away from this working-gar!!!
thanks for the help folks
scott

---

### Post by Cap'n Skyler on 2008-03-27
ok,ALMOST got this figured out.
on both comps,i uninstalled the INF driver,and re booted and re selected the driver and got it to all work.i did seem to have better luck with the win 98 driver(dont know if all 3 drivers are the same).
i am so far unsure if it is properly saved,but it does stay up and connected with users switching back and  forth.
i thought sometimes linux likes you to restart when you change something like windows does with EVERYTHING and i got this to work.
i will continue to try and get my settings to stay,and be available for all users.will also post back up when i do.
 and also,if anyone can explain better what i did and why,please post up--i really love learning this stuff :)
thanks for listening to my rambling :)

scott:popcorn:

---

### Post by Cap'n Skyler on 2008-03-28
well the athlon comp booted up with no more wireless troubles :) W00T!!!:lolflag:

---

