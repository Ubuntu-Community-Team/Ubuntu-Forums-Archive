---
title: "Wireless scanning solved on HP Photosmart 7520"
date: 2014-07-01
forum: Networking &amp; Wireless
---

### Post by bill-wilken-wilkenmail on 2014-07-01
When I first installed 14.04, using hplip made it easy to print and fax wirelessly to my HP Photosmart 7520 multipurpose device.  SANE, however, could not find the Photosmart's scanning function ... a major annoyance.  I am happy to report, however, that there is an easy workaround.  First, find the IP address of the device from its control panel.  Second, access the device via any web browser (e.g. [http://192.168.1.12](http://192.168.1.12)) which will provide a connection to HP's web interface to the device.  Third, click on the Settings tab to activate web services, after which you will need to turn the Photosmart unit off and on.  Fourth, re-connect to the Photosmart via the web browser, go to the scan tab and scan.

You may find, however, that it sometimes takes a couple of minutes to complete wireless handshaking with the Photosmart.  Also, it is not intuitively obvious where the web scanner writes the scanned file, indeed, it doesn't write anything until you right click on the app's thumbnail image of the output, which allows you to write the output to another window or to create an actual file.

In short, you can scan wirelessly, but not with SANE.

---

