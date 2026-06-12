---
title: "Wireless guide? Assistance please."
date: 2007-02-05
forum: Networking &amp; Wireless
---

### Post by hyby on 2007-02-05
Hi guys, 
I was wondering is there a guide to setting up Edgy for wireless conection to a wireless router. 

I have an intel 2200 BG inbuilt card. I believe this is well supported by Edgy Eft. When i go to Networks in the Administration menu and enable it, i can not type in my 26 letter secturity code as it the ASCII and the other option only allows for a few letter 12 the most (i believe). 

I have WEP encryption (128 bit). Is there a way i can setup the network card? Or, do i need third party software? 

Thanks guys.

Cheers

---

### Post by kylevan on 2007-02-05
I use NetworkManager myself.

"sudo apt-get install network-manager-gnome" and a restart of X (ctrl+alt+backspace) should help get you on your way.  when you store your WEP key with networkmanager, it will create a GNOME keyring for you, make sure the keyring password is the same as your login password so that you can then use the guide in the following link to get the keyring manager to stop asking for your keyring password every time you boot.

[http://ubuntuforums.org/showthread.php?t=192281&highlight=GNOME+session](http://ubuntuforums.org/showthread.php?t=192281&highlight=GNOME+session)

---

