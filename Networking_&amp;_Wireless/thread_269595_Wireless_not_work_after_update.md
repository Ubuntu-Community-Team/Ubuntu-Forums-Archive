---
title: "Wireless not work after update"
date: 2006-10-02
forum: Networking &amp; Wireless
---

### Post by Zerocool10482 on 2006-10-02
Hi, I did an update a few days ago. And after that I was away from my pc. For some reason my wireless stopped working.

I tried to deactivate and reactivate my network. But it's not working. I can get my wireless to work in windows for some reason. So the connection is work. But the networking setup is not working.

What do I do to fix this. Are there steps?? I really hope the updated didn't brake anything else. But not sure.](*,) 

I have a D-Link WDA-1320. It worked right out of the box for months. Now I'm stuck.

Help?

---

### Post by wieman01 on 2006-10-02
Are you using "ndiswrapper" or anything for your wireless card? I have experienced the same thing again & again... In particular kernel upgrades break wireless networking for a reason unknown to me. So frankly, I simply stopped upgrading at all. Stick to the current version of my kernel and that's it. Won't uprade until it is really necessary.

BTW: Wireless was not the only thing that would not work after an upgrade.

---

### Post by darth_vader_ca on 2006-10-02
Hi, are you using any encryption on your wireless, as well what type of router are you using, the last suggestion with ndiswrapper if used would be to unbind the driver and reinstall the driver. if it worked out of the box without any intervention, uninstall the eth0 or wifi adapter and reinstall.

cheers.

---

### Post by Zerocool10482 on 2006-10-02
How do I uninstall and reinstall. Do you mean physically? Or in networking. I'm not using ndiswrapper. It just worked out of box.

---

### Post by darth_vader_ca on 2006-10-02
you can try to physically uninstall and reinstall as well as the networking. I think the adapter you have is a pci card correct, as well you can try ndiswrapper for a backup procedure. have you ever used ndiswrapper before?

cheers

---

### Post by justinol on 2006-10-02
i had the exact same thing and i must say this is a major problem for me. 

i was able to update my edgy using the package manager. but then i decided to try and get beryl working. which meant i had to type in the sup apt get type update and upgrade commands.

BEFORE THIS MY EDGY EFT WIRELESS WORKED GREAT. but a quarter of the way into the apt upgrade part was when the connection was lost. the funny thing it actually knocked my network out as well (i had to pull the power cord out my netgear WGT-624 router and put it back in to get my wireless network working again).

after resetting my router i get netwrok/internet access fine on my windows machine, but now everytime i try to access any ubuntu update or even firefox and the connection (and my network overall) gets knocked out and i have to reboot the router (pull the power out and then put back in).

cheers

---

### Post by tripplep on 2006-10-03
I had the same problem. After I updated Dapper wireless was working like a traffic light (on/off/on/off/on/off...). Strangely it work now like a sharm. Not much of a help for you though (sorry).

Regards

---

### Post by Zerocool10482 on 2006-10-30
Ok, I got everything to work. It was dust in the pci slot.

---

