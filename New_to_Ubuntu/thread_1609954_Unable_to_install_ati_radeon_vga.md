---
title: "Unable to install ati radeon vga"
date: 2010-10-31
forum: New to Ubuntu
---

### Post by thinkLinuX on 2010-10-31
hi all, i need assistance in the device and hardwares. my cairo dock open gl innable to load due to what i have found, no ati adapter. i try to install the driver but not sure where to start. any advise?
Thank you.

---

### Post by Mark Phelps on 2010-10-31
What make and model is your radeon card? If you don't know for sure, open a terminal and enter "lspci" -- and look for the line containing "VGA".

If it's NOT one of the newer HD 3xxx/4xxx/5xxx cards, there is NO driver you can load --because the only driver that will work is ALREADY installed -- the open-source driver.  Downloading and forcing the installation of anything else is only going to hose up your display, forcing you to boot into a console, remove the drivers your forced, and reinstall the same drivers you already have in place.

---

