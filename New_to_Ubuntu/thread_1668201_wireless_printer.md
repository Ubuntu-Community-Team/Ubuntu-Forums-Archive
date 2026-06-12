---
title: "wireless printer"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by Billisnice on 2011-01-16
I have a brother hl-2170w wireless printer connected to my usb port on a ubuntu 10.04 box. How do i configure a windows xp wireless laptop to use the printer on the ubuntu box?

I have a linksis WRT54GS router connecting both to the net...

Thanks...driving me nuts...lol

---

### Post by taseedorf on 2011-01-16
You must share the printer via samba.

Install samba via synaptic.....and then, go to printers in system preferences and share it.  Add the printer on your XP laptop as a network printer using the address ...mmmmm... //IPOFPRINTERMACHINE/printername   I think!

Or try..... smb://username:password@yourhosthere/printername

or search for the correct url to add for the printer share, or XP may just find it..

Otherwise, connect your printer to the wireless router (no need to have it hardwired to your machine... and then share it via your router....add it on each machine.

---

### Post by thenickrulz on 2011-01-16
Yeah try Samba that should work if u set it up right.. it worked for me when i did it..:D

---

### Post by Billisnice on 2011-01-16
i installed samba, but the other stuff is greek...Any clarification?  thanks..

---

### Post by walt.smith1960 on 2011-01-16
It's a networked wired/wireless printer.  There's no need to use either Samba or a USB cable. If the printer is near the router, run a cat 5 cable from a router LAN port. If the printer is not near the router, set it up as a wireless printer.  I have 2 networked Brother MFDs. One is wired, one is wireless.  If it were me, I'd try the easiest first. After either plugging in a network cable from the router or configuring the wireless connection:

system -> administration -> printing -> add -> network printer and wait a couple minutes to see it the printer is found.  If that doesn't work, you can look here--Linux drivers and instructions  [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2170W](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#HL-2170W)

One thing to be aware of with Brother.  When I installed the MFC-6490CW, it has a wireless network connection...  The software installed it as a USB printer...oops.  I changed the URI from usb://......  to "socket://ip address" and that worked. This is found by going to printers as above, right clicking the printer icon and look at properties.

I hope this is helpful to you.  At least Brother does support Linux.  Canon & Lexmark among others---not so much.

---

### Post by Billisnice on 2011-01-16
I got it work with samba. But, only if the ubuntu puter is on will it work. I see the usb in properties...i will try to get a cord sometime and run to my router...sound easier...

---

### Post by walt.smith1960 on 2011-01-16
It should be easier and you can print from as many computers as you want. Also the printer is not hooked up to a computer so no computer except the one with the print job needs to be powered up. I'm pretty sure you can only use one connection though, so you can't have both USB _and_ a network connection at the same time.

---

### Post by Billisnice on 2011-01-19
I got a cable and connect directly to my wireless router and the computer will not recognize it. My router does not have a lan female adapter. Any other help?

---

### Post by walt.smith1960 on 2011-01-19
> **Billisnice said:**
> I got a cable and connect directly to my wireless router and the computer will not recognize it. My router does not have a lan female adapter. Any other help?

What make & model is your router?  Not having any LAN ports seems unusual.  Did you install the software from Brother's web site? You also indicated the printer supports wireless printing.  Did you try that? I'm assuming your router supports wireless networking? I'd guess you'll need the Brother software for wireless configuration. If your Ubuntu is 64 bit you may have to install from the command line and use the --force switch, I got an error when I tried to install my MFD-6490CW using the Ubuntu Software Center.

---

### Post by walt.smith1960 on 2011-01-19
> **Billisnice said:**
> I got a cable and connect directly to my wireless router and the computer will not recognize it. My router does not have a lan female adapter. Any other help?

What make & model is your router?  Not having any LAN ports seems unusual.  Did you install the software from Brother's web site? You also indicated the printer supports wireless printing.  Did you try that? I'm assuming your router supports wireless networking? I'd guess you'll need the Brother software for wireless configuration. If your Ubuntu is 64 bit you may have to install from the command line and use the --force switch, I got an error when I tried to install my MFD-6490CW using the Ubuntu Software Center.  I wonder if having the Samba installation is causing confusion?

---

### Post by walt.smith1960 on 2011-01-19
Duplicate

---

### Post by walt.smith1960 on 2011-01-19
Duplicate

---

### Post by walt.smith1960 on 2011-01-19
Duplicate  Proxy error 502-I think

---

### Post by Billisnice on 2011-01-20
i finally got it to work...Thanks for the help...It was a loose cable to the router.

---

### Post by wojto on 2011-08-05
Hi,

I came up with a sort of tutorial to configure the HP Laserjet p1102w wireless(wifi) printer, connected with USB cable, as well over wifi. I am currently usig Ubuntu 11.04, but it shoud work under older distributions too.

Connecting over USB

Is no big deal. Just plug and the system should configure it automatically. If not install the newest version of HPLIP```
sudo apt-get install hplip hplip-gui
``` and then simply add a new printer from MENU System > Administration > Printing or with Terminal ```
sudo hp-setup -i 
```

Connecting over wifi = wirelessly

Wireless printing uder ubuntu is a little tricky. The manufacter mostly supports it for Windows, on the installation CD, but it can work on the Linux the same way. Most of the job is to configure the ad-hoc connection. Turn on your printer and on  and make a sweep for wireless networks. You shoud find something like HP432CBA. Try to connect to it, but if will probably fail.

Therefore you have to edit this network : Edit connections > Wireless > [choose the network], click Edit and select the IPv4 Settings. Set Method to =Shared to other computers=, Save and try to connect again. It should work now.

Now press the button (x) on your printer for few seconds and wait until it prints the configuration page. Remember the printer cant be in sleep mode, use (I) to wake it. On this configuration page find the IPv4 address. Open your browsver and put the address in there. You should see the printers server page. If yes, it is almost done.

Now we can add the printer. At first install hplip-gui, if isnt installed on your machine. ```
sudo apt-get install hplip-gui 
``` Then open System > Administration > Printing, click to add a new printer, select =Find network printer=, enter the IPv4 address into the Host column. It would find Jetdirect, click foward, choose or download a proper driver and print a test page.

Hope that it helped.

---

