---
title: "Need some good and _working_ dialer for dialup!"
date: 2005-04-16
forum: Networking &amp; Wireless
---

### Post by Turin Turambar on 2005-04-16
I have managed to install my Lucent modem, but cannot get online. Simply put, wvdial and pon are not working. Nothing happens after connection or the line drops.

Is there some nice dialer for Gnome/Ubuntu? I used KPPP in SuSE... (should I say that it was the best dialer I ever used?)
I tried with gnome-ppp, but couldn't compile the program because some perl module was missing.

Sorry, but I'm really frustrated since I cannot get online in Ubuntu. In SuSE it was perfect and easy. :(

All suggestions are welcomed.

Thanks.

---

### Post by az on 2005-04-16
Gnome-ppp is in the universe repository.  The ubuntu networking thingy is also a frontend to gnome-ppp


anyway, froma console do 
sudo pppconfig enter your info (name the connection provider) and save your information before quitting.

From another console do 
sudo tail -f /var/log/messages

while you do
sudo pon
from the first terminal.  Post the output here...

---

### Post by Turin Turambar on 2005-04-16
Sorry, but I didn't understand what you said about gnome-ppp.  :| 

Here's what it said:

ivan@ubuntu:~$ sudo tail -f /var/log/messages
Apr 16 21:35:50 localhost kernel: UDF-fs: No VRS found
Apr 16 21:36:16 localhost kernel:  [__report_bad_irq+49/119] __report_bad_irq+0x 31/0x77
Apr 16 21:36:16 localhost kernel:  [note_interrupt+117/155] note_interrupt+0x75/ 0x9b
Apr 16 21:36:16 localhost kernel:  [__do_IRQ+211/273] __do_IRQ+0xd3/0x111
Apr 16 21:36:16 localhost kernel:  [do_IRQ+25/36] do_IRQ+0x19/0x24
Apr 16 21:36:16 localhost kernel:  [common_interrupt+26/32] common_interrupt+0x1 a/0x20
Apr 16 21:36:16 localhost kernel:  [default_idle+0/41] default_idle+0x0/0x29
Apr 16 21:36:16 localhost kernel:  [default_idle+35/41] default_idle+0x23/0x29
Apr 16 21:36:16 localhost kernel:  [cpu_idle+33/69] cpu_idle+0x21/0x45
Apr 16 21:36:16 localhost kernel:  [start_kernel+367/371] start_kernel+0x16f/0x1 73

.......and solution is?  :smile:

---

### Post by Turin Turambar on 2005-04-16
Ok, I'm online now, thanks to ALK-7 drivers! Those built-in Ubuntu drivers are NOT working! :(

I'm using gnome-ppp now. It's ok, but kppp is much much better.

---

