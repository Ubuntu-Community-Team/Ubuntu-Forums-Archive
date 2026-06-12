---
title: "Broadcom 4306 using ndiswrapper HELP"
date: 2006-08-09
forum: Networking &amp; Wireless
---

### Post by Mcqueen on 2006-08-09
Hello all,
    When i go to install the driver for my broadcom 4306 using ndiswrapper it told me that it couldn't install bcmwl5.inf on line 135 of ndiswrapper. Now when i list the drivers with ndiswrapper it says invalid driver. Also the files don't show up in ect/ndiswrapper/bcmwl5.inf. I have tried the bcmwl5a.inf but i get the same error message. Any ideas. I really like linux but i need the wirless to work.

---

### Post by wieman01 on 2006-08-09
When installing the *.inf file you should make sure that the other driver files (usually it's another two that come with the driver) are in the same directory. Somehow "ndiswrapper" needs all 3 of them although you "seem" to install only the *.inf file.

Still error messages?

---

