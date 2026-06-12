---
title: "ndiswrapper at login"
date: 2008-03-06
forum: Networking &amp; Wireless
---

### Post by timbosity on 2008-03-06
Alright,
 got my wireless working excellently [http://ubuntuforums.org/showthread.php?t=687290]("http://ubuntuforums.org/showthread.php?t=687290")
thanks to a little help :)
so now...

everytime I login to computer after a shutdown or restart Im doing the sudo modprobe thing and typing in my keyring password from network manager. I am guessing this can be automated to happen when I login. Briefly trawled though some threads but wasnt able to locate anything particularly useful (I said briefly...)

Anyone would like to share their knowledge?

Cheers

---

### Post by luisromangz on 2008-03-06
About modprobing ndiswrapper at boot-time, you can add the command to the /etc/rc.local file.

About the keyring thing I don't know, as I use Kubuntu and KNetworkManager, not nm-applet.

---

### Post by timbosity on 2008-03-07
Hi,

Thanks for reply.
So, looking at the rc.local script (which hasnt got anything in it), do I just add modprobe ndiswrapper at the end of it? do i need to remove the -e bit at the top beside #!bin/bash? Is there anything else i need to add /elete from that script for it to work? Im fairly new to the world of the linux so baby guidelines are necessary here...

---

### Post by luisromangz on 2008-03-07
Just add it, it should work.

---

### Post by ittiam on 2008-03-07
more easier thing would be add ndiswrapper in your /etc/modules file. Then it should get loaded in boot time. Regarding nm-applet, I use wpa_supplicant from command line so I dont know and I also use knetworkmanager sometimes, personally I feel knetworkmanager is better than nm-applet. So you could try knetworkmanager if you want.

---

### Post by timbosity on 2008-03-08
alright thanks guys. Putting ndiswrapper in etc/modules has done the trick excellently. Stil have to put in the password from the nm-applet keyring. Im still to get nm-applet to get the idea that I dont want to put in a password everytime i get on to the internet...

---

