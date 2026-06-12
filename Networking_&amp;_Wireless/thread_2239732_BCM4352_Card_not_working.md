---
title: "BCM4352 Card not working"
date: 2014-08-15
forum: Networking &amp; Wireless
---

### Post by arunscape on 2014-08-15
I already tried going on this page: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)
And there are a few problems:

1) My card isn't even on there...
2) I don't have a cdrom in my computer, so nothing can be mounted in media/cdrom so I can't use any repositories that require the LiveCD (and yes, I already tried plugging in the LiveUSB I used to install...)

I'm running ubuntu 14.04.1 LTS  64 bit

I also tried ndis but that also needed repositories on the LiveCD

I also tried installing some broadcam package from Dell (even though it's not a Dell computer) and that too asked for a LiveCD...

I tried plugging in ethernet to see if there would be something new in software & updates, but nothing showed up. Still under the proprietary drivers tab, it shows that the Broadcam, card isn't working. When I try to select the option to use the driver, it goes back rightaway to "do not use this driver"

So I'm stuck and don't know what to do next...

---

### Post by varunendra on 2014-08-15
Welcome to the forums arunscape!

You don't need ndiswrapper, nor a CD. You need packages that are on the cd/ISO. If you installed Ubuntu using a Live USB, you can directly install the required package from there. Have you read this part of the wiki page : [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA_-_No_Internet_access](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#STA_-_No_Internet_access) ?

---

