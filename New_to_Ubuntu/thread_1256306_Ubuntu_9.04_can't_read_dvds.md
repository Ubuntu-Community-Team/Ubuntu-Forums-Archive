---
title: "Ubuntu 9.04 can't read dvds"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by susan.kamal on 2009-09-02
Hi,

I just tried to play a dvd that is not encrypted and ubuntu reads the name of the dvd and shows that there are two folders on it but the files on the dvd ( video/audio ) are not shown inside those folders. I tried the dvd on windows and it's working fine. Any help?

Thanks

---

### Post by issih on 2009-09-02
Have a read here..

[https://help.ubuntu.com/community/RestrictedFormats/](https://help.ubuntu.com/community/RestrictedFormats/)

Hope that helps

---

### Post by philinux on 2009-09-02
And the medibuntu link below.

Although it's not encrypted it may need certain codecs installing.
From the link see "Playing Non-Native Media Formats".

---

### Post by NightwishFan on 2009-09-02
Do as philinux suggests. To play encrypted dvds you need the libdvdcss2 library in medubuntu.

---

### Post by issih on 2009-09-02
you no longer need to install the medibuntu repositories to get the css decoding packages, the page at:

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

Within my original link shows the slightly more user friendly techniques now generally suggested instead.

Nonetheless, reading the whole section would benefit any new user, as it covers a lot of multimedia issues fairly thoroughly.

Generally I'm on a promoting the existing documentation kick at the moment :)

---

### Post by susan.kamal on 2009-09-02
guys i did all the suggested things already and its still not working..

---

### Post by mapes12 on 2009-09-03
If you have installed ububtu-restricted-extras and the recommended codecs from medibuntu then I would try an alternative player. I have had more success with Xine and VLC than I have with the default Movie Player.

---

### Post by kansasnoob on 2009-09-03
What version of Ubuntu are you running?

Post the output of:

```
cat /etc/issue
```

---

