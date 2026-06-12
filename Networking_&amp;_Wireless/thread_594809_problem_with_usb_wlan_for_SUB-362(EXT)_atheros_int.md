---
title: "problem with usb wlan for SUB-362(EXT) atheros international not working."
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by mohit052 on 2007-10-28
I have a Sanyo SUB-362(EXT) usb wireless adapter for my internet connection.
With no driver to support Linux so i used ndiswrapper. 

0.Configuration
AMD athelon 64
512 MB RAM

1. I found that this driver need an aditional driver athfmwdl as all aterous drivers do.
So i installed this and net5523 the 

other driver....
These installed without any errors and show onlisting
root@homunculi:~#ndiswrapper -l
athfmwdl : driver installed
	device (0CF3:0002) present
net5523 : driver installed
	device (0CF3:0002) present

2.Then the following steps also show no erors..
root@homunculi:~# depmod -a
root@homunculi:~# modprobe ndiswrapper
root@homunculi:~# modprobe -m ndiswrapper

3.The device shows up on lsusb(The other is my logitech usb mouse)
root@homunculi:~# lsusb
Bus 003 Device 003: ID 0cf3:0002 Atheros Communications, Inc. 
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 046d:c016 Logitech, Inc. M-UV69a Optical Wheel Mouse
Bus 001 Device 001: ID 0000:0000  

4. The dmesg shows up saying that its not a 64 bit driver... Now where do i get a 64-bit driver?
Or is there any way around this..?Or am i doing something wrong...
root@homunculi:~# dmesg | grep ndis
[   52.915924] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[   53.354398] ndiswrapper (check_nt_hdr:153): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[   

53.354405] ndiswrapper (load_sys_files:216): couldn't prepare driver 'net5523'
[   53.354943] ndiswrapper (load_wrap_driver:118): couldn't load driver net5523; check system log for messages from 

'loadndisdriver'
[   53.354971] usbcore: registered new interface driver ndiswrapper

root@homunculi:~# lsmod | grep ndis
ndiswrapper           239608  0 
usbcore               154416  5 ndiswrapper,usbhid,ehci_hcd,ohci_hcd


root@homunculi:~# iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

5. Also The following error is showing when i try to open the ndisgtk
root@homunculi:~#ndisgtk
Traceback (most recent call last):
  File "/usr/bin/ndisgtk", line 309, in <module>
    NdisGTK()
  File "/usr/bin/ndisgtk", line 111, in __init__
    self.setup_driver_list()
  File "/usr/bin/ndisgtk", line 140, in setup_driver_list
    self.get_driver_list()
  File "/usr/bin/ndisgtk", line 168, in get_driver_list
    driver_name = p.search(line).group()[:-1]	# strip trailing space
AttributeError: 'NoneType' object has no attribute 'group'


6. The LED on my adapter never glows(if that is of any help)...
but the device is showing up the device manager:system>preferences>hardware information
I am really awaiting any help because i live in this place where we share net on the lan through MY comp.
The internet is on 24 hours(havent closed my comp in a month) on windows... And i havent touched my ubuntu 7.4 for 
quite some time cause this is inconvinient for others.. Would be really great if the wlan gets workin then i 
can be on linux 24/7...
---------------------------------------------
Now this is out of nowhere but can any one sugest any projects on ditributed computing.......


PS:did try the 64bit driver availible for the device for vista...
Doesnot work...

---

