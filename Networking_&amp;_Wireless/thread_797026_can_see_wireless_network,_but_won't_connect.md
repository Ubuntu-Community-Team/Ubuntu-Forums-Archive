---
title: "can see wireless network, but won't connect"
date: 2008-05-16
forum: Networking &amp; Wireless
---

### Post by bobdobbs on 2008-05-16
I installed Hardy Heron about a week ago.
To my frustration, I couldn't connect to my wireless network with my
broadcom network card, so I went out and bought a USB network card.
I plugged it in, and it just worked. 
I could see the network, and was able to connect to the net!
Yay!

But having a clumsy looking USB network card poking out the front of my PC
wasn't quiet on, so I enabled the patent-encumbered hardware drivers for my broadcom-based network card. I also allowed ubuntu to install drivers for my nvidia card.
Reboot...

Oh crap!
The display had a resoluion of 640x480, and couldn't be reconfigured.
So, I uninstalled the nvidia-drivers.
I can deal with that later...

But I'm also now cut off from the network!
When I use the networking applet in gnome, it shows me my home network,
but it winds around for ever, refusing to connect.
Doh.

So, I uninstalled the broadcom drivers and went back to use of the USB wireless networking card.

Alas, alack!
Now, the applet will show me my home network, but won't connect.
When I select it, it asks for my password to access the default keyring.
I provide the password, and the icon begins to whirl....
... but it just keeps winding, and never stops.
And I can't get onto the network.

What is happening?
How can I get onto my network, and back on the net?

---

### Post by Ayuthia on 2008-05-16
> **bobdobbs said:**
> I installed Hardy Heron about a week ago.
To my frustration, I couldn't connect to my wireless network with my
broadcom network card, so I went out and bought a USB network card.
I plugged it in, and it just worked. 
I could see the network, and was able to connect to the net!
Yay!

But having a clumsy looking USB network card poking out the front of my PC
wasn't quiet on, so I enabled the patent-encumbered hardware drivers for my broadcom-based network card. I also allowed ubuntu to install drivers for my nvidia card.
Reboot...

Oh crap!
The display had a resoluion of 640x480, and couldn't be reconfigured.
So, I uninstalled the nvidia-drivers.
I can deal with that later...

But I'm also now cut off from the network!
When I use the networking applet in gnome, it shows me my home network,
but it winds around for ever, refusing to connect.
Doh.

So, I uninstalled the broadcom drivers and went back to use of the USB wireless networking card.

Alas, alack!
Now, the applet will show me my home network, but won't connect.
When I select it, it asks for my password to access the default keyring.
I provide the password, and the icon begins to whirl....
... but it just keeps winding, and never stops.
And I can't get onto the network.

What is happening?
How can I get onto my network, and back on the net?

Have you checked to see if it is still trying to use your Broadcom card?  You can check and see if the firmware is still there by going to the Terminal and checking:
```
ls /lib/firmware/b43*
```
If it does not return anything, then the firmware is no longer there.  If it is still there, then there is a good chance that your computer is trying to use your Broadcom card.

Just out of curiosity, can you tell me your Broadcom card info?  Go to the terminal and type lspci -nn.  Look for the line with Broadcom and find a number that looks like [14e4:43xx] rev 01.  Can you give me that number with the rev?

---

### Post by bobdobbs on 2008-05-16
Hi Ayuthia.
Thanks for jumping in.

ls returns two directories -
/lib/firmware/b43   which appears to have many *.fw files. And,
/lib/firmware/b43legacy

So, there is firmware there. 

lspci says that the card is a:
"Broadcom Corporation BCM4318 [Airforce One 54g] 802.11g Wireless LAN controller...

I know that this card can be made to work Ubuntu. But I guess, at the moment I'd just like the network up no matter which card I'm using.

What do you think could be happening here?

---

### Post by Ayuthia on 2008-05-16
> **bobdobbs said:**
> Hi Ayuthia.
Thanks for jumping in.

ls returns two directories -
/lib/firmware/b43   which appears to have many *.fw files. And,
/lib/firmware/b43legacy

So, there is firmware there. 

lspci says that the card is a:
"Broadcom Corporation BCM4318 [Airforce One 54g] 802.11g Wireless LAN controller...

I know that this card can be made to work Ubuntu. But I guess, at the moment I'd just like the network up no matter which card I'm using.

What do you think could be happening here?

I have seen a lot of people having trouble with using the native Linux Broadcom drivers with your card.  They have had more success with NDISwrapper.  The easy way for now is to move those b43/b43legacy directories into your home directory.  What this will do is remove the firmware, but not delete the files (in case something strange happens and you want them back):
```
sudo mv /lib/firmware/b43 $HOME
sudo mv /lib/firmware/b43legacy $HOME
```
You will then want to restart your computer.  That should bring you back to where you were before.

EDIT:
I forgot to explain what happened.  The purpose of b43-fwcutter is to extract firmware out of the proprietary drivers.  If you remove the b43-fwcutter package, the firmware that it extracted is still there.  That firmware is what the b43 drivers need.  Since those files were still there, the driver remained active.

---

### Post by bobdobbs on 2008-05-16
Thanks.

I became aware of the the need for the b43-cutter software along with the firmware, when I installed Gutsy a while back.
It was pretty frustrating:
In order to install the software to get my network connection going, 
I first required a network connection!

Of course, this is the price to pay for buying a pc with components that have proprietry drivers. I don't blame ubuntu, but it was frustrating nonetheless.

My situation at the moment:
I'm back online.

I selected the network applet, and gave it the details of my network manually. It found the network and asked me for the pass and the level of encryption. I got the encryption type wrong the first time, but I got it 
the second time.

The network connection got established.
It disconnected once, but I repeated the process, and I've been up for about an hour.

Again, thanks.

Now to get the video card set up...

---

### Post by bobdobbs on 2008-07-17
update - 

I find wireless network in ubuntu a right pain in the rear.

nm-applet won't hold wireless connection settings. It's not suitable for a desktop computer.

There seems to be no graphical tool that will keep and hold wireless connection settings. 

I've been kindly pointed to configuration files that must be edited by hand.
But even these, when set correctly will not allow wireless connection information to persist after a reboot.

I think that this needs to be fixed, if ubuntu is to appeal to newcomers to linux, who won't want to fix things by hand after coming from a windows environment where wireless connection is a much simpler matter.

---

