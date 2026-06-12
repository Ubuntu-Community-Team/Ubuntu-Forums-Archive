---
title: "realtek 8111B driver loads, but no eth0"
date: 2007-01-17
forum: Networking &amp; Wireless
---

### Post by apanloco on 2007-01-17
I have a P5B motherboard with a Realtek 8111B network controller. I am running Edgy with kernel 2.6.17-10-386. I cannot get the 8111B network controller to work.
I have downloaded the sources from Realtek (r1000_v1.05), unpacked it and installed it. I have loaded the driver and it shows in lsmod. But I do not get a eth0 device. Here is what happens:

```

mythtv@brutus:~/network$ sudo modprobe r1000
mythtv@brutus:~/network$ dmesg | tail -12
[17180939.092000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 19 (level, low) -> IRQ 177
[17180939.092000] PCI: Setting latency timer of device 0000:03:00.0 to 64
[17180939.092000] eth0: Identified chip type is 'RTL8168B/8111B'.
[17180939.092000] eth0: r10001.05, the Linux device driver for Realtek Ethernet Controllers at 0xa800, 00:18:f3:08:0a:74, IRQ 177
[17180940.848000] Realtek RTL8168/8111 Family PCI-E Gigabit Ethernet Network Adapter
[17180940.848000] Driver version:1.05
[17180940.848000] Released date:2006/10/25
[17180940.848000] Link Status:Linked
[17180940.848000] Link Speed:100Mbps
[17180940.848000] Duplex mode:Full-Duplex
[17180940.848000] I/O Base:0xA800(I/O port)
[17180940.848000] IRQ:177
mythtv@brutus:~/network$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

mythtv@brutus:~/network$ lspci

...
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. Unknown device 8168 (rev 01)
...


```

Would appreciate any help.

/D

---

### Post by drpepper on 2007-02-08
Hi! I am too installing mythtv with ubuntu on this motherboard. I like you downloaded the realtek driver, but could not get it to compile. I'm new to installing modules and am gettin very frustrated! i get errors with unkown directorys, so i tried editing the Makefile, correcting directorys, but still more errors, about not being able to find target modules? All i can find on the net is to do wit SUSE. any help would be great thanks!

nick

---

### Post by drpepper on 2007-03-11
I don't know if you managed to get this sorted, I did. Here's how:

I used **modprobe r1000** to load the module with the kernel
then i edited **/etc/modules** and added r1000
then **[B][B]sudo ifconfig eth0** up[/B][/B] to bring up the interface
and **sudo dhclient** to obtain an ip adress

this works fine, except i have to bring up the interface and run dhclient after every boot. i think the solution is propably something to do with **/etc/network/interfaces**

i'll post if i figure the last bit out. But this should get it working alteast

---

### Post by dmitryilyin on 2008-02-19
By default GNU ifconfig do not dhow down interfaces/ Try ifconfig -a or make ifconfig eth0 up.
(FreeBSD ifconfig shows all interfaces)

---

