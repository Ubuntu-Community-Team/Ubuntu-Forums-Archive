---
title: "Some Hardware questions"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by Salamancero on 2009-04-19
Hi,

I've encountered some sound related problems with my toshiba satellite a100-s2211td.  I tried playing some E.S. Posthumus tracks but all I've been getting, for lack of a better term, is a screectchy.  Admittedly, I busted the left side of my laptop's speaker (bass is shot) but I never had a problem with headphones before. Tried poking around sound preferences but when I tickered with some options, I ended up crashing it.  My codec is a Realtek ALC861 if that'll help. 

I'm hoping someone could point me towards the right direction on this. 

Thanks. :D

Second Issue:

Tried connecting my seagate external hard drive but the OS didn't detect it.  Pendrives seem to be fine but the hard disk isn't detected at all.  Again,not sure what to do.  I downloaded a program - usbmount i think but apparently, it doesn't help in this case.

Again, any help would be much appreciated.

Thanks :)

---

### Post by gackt on 2009-04-21
First Problem:
1. Dont really understand your problem (my bad), care to elaborate more?
2. I do experience the same problem, some seagate can connect some can not. try to plug it in and type this in terminal:
1. sudo modprobe -r ehci_hcd"
2. modprobe ehci_hcd

Still not working? Try this

plug it in, 
1. lsmod | grep usb
2. there will be listing of all usb that u used, we are going to reload it
3. sudo modprobe -r usb_storage and then call it again with modprobe usb_storage
4. you might want to reload the usb_core too with sudo modprobe -r usb_core and call it again with modprobe usb_storage

Hope it works

---

