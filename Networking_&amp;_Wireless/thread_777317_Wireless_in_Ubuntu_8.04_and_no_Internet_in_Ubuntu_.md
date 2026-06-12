---
title: "Wireless in Ubuntu 8.04 and no Internet in Ubuntu Studio 8.04 on the same machine!"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by the8thstar on 2008-05-01
Hello all,

I'm trying to figure this one out. In my current config (see my sig below), wireless works right out of the box in Ubuntu 8.04 - I use a Broadcom 4530 I believe.

I installed Ubuntu Studio last night and I have no Internet, no wireless, not even the Gnome nm-applet is showing... I wonder what's going on.

Your help will be appreciated. :)

---

### Post by Ck.asdf on 2008-09-07
This isn't the greatest suggestion, but surprisingly, it worked for me.  I had the same problem - I installed uStudio one night without Internet by my side, and told it to forget about configuring network stuff during the install.  Later, it acted quite weird ...
Anyway, what I did tonight was to reinstall uStudio with the Ethernet cable plugged in, so it found automatic DHCP setup, then went from there ... But it didn't show nm-applet, the thing that Ubuntu uses for network setup.

Go to a console (Applications -> Accessories -> Terminal), and type:
```
sudo apt-get install network-manager-gnome
```
It'll ask for your password, and then install.  After that, you can type "nm-applet" and it will run.

It might still act weird, but go ahead and install all your updates, and restart the computer.  Afterwards, it will hopefully be fixed!

---

### Post by buck2825 on 2008-11-09
ok I have tried everything i can see on the internet about this all questions and no real answers.

ubuntu studo 8.04, drivers are installed, network manager gnome, but no wireless internet whats missing WE need help. 

Thanks everyone in advanced

---

### Post by el Arm on 2009-04-06
> **buck2825 said:**
> 
ubuntu studo 8.04, drivers are installed, network manager gnome, but no wireless internet whats missing WE need help. 


You need to turn on roaming mode for the wireless adapter.

- Left click on the network manager applet -> Manual Configuration, unlock it
- Select Wireless connection, click properties
- Click Enable roaming mode

Shortly you should see the available wireless networks in the applet.

---

### Post by Ck.asdf on 2009-04-06
Hello, I am wondering - why is it any different in Ubuntu Studio than normal Ubuntu? When I install Ubuntu, it doesn't ask me to set up the network inside the installer, so why does it do it in Studio? (Or if it does ask, if I ignore it in the installer, it does work after installation is done.)

---

### Post by m.beige on 2009-04-09
did anything work for you ?

---

### Post by Ck.asdf on 2009-04-09
I don't understand your question.
Could you please expand on it?
Thanks.

---

### Post by BluShift on 2009-07-24
Perfect! Enabling roaming mode worked perfectly for me. :D

Thanks very much :)

---

### Post by boarder428 on 2011-03-14
I have an older notebook I just installed ubuntu studio 8.04 on and cannot get wireless set up. The above methods are not working.  I an using a trendnet usb wireless adapter because the onboard adapter is not working.  My only other thoughts are to try to set up ndis.  Are there any other suggestions?  This adapter worked fine using jaunty on this notebook?

---

