---
title: "D-Link"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by Sordelka on 2008-12-04
IS there a way to use rt2500usb drivers without ndiswrapper?

Thanks ^^

---

### Post by Michael.Godawski on 2008-12-05
> [IMG]https://help.ubuntu.com/htdocs/ubuntunew/img/alert.png[/IMG] To get this working with a D-link DWL-G122 USB wireless device, we had to blacklist rt2500usb as well, then restart. Our big clue came when the device's "Connection Information" kept saying rt2500usb was the driver even though we had followed all the instructions on this page.

Taken from [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
So I guess no... the ndiswrapper method should be used.

---

