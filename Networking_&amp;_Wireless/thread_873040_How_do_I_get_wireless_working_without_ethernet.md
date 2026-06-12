---
title: "How do I get wireless working without ethernet?"
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by Luther11 on 2008-07-28
My roommate recently got a new desktop computer, and I've got him set up with a dual-boot Vista/Ubuntu 8.04.1. The problem is, his computer is at the other side of the house, and it was much cheaper for him to get a wireless card than to get enough network cable to reach my router. Here's where I stand now:

The card is a "Dynex Wireless G Desktop Card" (no model # on the box). According to [this page]("http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_c-f/#d"), I should be able to use bcmwl564.sys from the CD with ndiswrapper.

I can use a USB stick to transfer files if need be.

I need to know where to get the necessary .deb files, along with dependencies, how to install them, and how to plug in the driver from the CD.

Thank you for any help.

---

### Post by Neobuntu on 2008-07-28
If you don't have an (inexpensive) wireless Bridge, otherwise known as a WiFi "game" adapter for game consoles (and it goes into their Ethernet plugs) then you could use a computer (like a working laptop with **Wifi AND Ethernet**) with what is normally known as ICS (Internet Connection Sharing). This of course, requires an (Ethernet card or NIC) output (with a **crossover cable**) to your wired Ethernet port (Assuming your target computer has a wired Ethernet device or can add one easily) **and** the other (second) port somehow(by WiFi) getting the Internet.

So, if you had access to one of those "game adapters". It would pick up WiFi Internet from a wireless router (which you have) and send it to it's wired Ethernet port (thus bridging one to the other.) Thus you have made a wired input (from wireless) for your install. Obviously you just set the port (if not DHCP) for Internet wired on your target install box. 

Without a "game adapter/bridge", if you have a spare computer (with the two ports, presumingly one with WiFi) you either turn on ICS on a spare Windows computer and use it as a temporary bridge or you set up your Linux box. You could simply use the Firestarter firewall front-in, as it has a simple wizard to setup connection sharing. For simplicities sake, don't try to do DHCP (wired to target install), with firestarter, just set a static address on the wired LAN (shared Internet) out.

How's that?

---

### Post by Luther11 on 2008-07-28
OK. I've downloaded Firestarter. I've plugged an ethernet cable between my laptop (which has WiFi) and the desktop. In the wizard I set the internet device to wlan0. I check the box for "Enable Internet connection sharing". I set the local network device to eth0. I then check "Start firewall now". When I click Save, it fails to start the firewall, saying "The device eth0 is not ready."

The desktop shows a wired network connection, but that's only to my laptop, so I can't do anything with it.

I don't really know what I'm doing, so I'm sure I'm missing some step. Is there anything else I can do?

---

### Post by CarlosNYB on 2008-07-28
I use Hardy Heron, and I burned an iso of the most recent version.  After installing linux, I went to SYSTEM>>ADMINISTRATION>>SYNAPTIC, and then I put in the CD, and I made sure in SYNAPTIC on the repositories the CD was available, refreshed the repositories, and enabled ndisgtk, and SYNAPTIC installed everything needed from the CD.  Then in SYSTEM>>ADMINISTRATION there was an applet for Windows Wireless Drivers.  I opened it and put in my wireless device install CD and pointed to a directory and then everything was fine.

---

### Post by sandeepy on 2008-07-28
> **CarlosNYB said:**
> I use Hardy Heron, and I burned an iso of the most recent version.  After installing linux, I went to SYSTEM>>ADMINISTRATION>>SYNAPTIC, and then I put in the CD, and I made sure in SYNAPTIC on the repositories the CD was available, refreshed the repositories, and enabled ndisgtk, and SYNAPTIC installed everything needed from the CD.  Then in SYSTEM>>ADMINISTRATION there was an applet for Windows Wireless Drivers.  I opened it and put in my wireless device install CD and pointed to a directory and then everything was fine.

This is a first for me ... seems to be very cool !! thanks

---

### Post by Luther11 on 2008-07-28
> **CarlosNYB said:**
> I use Hardy Heron, and I burned an iso of the most recent version.  After installing linux, I went to SYSTEM>>ADMINISTRATION>>SYNAPTIC, and then I put in the CD, and I made sure in SYNAPTIC on the repositories the CD was available, refreshed the repositories, and enabled ndisgtk, and SYNAPTIC installed everything needed from the CD.  Then in SYSTEM>>ADMINISTRATION there was an applet for Windows Wireless Drivers.  I opened it and put in my wireless device install CD and pointed to a directory and then everything was fine.

Alright, I've done this, and it seemed to install smoothly, but there's still no sign that it recognizes any networks. Beyond that, I can't figure out what the status is. :confused: I've turned off the wireless encryption for now until I can figure this out.

---

### Post by Ayuthia on 2008-07-28
Since it is a card instead of a USB device, you might want to be sure that you are looking for the right driver.  You can check this by opening up the Terminal and typing:
```
lspci -nn
lshw -C network
```
For the first command, you are looking for a device that is called Network Controller or Ethernet Controller.  There could be more than one if that computer has a wired and wireless card in it.  If you are not sure you can report back what you find.

For the second command, it will tell you if the card is UNCLAIMED or DISABLED or it might be found.  It will also help you determine what your wireless card is called.

---

### Post by Neobuntu on 2008-07-28
> **Luther11 said:**
> OK. I've downloaded Firestarter. I've plugged an ethernet cable between my laptop (which has WiFi) and the desktop. In the wizard I set the internet device to wlan0. I check the box for "Enable Internet connection sharing". I set the local network device to eth0. I then check "Start firewall now". When I click Save, it fails to start the firewall, saying "The device eth0 is not ready."

The desktop shows a wired network connection, but that's only to my laptop, so I can't do anything with it.

I don't really know what I'm doing, so I'm sure I'm missing some step. Is there anything else I can do?

If your going to continue to set up a temporary (wireless; remote) bridge to get full Internet, you have to set up your Ethernet port correctly for sharing and then it will stop saying "The device eth0 is not ready." Let's see... assign a static port on the Internet shared eth0 as like 192.168.0.1 and no gateway (because it is the gateway) and to start at boot. That should do it. Then your notebook should work like a (bridge WiFi to wired) charm.

BTW, (cut and paste able) > sudo /etc/init.d/networking restart...will restart you networks after changing settings (if you don't want to just reboot).

If you (set as above) to 192.168.0.1 then simply make your static Ethernet on your target (remote) computer 192.168.0.10 and restart it's network (or reboot. Don't forget to set the firewall (or temporarily turn it off with Firestarter) on your target box too (and use a **cross over cable**).

Also, you'll want to set the DNS as your actual wireless router address (192.168.1.1 perhaps). Plus, you may need your actual wireless router to be set for 192.168.1.1 if not already(note the next to last "1") so that it will not interfere with your temporary sub net(bridge.) 

Sorry, networking is complicated on any system. You would think, you could just run DHCP(slower than this above; to install) like Windows does; with ICS but there are advantages (AKA reasons) why you'd prefer a static address (if permanent ICS.) If you have never setup a static address before then you may have to review how it's done. 

A game adapter (the "B" ones are cheap) is the fastest solution. It's cool; because they are effectively driver/module-less (because **Wired** Ethernet usually sets the driver automatically; without any work) but they require a power supply for their external unit. So, if your using a laptop instead, you have to deal with the details.

Remember, if you are going from computer to computer directly via two wired NICs (Ethernet cards or ports) then they normally go into a router and that's **NOT** what you're doing with the bridge. Use a cross over cable for direct connection. If you hold the two ends in the same orientation, the (Eight) "colors" (some may be striped) of the wires seen in the clear (RJ45) plugs are reversed. If not and if they're the exact same, it's a regular patch cable, not a cross over.

---

### Post by Luther11 on 2008-08-01
Well, I've been busy with other things for the last couple of days, but now I'm back.

I decided to just move his computer into my room and plug the ethernet in. It was a choice between trying to learn something new about how to install drivers properly and getting off my *** and doing some lifting. Here's how it went:

First, I turned on the computer and opened Firefox. The internet looked fine from there. Then, I opened up the Driver Manager. It showed the wireless driver as being "In use" even though the box was not checked. I tried checking the boxes for both the wireless and video drivers, and both times it told me it could not reach the site to fetch the firmware. I decided the Driver Manager was broken from all my previous fiddling with it, and I did a clean reinstall. After that, everything went pretty smoothly. I installed the media codecs, including DVD playback. Then, I moved the computer back to where it was, turned it back on to make sure it was still receiving the wireless signal, and switched it off.

Anyway, thank you guys for the effort.

---

### Post by Neobuntu on 2008-08-01
You're welcome. Thanks for the considerate "thank you".

Lesson #1 This is why I say an install, can't be too fast or easy.

Lesson #2 You are so correct. It's far wiser and faster to do non software solutions and use physical solutions, especially with networking. That goes for any system. You may rather enjoy the simple benefits of another Wireless device. One that just (automatically) works without any driver fiddling.

---

