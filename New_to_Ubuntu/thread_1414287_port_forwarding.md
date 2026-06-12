---
title: "port forwarding"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by Christopher Newtoit on 2010-02-23
Hi

I need some help port forwarding with Transmission. I am confused how to open the port on my router and on my computer. I can get ip adresses using the "ifconfig" command prompt, can open the port for bittorrent(same as Transmission?) with Firestarter, but I still seem to have trouble getting good connectivity peer to peer.

Thanks

---

### Post by The Cog on 2010-02-23
In Transmission, under Edit->Preferences->Network, look at the "Port for incoming connections". This is the TCP port you need to forward through your router to your IP address. It might help to enable UPnP, depending on your router.

You will also need to configure firestarter to allow that port through, if you have installed firestarter. I don't know how to do that - I have never looked at firestarter.

You can also verify that the PC is listening for incoming connections with this command (which it should be whenever you start transmission):
```
netstat -lnt
```

---

### Post by lovinglinux on 2010-02-23
I recommend reading the [BitTorrent optimization and troubleshooting guide](http://ubuntuforums.org/showthread.php?t=1259923). I use Deluge as an example, but the principle is the same for any client.

---

### Post by laceration on 2010-02-23
Just switch to Deluge and you will probably not have to mess with any of this.

---

### Post by wojox on 2010-02-23
Is this using UPnP or Manual using a static IP? What are your network speed test numbers?

---

### Post by Jeff Anthony on 2010-02-24
Your router administration panel will likely be available via your browser at 192.168.1.1 or 192.168.2.1. You may have to enable port forwarding to the port matching Transmission's settings The Cog described.

---

### Post by Christopher Newtoit on 2010-02-25
thanks for all the help.  Think I've got it working now, though not totally sure.

---

### Post by sevenX on 2010-03-14
I was having the same problem my port keeps saying its closed.  Yet I have been downloading and uploading for days now... I am trying to upload my own torrents now and friend cant download because it says not connected.. heres a screenshot, I've been trying to follow help guide at Transmission website [http://www.transmissionbt.com/help/gtk/1.7x/html/portforward.html](http://www.transmissionbt.com/help/gtk/1.7x/html/portforward.html)

but problem is it says: Go to Preferences >> Network, and check 'Automatically map port'.

Well I dont have autimatically map port... anyone have any ideas?

---

### Post by Rich.. on 2010-03-16
Hey, I am new to ubuntu (only ever had windows) I am having the same problem with Transmission (very slow), If i try to enter 192.168.2.1 the connection times out and when i enter 192.168.1.1 in my browser i have to put a username and password... does anybody know if this means my provider has tried to stop people forwarding ports and such.
would be great to be getting fast downloads!
thanks for reading.

---

### Post by RemiemB on 2010-03-16
Usually, routers use the term filter or firewall to identify port forward. In my router, i added an entry to open a port in my firewall. Once you open that port, just enter it in Transmission or Deluge. IMHO, Deluge is far better than Transmission. Cheers......

---

