---
title: "Anyway to reset 11.04 to default settings?"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by sheldonhuelin on 2011-04-29
Hi Everyone;
Yesterday I upgraded to 11.04, things went OK until I went into the CCSM and started playing around with the desktop effects. I'm not sure what I did, but all I see now are my desktop icons, unity is not there,or the top panel. Is there anyway I could go back to the look of 11.04 when I first installed it? Thanks
Sheldon

---

### Post by beew on 2011-04-29
Sounds like you have accidentally disabled Unity.

Right click anywhere to add a folder, click on the folder to open the file  manager, go to /usr/share/applications, from there you can  start ccsm and re-enable Unity.

---

### Post by sheldonhuelin on 2011-04-29
For some reason Unity is not there anymore. Also, for some of the windows, they are hid behind the top panel (I'm using Ubuntu classic until the problem is fixed), and shading behind windows have disappeared. Can I reinstall Ubuntu 11.04 without using a disc to get the default settings? Things just seem really messed up with the interface.

---

### Post by TBABill on 2011-04-29
I'm not sure it's still the case in 11.04 and I'm not at a machine to confirm, but you used to be able to just install ubuntu-desktop or something like that. And you could do the same for Xubuntu, Lubuntu, Kubuntu...so you could have each DE. I would imagine if that capability still exists it would reinstall all your Gnome and Unity items back to default.
 
Search via Synaptic to find it but I think the name is ubuntu-desktop or very similar.

---

### Post by sheldonhuelin on 2011-04-29
I managed to get everything working. I installed the unity plugin, checked off window placement and window decoration in CCSM.

---

### Post by skyzthelimit230 on 2011-04-29
I had the same issue last night! Thanks for this! your instructions helped me fix it :)

---

### Post by djtarki on 2011-05-01
> **beew said:**
> Sounds like you have accidentally disabled Unity.

Right click anywhere to add a folder, click on the folder to open the file  manager, go to /usr/share/applications, from there you can  start ccsm and re-enable Unity.

That also did the trick for me. Thank you very much.

Regards.

---

