---
title: "upgrading from 8.04"
date: 2010-11-12
forum: New to Ubuntu
---

### Post by Dermot Doyle on 2010-11-12
Hi All,
I want to upgrade from 8.04 and have been advised on this site to go up one at a time through 8.10, 9.04, 9.10 and 10.04 rather than a clean install to save all my files etc (I have backed everything up on a separate hard drive and I'm aware it will take some time having upgraded my other computer from 9.04 to 9.10). When I try to upgrade with the Update Manager I get 'Couldn't find the release notes - The server may be overloaded'. I've tried this enough times now over the past week to be suspicious. Am I trying to do something impossible? Is 8.10 no longer downloadable and if so, will I have to go for a clean install? I really don't want to if I can avoid it. I'm not very computerate and I have a lot of music and photos to not get mixed up. It's taken me long enough to get where I am even now.
Thanks for any advice.

---

### Post by Malta paul on 2010-11-12
I would recomend a clean instalation as you have a backup of your files you can the restore them afterwards. All those updates may get mixed up a bit where as a clean intalation will be stright forward.:)

---

### Post by beew on 2010-11-12
Clean install for sure. Upgrade may break things without you even knowing it until later, and it would be difficult to diagnose. Moreover a clean install is a lot faster, takes about 15 minutes to install 10.10 from usb and maybe half an hour to install all your apps. Upgrade from 10.04 to 10.10 alone would take hours and upgrading from 8.10 would definitely takes lot longer if you have to go through all the intermediate upgrades.

---

### Post by lobralleo on 2010-11-12
Have you tried to change the update server? You can do it using the Software Sources tool, go to System > Administration > Software Sources and change the download server to another. This could help.
As a side note, I've tried the step-by-step update myself and, although it is generally reliable, it's a potential pain and will take a lot of time. Also, this process is likely to leave behind a lot of useless garbage (config files and the like).
If you can backup your data, I would definitely recommend a fresh install.

---

### Post by ibizatunes on 2010-11-12
if you have 8:04 you can go straight to 10:04 personally i would do clean install but its up to you!

---

### Post by Dermot Doyle on 2010-11-12
Okay, I'm convinced if slightly nervous. Where can I download 10.04 LTS to burn onto a CD and will it come with idiot-proof instructions?
Cheers

---

### Post by Rex Bouwense on 2010-11-12
Dermot you can download 10.04.1 here:  [http://iso.linuxquestions.org/ubuntu/ubuntu-10.04.1/](http://iso.linuxquestions.org/ubuntu/ubuntu-10.04.1/).  Installation instructions are the same as before.  Download it.  Run the md5sum.  Burn the ISO to a CD.  Install.  Any problems bring them up here.

---

### Post by Dermot Doyle on 2010-11-12
Thanks everyone, I'll upgrade over the weekend and no doubt be asking for help next week.

---

### Post by ssulaco on 2010-11-13
> **Dermot Doyle said:**
> Hi All,
I want to upgrade from 8.04 and have been advised on this site to go up one at a time through 8.10, 9.04, 9.10 and 10.04 rather than a clean install to save all my files etc (I have backed everything up on a separate hard drive and I'm aware it will take some time having upgraded my other computer from 9.04 to 9.10). When I try to upgrade with the Update Manager I get 'Couldn't find the release notes - The server may be overloaded'. I've tried this enough times now over the past week to be suspicious. Am I trying to do something impossible? Is 8.10 no longer downloadable and if so, will I have to go for a clean install? I really don't want to if I can avoid it. I'm not very computerate and I have a lot of music and photos to not get mixed up. It's taken me long enough to get where I am even now.
Thanks for any advice.
Back up your important stuff,whether upgrading or reinstalling....things go wrong

> **ibizatunes said:**
> if you have 8:04 you can go straight to 10:04 personally i would do clean install but its up to you!
I would try upgrading first,if it fails,then reinstall.......ibizatunes is correct,you can upgrade LTS-LTS
if you want to try upgrading.....check this,go to System -> Admin -> Software Sources click updates tab at the bottom where it says "show new distribution releases"click "long term support releases only" close software sources and see if you get an option to upgrade to 10.04.1 in update manager.....if you do decide to upgrade I recommend disabling any PPA's  and proprietary drivers you have installed i.e. (nvidia)

---

