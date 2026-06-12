---
title: "belkin f5d7050 won't work on newest computer."
date: 2007-05-17
forum: Networking &amp; Wireless
---

### Post by lunaz on 2007-05-17
i had issues w this before on this old comp & got them resolved by following this post:
[http://ubuntuforums.org/showpost.php?p=2192549&postcount=22](http://ubuntuforums.org/showpost.php?p=2192549&postcount=22)

now i switched to cable & have to either use the belkin on the new comp or move it out the the living room.... since i don't want to do that i put the edgy cd in & got the ndiswrapper-utils1.8 stuff off it.

i tried to re do what i did before but 2 problems:

the green light on the belkin only comes on for part of boot up time then turns off.
i can't find BLKWGU.sys anywhere on the belkin cd. it just has an .inf one, and the BLKWGUxp,2k,or 9x.sys files.

---

### Post by lunaz on 2007-05-18
last night i downloaded [this stuff](http://www.belkin.com/support/article/?lid=en&pid=F5D7050&aid=5381&scid=0&fid=2599&fn=F5D7050v4000_V1.0.0.9_FCC.exe) again thinking i could find a BLKWGU.sys in there but i didn't.  i didn't so i tried w32n55.ini only to see it not work. i don't understand why it says blkwu.inf driver installed hardware present when nothing works....

```

gail@badassness:~$ sudo ndiswrapper -l
Password:
Installed drivers:
blkwgu          driver installed, hardware present 
blkwgu2k.sys    invalid driver!
blkwgu.cat      invalid driver!
blkwgu.sys      invalid driver!
blkwguxp.sys    invalid driver!
w32n55.ini      invalid driver!
gail@badassness:~$ sudo ndiswrapper -e
Usage: ndiswrapper OPTION

Manage ndis drivers for ndiswrapper.
-i inffile        Install driver described by 'inffile'
-d devid driver   Use installed 'driver' for 'devid'
-e driver         Remove 'driver'
-l                List installed drivers
-m                Write configuration for modprobe
-da               Write module alias configuration for all devices
-di               Write module install configuration for all devices
-v                Report version information


where 'devid' is either PCIID or USBID of the form XXXX:XXXX
gail@badassness:~$ sudo ndiswrapper -e blkwgu2k
Driver blkwgu2k is not installed.Use -l to list installed drivers
gail@badassness:~$ sudo ndiswrapper -e blkwgu2k.sys
gail@badassness:~$ sudo ndiswrapper -e blkwguxp.sys
gail@badassness:~$ sudo ndiswrapper -e blkwgu.sys
gail@badassness:~$ sudo ndiswrapper -e blkwgu.cat
gail@badassness:~$ sudo ndiswrapper -e w32n55.ini
gail@badassness:~$ sudo ndiswrapper -l
Installed drivers:
blkwgu          driver installed, hardware present 
gail@badassness:~$ 

```

---

### Post by lunaz on 2007-05-19
any ideas? i did some more looking tonight & pretty sure i got ndiswrapper working & the right driver files off the belkin cd.

the adapter light only stays on for short time during boot & then goes off/stays off. i do sudo ndiswrapper -l & it says blkwgu driver & hardware present.

i do see a wireless option in my system>networking box, and it's enabled. iwconfig shows stuff for wlan0.

i tried & retried the instructions & still dont work.

even got the v3xxx & v4xxx drivers off their website but no windows comp to put them on. wine wont work well with that either.

---

### Post by lunaz on 2007-06-04
-uninstalled all ndis stuff with synaptic
-reinstalled ndiswrapper-common & ndiswrapper-utils-1.8 with synaptic
-restarted computer

the light on the usb adapter is ON.

```

gail@badassness:~$ ndiswrapper -v
utils Error: no version specified!
driver version:        1.22
vermagic:       2.6.17-11-generic SMP mod_unload 586 REGPARM gcc-4.1
gail@badassness:~$

```

```

gail@badassness:~/Desktop/v4/files/Driver$ ls
BLKWGU2K.sys  BLKWGU.CAT  BLKWGUXP.sys  Driver.98
BLKWGU9X.sys  BLKWGU.inf  Driver.2K     Driver.ME
gail@badassness:~/Desktop/v4/files/Driver$ sudo ndiswrapper -i BLKWGU.inf
Password:
Installing blkwgu
gail@badassness:~/Desktop/v4/files/Driver$ sudo ndiswrapper -i BLKWGUXP.sys
Installing blkwguxp.sys
gail@badassness:~/Desktop/v4/files/Driver$ sudo ndiswrapper -i BLKWGU.CAT
Installing blkwgu.cat
gail@badassness:~/Desktop/v4/files/Driver$ sudo ndiswrapper -l
Installed drivers:
blkwgu          driver installed, hardware present 
blkwgu.cat      invalid driver!
blkwguxp.sys    invalid driver!
gail@badassness:~/Desktop/v4/files/Driver$ sudo modprobe ndiswrapper
gail@badassness:~/Desktop/v4/files/Driver$ sudo ndiswrapper -m
modprobe config already contains alias directive

```

the light went off at this point...

there is a wireless interface in system>networking. this is where i get stuck. the same happens if i use the v4 drivers or the v3 drivers.

here's some of lsmod.

```

gail@badassness:~$ lsmod
ehci_hcd               34696  0 
uhci_hcd               24968  0 
usbcore               134912  7 ndiswrapper,usb_storage,libusual,usblp,ehci_hcd,uhci_hcd

```

---

