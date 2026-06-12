---
title: "How am I suppose to act?"
date: 2007-02-07
forum: Networking &amp; Wireless
---

### Post by Robotuner on 2007-02-07
I'm new to linux and want very much to be productive with it.  From what I have seen, I can be productive, as the Office package works good enough.  However, there are nagging problems getting the hardware to work.  

I currently have wired connectivity. but am unable to get wireless to work.  After two installations, I have come to the conclusion that the System/Admin/Networking dialogs don't do anything, and no one other than me expected it to configure networking.  That is evidenced from reading this forum where no-one offers a solution that involves any menus.  Instead there seems to be an endless number of permutations of installing this and that, and modifying this file or that, all of which is basically what I call blind help.  

What I mean is that the help or suggestions alway provide snippets of script that is supposed to be typed into or cut and pasted into terminal server.  I think that is fine, except that it hasn't worked.  In the meantime, I've done/run a bunch of stuff on my machine that makes me wonder if I eventually do find something that should work, It might not because I have done a bunch of stuff that is unintended for the solution.

So, Is there anyone out there that knows how wireless networking is managed by the linux kernal?  I need wireless set up on my Dell 700m laptop.  What files control that, where are they located, and what do I need to know in order to modify the file in order for wireless to work?  And as an aside, networking is so basic, after all these years talking about how great linux is, why can't it be done through the menus?  Those other guys seem to be able to do it.

---

### Post by m.musashi on 2007-02-07
I don't really know how wireless is managed but I do have wireless working on several dell laptops. If you can be a bit more specific about what you need to know I might be able to help. There will be some typing or copying of code into a terminal as this is simply the easiest way to give you directions and collect the info we need to help diagnose the problem. Sorry about that but it's really a pain to say click x, y, and then z and then click this and that and so on. With phone support that's easier by via text a pain.

Before we can help much, we need to know the problem. Is your wireless card recognized? If not, I'll leave it to someone else as I have no experience there. All mine have just been set up automatically at instal.

If your card is recognized and you just need to configure the wireless client then I can help. Can you give a bit more info?

---

### Post by Robotuner on 2007-02-07
Thanks, I don't care if I have to type, thats not a problem, . . .

I'm running a dell 700m. Wireless works on eth0.  If I click on the icon in the upper right, it sees eth0 and lo.

If I open the system/admin/networking dialog, the wireless in not configured.  I know there is a wireless card in the dell 700m because it worked on the first install, even when the system/admin/networking said it wasn't configured.  The configuration dialog will not enable the connection.

So, is my wireless card recognized, I doubt it.

---

### Post by m.musashi on 2007-02-07
> **Robotuner said:**
> If I open the system/admin/networking dialog, the wireless in not configured.
The network settings window will say "not configured" if you are using something else to control networking (I'm using a program called Network Manager so mine also says not configured). If you highlight the option that says "wireless connection" and then click properties there is a checkbox to enable it. Is it checked? If not can you check it?

Also, can you copy the output from
```
ifconfig
```
I just want to see wht network adapters are being recognized. I need to start somewhere :).

---

### Post by kerry_s on 2007-02-07
Fantastic wireless support-> [http://ftp.belnet.be/linux/pclinuxos/live-cd/english/preview/pclinuxos-p93a-minime.iso](http://ftp.belnet.be/linux/pclinuxos/live-cd/english/preview/pclinuxos-p93a-minime.iso)

---

### Post by Robotuner on 2007-02-07
Nope, I can check it, but as soon as I close the dialog, it unchecks itself.

my ifconfig

eth0      Link encap:Ethernet  HWaddr 00:0F:1F:AF:61:98  
          inet addr:192.168.111.5  Bcast:192.168.111.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:1fff:feaf:6198/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19434 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9485 errors:0 dropped:0 overruns:0 carrier:0
          collisions:1414 txqueuelen:1000 
          RX bytes:14215010 (13.5 MiB)  TX bytes:881396 (860.7 KiB)
          Interrupt:10 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:98 errors:0 dropped:0 overruns:0 frame:0
          TX packets:98 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8100 (7.9 KiB)  TX bytes:8100 (7.9 KiB)

---

### Post by Robotuner on 2007-02-07
> **kerry_s said:**
> Fantastic wireless support-> [http://ftp.belnet.be/linux/pclinuxos/live-cd/english/preview/pclinuxos-p93a-minime.iso](http://ftp.belnet.be/linux/pclinuxos/live-cd/english/preview/pclinuxos-p93a-minime.iso)

Except that it is a bad link.

---

### Post by m.musashi on 2007-02-07
I only see eth0 and loopback. Since you are online wired, I'm guessing that eth0 is your wired connection. It has an IP address and seems to be sending and receiving. This suggests that your wireless card is not set up. I'm afraid I really don't have any experience installing wireless drivers. I'm somewhat supprised though that it wasn't automatically recognized. I have both a 600m and d820 (from Dell) and both worked out of the box as they say. I can't imagine why a 700m would be that different.

Are you familiar with [Automatix](http://www.getautomatix.com/)? It is a great tool for adding a lot of software that does not come with ubuntu. One this is will do is add NDISwrapper which will allow you to use windows drives for wireless in Ubuntu/Linux. I've never used it but it may be what you need to get your wireless activated.

Another thought? Do you have Network Manager installed? You may have installed it (actually, I think it's installed by default in edgy) when receiving support earlier. If it is currently handling wirelss then you will not be able to use the network settings window. Is your wired connectional saying not configured there? If so, I bet Network Manager is managing. Although, I still would have expected to see eth1 or something in the ifconfig output if that was the case. I'm guess it's just not "live" yet. Does your 700m have the little switch on the side to turn on the wifi catcher and turn off the wireless? If so, make sure it's on. I had that off before and had similar problems.

If you truly need to install the drive then I'm afraid I'm going to have to defer to someone else. Sorry. Check the above suggestions and post back. It may be something simple like the switch.

---

### Post by gradedcheese on 2007-02-07
Actually, all the Administration->Networking and other 'menu' tools do is edit files like /etc/network/interfaces and run commands like ifup, ifconfig, and iwconfig.  The trouble is that, at least to me, it's a lot easier to explain something in the shell rather than telling you where to click, what icon you're supposed to see, and what to type in what box.  Also the shell commands just seem more natural to a lot of people, and they have the advantage of being able to be written down, pasted here, and so on (rather than screenshots or the like).  However, the graphical utilities really do the same stuff, even if they're not 100% as powerful as the direct commands.

Generally speaking, unless you are using 'network manager', your network interfaces are described by this file:

/etc/network/interfaces

you need to edit it with 'sudo' privileges, so if you want to edit it with gedit, for example, run "sudo gedit /etc/network/interfaces".  You'll see most of the settings from the graphical Networking tool there.  Now, some commands:

'ifconfig' lists all of your network interfaces and their settings.  You can use it to configure an interface (named eth0, for example).  For instance, you can assign a static IP and bring the interface up like this:

sudo ifconfig eth0 192.168.1.12 up

The ifup and ifdown commands bring an interface up or down, and if you need a DHCP address you can run:

sudo dhclient eth0

for example.  The wireless state and settings are managed with 'iwconfig', you can run that to list all interfaces, and you can do things like:

sudo iwconfig eth1 essid my_ssid_here

to associate.  "sudo iwlist eth1 scanning" would do a scan and show you the available networks.  Finally, if you want to just bring everything down and then up again, using the settings in /etc/networking/interface and getting a DHCP address as needed:

sudo /etc/init.d/networking restart

I hope that helps.  Again, this is nothing that the graphical tools won't do, it's just easier to type and feels more natural.

---

### Post by kerry_s on 2007-02-08
> **Robotuner said:**
> Except that it is a bad link.

My bag, looks like they dumped the .93 line small installs. You can try the newest version, but it's full size so there's alot of stuff-> [ftp://ftp.nluug.nl/pub/os/Linux/distr/texstar/pclinuxos/live-cd/english/preview/livecd.iso](ftp://ftp.nluug.nl/pub/os/Linux/distr/texstar/pclinuxos/live-cd/english/preview/livecd.iso)

They have all the stuff for wireless like ndiswrapper, etc .. all ready installed, you just go to the "PClinuxOS Control Center" and set it up if it isn't done automatically. Mine was done automatically, but connected to a open wifi signal, mine is protected so i had to set it up for that.

---

### Post by Robotuner on 2007-02-08
Gradedcheese, thanks for the info.  I appreciated hearing about the ifconfig and the iwconfig commands and how they relate to the /etc/network/interfaces file.  That makes sense to me and also lets me know where I need to look to solve my problem.

Apparently, when I run iwconfig, I have no wireless extensions.  Does that mean something was not installed?  What are my choices?  Is it the Automatix or network manager that has been mentioned several times here?  I know I have ndiswrapper installed because I followed the instructions of one of the how to links a couple days ago

---

### Post by secion8 on 2007-02-08
Hello Robotuner,

Can you run lspci and post the output here. Need to see if the card is being recognized as installed then we can go from there. Sounds like you propably have the infamous broadcom card.

---

### Post by m.musashi on 2007-02-08
Sorry. I was hoping this would be a simple issue of configuring the client but I guess not. Hopefully someone else will be able to walk you through setting up drivers or whatever it ends up being.

One thing I keep coming back to is the feature on the dells to turn off wireless. The newer ones have a switch on the side. If that is off then nothing will happen. On the older models like the 600m there is an fn key for turning it off. I don't have my computer at the moment but I think it's fn-f2. On mine it is used to turn of bluetooth but it also turns off the wireless card. I spent a fair amount of time once trying to figure out why I didn't have wireless and it ended up being the dumb switch.

Good luck.

---

### Post by Robotuner on 2007-02-08
Thanks everyone.  I did some snooping around with the various commands and have resolved the problem.  What I learned was that wireless was not activated on the laptop.  There is a bios switch to turn it on at boot.  Second, Network Manager was not installed automatically, which is interesting because on my first installation, it apparently was installed.nto 

Once I activated wireless and installed NetworkManager, I was able to connect.  I'm wondering if the Ubunto install reacts differently if the machine is connected to a network during installation.  

The first installation, was unconnected and I got both wired and wireless.  The second installation I had my cat5 plugged in, I got wired but no wireless.  Also, I found that the system was apparently able to switch on/activate my wireless card initially, but now I had to change the bios setting.

I do have one nagging question about network connectivity.  On my windows computers, I have to tell each machine the ip of my dns server.  Right now, it appears that the dsl router is assigning ip to both my wired and wireless connections.  How can I direst my laptop to be part of my windows domain?

---

### Post by m.musashi on 2007-02-08
Glad to hear you got it working.  As for the install, I believe that Ubuntu tries to install all the hardware it finds. If something is turned off during install - like a wireless care - it probably will not detect it or install it. However, that is a guess but I can't quite see how it could install something if it doesn't know it's there.

> I do have one nagging question about network connectivity. On my windows computers, I have to tell each machine the ip of my dns server. Right now, it appears that the dsl router is assigning ip to both my wired and wireless connections. How can I direst my laptop to be part of my windows domain?

I'm not sure I understand the question. Are you running your own dns server or are you refering to your isp's dns servers? Or are you are tying to get Ubuntu to access files on a windows box? I've seen some how tos on doing this but I can't seem to locate one at the moment. If I can find one I'll post back. However, as this is a new issue you might have better luck finding an answer if you post a new thread.

---

