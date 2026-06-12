---
title: "Need help with NAS drive"
date: 2011-03-12
forum: New to Ubuntu
---

### Post by tommygjr on 2011-03-12
I just purchased the Western Digital My Book Live drive. I'm trying to put it on my network it is connected to my router. but I am having a problem putting it on ubuntu.
:confused:

prob need step by step instructions cause i'm really new at this command line stuff.

---

### Post by Paqman on 2011-03-12
You can get access to the NAS on a one-off basis by going to Places  and browsing through your network to the shares on the NAS. The trouble with this is you have to do it that way every time, it won't automatically mount so it's no good for storing a music collection, for example. But it'll give you access for now.

To solve that problem you want to permanently mount the shares to your local machine (what would be called "map network drive" on Windows). Here's how to [set that up]("http://ubuntuforums.org/showthread.php?t=288534"). It's not as complicated as it looks, you install one package, make a couple of quick edits to two files and you're done.

---

### Post by ugm6hr on 2011-03-12
Assuming the address is fixed, you could just add a "bookmark" in nautilus (file browser) to the NAS.
That way, you could access (mount) it by 2 clicks each time.

---

### Post by tommygjr on 2011-03-14
i cant find the fixed address of my drive.

when i go to network its says Unable to mount location Failed to retrieve share list from server

---

### Post by Paqman on 2011-03-15
> **tommygjr said:**
> i cant find the fixed address of my drive.


You can set that yourself in your router's control panel. Normally a router will assign an IP address to devices on your network on-the-fly (called DHCP), but if you want a device to have a specific address then you can reserve one and it'll always be given the same IP. Exactly how you do that depends on your router.

---

