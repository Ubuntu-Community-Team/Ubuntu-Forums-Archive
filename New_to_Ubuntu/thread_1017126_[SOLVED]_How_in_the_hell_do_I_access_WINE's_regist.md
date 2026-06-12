---
title: "[SOLVED] How in the hell do I access WINE's registry?"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by Cadeyrn on 2008-12-20
Self-explanatory. I want to access it so that I can force my WINE installation of Wc3 to have 1440x900 text.

---

### Post by phantomjoker on 2008-12-20
it not exactly what you want, but if you go to applications>wine>configure wine

under the graphics option you can change the screen resolution, the desktop size, and under the desktop intergration option you can change specific text (eg window text) to be a perticular size...

might help?

---

### Post by Cadeyrn on 2008-12-20
No, sorry. That wouldn't affect Warcraft 3.

---

### Post by howefield on 2008-12-20
Have you browsed over here...

[http://www.winehq.org/docs/wineusr-guide/using-regedit](http://www.winehq.org/docs/wineusr-guide/using-regedit)

---

### Post by Carl Hamlin on 2008-12-20
-----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

You access the WINE registry the same way you access the Window registry - by using regedit.exe.

It's locating in the Windows directory on your virtual drive. Mine is located at:

~/.wine/dosdevices/c:/windows/regedit.exe

Give that a shot and let us know how you fare, please.

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAklNhscACgkQyLm4ydrABvfiCgCgyqpDykwPvgULSI39vSN4JYXh
PucAoLpNl7vEo4jHeWsfmj/s3Cuu6LHu
=O+wz
-----END PGP SIGNATURE-----

---

### Post by Cadeyrn on 2008-12-20
Oh... I was looking for it in system32. So it's in a different place? I'll try that XD

---

### Post by mc4man on 2008-12-20
Just as a final point, you can simply enter regedit in a terminal to access.

---

