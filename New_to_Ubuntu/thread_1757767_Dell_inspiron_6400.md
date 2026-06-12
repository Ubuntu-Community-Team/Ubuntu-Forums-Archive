---
title: "Dell inspiron 6400"
date: 2011-05-13
forum: New to Ubuntu
---

### Post by Scout5950 on 2011-05-13
I am very new to this, recently ran live cd version 11 and the wireless driver installed and ran just fine. So liking the OS I went ahead and installed it on my system, Now the wireless card doesnt work and after reading forums for 2 days and trying different tips I havent made any progress. Any help would be great!!!!

---

### Post by wildmanne39 on 2011-05-13
> **Scout5950 said:**
> I am very new to this, recently ran live cd version 11 and the wireless driver installed and ran just fine. So liking the OS I went ahead and installed it on my system, Now the wireless card doesnt work and after reading forums for 2 days and trying different tips I havent made any progress. Any help would be great!!!!

Hi believe that computer uses a broadcom wireless card like mine, all I had to do was go into restricted drivers and activate the card driver and then restart the computer, then type in your password. Let me know if that fixed it or if we need to go further. You will need to plug into a ethernet connection to get the restricted drivers.:)

---

### Post by sandyd on 2011-05-13
You have to have an internet connection for propriety drivers to be installed. This is because they are not installed on the system by default (which is a bit weird I find).

But anyways, you can add the Ubuntu LiveCD as a repo and install the drivers from there.

1. Open  Applications -> Accessores -> Terminal

Type in
```

gksu synaptic
```

After typing in the password, Choose the Software Sources/Repositories menu entry (I don't remember menu its under). Click third party software, slap teh cd in the drive, and add the cd. You should now be able to install the drivers.

---

### Post by Scout5950 on 2011-06-03
Well I ended up going with the ndiswrapper. So far all is working fine a little unsure about the injection and if its working right. And both of your tips worked also THANKS!!!

---

