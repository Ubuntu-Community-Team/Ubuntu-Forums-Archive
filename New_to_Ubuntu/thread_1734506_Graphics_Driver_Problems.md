---
title: "Graphics Driver Problems"
date: 2011-04-20
forum: New to Ubuntu
---

### Post by PPowerHouseK on 2011-04-20
Hello all, 

I am currently running Ubuntu 10.10 x64 on Vmware. I also have a GeForce GTS 450 graphics card. After installing ubuntu-desktop and doing sudo apt-get install nvidia-current, I am still unable to use the desktop effects feature. In other words, when I try to select normal or extra effects it just goes back to no effects after displaying the error: "Desktop Effects Could Not Be Enabled."

There appears to be no proprietary drivers installed either. As nothing shows up under System>Administration>additional drivers

When I went to the Nvidia website and selected the proper driver, I tried to install it and it prompted, "no supported GPU's found." But it was definitely the correct driver, according to their site.

I would greatly appreciate any help on this, as I would like to see Ubuntu in action with proper display drivers installed. I will gladly supply more information if needed.

---

### Post by falko on 2011-04-20
> **PPowerHouseK said:**
> I am currently running Ubuntu 10.10 x64 on Vmware.That is the problem. If you want to use desktop effects, you must use a physical machine (so that it has direct access to the graphics card).

---

### Post by torgrot on 2011-04-20
You could always try booting it with WUBI then you would have access to the physical hardware and if (god forbid) you don't like Ubuntu, it is a fairly painless uninstall and you are back to windows.

---

