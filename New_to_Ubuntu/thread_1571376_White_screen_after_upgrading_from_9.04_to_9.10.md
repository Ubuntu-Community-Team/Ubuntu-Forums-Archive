---
title: "White screen after upgrading from 9.04 to 9.10"
date: 2010-09-09
forum: New to Ubuntu
---

### Post by patC42 on 2010-09-09
I had windows on the first 60GiB, ubuntu 9.04 root on 11GiB and home on the next 68 GiB, with Ubuntu 10.4 on 11GiB and swap on the last GiB.

I decided to bite the bullet and upgrade via update manager 9.04 to 9.10 but unfortunately now when I boot into  the old 9.04 it goes to a white screen.

I have looked at it with gparted and root looks empty but home looks just the same.

root has been renamed 9.04_roo and when I select information it just says could not find mount point.

I probably can't get back to how it was, but have a copy of 9.10 on a USB stick is there a way to install 9.10 into the root partition and connect to the old home partition that was 9.04 home.

Thank you in advance tor any help you are able to give.

I have screen shots of gparted but don't know how to include them with this post

---

### Post by Peter09 on 2010-09-09
White screen most probably means that you are having a problem with your video drivers. You need to find out what your graphics card is. Try going to recovery mode  and selecting the reconfigure graphics option.

---

### Post by bodhi.zazen on 2010-09-09
Or compiz, white screen of death is (was) a classic for compiz.

---

### Post by Gone fishing on 2010-09-09
> Or compiz, white screen of death is (was) a classic for compiz.

That is what I was thinking, when you upgraded the user account had desktop effects enabled but the upgrade hasn't installed the video drivers necessary to run the effects.

I think if you create another account from a terminal alt control F2 

sudo useradd -m username then sudo passwd username you will be able log in using that account. To fix the problem you will need to get the video drivers working.

---

### Post by patC42 on 2010-09-11
Thank you all for your responses. As I remember I did have some effects running on the old 9.04 so the video drivers could well be the problem. The home partition looks fine. The new root looks good except that it has an empty home folder. I tried redirecting the fstab to the old home location which didnt work. So video drivers it is. I will see what I can do in recovery mode before reinstalling 9.10 from scratch on the old root. Thanks once again.

---

### Post by Gone fishing on 2010-09-12
I can think of two ways of allowing you to get a graphical admin login back. If you login to a shell Alt Control F1 then you could remove the .compiz and .gconf? using the rm command I think you would be as you were before you enabled desktop effect i.e. no white screen of death.

The other method I've private messaged to you.

---

