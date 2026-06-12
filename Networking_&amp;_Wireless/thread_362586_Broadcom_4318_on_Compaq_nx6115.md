---
title: "Broadcom 4318 on Compaq nx6115"
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by Variorum on 2007-02-15
I have a HP/Compaq nx6115 and just switched to Ubuntu.  The wireless built-in isnt working, and I've tried every guide that I could find on these forums.  After each failed try I reinstalled Ubuntu just to be safe.  Finally I used the general ndiswrapper guide to install the drivers directly from HP for 64 bit.  I dont htink its actually a driver issue.  The wireless ligt on the laptop and the button arent coming on.  in windows if the light wasnt on, i.e. enabled, then the OS thought it existed but had no signals in range.

Also in networking tools its not coming up as an interface, but iwconfig does see it, but iwlist scan shows no scan results.

Does anyone have any insight as what to do to get the card working?

---

### Post by Metaljaz on 2007-02-17
Did you check to make sure the driver was installed correctly?

      Run the following command from a Terminal:

        ndiswrapper -l
        

      If the driver is installed correctly, you should see the following output:

        Installed ndis drivers:
        {name of driver}  driver present, hardware present

---

