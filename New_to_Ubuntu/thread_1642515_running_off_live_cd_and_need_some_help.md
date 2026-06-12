---
title: "running off live cd and need some help"
date: 2010-12-10
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-12-10
i always use this form but i also have a linux help site and test out all my advise, ran into a problem when i tried to do this. here is link. do not install this deb

[http://www.ubuntugeek.com/how-to-editadd-menu-items-in-ubuntu-10-10-maverick-unity-desktop.html](http://www.ubuntugeek.com/how-to-editadd-menu-items-in-ubuntu-10-10-maverick-unity-desktop.html)
when i install this it really pouched my system
i am now in an old live cd 
i have a separate partition for both my home and system
if i can access the program computer janitor on my partition which i can mount with the live cd i can fix. the only good thing about the program computer janitor is that it is good for completely removing installed deb file. or if anyone has an idea great.
all i get when i boot up reg is a welcome sceen that just has my name and dont list my other computer user.
or maybe if i can access the spm on my mounted partition i could fix. but have no idea how to/rks

---

### Post by rburkartjo on 2010-12-10
also removed the live cd and booted into recovery mode and just for the heck of it removed anything to do with unity. did an autoremove and a purge this did not help though. cant get past a log in screen when normally boot

---

### Post by cariboo on 2010-12-10
If all you want to do is remove the prixefix deb, you will have to chroot your current / partition from the live CD. Assuming you are running Lucid or newer, once at the desktop, open a terminal and type the following commands, pressing enter after each one:

[LIST=1]
[*]sudo mount /dev/sdXx /mnt
[*]sudo mount -o bind /sys /mnt/sys
[*]sudo mount -o bind /dev /mnt/dev
[*]sudo mount -o bind /porc /mnt/proc
[*]sudo chroot /mnt
[/LIST]

/dev/sdXx = your / partition

Once you are at the chroot prompt type the following command to purge prixefix:

```
apt-get purge prixefix
```

I tried to download the package to have a look at it, but chromium throws up a red screen and says the sites security certificate is untrusted, so I'm not going there.

---

### Post by rburkartjo on 2010-12-10
car just some advise before i proceed because that might not be the problem. i also booted into the recovery mode without the live cd

went to the root terminal mode and entered
apt-get purge prixefix

didnt work. if the above didnt work dont think what you advised will work. could be another problem not sure all i did was install the deb. please advise. appreciate  your help.

---

### Post by rburkartjo on 2010-12-10
do you think that trying to reinstall the ubuntu desktop from the recovery mode might help and if so how would i do that, i can always do a reinstall but prefer to find fix. learn a lot more from that

---

### Post by rburkartjo on 2010-12-10
just had to do a re-install no big deal. car tks for your advise. that is why i check out anything we i post a response. i rather have it happen to me. i can fix than someone else/tks

---

