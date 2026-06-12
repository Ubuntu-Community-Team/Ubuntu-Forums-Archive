---
title: "Help with setting up bridge connections"
date: 2011-04-10
forum: New to Ubuntu
---

### Post by retskrad on 2011-04-10
Hi everybody!

I just installed 11 and I want to create a bridge connection between my android 2.2 phone and my desktop computer.

I've read this tutorial, but I do not fully understand step 3.

[http://blog.mycila.com/2010/06/reverse-usb-tethering-with-android-22.html](http://blog.mycila.com/2010/06/reverse-usb-tethering-with-android-22.html)

> STEP 3:

On Linux Computer, setup a bridge:

# usb0 is the new network intreface
# eth0 is the main interface connected to internet (or a gateway)
sudo ifconfig eth0 0.0.0.0
sudo ifconfig usb0 0.0.0.0
sudo brctl addbr br0 
sudo brctl addif br0 eth0
sudo brctl addif br0 usb0
sudo ifconfig br0 up
sudo dhclient br0

See [https://help.ubuntu.com/community/NetworkConnectionBridge](https://help.ubuntu.com/community/NetworkConnectionBridge) to setup bridges

Could anyone please explain this step to me in more fammiliar words? I do not know very much about Ubuntu 11. I just came once again from Win7, because I wanted to try Ubuntu again.

---

### Post by retskrad on 2011-04-10
The thing I don't understand is what I must write in the 0's and such... ip adress, gateway or what?

---

### Post by bodhi.zazen on 2011-04-10
The short answer is that you are creating a bridge , which is a virtual device, and gets an IP address. You are then adding intwork interfaces to it. The network interfaces are in promiscous mode and do not get an ip address.

See also : [http://blog.bodhizazen.net/linux/virt-manager-bridged-networking/](http://blog.bodhizazen.net/linux/virt-manager-bridged-networking/)

Or any tutorial on bridging on Linux or windows, the bridging protocol is fairly generic.

---

### Post by retskrad on 2011-04-10
I just did the "bridge connections" part.. is it suppose to look like this?

[http://i53.tinypic.com/nedbis.jpg](http://i53.tinypic.com/nedbis.jpg)

---

### Post by bodhi.zazen on 2011-04-10
Looks good. Is that windows ? Are you trying to bridge a virtual machine ? If so you using VirtualBox ?

---

### Post by retskrad on 2011-04-10
> **bodhi.zazen said:**
> Looks good. Is that windows ? Are you trying to bridge a virtual machine ? If so you using VirtualBox ?

That's windows 7.

I'm trying to use my desktop computer's (lot laptop or anything, my pc) internet connection, which is not wireless, to my samsung galaxy s, which is an android phone.

---

### Post by bodhi.zazen on 2011-04-10
OK, well as I said bridging is generic enough I hope I answered your question.

If you are having a problem with Windows we normally suggest you use a windows forums ;)

---

