---
title: "Need Help w/ Wireless"
date: 2007-04-17
forum: Networking &amp; Wireless
---

### Post by prolifik on 2007-04-17
I'm a Ubuntu newbie so please bear with me.

I recently installed Xubuntu into my Compaq Presario 2200. At first I had problems with Wireless Assistant coz everytime I run it, I get a message about restricted permissions. Later I found out that I had to run it using sudo and I did it through "gksudo wlassistant".

Now, I don't that message anymore but I still can't connect via wireless. Btw, I can connect via ethernet w/o any problems and I also tried to connect to a neighbor's open wireless network just to test it and I was able to connect. So I'm guessing it's the settings that I used. My WEP key is a 10 digit number and it uses a key index of 2. Should I use the Automatic (DHCP) or Manual? WEP mode - Open or Shared? WEP key - Hex or ASCII?

I would really appreciate the help I can get as I won't be able to connect via ethernet once I move out of my apartment. Thanks in advance! :)

---

### Post by Kobalt on 2007-04-17
Are you trying to connect to your network with Network-Manager ? It has a know bug with wep encrypted networks...

---

### Post by prolifik on 2007-04-17
At first I did, but I now I've removed the information I typed and have enabled roaming mode on Network Settings. So now I'm only using Wireless Assistant.

Also, I installed the gnome-network-manager and wpsupplicant. Should I remove them and leave wlassistant by itself? Thanks!

---

### Post by Kobalt on 2007-04-17
> **prolifik said:**
> Also, I installed the gnome-network-manager and wpsupplicant.

This is Network-manager... I'd suggest you to remove it with Synaptic (both "network-manager" and "gnome-network-manager" packages) and restart. Then try to connect to your wep network with either wlassistant (though I don't know this tool, that is KDE based by the way : do you have Ubuntu or Kubuntu ?) or System > Admin. > Networking.

---

### Post by prolifik on 2007-04-17
I'm using Xubuntu with the Gnome session. I already removed network-manager and network-manager-gnome and rebooted my laptop. Tried to connect to via wireless assistant and still won't work. I tried connecting again to someone's open wireless network and was successful. I also filled out the necessary data in System > Admin > Network.  

Should I also remove wpsupplicant?

Thanks for taking time to answer. Looks like you're the only one who's willing to help me. :)

---

