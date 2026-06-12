---
title: "Intel PRO/Wireless 5100 AGN / HP Compaq 6730b"
date: 2013-12-04
forum: Networking &amp; Wireless
---

### Post by dylanp6299 on 2013-12-04
Hello, I am new to ubuntu, and I have been trying to use an HP Compaq 6730b laptop, with the aforementioned Intel PRO/Wireless 5100 AGN. The laptop will recognize that there are wifi networks available, but upon trying to connect to one, after entering the password, the wireless icon in the top right 'flashes' and then it asks for the password again. The password is correct. It does this infinately. 
Thanks in advance.

---

### Post by claracc on 2013-12-05
What ubuntu have you installed?, is network manager controlling the wifi?

I have an h compaq 6720s with 

 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

and cannot use network manager to control the net (connecting and disconnecting all the time) but wicd works well.

---

### Post by dylanp6299 on 2013-12-05
Hi, I have ubuntu 13.10 installed, and It's a vanilla install, so whatever controls the wireless by default is what's doing it. I'm not exactly sure, sorry!

---

### Post by claracc on 2013-12-06
You can try to install wicd (as I assume you are running network manager to control wifi), here you have how to install it: [https://help.ubuntu.com/community/WICD](https://help.ubuntu.com/community/WICD)

You always can revert to network manager if wicd don't solve the problem

---

### Post by dylanp6299 on 2013-12-07
sorry for such a noobish question, but how do I install wicd once the files are on the computer?

---

### Post by claracc on 2013-12-08
The steps are in the link provided. You have to use the command line way in terminal. From this link and assuming gnome/unity ubuntu:

```
Open up a Terminal and execute the following commands:

    First, we download the latest NetworkManager, in case we need to reinstall if WICD doesn't works:

        sudo apt-get install -d --reinstall network-manager network-manager-gnome 
    Then we install WICD:

        sudo apt-get install wicd-gtk 

    And only then do we uninstall NetworkManager:

        sudo apt-get remove --purge network-manager-gnome network-manager 


```

To open a terminal you run: ```
ctrl+alt+T
```

In the same link are the instructions to configure WICD after installing

---

