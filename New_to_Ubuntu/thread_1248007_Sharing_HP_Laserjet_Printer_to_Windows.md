---
title: "Sharing HP Laserjet Printer to Windows"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by Buuntu on 2009-08-23
I'm trying to set up sharing so I can print from a computer with Windows Vista.  
The printer is connected to the Ubuntu computer.  Its model is HP Laserjet 1012.

I installed Samba, but I don't know if there's something else I have to do?  I also enabled sharing of the printer and checked "Publish shared printers connected to this system".

Trying to browse from the Vista computer doesn't show anything, not even this computer (don't know if it's supposed to :P).  
Any help would be appreciated...

---

### Post by perce on 2009-08-23
> **Buuntu said:**
> I'm trying to set up sharing so I can print from a computer with Windows Vista.  
The printer is connected to the Ubuntu computer.  Its model is HP Laserjet 1012.

I installed Samba, but I don't know if there's something else I have to do?  I also enabled sharing of the printer and checked "Publish shared printers connected to this system".

Trying to browse from the Vista computer doesn't show anything, not even this computer (don't know if it's supposed to :P).  
Any help would be appreciated...

If your Ubuntu computer has a fixed IP address, you can share the printer using the IPP protocol. First, you have to go to System > Administration > Printing, then in the printers windows you go to server > settings and check the boxes "Publish shared printers connected to this system" and "allow printing from the Internet". A reboot may or may not be needed, I'm not sure about that. 

Then you go to your Windows machine, and use "Add Printer" to add a new network printer, selecting "Connect to a printer on the Internet", and using a URL of [http://hostname:631/printers/RawPrinterQueueName](http://hostname:631/printers/RawPrinterQueueName). 
(here hostname must be your Ubuntu computer's IP address, and RawPrinterQueueName the name of the printer on the Ubuntu system).  Select the printer driver for this printer as you would for a locally connected printer. Vista, I think, works the same as XP.

It is important in thei configuration, that the ip address of the Ubuntu box doesn't change from time to time, otherwise you have to edit the address in the Windows configuration.

---

### Post by pedro3005 on 2009-08-23
I'd suggest you use Webmin. 'sudo apt-get install webmin' . After installing, access [https://127.0.0.1:10000/](https://127.0.0.1:10000/) from your browser. Log in with root details. Go to Server - Samba windows bla bla. Create a new printer share, set it up. Go to default printer options, security, and allow guest access and everything there (it should all be pretty straight forward, i can't remember exactly). run 'sudo /etc/init.d/samba restart'. Now go on Windows, and while setting up a new printer, it should find it while browsing the network. If not, fiddle with the configs at Webmin, you should find it quickly. Make sure on the Windows Networking section that the Workgroup matches. Anyways, good luck :)

---

### Post by Buuntu on 2009-08-23
Printers still wasn't found in Vista.  

I also can't even see my Ubuntu machine from Network in the Vista computer.

---

### Post by Buuntu on 2009-08-23
> **perce said:**
> If your Ubuntu computer has a fixed IP address, you can share the printer using the IPP protocol. First, you have to go to System > Administration > Printing, then in the printers windows you go to server > settings and check the boxes "Publish shared printers connected to this system" and "allow printing from the Internet". A reboot may or may not be needed, I'm not sure about that. 

Then you go to your Windows machine, and use "Add Printer" to add a new network printer, selecting "Connect to a printer on the Internet", and using a URL of [http://hostname:631/printers/RawPrinterQueueName](http://hostname:631/printers/RawPrinterQueueName). 
(here hostname must be your Ubuntu computer's IP address, and RawPrinterQueueName the name of the printer on the Ubuntu system).  Select the printer driver for this printer as you would for a locally connected printer. Vista, I think, works the same as XP.

It is important in thei configuration, that the ip address of the Ubuntu box doesn't change from time to time, otherwise you have to edit the address in the Windows configuration.

Would the name of the printer be the name on the Ubuntu system or the share name?

---

### Post by perce on 2009-08-24
> **Buuntu said:**
> Would the name of the printer be the name on the Ubuntu system or the share name?

It is the name on Ubuntu, this setup has nothing to do with Samba (in fact I have a configuration like that at home, and no Samba)

More precisely, you can go to the page [http://hostname:631/printers/]("http://hostname:631/printers/") with your browser, and read the exact name (case sensitive!) of the printer there. (Of course hostname should be the address of the Ubuntu computer)

---

### Post by The Cog on 2009-08-24
> **perce said:**
> It is the name on Ubuntu, this setup has nothing to do with Samba (in fact I have a configuration like that at home, and no Samba)

More precisely, you can go to the page [http://hostname:631/printers/]("http://hostname:631/printers/") with your browser, and read the exact name (case sensitive!) of the printer there. (Of course hostname should be the address of the Ubuntu computer)

Furthermore, that bold printer name is a link, and the link is the URL you want - hover the mouse over it.

It would be wise to use an IP address rather than the host name when configuring it into windows. That way, you don't have to installing extra software on the print server to advertise the hostname into Microsofts proprietary network browsing protocol.

---

### Post by Buuntu on 2009-08-24
I tried connecting to it on my windows computer, and it won't load, giving me "The Connection has Timed out".  

Connecting from my Ubuntu computer works fine though.  This is using my IP as the host name, since using the host name wasn't even working on my Ubuntu computer.

What am I doing wrong?

---

### Post by wojmur on 2009-08-24
Have you, by any chance, enabled a firewall on your Ubuntu? I'm not an expert in this, but that's what occurred to me might explain what you are seeing, firewall might be doing its job of hiding your Ubuntu totally. I'm not sure if Ubuntu's file / printer sharing software can automagically get the firewall to open appropriate ports/protocols.

---

### Post by Buuntu on 2009-08-24
No, I used to have Firestarter, but I uninstalled it.

---

### Post by pedro3005 on 2009-08-24
Run 'sudo iptables -L' and post the output.

---

### Post by Gazneth on 2009-08-25
Check in your Vista machine and make sure under the networking center that your Vista computer makes itself available on the network. If it is set to Public you can't see anything because it assumes you are not at a home or safe network.

---

### Post by perce on 2009-08-25
Have you done this step on your *Ubuntu computer* first? sorry if I was not completely clear about this step.

> **perce said:**
>  First, you have to go to System > Administration > Printing, then in the printers windows you go to server > settings and check the boxes "Publish shared printers connected to this system" and "allow printing from the Internet". A reboot may or may not be needed, I'm not sure about that. 


---

### Post by greenstar on 2009-09-11
Also remember to configure the firewall on your Vista box to allow network printing. Some sources may advise you to uninstall your firewall, but a better solution is to disable the firewall from starting when Vista boots up. With a desktop icon, you can load up your firewall at a second's notice. If your home network is secured, you can safely disable your firewall on your PC while at home. In the case of laptops, this is especially useful, as you can just click to enable your firewall before you connect in a public (non-trusted) location.

That's what caused my wife's Vista laptop to be unable to use network printers or even see other PCs on our network. With the firewall off, the problems were gone.

---

### Post by ningke on 2010-05-06
This problem is due to a bug in Samba 3.4.x. And it affects Windows 64bit client only. Here is the Samba discussion about it:

[http://lists.samba.org/archive/samba/2010-January/153456.html](http://lists.samba.org/archive/samba/2010-January/153456.html)

and the Bugzilla entry:

[https://bugzilla.samba.org/show_bug.cgi?id=6888](https://bugzilla.samba.org/show_bug.cgi?id=6888)

And here is another thread about the status and work arounds:

[http://bugs.launchpad.net/fedora/+bug/482836](http://bugs.launchpad.net/fedora/+bug/482836)

---

### Post by greenstar on 2010-05-13
If you're using Windows Vista, your printer should automatically show up in the add printer dialog. 

If it doesn't, see my previous post about firewalls, and also be sure that your Vista box is on the same workgroup as your Ubuntu box. If the workgroup is different, Vista will not let you easily add that printer. 

You can view & change this setting by right-clicking Computer in your start menu and selecting properties or going to Start -> Control Panel -> System and then choose Advanced System Properties from the left column. This opens the System Properties window. Then click the Computer Name tab in the System Properties window and then click change.

Once you have your PCs on the same workgroup, you should be able to easily add your shared printer. Remember that you also have to install the appropriate driver for your printer on your Windows box. Most driver installers let you install without connecting the printer which will make this even simpler.

Good luck,
Greenstar

---

