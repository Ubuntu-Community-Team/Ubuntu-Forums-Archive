---
title: "bluetooth + 7.10 + Samsung E900"
date: 2008-04-22
forum: Networking &amp; Wireless
---

### Post by yeleek on 2008-04-22
Hi,

Been trying to get files sent from my phone to my pc.  Followed the bluetooth guides here.

Kept on getting errors 
Couldn't display "obex://[...]".
Check if the service is available.

Someone recommended blueman [http://blueman.tuxfamily.org/](http://blueman.tuxfamily.org/) which does let me send files from PC -> phone however when sending files from phone to pc.  The phone can't get a service list and when trying to browse the phone from the blueman app the phone connects and disconnects straight away.  Any ideas?
[http://blueman.tuxfamily.org/forum/viewtopic.php?f=5&t=37](http://blueman.tuxfamily.org/forum/viewtopic.php?f=5&t=37)

And yes i do have gnome-vfs-obexftp installed

Thanks

---

### Post by scorp123 on 2008-04-22
Do you have the **gnome-bluetooth** package? If yes you need to activate the **gnome-obex-server** program or else your PC will not be able to receive files from your phone. You will find an icon for this program in your menus if it is correctly installed:

Applications > Accessories > Bluetooth File Sharing

Once activated there should be a new icon in your system tray (usually the top right corner): a blue pyramid emitting blue radio waves (it looks a little like the symbol for Earth in the "Stargate SG-1" TV show :D )

Once this program is running your PC is able to receive files via Bluetooth.

---

### Post by yeleek on 2008-04-22
Am afraid already tried that - phone connects and disconnects straight away when trying to search for services list.  Tried enabling network etc in case that did it in preferences.  No joy.

Is this phone not supported?  Could that be the issue?

Thanks

---

### Post by scorp123 on 2008-04-22
> **yeleek said:**
>  Am afraid already tried that - phone connects and disconnects straight away when trying to search for services list.  And the filesharing service was running in that moment? e.g. you saw the blue pyramid icon? (sorry if this is a stupid question).

> **yeleek said:**
> Tried enabling network etc in case that did it in preferences. That's "PAN" = Personal Area Networking. Some PDA's can do that. Imagine you have a laptop that connects to your company's VPN and there is no client for your PDA. So how can you sync your PDA with your company's network? Via "PAN": Your laptop activates the service and your PDA hops on the TCP/IP connection via Bluetooth, thus using your VPN-connected laptop as a proxy ... sort of. But to make use of this feature the client device (e.g. a PDA) has to support this feature too. Most phones don't support it, as far as I know. So that's not really related to your problem here.


> **yeleek said:**
>  Is this phone not supported?  Could that be the issue?  The question is rather: Does your phone support it? Some phones have non-standard Bluetooth stacks, e.g. they don't implement all features. Apple's iPhone comes to my mind -- the Bluetooth stack there is seriously crippled in every way. 

I myself have a Samsung SGH-G800 and I had to fully "trust" my PC so I don't have to type PIN codes all the time.

What if you delete the bonding between your PC and your phone and then re-establish it again and then tell your phone to fully trust your PC?

---

