---
title: "Can't play DVDs on Intrepid!"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by mag1strate on 2008-12-21
I have intrepid x64 on an AMD^64 system and I can't seem to get any of my dvds to work on my system. I installed mplayer hearing it could work, but it only plays it scrambled. Is there anything I can install for the players to work?

---

### Post by night_fox on 2008-12-21
Have you installed ubuntu-restricted-extras?

---

### Post by laurielegit on 2008-12-21
It could be that your dvds are incrypted. If so, try this:
>  
The movie players provided in Ubuntu can play back unencrypted DVDs. However, many commercial DVDs are encrypted with a weak algorithm called Content Scrambling System (CSS).You can enable playback of encrypted DVDs with MPlayer, xine and Totem-xine by installing libdvdcss2.

The CSS key sets are licensed to manufacturers who incorporate them into products such as DVD drives, DVD players and DVD movie releases.Most DVD players are equipped with a CSS Decryption module.

Installing libdvdcss2

First you need to install the libdvdread3 package using the following command

sudo apt-get install libdvdread3

Now download the libdvdcss2 library using the following command

sudo /usr/share/doc/libdvdread3/install-css.sh

For AMD64 Users

First you need to install the following packages

sudo apt-get install debhelper build-essential fakeroot

Now download the libdvdcss2 library using the following command

sudo /usr/share/doc/libdvdread3/install-css.sh


That’s it now Your DVD player should now play back encrypted DVDs.You can open your Movie player from Applications > Sound & Video

Best of luck,

Laurie

---

### Post by jimmy the saint on 2008-12-21
ubuntu-restrictd-extras should do the job and it is dead simple.  
One final method, which I only mention because it will also make it easy to install some other very cool things as well.
If you add the medibuntu repository, you get access to a few extras like google earth, some good codecs and a few others.  Details here:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by night_fox on 2008-12-21
Ramen!

---

### Post by Tatty on 2008-12-21
As Jimmy the saint said, you need to add the medibuntu repo, then you can install the libdvdcss2 package from there.

[https://help.ubuntu.com/community/Medibuntu#Playing](https://help.ubuntu.com/community/Medibuntu#Playing) Encrypted DVDs


If it still fails to work then you may need to install regionset, and use it to set your dvd region.

---

