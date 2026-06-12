---
title: "Bluetooth DUN for Verizon EVDO connection"
date: 2008-09-15
forum: Networking &amp; Wireless
---

### Post by jvolzer on 2008-09-15
Newbie question here.  I'm exploring Ubuntu for the first time, not at all familiar with Linux.  I'm impressed at how quickly I could download and install the OS and have it automatically recognize my hardware, network, etc.  I'm installing this to a laptop and one of my primary uses will be to get on the Internet using my Bluetooth-enabled Verizon phone the VX9100 (env2).  I can successfully do this under Windows by pairing the phone then using DUN via bluetooth through a network connection configured to use the virutal serial ports that were created once serial service was installed by the bluetooth manager.  Now I'd like to do the same thing under Ubuntu.  I have Ubuntu 8.04 / GNOME 2.22.3 -- all default install from CD.

I've been able to successfully pair the phone.  I can connect and browse to transfer photos, etc.  I went into Bluetooth Preferences and found the Services tab and enabled "network service" and "serial service".  Next, I went into Network settings and from connections went to properties for the Point to point connections.  From here I clicked "enable this connection.  Here's where I get stuck.  The only way to get a box to allow a number to be dialed (which should be #777 for EVDO)is to set the Connection Type for "Serial Modem", so I've done this and entered the phone number (#777) the username (myphonenumber@vzw3g.com) and password (vzw).  But then I'm not sure what modem port to choose.  I see /dev/modem, /dev/ttyS0 through S3.  I'm not sure which port is the one that links back to the Bluetooth service for my phone.  No matter which one I choose, it hangs for a minute after clicking OK, then for a few mintues back at the main connections tab.  Eventually I can click properties again, but I find it set back to "PPPoE" instead of retaining the serial setting I selected previously.  

I'm guessing that there should be some new device shown in that list for a virtual BT serial port or something, no?


It's a bit frustrating because each time I try to make a change, the network settings window freezes for a minute or two before I can do anything, then hangs again when trying to open the Network Settings again later.  Even if I do get the right settings, I'm not sure how to tell it to connect using that particular group of settings.

Can anyone help?  Am I on the right track?  If you provide any hints or suggestions, please remember that I'm brand new to this environment.

---

### Post by jvolzer on 2008-09-18
Can anyone help with this?

---

### Post by jvolzer on 2008-09-21
I could really use some help with this.  Does anyone have any ideas? Even if not familiar with Verizon's connection it seems to me that it would be helpful just to be able to get the BT serial ports to show up as devices to connect to when setting up a dial up connection.  I currently see tty/modem,  along with S0 through S3, none of which seem to represent the serial connection that should be available after connecting the Bluetooth phone.  I set Serial as one of the services in the BT manager, but that doesn't seem to change anything.  Ideas?  Am I even in the right place?

---

### Post by webbhawk on 2008-10-26
I feel your frustration sir. I've been trying to get DUN working on ubuntu since feisty fawn. I've tried first on my old treo 650 and more recently on my HTC 6800 (mogul)

I've seen one or two wiki's linked on the forum but I can't remember how to get to them. I'm hoping that the new release (8.10) will have some better mobile phone support. 

I don't know why there isn't more support for this. Technology is going more towards mobile devices and Microsoft is doing a much better job in this field right now than Linux. I love Linux and Ubuntu, but if they don't get on top of this technology soon I think I will be switching back to windows permanently just for the convenience. Because "IT JUST WORKS".

---

### Post by jvolzer on 2008-10-28
Webbhawk,
I've finally had some success with this!  I've not had time to post a comprehensive list of what I did, but the basics are here: [http://forum.eeeuser.com/viewtopic.php?id=44436](http://forum.eeeuser.com/viewtopic.php?id=44436) and involve downloading Gnome-PPP and Blueman ([http://www.ubuntu-eee.com/wiki/index.php5?title=How_to:_Connect_to_the_Internet_via_Bluetooth](http://www.ubuntu-eee.com/wiki/index.php5?title=How_to:_Connect_to_the_Internet_via_Bluetooth))

---

### Post by johnh123 on 2008-10-30
> **jvolzer said:**
> Can anyone help with this?

This worked for me - sprint mogul


[http://forum.ppcgeeks.com/showthread.php?t=29134](http://forum.ppcgeeks.com/showthread.php?t=29134)

---

