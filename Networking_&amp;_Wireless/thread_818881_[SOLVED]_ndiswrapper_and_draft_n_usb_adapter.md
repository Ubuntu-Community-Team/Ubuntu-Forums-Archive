---
title: "[SOLVED] ndiswrapper and draft n usb adapter"
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by AvengingAngel718 on 2008-06-04
hello, i am having trouble getting my wireless to work with my new draft n gear. i installed ndiswrapper and the driver, and it recognized the driver and hardware as having been installed, but now i dont know how to make it connect to my network. i had been previously using wireless g and after connecting my USB dongle it automatically detected my network after a minute or so. if anyone knows how to do this or needs more specific details let me know.

---

### Post by Unix_Slayer on 2008-06-04
> **AvengingAngel718 said:**
> hello, i am having trouble getting my wireless to work with my new draft n gear. i installed ndiswrapper and the driver, and it recognized the driver and hardware as having been installed, but now i dont know how to make it connect to my network. i had been previously using wireless g and after connecting my USB dongle it automatically detected my network after a minute or so. if anyone knows how to do this or needs more specific details let me know.


Have you tried knetworkmanager?

---

### Post by AvengingAngel718 on 2008-06-05
i actually dont have any KDE apps installed and i was hoping there was a way i could do it with gnome so i dont have to drag my computer downstairs and hook it up to my ethernet modem because that would kind of defeat the purpose of having wi fi...i might try it in the morning if i feel ambitious or possibly later tonight

---

### Post by Unix_Slayer on 2008-06-05
> **AvengingAngel718 said:**
> i actually dont have any KDE apps installed and i was hoping there was a way i could do it with gnome so i dont have to drag my computer downstairs and hook it up to my ethernet modem because that would kind of defeat the purpose of having wi fi...i might try it in the morning if i feel ambitious or possibly later tonight

No problem. I know how that goes. There are too many wireless applications in Linux. People fall into traps with them. They look at them all. Try them all, and get disgusted when they don't get anywhere. Some of them just don't work with every card/USB adapter, because of the chips. Also... you do know that you won't get wireless, if your wired card is plugged in. You need to setup the wireless driver, and then unplug your cat5. Hope this helps.

---

### Post by AvengingAngel718 on 2008-06-05
ok i'm pretty sure i got what you said, but just to make sure, i dont have to actually remove my ethernet card right? lol just as long as my cable isnt plugged into a modem?

---

### Post by Unix_Slayer on 2008-06-06
> **AvengingAngel718 said:**
> ok i'm pretty sure i got what you said, but just to make sure, i dont have to actually remove my ethernet card right? lol just as long as my cable isnt plugged into a modem?


You got it.

---

### Post by AvengingAngel718 on 2008-06-10
i finally got around to figuring this one out. what i had to do was install ndiswrapper, then then install ndisgtk, and then run 'sudo gedit /etc/modules' and add ndiswrapper to the list so it would run on startup.

---

### Post by Unix_Slayer on 2008-06-11
> **AvengingAngel718 said:**
> i finally got around to figuring this one out. what i had to do was install ndiswrapper, then then install ndisgtk, and then run 'sudo gedit /etc/modules' and add ndiswrapper to the list so it would run on startup.

How'd it come out for you?

---

### Post by AvengingAngel718 on 2008-06-11
works great, although the signal i get isnt the best, since the router and my computer are on different sides and different floors of my house. still, i get about a 50% connection, which is better than the 0% i got with our old wireless G router.

---

### Post by AvengingAngel718 on 2008-06-11
and might i add thats some pretty amazing hardware you're packing. how much did that cost ya? my comp's an Acer Aspire T180 or something like that-sort of a mid range PC but i sunk about 3-4 hundred dollars into it and it's pretty badass now-AMD athlon 64 5200+ dual core cpu, Nvidia GeForce 8500 with 256 MB onboard RAM (not the best, but it plays oblivion with no trouble and the graphics up the whole way) and 3.5 gigs of RAM

---

### Post by Unix_Slayer on 2008-06-12
> **AvengingAngel718 said:**
> and might i add thats some pretty amazing hardware you're packing. how much did that cost ya? my comp's an Acer Aspire T180 or something like that-sort of a mid range PC but i sunk about 3-4 hundred dollars into it and it's pretty badass now-AMD athlon 64 5200+ dual core cpu, Nvidia GeForce 8500 with 256 MB onboard RAM (not the best, but it plays oblivion with no trouble and the graphics up the whole way) and 3.5 gigs of RAM

Setup was about five grand. Each CPU was $1650. The mobo was $650. And the rest is history.

---

