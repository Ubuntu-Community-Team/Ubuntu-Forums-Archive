---
title: "Installing Cisco Packet Tracer version 6.0.1 on Ubuntu 13.04"
date: 2013-09-19
forum: Networking &amp; Wireless
---

### Post by pacian on 2013-09-19
Hello,

I am so new and so green to Ubuntu .. I am attempting the impossible..

installing Cisco Packet Tracer on 13.04

any help with step by step instructions would really help.

thanks
**Cisco Packet Tracer 6.0.1 for Linux - Ubuntu installation (with tutorials)**


[https://www.netacad.com/documents/301287/48648242/Cisco+Packet+Tracer+6.0.1+for+Linux+-+Ubuntu+installation+%28with+tutorials%29/d5ab993a-ec68-4d89-8b13-4734250d3137](https://www.netacad.com/documents/301287/48648242/Cisco+Packet+Tracer+6.0.1+for+Linux+-+Ubuntu+installation+%28with+tutorials%29/d5ab993a-ec68-4d89-8b13-4734250d3137)

---

### Post by sandyd on 2013-09-19
> **pacian said:**
> Hello,

I am so new and so green to Ubuntu .. I am attempting the impossible..

installing Cisco Packet Tracer on 13.04

any help with step by step instructions would really help.

thanks
**Cisco Packet Tracer 6.0.1 for Linux - Ubuntu installation (with tutorials)**


[https://www.netacad.com/documents/301287/48648242/Cisco+Packet+Tracer+6.0.1+for+Linux+-+Ubuntu+installation+%28with+tutorials%29/d5ab993a-ec68-4d89-8b13-4734250d3137](https://www.netacad.com/documents/301287/48648242/Cisco+Packet+Tracer+6.0.1+for+Linux+-+Ubuntu+installation+%28with+tutorials%29/d5ab993a-ec68-4d89-8b13-4734250d3137)
Version 5.3 installs and works perfectly with wine ([http://appdb.winehq.org/objectManager.php?sClass=version&iId=27403](http://appdb.winehq.org/objectManager.php?sClass=version&iId=27403))

Install wine from the ubuntu software center, and double click the installer, which should install cisco packet tracer

---

### Post by pacian on 2013-09-19
there are features added to 6.0.1 that are required for this course I am taking in Sweden..

thanks though

---

### Post by pacian on 2013-09-19
I wanted to install 5.3 but we are required along with the rest of my class who have 6.0.1 running on Windows.. I use Linux.. so I really need this installed.

---

### Post by pacian on 2013-09-20
Please someone out there help me with this version of packet tracer..

I really need to install it.

---

### Post by dmadiedo on 2013-09-25
It's a .bin file? If so, please make sure that the name of the file doesn't have spaces.

Let's say for this example that the file is cisco.bin.

From the terminal, go to the folder where the file is stored.

Then, you have to make the file executable (no quotes): "chmod a+x cisco.bin".

Then you have to run that file as root: "sudo ./cisco.bin"

And  follow the instructions.

Hope it helps.

---

### Post by elemer2 on 2013-10-02
> **dmadiedo said:**
> It's a .bin file? If so, please make sure that the name of the file doesn't have spaces.




Unfortunately it is not a .bin file.

There are severall versions:

1. "*Cisco Packet Tracer 6-0-1 for Linux (no tutorials)"*     (there is no file extension to this file)
2. "*Cisco Packet Tracer 6-0-1 for Linux - Ubuntu installation (no tutorials)-*"  (there is no file extension to this file either)

I depakaged one of this files and it includes a file called install  (no extension again)

I put here the beginning of install



#!/bin/bash


# Thanks to Felix Wolf (felix@bar.bz) for providing this install script.
initInstall ()
{
echo
echo Welcome to Cisco Packet Tracer 6.0.1 Installation



I don't Felix Wolf for the script because he didn't gave me instructions 



Any ideas?

---

### Post by berny424 on 2013-10-14
Change the name of the file like Cisco 
1- tar xvf Cisco
2-cd PacketTracer601 && sudo sh ./install

By the way I'm in the Downloads directory. And to open Packet Tracer, you need to put packettracer in a terminal.

---

### Post by berny424 on 2013-10-15
If you want I found this [http://www.labcisco.com.br/app/Cisco-PT-601.bin](http://www.labcisco.com.br/app/Cisco-PT-601.bin) it's a bin file. Download that file and put in the terminal sudo sh ./Cisco-PT-601.bin and follow the instructions.

---

### Post by malnacido on 2013-11-06
Your solution worked berny424. Quick, easy, and painless. Thanks!

---

### Post by fcm200837354 on 2013-11-19
[FONT=Verdana]> **berny424 said:**
> [/FONT][FONT=Verdana] Download that file and put in the terminal sudo sh ./Cisco-PT-601.bin and follow the instructions.[/FONT]
Great!.
That worked!
For Ubuntu , version 13.10, 32bits

---

### Post by pbane73 on 2013-11-21
I am also trying to install Cisco Packet Tracer version 6.01 on Ubuntu but when I click on the link you gave, google tells me it can't find the site.  I really need to get this installed for a class that I am taking.  Everyone else in class is using windows but I use Ubuntu.  Any help is greatly appreciated.

---

### Post by jdarby1983 on 2013-11-21
why use packet tracer when you have GNS3 at your disposal? Find yourself a copy of Cisco IOS from somewhere *rolls eyes* and start configured up a Router with no limitations

---

### Post by pbane73 on 2013-11-21
I am in a Cisco College class and they do all the labs with tutorials in packet tracer.  I am also very new to using Ubuntu and I am still learning it.  Do you know of any web sites that I can use to learn how to use Ubuntu better?

---

### Post by 17.madhusudhanhn on 2013-12-26
How to download cisco packet tracer in ubuntu 13.04

---

### Post by prakashbankar5 on 2013-12-26
Hi thanks for sharing and it is working for me dont know about others? thanks and keep posting. [Buy Twitter Followers]("http://www.boostfollower.com/")

---

