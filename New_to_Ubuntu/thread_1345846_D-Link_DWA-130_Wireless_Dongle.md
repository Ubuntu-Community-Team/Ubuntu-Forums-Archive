---
title: "D-Link DWA-130 Wireless Dongle"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by Ted3929 on 2009-12-04
Using Xubuntu 9.10 and wireless is really a sketchy proposition as far as range.  I do have a D-Link DWA-130 USB wireless dongle with B/G/N.

It's recognized when plugged in and even shows in the wireless section, but no matter what I can't get the drivers to work with NDIS Wrapper and the driver supplied with the unit.

Does anybody know of a workaround on this?  I get a consistent 4 bars with the D-Link and only 1 with my standard wireless.

Thanks

---

### Post by bkratz on 2009-12-04
> **Ted3929 said:**
> Using Xubuntu 9.10 and wireless is really a sketchy proposition as far as range.  I do have a D-Link DWA-130 USB wireless dongle with B/G/N.

It's recognized when plugged in and even shows in the wireless section, but no matter what I can't get the drivers to work with NDIS Wrapper and the driver supplied with the unit.

Does anybody know of a workaround on this?  I get a consistent 4 bars with the D-Link and only 1 with my standard wireless.

Thanks

I use the DWA-130 in Ubuntu.  Mine is the rev A version.  Do you know the version of yours?  Anyway, I am forced to use Ndiswrapper and have done so since 8.10.  Version 9.10 ( at least in Ubuntu--probably in Xubuntu 9.10) utilizes ndiswrapper version 1.55.   There is a "bug" in this version which will not let you use any encryption.  There is a work around ( compiling your own ndiswrapper) which I haven't tried yet.  You should be able to connect to a non-encrypted network though.  Is your's encrypted? If so, you may want to temporarily remove that function from your A/P.

I will dig-up the documentation and will post links here a little later. If you can't connect to any network, I would be happy to help.

---

### Post by Ted3929 on 2009-12-04
States rev B-1 on the back but the disk with drivers was some generic reburn so I can't really tell.

It's not recognition of the dongle that's the problem, it's keeping it active.  It appears to kick in and then disconnect just as quickly.

Goofy to say the least

---

### Post by bkratz on 2009-12-04
> **Ted3929 said:**
> States rev B-1 on the back but the disk with drivers was some generic reburn so I can't really tell.

It's not recognition of the dongle that's the problem, it's keeping it active.  It appears to kick in and then disconnect just as quickly.

Goofy to say the least

The D-Link website has their own forum and it appears 

[http://forums.dlink.com/index.php?topic=5032.0](http://forums.dlink.com/index.php?topic=5032.0)

(see post from tfunk)

that several people have complained about the REV B dropping out randomly and recommending use of the Ralink USB RT2870/2770 driver rather than the Dlink supplied one.  I haven't found these on the web yet, but I will keep looking.

[ATTACH]138561[/ATTACH]

---

### Post by Ted3929 on 2009-12-04
Found it at [http://www.driversforwindows.com/ralink_rt2870_2770_usb_driver_1.0.3.0_7156.htm](http://www.driversforwindows.com/ralink_rt2870_2770_usb_driver_1.0.3.0_7156.htm)

Will check to see if it works.

Thanks

---

