---
title: "major sound issues"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by Caletara on 2009-01-09
I have successfully been able to play rm's now, but i had previously installed realplayer. And it screwed up all the sound on my computer and everything is distorted. I can't figure out how to uninstall it. It's so bad I'm ready to completely reinstall ubuntu, but I have a dual boot with XP. I tried going into partition magic and deleting the linux partition, but it doesnt recognize the format. I tried reinstalling ubuntu with the guided partition, but it only sees the ubuntu parition i want to over-ride, not the xp parition i want to dual boot with.
Please help, I'm at my wits end here. I need my sound to work for work and medical reasons.

---

### Post by wolfen69 on 2009-01-09
choose manual partition and select the ext3 partition to install to.

---

### Post by Caletara on 2009-01-09
Parition magic shows that I have an ext3, extended and a swap partition. Should I still use ext3?

---

### Post by linux_tech on 2009-01-09
ext3 should work

---

### Post by Caletara on 2009-01-09
It's telling me there is no root file system defined.

I manually uninstalled (i think?) all of realplayer in terminal but the sound is still funky--at start up it's loud and crackly. Most sound is, DVD's are fine, YouTube is occassionally funky, but my mp3's and avi's, ogg video and music files are all completely distorted. Is there a way to fix this? RealPlayer obviously did something to my entire sound system...

---

### Post by Caletara on 2009-01-09
Thanks so much for your help! I screwed around with  it and it seems when realplyer installed it upped the PCM mixer to an unfathomly  loud level and screwed everything up. I played with the settings and i think it's working again.

Thanks so much!

---

