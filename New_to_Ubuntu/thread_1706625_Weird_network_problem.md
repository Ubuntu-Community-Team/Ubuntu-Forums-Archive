---
title: "Weird network problem"
date: 2011-03-14
forum: New to Ubuntu
---

### Post by Blutkoete on 2011-03-14
Hello!

I've a weird problem. I had to re-install Windows because I'll need it for the next few days, so I installed it first, then Fedora 14 because I wanted to look at it and lastly Kubuntu.

Kubuntu is able to connect (I'm using a cable) to the local network, access every other computer and the router, ping web sites (e.g. [www.ubuntuforums.org](www.ubuntuforums.org)), but doesn't open any web sites or downloads updates. *apt-get update* hangs showing a download speed of 15 Bytes per second; *w3m* opens the sockets, sends the request but then hangs with "Waiting for reply".

Two other computers running Kubuntu still work normally, so does a Vista computer and both the Windows 7 and the Fedora installation on the computer.  Yesterday, before I did all the reinstallations, the Kubuntu on that computer was working perfectly.

The system is completly fresh - as I'm not able to download anything, it still is the basic system. I think it downloaded normally during the installation process though.

Any ideas? Maybe something went wrong during the installation, but there are no error messages.

Best regards,

Blutkoete

---

### Post by TBABill on 2011-03-14
I had a similar issue with openSUSE recently and I had to go into system settings and I believe it was under the user settings, but not positive....and enable KDE wallet. For some reason until I did that the system would just not work properly. Even if I connected I couldn't do much until I enabled it and setup the password for it.

---

### Post by mastablasta on 2011-03-14
i thought wallet is some homebanking programme so i uninstalled it. :-O
 
i reinstaleld it when i noticed i need it to save passwords. However rekonq is not saving them. kind of stupid name and icon for password saving application.

---

### Post by Blutkoete on 2011-03-15
> **TBABill said:**
> I had a similar issue with openSUSE recently and I had to go into system settings and I believe it was under the user settings, but not positive....and enable KDE wallet. For some reason until I did that the system would just not work properly. Even if I connected I couldn't do much until I enabled it and setup the password for it.

The password alone didn't work, but you showed me the difference to the other installations that worked: WLAN. After enabling the WLAN access and surfing for some time, the cable LAN is now working as well. So thank you!

Strange behaviour still.

Why doesn't the normal LAN work when I don't configure my WLAN? Weird.

Maybe I should try to reproduce the problem to file a bug, but I don't want to reinstall everything again just to check whether the LAN won't work again.

---

