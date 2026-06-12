---
title: "Ideapad 310, WIFI and Blue-tooth not working"
date: 2017-10-19
forum: Networking &amp; Wireless
---

### Post by betouar-hamza-89 on 2017-10-19
After update ubuntu to 17.10, i have same probleme.
and after launch command make i have this error :

> make -C /lib/modules/4.13.0-16-lowlatency/build M=/home/hamza/Téléchargements/rtlwifi_new modulesmake[1]: *** /lib/modules/4.13.0-16-lowlatency/build : Aucun fichier ou dossier de ce type. Arrêt.
Makefile:58 : la recette pour la cible « all » a échouée
make: *** [all] Erreur 2




---

### Post by QIII on 2017-10-19
Moved to its own thread from [https://ubuntuforums.org/showthread.php?t=2372356](https://ubuntuforums.org/showthread.php?t=2372356)

Hello!

Adding a question to someone else's solved thread is very unlikely to result in support being provided for your request.  People look at solved threads when they are searching for a solution to their own issues, not when they are looking to give help.

---

### Post by wildmanne39 on 2017-10-19
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results to pastebin, then posting the link here.

---

### Post by betouar-hamza-89 on 2017-10-19
Hi, Thanks for help, this script result

[https://pastebin.com/AbvdGpfC](https://pastebin.com/AbvdGpfC)

---

### Post by wildmanne39 on 2017-10-19
I am looking into this issue but I want to ask what is the Docker0 virtual device?

---

### Post by betouar-hamza-89 on 2017-10-19
is a container like virtual machine, it's contains a web server for my developed websites

---

### Post by wildmanne39 on 2017-10-19
That is what I thought but I wanted to be sure, please do:
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Then if you live in Africa/morocoo region we need to set the routers country code:
```
sudo iw reg set MA
```
```
sudo sed -i 's/^REG.*=$/&MA/' /etc/default/crda
```
Set your routers channel to 1, 6 or 11 for now, I want to make sure it is not set to a high channel and the reason for the issue. You need to be disconnected from your wired connection when you try to connect to the internet.

In dmesg is does not show any response from your AP. If this does not work reset your router and if there is any wifi connections in network manager remove them then reboot the compuer once your router is completely back up and see if the network is discovered, if no connection post a new script file so we can see the changes.

Thanks

---

