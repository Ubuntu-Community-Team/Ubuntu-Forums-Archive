---
title: "Not sure where to start, setting up wireless with linksys wusb11v4"
date: 2006-07-31
forum: Networking &amp; Wireless
---

### Post by awong on 2006-07-31
I just ordered one a few days ago and got it up and running on my windows 98 boot.  But not sure where to start on ubuntu 6.06.  I did a search and found that I need to use ndiswrapper.  But I want to use it with the GUI, using ndisgtk.  The problem is when I look under System>Administration titled 'Windows wireless drivers'  I do not see it listed.  I was able to install ndiswrapper using synaptic.  But I did not see ndisgtk.  

If anything I can probably do the installion via command line if I need to, but I am still learning the commands and not sure what .inf files to use and also where to put the files.  On the linksys drivers there are about 3 files:
lspmusb.inf
NETUSB.inf
wusbv4.inf

edit: I found the ndisgtk on the how to page.  I'll see how that goes and report back

---

### Post by Dr. Nick on 2006-07-31
My v3 of that card needs lspmusb.inf.

run this from a terminal and post the output on the usbcore line

lsmod

---

### Post by awong on 2006-07-31
usbcore               129668  2 uhci_hcd

that is what I have on the usbcore

---

### Post by Dr. Nick on 2006-07-31
looks alright then, I would just proceed using ndisgtk then to get it setup. I wanted to see your lsmod to make sure thier isnt a native driver already loaded that would conflict.

---

### Post by awong on 2006-08-01
when I selected the lspmusb.inf, ndisgtk, it did not detect the hardware, but it allowed it to install, but when I selected wusbv4.inf.

But I not sure what else to do or if that is right

---

### Post by Dr. Nick on 2006-08-01
just try each one at a time until it says hardware present:yes

---

### Post by awong on 2006-08-01
I got hardware present: yes when I selected wusbv4.inf.  But nothing shows up.  I checked configure network I cannot add it or configure it

---

### Post by Dr. Nick on 2006-08-01
ok, you may have to load ndiswrapper. when it says hardware present open a terminal and run

sudo modprobe ndiswrapper

then see if your hard ware shows up in the network panel

---

### Post by awong on 2006-08-01
thanks, I got it to work and I was able to get online.  THough it seems now my computer is freezing more often, I dont think its related to the wireless and probably my pc's memory (256sdram and amd k6-2)

edit: found this thread
[http://ubuntuforums.org/showthread.php?t=193283&highlight=freezing+updating](http://ubuntuforums.org/showthread.php?t=193283&highlight=freezing+updating)
very similar to what I have

---

