---
title: "Belkin USB Wireless G Adapter."
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by yogiman_uk on 2008-03-24
Hi All.

Until recently I had a Belkin Wireless G Adpter (Sorry don't know what version) it worked perfectly with  Ubuntu, however being a softy I gave the USB adapter to my nephew along with a copy of ubuntu installed on a new machines and he works away quite happy.

Now the problem.....

I replaced my old adapter with a new USB Wireless G adapter from Belkin, (Version 5) and it doesn't even get detected when I plug it in.

Also got hold of a Version 3 Adapter and although detected it says it does not support WPA/PSK and I am unable to tell it other wise.

Now..... both of these were plugged into a laptop that had an installed version of ubuntu that worked with the old adapter.... strange.

I know you are possibly going to tell me that Belkin keep changing there chipsets....

So has anyone got any help they can give me....  I am rather puzzled.

Thanks


Yogiman!

---

### Post by SeePU on 2008-03-25
I am not sure of the chipset for a ver. 5 but the version 4 uses the zydas chipset and is supported (built into the kernel in more recent Linux OS versions - i.e. more recent kernels).   

To find out the chipset in your particular usb adapter, I suggest a couple of commands:

lsusb
and
dmesg

Some info might be presented that helps.   It's possible that you need to do some tweaking in order to get it to work.

---

### Post by yogiman_uk on 2008-03-25
Hi

Thanks for the reply.

Been doing some Sherlock work. Found out the following.

Additional Information.

I have had 3 of these USB adapters and found that as usual Belkin can't leave well alone.

The Adapter chipsets are as follows:-

				
1xxx		                     K7SF5D7050		Unknown	Unknown.
					
2xxx		                     K7SF5D7050A	Realtek 2500 	Unknown.
					
3xxx		                     K7SF5D7050B	Realtek 73	                     Detected only seems to support WEP not WPA/PSK
					
4xxx		                     RAXWN4501H	ZyDAS 1211B	Detected and works perfectly under Fisty Fawn and Gusty using WEP and WPA/PSK.
					
[COLOR="Red"]5xxx		                     K7SF5D7050E	Realtek 8187B	Not Detected.[/COLOR]

I currently have a version 5xxx of this adapter (marked in red).

Checked Realtek's support site and there is no Linux driver, deb or otherwise.  Should rename themselves RealUseless.

I found some modified version of a Realtek driver on someones site but I am a little reluctant to try it.

Does anyone know if the new Ubuntu Beta supports this chipset?

Thanks

Yogiman!

---

### Post by james_vanb on 2008-03-25
For what it's worth, I'm submitting this reply using the Belkin USB G Wireless Adapter Version 3000 with Xubuntu 7.10.  Only way I could get it to work was using the original install cd and ndiswrapper.  If you have the cd, Process is as follows:

Unplug adapter before you boot.

Install ndiswrapper through Synaptic.

Open terminal.

Remove the following drivers using these commands (If not using Xubuntu, substitute commands as appropriate):

sudo modprobe -r rt2500usb
sudo modprobe -r rt73usb

'm not sure that this actually removes the drivers, but after 3 weeks of farting around with them it made me feel better.

Blacklist rt2500usb and rt73usb by opening text editor (My default is mousepad) as follows:

sudo mousepad /etc/modprobe.d/blacklist

add rt2500usb and rt73usb to end of list, save and close.

REBOOT

This is where the guides I was following failed. Blacklist doesn't work until you reboot. If you don't, the wrong driver will be associated.

On your desktop, open "Home" - right click in an open area and create a file - I called mine "Belkin".
Insert the install cd. Open and navigate to the driver file under XP. there will be 3 files. Copy all 3 files to the file you created under "Home" by dragging and dropping. The drivers will not load directly from the cd.

Now install the driver you just copied with the following :

sudo ndiswrapper -i /home/(your user name)/Belkin/rt73.inf

Insert the wireless adapter.

Now issue the following commands:

sudo depmod -a
sudo modprobe ndiswrapper

I think these create the module. Now edit modules to load ndiswrapper when you boot as follows:

sudo mousepad /etc/modules

Add "ndiswrapper" (without quotes) to the end of the list.

Establish alias with following command:

sudo ndiswrapper -m

Reboot

You should now have a connection. Roaming mode works sporadically, so I manually configure. Left click on the network manager at the upper right corner and enter manual configuration. Open wifi properties. Untick "enable roaming". Next to Network name, you should be able to click on the arrow and a drop down will show available networks, click on yours. Set Password type to WPA personal. Set Configuration to Automatic configuration (DHCP). I don't use WEP yet, but if you do, you may have to enter your password in Network password.

Good luck - Hope it works.

---

