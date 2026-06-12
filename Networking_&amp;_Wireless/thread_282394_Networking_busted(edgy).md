---
title: "Networking busted(edgy)"
date: 2006-10-22
forum: Networking &amp; Wireless
---

### Post by |VeN| on 2006-10-22
OK so iv been running Ubuntu Edgy happily for a few weeks now(was really happy when it was easy to get beryl working on it).The netwrking menu in edgy hasnt been giving me a list of the available networks since i installed it. That was ok though seeing as i just typed in my SSID and key and it connected fine in my apt.
 So ivisted my uncles this weekend and couldnt connect to his wireless hookup(i later found out it was his setup at fault!). So i decided to install network manager through synaptic, clicked apply and error it didnt work as i didnt have the dvd in the drive and obviously no internet connection. Since this incident anytime i try to click on 'Networking' or 'Network Tools' from the drop down menu it screws up and the bug report tool pops up. I would pastre/submit the bug but i have no net connection to do that :(.

So 1. has anyone else encountered this or could guide me through a possible fix via the comand line.

I booted into windows and downloaded networkmanager from teh gnome webby and copied it over to ubuntu. When i run ./configre it gives me the follownig error:

checking for C compiler default output name... configure: error: C compiler cannot create exectuables.

Any idea how to fix this? I though i had the C compiler installed and that it would automatically be able to do that, bt i guess not.

Sorry for the long post, but im new to linux and ubuntu(tried suse but was a pain to get setup how i wanted it).

Anyway any help is appreciated
thx!

---

### Post by joergenlie on 2006-10-23
are you using any encryption? Uninstall network manager, run in terminal: sudo gedit /etc/networking/interfaces

post the outcome here.

Jørgen

---

