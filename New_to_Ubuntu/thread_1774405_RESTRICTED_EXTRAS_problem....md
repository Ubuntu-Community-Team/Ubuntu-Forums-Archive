---
title: "RESTRICTED EXTRAS problem..."
date: 2011-06-03
forum: New to Ubuntu
---

### Post by ishueli on 2011-06-03
I am unable to install UBUNTU RESTRICTED EXTRAS. Whenever I try to install from 'Software Center' I get the message to remove the following 2 files - 

Libav codec library (libavcodec 52)
Libav utility library (libavutil 50)

If I click 'Install Anyway' it does not load anything.

Can someone give me a solution to this. Without the extras i guess I cant watch any videos in VLC player.

Regards

---

### Post by TeoBigusGeekus on 2011-06-03
Open Synaptic Package Manager, try to locate these two packages and remove them.

---

### Post by ishueli on 2011-06-03
Dear TeoBigusGeekus

Thanks for your advise. I removed the packages from using synaptic manager and then managed to get restricted extras with following command

$ sudo apt-get install ubuntu-restricted-extras --fix:missing

This command installed the package, which eventually allowed me to seamlessly install VLC player. I had to then install dvdread package to play the DVD's.

Once again thanks for your guidence.

Regards

---

