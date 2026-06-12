---
title: "wget during cli"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by dzon65 on 2010-10-21
A good while back I had to do a ubuntu (debian actually) install on a iMac G3.The xorg.conf file had to be edited during the cli install,otherwise it simply wouldn't work.Now,the only xorg.conf for this particular model is a huge one and to finish it off,for some weird reason,the ,how to say,cli screen is of center,the first four letters can't be seen.Today,I received the exact same model.I really don't feel like typing that big file again,so I was wondering if it's possible to install it during cli with the wget command.I have a site where to download it from but I have no idea how to replace the existing one with the new one.
Should be something like wget//http....../boomer
                                     cp boomer xorg.conf
But I'm really guessing here.Any help appreciated.
Regards,J.

---

### Post by marshmallow1304 on 2010-10-21
```
wget http://somesite.com/folder/file
mv file /etc/X11/xorg.conf
```


Edit: Oops, thanks LowSky.

---

### Post by LowSky on 2010-10-21
Just a quick thing i notice was wrong with marshmellow1304 instructions

the xorg.conf folder is located at

```
/etc/**X11**/xorg.conf
```

---

### Post by dzon65 on 2010-10-21
That's mv,not cp wright?
And yes,X11 was a missing part.
Cool,gonna give it a try,thanks guys!
Kind regards,J.

---

