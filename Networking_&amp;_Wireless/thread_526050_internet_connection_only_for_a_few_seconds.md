---
title: "internet connection only for a few seconds"
date: 2007-08-15
forum: Networking &amp; Wireless
---

### Post by tmray on 2007-08-15
I installed kubuntu feisty on my son's computer, a Compaq desktop with AMD sempron, ATI Radeon x200 video card and Realtek ethernet and I'm having some problems.

But first and foremost, it will not stay connected to the internet. To get it to connect I have to right-click on the knetwork manager on the panel chose options> connect on start up. then it will connect for about ten seconds, then disconnect. So I have to do that again to get it to re-connect.

Any clue how I can fix this?

---

### Post by scifi76 on 2007-08-15
Not that I know what is causing your problem, but what Realtek chipset are you using?

---

### Post by tmray on 2007-08-15
how do I check that? lspci?

---

### Post by scifi76 on 2007-08-16
I'm not entirely sure as I'm new to this myself. I think you could try lshw and look for the network entries. Try lspci also! :)

---

### Post by tmray on 2007-08-18
It says my ethernet is a Realtek RTL-8139/8139C/8139C+
Which on their website it says the driver for that is already in the kernel so I can't download a driver to try and install it.

---

### Post by tmray on 2007-08-21
I removed knetwork manager and set a manual IP in the system network settings based on my other Kubuntu system (giving it it's own # in the last 3 digits) but that didn't work either.
And it's not the router or the plug cuz I physically switched it with my other kubuntu computer and it hooked up and connected just fine.

---

### Post by tmray on 2007-08-24
I removed knetwork manager and it stayed connected but on reboot it lost the connection. And since the knetwork manager was not in the system tray I couldn't right click to re-connect it. So I had to re-install it. Ugh!

Any thoughts?

---

