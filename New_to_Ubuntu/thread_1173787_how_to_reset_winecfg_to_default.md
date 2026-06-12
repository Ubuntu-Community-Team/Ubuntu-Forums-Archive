---
title: "how to reset winecfg to default"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by smokystone on 2009-05-30
[SIZE=3]Hi, I have done a quite stupid mistake, I have to say. I have ticked "emulate a virtual desktop" in windcfg, but accidentally set the window size to 1*600. Now the windows look like a stick. Worst, I can't set it back because I can't see the configuration window. 
What should I do now? How can I set it back to default size 800*600.

Thanks a lot

:(:(:(
[/SIZE]

---

### Post by CatKiller on 2009-05-30
The resolution that Wine uses for the emulated desktop is stored in the HKCU\Software\Wine\Explorer\Desktops registry entry. Since you can't run regedit because of your problem, and because the pretend registry is just a text file, you can change this manually. Open up ~/.wine/user.reg and look for this value. Change it to what it should be.

---

### Post by smokystone on 2009-05-30
> **CatKiller said:**
> The resolution that Wine uses for the emulated desktop is stored in the HKCU\Software\Wine\Explorer\Desktops registry entry. Since you can't run regedit because of your problem, and because the pretend registry is just a text file, you can change this manually. Open up ~/.wine/user.reg and look for this value. Change it to what it should be.


Really thanks, exactly as you said.

Just in the user.reg, [Software\\Wine\\Explorer\\Desktops] 1243667579
"Default"="800x600"

Then it's done.

Thanks again.:)

---

### Post by CatKiller on 2009-05-30
No worries. Welcome to the community.

---

