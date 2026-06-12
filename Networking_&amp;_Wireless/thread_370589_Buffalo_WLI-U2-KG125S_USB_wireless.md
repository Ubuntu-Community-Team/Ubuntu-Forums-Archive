---
title: "Buffalo WLI-U2-KG125S USB wireless?"
date: 2007-02-25
forum: Networking &amp; Wireless
---

### Post by Skooj on 2007-02-25
I recently bought a Buffalo WLI-U2-KG125S usb wireless adapter to connect my PC (running ubuntu Edgy 6.10) wirelessly to my network. After finding out that there is no plug and play support, I quickly jumped to the ndiswrapper route. However, upon downloaing the latest ndiswrapper and driver, I see this on the ndiswrappe -l output: 
"****@*****:~/Desktop/ndiswrapper-1.37# ndiswrapper-l
netg125s : invalid driver!"

I don't know if it just isn't supported or what. Any help sorting this out will be greatly appreciated. I've seen WLI-U2-G54's apparently working, but considering my router can handle 125, I would really like to keep this adapter.

---

### Post by teemu on 2007-02-26
Hi, 

I just got the adapter working with ndiswrapper (only run it in 54 mode, haven't tried in 125)... 

I found most of the critical information from: [http://ubuntuforums.org/showthread.php?t=225206](http://ubuntuforums.org/showthread.php?t=225206)

So here it is (insert sudo where appropriate):

1) Install ndiswrapper-utils-1.8

2) Run ndiswrapper -i netg125s.inf

3) Copy rndismp.sys and usb8023.sys manually under /etc/ndiswrapper/netg125s/

4) Maybe run ndiswrapper -m and ndiswrapper -d 0411:00BC netg125s (I'm not sure if I really did this... I think I did)

At this point running ndiswrapper -l told that driver is installed. 

Finally I followed the instructions from above link, section 'Getting WUSB54GS to Work in Edgy and Feisty', replacing values for idVendor with 0411 and idProduct with 00bc. 

Reboot and wlan0 was up. And I'm somewhat happy... 

I hope this helps.

- Teemu

Edit: Couple of system freezes in two hours... I don't have monitor attached so I don't know the reason but...

---

### Post by teemu on 2007-02-27
Just for reference, it seems that the following happens during heavy wlan traffic:

Feb 27 08:25:33 xxxxx kernel: [17180505.536000] BUG: soft lockup detected on CPU#0!
Feb 27 08:25:33 xxxxx kernel: [17180505.536000]  <c01491cf> softlockup_tick+0x9f/0xf0  <c012bee1> update_process_times+0x31/0x80
Feb 27 08:25:33 xxxxx kernel: [17180505.536000]  <c0114d13> smp_apic_timer_interrupt+0x53/0x60  <c010413c> apic_timer_interrupt+0x1c/0x30
Feb 27 08:25:33 xxxxx kernel: [17180505.536000]  <e0c28884> ExInterlockedPopEntrySList+0x84/0xb0 [ndiswrapper]  <e0c34175> tx_worker+0x585/0x700 [ndiswrapper]
Feb 27 08:25:33 xxxxx kernel: [17180505.536000]  <c0132702> run_workqueue+0x72/0xf0  <e0c33bf0> tx_worker+0x0/0x700 [ndiswrapper]
Feb 27 08:25:33 xxxxx kernel: [17180505.536000]  <c01332e7> worker_thread+0x117/0x140  <c011bde0> default_wake_function+0x0/0x10
Feb 27 08:25:33 xxxxx kernel: [17180505.536000]  <c01331d0> worker_thread+0x0/0x140  <c0135f8b> kthread+0xab/0xe0
Feb 27 08:25:33 xxxxx kernel: [17180505.536000]  <c0135ee0> kthread+0x0/0xe0  <c0101005> kernel_thread_helper+0x5/0x10

Have to investigate this later on...

---

### Post by Skooj on 2007-02-27
Thank you very much. This worked to perfectly to get ubuntu to recognize the device. However, I can't seem to get it to connect to my network. I'm using a 64bit wep key currently and a visible SSID. I have set the device up with a static-ip and everything. my current set up is also 54mbps, however my new router should be in thursday that will allow 125.

So, what I need now is help configuring the network to work, and also how to change it from 54mbps to 125.

thanks for the extra help.

---

### Post by Skooj on 2007-03-01
^nevermind. it randomly decided to work today (with no changes..) thanks for everything :)

---

### Post by jimcpl on 2007-10-14
Hi,

I have this same USB interface, and have been trying to get it working.

I have things to the point that "ndiswrapper -l" is working:

root@ubuntu:/etc/udev/rules.d# ndiswrapper -l
netg125s : driver installed
           
The above was with the USB dongle unplugged because I have to send this using another USB hardline Ethernet interface, but when the Buffalo is plugged in, there is an additional line:

   (0411:00bc) device...

The problem that I am having is after the ndiswrapper stuff. 

I've done "ndiswrapper -m", "depmod -a", and "modprobe ndiswrapper", but then, when I do "ifconfig wlan0", I get an error saying that it can't find the device.  The same thing happens when I do "iwconfig" to configure it.

I've added the line using "nano" using 0411 and 00bc, but still no joy :(...

I've also added the lines to /etc/network/interfaces.

I've tried network-manager-gnome, but that only sees "lo" and "eth0" (my USB Ethernet interface).

I've rebooted multiple times.

I was very hopeful when I found this thread, but I've been unsuccessful so far on this.

FYI, I did the ndiswrapper installation by building 1.48.

Thanks in advance!!  Hope that someone here can help!

Jim

---

