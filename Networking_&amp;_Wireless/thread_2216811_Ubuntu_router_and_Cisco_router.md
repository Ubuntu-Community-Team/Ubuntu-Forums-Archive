---
title: "Ubuntu router and Cisco router"
date: 2014-04-14
forum: Networking &amp; Wireless
---

### Post by simon_lin on 2014-04-14
hi all

i like to know if its possible to connect a Ubuntu router to a Cisco router?
if so how can this be done?

thanks

---

### Post by grahammechanical on 2014-04-14
What is a Ubuntu Router? A router running on embedded Ubuntu? Canonical (the supporter of Ubuntu) is a software company. I do not think that Canonical makes hardware like routers.

Please tell us what you want to do. There are standard protocols for connecting network devices to each other. If an OS recognises and activates the network adapters in the computer then it should not be too difficult to connect the computer to the router/hub/modem whoever the manufacturer is. We will need to enter a pass phrase, also called a wireless key or WPA-PSK key if we are making a connection to the router by wireless. But no such pass phrase is needed if the connection is by cable.

Ubuntu makes it easy for us to set up network connections. There is a utility called Network Manager that takes care of most of the difficult bits.

What version fo Ubuntu are you using? We need more information that is specific to your needs and your machine.

Regards.

---

### Post by simon_lin on 2014-04-14
sry i mean the Ubuntu virtual router. i was task to connect a Ubuntu (13.10) virtual router to a actual Cisco router this was for a mini project. 
i have been searching for awhile and came up with no result as to how it could be done or was it even possible. maybe im just doing the wrong search. im not even sure if im making any sense here.

thanks

---

### Post by SeijiSensei on 2014-04-14
What is an "Ubuntu virtual router?"

If the Ubuntu box has two interfaces, you would connect its externally-facing interface to the internally-facing interface on the Cisco, then connect the LAN to the internally-facing interface on the Ubuntu box.  You'll need to use masquerading with iptables as well.

---

### Post by SeijiSensei on 2014-04-14
[QUOTE=simon_lin]sry i don't quite understand your last reply but i think what your saying is similar to this setting up a Ubuntu wired/wireless guide
[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router). 
i believe that guide is only for setting up the router.[/QUOTE]

Please don't use private messages since other people who might post comments will not see them, nor will people who consult this thread in the future.

You need to tell us *exactly* what you are trying to do.  Are you trying to replace a Cisco with an Ubuntu box?  Add another router behind the Cisco box (that was what my reply referred to)?  The phrase "connect an Ubuntu router to a Cisco router" can mean many different things.  What is the specific problem you are trying to solve?

I'm assuming this isn't a homework project, but if it is, please read [item #7 here]("http://ubuntuforums.org/showthread.php?t=2158945").

---

### Post by simon_lin on 2014-04-14
hello

sorry for the confusion of questions. i did little searching and i think i wanted something like this.
i will have 1 Ubuntu(13.10) install on a machine and i want that Ubuntu box to act as a router.  
i will or i want that Ubuntu router that's been setup to connect to the Cisco router, i believe i will need network card to connect to the Cisco router either the on-board card or a pci card.
sorry i am not sure if im being clear here.

thank you

---

### Post by SeijiSensei on 2014-04-15
A "router" has at least two interfaces connecting to different networks so that it can route the traffic between them.  From your description it doesn't sound like you want to build a router, but just connect a PC running Ubuntu to an existing Cisco router.  Or will there be another network behind the Ubuntu box?

---

### Post by simon_lin on 2014-04-15
hello

yip that what i want just couldn't find the right words to describe it but not just a running pc with Ubuntu install, i need one of the network interface connecting to the Cisco router. as you said in your earlier reply connect the external interface to the internal interface on the Cisco something like that.

thank you

---

### Post by SeijiSensei on 2014-04-16
If the Cisco is running a DHCP server, you should be able to plug the Ubuntu box into the Cisco and let it get an address automatically.  Otherwise you'll need to use static addressing on both adapters.  The default gateway should point to the Cisco.  You might want to set up **isc-dhcp-server** on the Ubuntu box to have it manage the client configurations on the network behind that box.

---

### Post by simon_lin on 2014-04-16
hello

i will not be using a DHCP on the Cisco so this will be done with Static. yeah i may setup the isc-dhcp-server after because right now i just want to focus on the Ubuntu box and the Cisco router all else can come after.
thanks for all the help.

thank you

---

