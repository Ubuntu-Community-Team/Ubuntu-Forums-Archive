---
title: "Help With Setting Up A Network"
date: 2008-09-02
forum: Networking &amp; Wireless
---

### Post by uzzo2 on 2008-09-02
hello all, i have just ordered a linksys BEFSR41 wired router from tigerdirect and just need a little advice as to how to set this up as far as preliminary goes. i am actually going to try and share the internet connection with my old box which is a XP machine. some of the browsing i've seen here looks like this can be a bit tricky, i've never done it before. i followed a thread the other day that mentioned something about installing samba from synaptic to be able to share linux/windows machines. i believe that thread though the OP was running an older version of ubuntu. so is samba still a necessity and if so is there anything else that i need to do to prepare, thanks in advance.

---

### Post by NadmanET on 2008-09-02
Samba is not for sharing an internet connection; it is for sharing files between computers.  It would allow you to share a folder or a drive with other users/computers on the local network.  If all you want to do is share your internet connection, you've done all you can.  The router will do everything that you need to share the internet connection by default.  In fact you would want to make sure that internet connection sharing is disabled on your Windows computer as that would be a security risk.  You would only want to turn that on if that computer was directly attached to the internet and other computers were going to connect through it.

Keep in mind, sharing your internet connection is only half the fun of a home network.  Sharing resources such as printers and storage as well as your music library are now all possible!

Oh, and yes, samba (or a variant) is built into Ubuntu now.  Click places and go to network to view shares.  HTH

---

### Post by NadmanET on 2008-09-02
I just want to reiterate that this is not a tricky operation.  Most ISPs will work with this router's default settings.  Just plug your modem into the port labeled WAN or Internet and the computers into the other ports.  (And of course power.) The router will use NAT (dynamic PAT if you want to get technical) to share the internet connection.  Let us know how you make out.

---

### Post by uzzo2 on 2008-09-02
> **NadmanET said:**
> Samba is not for sharing an internet connection; it is for sharing files between computers.  It would allow you to share a folder or a drive with other users/computers on the local network.  If all you want to do is share your internet connection, you've done all you can.  The router will do everything that you need to share the internet connection by default.  In fact you would want to make sure that internet connection sharing is disabled on your Windows computer as that would be a security risk.  You would only want to turn that on if that computer was directly attached to the internet and other computers were going to connect through it.

Keep in mind, sharing your internet connection is only half the fun of a home network.  Sharing resources such as printers and storage as well as your music library are now all possible!

Oh, and yes, samba (or a variant) is built into Ubuntu now.  Click places and go to network to view shares.  HTH

well, i was only going to share the internet but if i could share files and the printer too would be pretty sweet. as far as disabling the internet sharing on my windows box. you need to do this even if you have a virus protection program on it. sorry for the dumb questions, thanks a bunch for the advice.

---

### Post by uzzo2 on 2008-09-02
> Click places and go to network to view shares. HTH
the only thing i see when i go here is an icon labeled "windows network".

---

### Post by NadmanET on 2008-09-03
Yes, you would want to disable internet connection sharing even with an antivirus program.  I mean, you could technically leave it on but I'm not even sure that you could set it up without multiple network cards.  I forget exactly how it is set up to work by default but in any case it would open up the ability for other people to connect through that computer.  I say that is a security risk because they would be just one step closer to comprimising that box.  Technically you should be fine if the software doesn't have any security vulerabilities but didn't you say this is a Windows box?? (Zing!)  It's a security risk on the principal that a computer that refuses all incoming connections is more secure than one that doesn't.

Regardless, that feature is for someone that wants to use their computer as a router.  You bought a seperate router so you don't need to do any of that.  And trust me, you don't want to use a Windows box as a router in the first place.  If you do ever have to use a non-purpose built device as a router I would look into a stripped down linux distro like FreeBSD.

As far as not seeing anything when you look in your network, you would first have to set up a shared resource.  For instance if you right click on your C drive and go to sharing and security you should be able to figure out how to setup a network share.  DON'T share out your entire C drive, that would be another one of those security vulnerablities I mentioned.  Instead pick a folder that you want to share and put everything that you want to have remote access to in there.  Once that it shared out you should be able to go into your Windows Network icon that you mentioned, then to your Windows Computer, then you should see the shares on that computer.

[[COLOR="Blue"]This[/COLOR]]("http://en.wikipedia.org/wiki/Server_Message_Block") should give you a backgroud on file sharing.  Armed with google you should have no problem figuring out how to share files and printers between Windows and Ubuntu; it practically does it for you.  Let us know if you run into any problems.

---

### Post by uzzo2 on 2008-09-03
ok, thanks a lot, UPS should be here with my stuff tomorrow. if i have any trouble i'll post it here.

---

### Post by uzzo2 on 2008-09-05
ok, got the router yesterday and just got through hooking it up, the internet connection is not working. i had to unplug from the router and straight back in to the modem to be able to access the internet. all the lights on the router are on as if it was working but i can't open up any web sites.

---

### Post by uzzo2 on 2008-09-05
here's the output from ifconfig.

eth0      Link encap:Ethernet  HWaddr 00:1d:92:e1:57:9d  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:92ff:fee1:579d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3939 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4272 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4479326 (4.2 MB)  TX bytes:574085 (560.6 KB)
          Interrupt:219 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1749 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1749 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:94579 (92.3 KB)  TX bytes:94579 (92.3 KB)

---

### Post by uzzo2 on 2008-09-05
UPDATE:

i called linksys tech support and they were able to get me up and running as far as the internet connection goes. now i would like to find out more about sharing files and the printer. looks like samba is the preferred choice for sharing files and is a server on its own i am assuming. i already have xampp installed for another application, will it work like samba?

---

### Post by NadmanET on 2008-09-05
Glad to hear that you got it working.  While most ISPs will work with the router out of the box, however some do require special configuration of the router.

Check [[COLOR="Blue"]this[/COLOR]]("https://help.ubuntu.com/community/SettingUpSamba") out and definitely check [[COLOR="Blue"]this[/COLOR]]("http://www.justfuckinggoogleit.com/") out.  ;)

Obviously I'm just poking fun with the second link but there should be plenty of information out there on setting up Samba within Ubuntu and sharing files between dissimilar operating systems.  If you run into a specific problem let me know and I'll see what I can do to assist.

Good luck!

---

### Post by uzzo2 on 2008-09-05
> Check this out and definitely check this out
why don't you tell me how you really feel, LOL. i accomplished my main goal today, think i'll turn in for the evening and work on it tomorrow, thanks for the advice.

---

### Post by uzzo2 on 2008-09-06
ok, i got samba set up and can see the shares but i've run into a couple of snags.i guess for all intensive purposes i should list the configuration here whereas, linux box= server, xp box= client. if i go to places/network/windows network/workgroup i can see both computers. main(client) and phillip-desktop(server), i can click on main and access some files from the client but if i click on phillip-desktop it prompts me for a password. i never set one up during the installation, it didn't ask me to. i've tried running "smbpasswd" from the terminal to change it but you have to know the old one in order to do that. i also ran into trouble trying to install the printer on the client. when i do start/control panel/printers/add printer and start the wizard, it browses and comes up with 3 options microsoft windows network, workgroup, and phillip-desktop, i've tried all 3. at the top where you have to put in the printer name i put it exactly like it's listed on the server namewise. i am getting the error "windows cannot connect to the printer. either the printer name was typed incorrectly or, the specified printer has lost it's connection from the server." i printed a test page from the server, it works just fine. i somehow feel that this may be related to the password issue but not sure.

---

### Post by uzzo2 on 2008-09-09
bump...
at this point i am really not all that interested in being able to share the files. if someone could help me figure out how to be able to print from the xp box i would be most appreciative.

---

