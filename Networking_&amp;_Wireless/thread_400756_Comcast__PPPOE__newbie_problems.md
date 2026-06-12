---
title: "Comcast / PPPOE / newbie problems"
date: 2007-04-03
forum: Networking &amp; Wireless
---

### Post by ingsy on 2007-04-03
big time newbie here.  i just built a new PC, and installed ubuntu 6.10.  i love it, but can't get the internet to work (firefox says server not found).  i use a comcast cable internet connection, and it runs fine on my XP laptop - no wireless is involved.  when i run pppoeconf, i get the message stating "Access Concentrator of your provider did not respond.".  i know others have had this problem - i did a search but the various solutions did not work.  here are some more details:

- System / Administration / Network Tools: shows eth0 receiving packets
- System / Administration / Networking: shows eth2, eth1, and eth0 all w/ the connected box checked on. i have tried setting eth0 as 'automatic configuration (DHCP) and as Static IP address using the XP ipconfig info - neither works
- i tried using the opendns website notes, still nothing
- when i run 'dpkg -s pppoeconf' it says 'install ok installed'
- if config shows an 'inet addr' for eth0 that is the same as the IP on my laptop
- In the firefox address/URL space i typed "about:config" , i scrolled down to network.dns.disableIPV6 = false ,double clicked this line to change it to true -> still no dice
- i ran 'poff dsl-provider'and i actually typed in "dsl-provider" - i get "No pppd is running.  None Stopped".  when i type 'pon dsl-provider' i get a bunch of wierd characters that go across the terminal screen.

a friend told me i should get a router, make sure it works for the XP laptop, then just plug in the new ubunto PC and it should work...i am willing to do this, but would rather save the 50 bucks.  any help would be greatly appreciated.  thanks!

---

### Post by jglen490 on 2007-04-03
If you are using a cable ISP, the PPPOE is not appropriate as that is a DSL protocol.  Use your PPP dialer app and enter your ISP's address (whatever they provided you when they installed your cable modem), your user id, and password.

---

### Post by ingsy on 2007-04-03
> **jglen490 said:**
> If you are using a cable ISP, the PPPOE is not appropriate as that is a DSL protocol.  Use your PPP dialer app and enter your ISP's address (whatever they provided you when they installed your cable modem), your user id, and password.


thank you very much for the feedback - i am not exactly sure what a PPP dialer app is, but i do have my user ID/Password so i will search the ubuntu help to figure out how to start the PPP dialer app.  thanks again!  i will let you all know if it works.  cheers, ingsy

---

### Post by ingsy on 2007-04-03
alrighty...

i am still in need of help.  first, i am not sure where i can find the 'ppp dialer app'.  second, i called comcast and they had no idea what the 'ISP address' means.  they gave me the IP of my cable modem, but i am not sure where this goes.  i do have my username/password for comcast highspeed internet, but i can't find out where i need to put this.  

again - very appreciative of any help, even if it doesn't work.  if i can't get this figured out soon, i will buy a router tommorrow.  thanks again!

---

### Post by Mach1US on 2007-04-04
If you are connecting to cable modem via your Ethernet card you should enable it for DHCP and activate the interface.
To do so right click on little monitor icon in right upper conner select properties , select or type in your NIC card (ethernet card usually is  eth0 ), click configure, then in configuration select DHCP and check box "enable this connection" .
This enables ethernet port on yor pc but you should still invest in a router simply because it gives you NAT protection which hides your machine's ip address , protects it with SPI firewall and gives you ability to use this modem for more than one machine and it can be configured to stay always on so you wan't need to login every time you need to use internet. 
You can get one on e-bay really cheap just make sure to either turn off wireless or change default password and turn on at least wep protection otherwise you inviting whole neighborhood to trash your  network.

---

### Post by ingsy on 2007-04-04
hello,

thank you both for helping me out.  i am not sure exactly what did the trick - as i tried so many things - but i have internet now and i am very happy!  i think re-starting the cable modem combined w/ changing it back to DHCP instead of static IP did the trick.  i still plan on getting a router someday though as i now have 2 pcs.

\\:D/

---

