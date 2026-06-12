---
title: "running ifconfig wlan0 up at boot"
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by dehuszar on 2007-03-18
I just did a reinstall of Edgy on my laptop after getting a new, larger hard drive.  I was pleasantly surprised at how much the ndiswrapper, network-manager tools have gotten easier since I first set up my network on the last install.  

One thing I can't seem to make sense of though... my wlan0 device now has to be manually turned on after the machine boots.   I don't recall having to do that before (though I had to do a MESS of other things).

I'm using network-manager with a WPA key.  Don't know if that makes a difference.  Again, once booted, the command ```
ifconfig wlan0 up
``` does the trick.  

I suppose putting it in my Sessions config would do the trick, but there has to be a more elegant way to do this.  

Any advice would be appreciated.

Sincerely,
Sam

---

### Post by Kobalt on 2007-03-18
Do you have an 'auto wlan0' line in your /etc/network/interfaces file ?

---

### Post by dehuszar on 2007-03-18
No, because I'm using Network-Manager, and therefore don't want the stock Networking tools to try and take control.  

I also don't have an eth0 line in my interfaces file, but eth0 comes up automatically at boot, and nm-applet has no trouble loading the device and acquiring an address.  I'm not sure why eth0 is loading and not wlan0, though.

My interfaces file only has an 'auto' for the lo loopback device.

---

### Post by Kobalt on 2007-03-18
Just so you know : I use network-manager and I still have an 'auto wlan0' line in my /etc/network/interfaces ... 
My wifi starts automatically at boot though.

---

### Post by dehuszar on 2007-03-19
Well, I put auto wlan0 in my interfaces file.  Still won't load at boot time.  Anything else I can try?

---

### Post by scxtt on 2007-03-19
what about putting a script in /etc/rc2.d/ w/ that command in it?

---

### Post by dehuszar on 2007-03-29
Still doesn't seem to work.  Have to manually load the wlan0 device everytime.  What's weird is that everything worked fine under Edgy.  I did a dist-upgrade to Feisty and it started acting strangely.

I also tried to reinstall the ndiswrapper and just about every wireless LAN app I could find installed in synaptic, but no dice.

Any other suggestions would be most welcome.

Thanks in advance,
Sam

---

