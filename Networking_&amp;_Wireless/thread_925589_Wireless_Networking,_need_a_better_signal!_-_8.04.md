---
title: "Wireless Networking, need a better signal! - 8.04"
date: 2008-09-20
forum: Networking &amp; Wireless
---

### Post by alloftheabove on 2008-09-20
Just like the title says.  I have a computer set up in my living room that's using my linksys wusb54gv4 adapter to connect to the wireless network.  Although I can get a connection, it's not good enough for my mom to use.  The quality fluctuates between 30-50%, usually staying around 30%.  I am using xubuntu 8.04, but noticed this problem on other variants as well.  I even turned off ipv6 and edited a couple firefox config settings, and it still does not go as fast as I know it can go.  It went way faster in Windows ( of course ), but our windows vista computer got updated and rejected the adapter.  Right now, anything involving purchasing stuff is out.  Not to mention, I can get a 75% connection in the living room from my Nintendo DS to the router in my bedroom.

Is there anything I can do to boost the connection?

---

### Post by pytheas22 on 2008-09-20
There may be a different driver that you can use.  How did you install this device originally--did you have to do anything, or did it "just work" out-of-the-box?

If you post the output of this information, we can try to figure out which driver you're using a look into an alternative:
```

lsusb
lspci -nn
lshw -C Network
```

---

### Post by alloftheabove on 2008-09-20
It "just worked" out of the box.  Unfortunately the internet runs so slow on it I can't post commands from there.  And I don't have front-side usb ports on this computer, so I can't just transfer txt files over.  This kind of problem makes everything tough for me lol.

EDIT:  When I had puppy linux running on that computer, it recognized the ralink chipset inside my adapter.  What would be the specific code to find the exact chipset?

---

### Post by alloftheabove on 2008-09-20
Neither lspci nor lsusb provide information on the chipset for the adapter.  However I do know that it is using IEEE 802.11g.

---

### Post by alloftheabove on 2008-09-21
bump.

---

### Post by pytheas22 on 2008-09-21
Without knowing the exact chipset it's hard to make a recommendation on which driver would work better.  But if you have an Ralink chipset, probably installing one of the legacy drivers from [serialmonkey]("http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads") would improve performance.  Ubuntu by default uses the "next-generation" Ralink drivers (also from serialmonkey), which in some cases are not as stable yet as the tried-and-true legacy drivers.

To figure out which chipset you have, run the command 'lsusb' with the wireless card plugged in.  You should get output that looks something like:
```

Bus 005 Device 008: ID **07d1:3c03** D-Link System 
```

(The line above is for my DWL-G122 card, which has an Ralink rt73 chipset.  Notice that the lsusb line for your card may not necessarily mention what exactly the device is.  If there are multiple entries, you'll just have to guess which one is which.)  To find the chipset of your card, google for the PCI ID number--that's the XXXX:XXXX number (in bold above).  It should be relatively easy that way to figure out which driver you need.

If you do indeed find that you have an Ralink chipset that's supported by the legacy drivers, let me know and I'll tell you how to install them.

---

### Post by alloftheabove on 2008-09-21
Id of the device shows as 13b1:000d.

---

### Post by pytheas22 on 2008-09-21
Google suggests that your card has an rt2500 chipset.  You have two options to get it working better.  One is to follow [this guide]("http://blog.eksfiles.net/2008/01/05/using-the-linksys-wusb54g-v1-or-v4-with-ubuntu-gutsy/"), in order to get it working under ndiswrapper.  This should work fine and may be a little easier, since you're working without any kind of Internet connection on the machine in question right now.  Note that if you follow that guide, you should run these commands first:
```

sudo -s
echo 'blacklist rt2500usb' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2500pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt61pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2400pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00lib' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00usb' >> /etc/modprobe.d/blacklist
exit
```

They'll blacklist the existing Ralink drivers, which is necessary before ndiswrapper can take effect.

The other method is to use the serialmonkey drivers.  It will be a little more complicated since you don't have any Internet connection available, but it's still possible to pull off.  You will need first to download [this file]("http://ubuntu.secs.oakland.edu/pool/universe/r/rutilt/rutilt_0.16-0ubuntu1_i386.deb"), [this file]("http://rt2x00.serialmonkey.com/rt2500-cvs-daily.tar.gz") and [this file]("http://rt2x00.serialmonkey.com/rt2570-cvs-daily.tar.gz"), then transfer them (using a CD or USB drive or something) to your Ubuntu computer.  On your Ubuntu computer, copy those three files to your desktop.

You will also need to put your Ubuntu live CD in your drive, go to System>Administration>Software Sources, and, under the "Ubuntu Software" tab, make sure that the box to enable use of your CD as a software repository is checked.  Then close the window; if you're asked about reloading the software list, say yes.

Now, on Ubuntu, run these commands (remember that case matters):
```

cd ~/Desktop
sudo apt-get update
sudo apt-get install build-essential
tar -xzvf rt2500*
cd rt2500*
cd Module
make
sudo make install
cd ..
cd ..
tar -xzvf rt2570*
cd rt2570*
cd Module
make
sudo make install
sudo -s
echo 'blacklist rt2500usb' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2500pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt61pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2400pci' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00lib' >> /etc/modprobe.d/blacklist
echo 'blacklist rt2x00usb' >> /etc/modprobe.d/blacklist
exit
```

Finally, on your desktop you should see an icon to install a program named Rutilt.  Double-click on the icon and an installer open.  Run it.

Then reboot your computer.  After you reboot, you won't be able to use Network Manager to connect to your wireless network as you did before.  Instead, you have to use Rutilt, which will be under the System>Administration menu.

Let me know how this goes.  There are obviously a lot of steps and some things may not go as planned, but in that case we can work around them.

Also, if there is any way for you to get this computer online, even with a slow download speed, let me know, as the instructions for compiling the rt2500 driver could be greatly simplified if you could get online in some way.

---

