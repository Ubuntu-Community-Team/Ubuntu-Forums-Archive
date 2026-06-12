---
title: "How to set up Lan"
date: 2006-08-02
forum: Networking &amp; Wireless
---

### Post by Linux_Noobie on 2006-08-02
I am trying To Get My Other Ubuntu Pc on The Internet using a lan. One Computor is Ubuntu Linux 6.06. And My other Pc is UbuntuLinux Server Version Running The First Configuration. I Have A crossover Cable (2 of them.) I am currently Connected Wirelessly To My [Motorola SBG-900](http://broadband.motorola.com/consumers/products/sbg900/) And The Network Is "Motorola" (Open) And i also have a Unconnected [D-Link DI-514](http://support.dlink.com/products/view.asp?productid=DI-514) My 2 Pc's Are both. [Emachine T2692's](http://www.emachines.com/products/products.html?prod=T2692) 
Pc #1 Is connected By Dlink Dwl-122 To My Wireless Network.
I Need The Other Pc Connected To it And To Share the internet. And i need it to Use The Crossover cable. 
(People always say im to unpessific SO i am trying to be major Pecific.)
How can i set This Up.

---

### Post by dmizer on 2006-08-02
okay ... two pc's.  server (no gui) and workstation (gui).

IF i understand this correctly, you have the following configuration:

modem->router - - - > workstation->server

this will actually make things difficult because your workstation will have to be setup as a server to serve your server. in effect forcing you to have two servers, both of which must run all the time.

just install ssh and webmin on your server.  then, your best bet is to simply connect the server directly to the router (no crossover cable).  you won't need a monitor or keyboard, or mouse attached to your server, just power and lan (this is especially true of a non-gui server type install).  but be sure to change the bios configuration to ignore keyboard error.

you will be able to ssh into your server and it will be as though you are sitting right infront of it.  webmin will give you a bit more of a graphical interface which is handy to have at times.

---

### Post by mips on 2006-08-02
Configure the ethernet port on your pc with an IP address, subnet mask and the gateway as the wireless interface on the pcs ip address. Make sure that you use a different network to the wireless one,if you are using 192.168.1.0 for the wireless use 192.168.2.0 for the wired lan.

Install Firestarter and configure your server with a IP address in the same network as the pcs wired lan, make the gateway the pcs ethernet port address.

---

### Post by Linux_Noobie on 2006-08-02
Can you give Me Step By Step Intructions For That? Im Kinda New to all This.

---

### Post by mips on 2006-08-02
I'm off to the pub right now but will be back later. maybe someone else can tell you how to setup firestarter or alternatively do a search here for now. If you do an advanced search for Keywords=firestarter and Username=mips you might come across one of my previous explanations on how to do this if this helps in any way.

Somewhere in here should be an explanation, just do a quick scan through them, [http://www.ubuntuforums.org/search.php?searchid=7167542](http://www.ubuntuforums.org/search.php?searchid=7167542)

---

### Post by dmizer on 2006-08-02
in synaptic ... search for firestarter.  you'll also need dhcpd (to serve up a dhcp address to your attached box).

give it a shot. try configuring firestarter on your own, it has a wizard configuration style.  if you run into problems, post back.

---

### Post by jrjr on 2006-08-02
.

---

### Post by Linux_Noobie on 2006-08-02
I still cant figure it out Im Now considering just getting another D-Link...WHat is a cheap one from  a non online store and where can i get it?

---

### Post by dmizer on 2006-08-02
what are you having trouble figuring out?  how to install the software? how to configure it?

tell us exactly what is giving you difficulty figuring out and we can help you. what exactly is stopping you from proceeding?

---

### Post by mips on 2006-08-02
> **Linux_Noobie said:**
> I still cant figure it out Im Now considering just getting another D-Link...WHat is a cheap one from  a non online store and where can i get it?

Before you spend any more money tell us what you cant figure out.

---

