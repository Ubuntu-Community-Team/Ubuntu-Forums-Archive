---
title: "Grub on lucid not loading Karmic"
date: 2010-03-20
forum: New to Ubuntu
---

### Post by mcoleman44 on 2010-03-20
Ok, so i had karmic, then I installed lucid alpha 2 a few weeks ago. I upgraded alpha 3 to beta 1 befor I saw the warning that it mucked things up with nautilus. Now when I choose karmic from grub i get a black screen. Keep in mind that lucid will still boot though. But it wont load the desktop
All I can do is move the mouse around. I just really need to get back into Karmic. Any ideas? 

Thanks!

---

### Post by bumanie on 2010-03-20
The fix is out for the nautilus issue in lucid. To fix, choose recovery mode at the grub screen. Use arrow buttons to choose 'drop to shell prompt' (or something to that effect). Then where the root# is, type > sudo apt-get update && sudo apt-get upgrade and updates will install. This should allow lucid to load properly. Unfortunately, I am not up to speed with grub 2 yet, so can't help too much with grub and booting karmic. I too run karmic and lucid and have karmic dual booting windows with grub 2 installed in the mbr, I then got grub2 to boot lucid from it's own partition, but I am not sure I am competent enough to take you through it step by step and would need to know more about your setup, as in how many hard drives, what OSes on the computer etc. But certainly, by going into recovery and the shell prompt, you should get lucid working again.

---

### Post by mcoleman44 on 2010-03-21
Well... I have lucid working. Sort of. I updated and upgraded and got x to start. Then when I entered my password it would take me right back to the login. So I purged gdm and reinstalled gdm. Rebooted and can login now. When I login however, all that is there is a white terminal at the top left corner. I started gnome panel from this terminal and also started metacity. But I still cant interact with my desktop? Any way to fix those problems?

---

