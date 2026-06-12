---
title: "Google Earth Linux Won't Run"
date: 2009-03-28
forum: New to Ubuntu
---

### Post by rich1939 on 2009-03-28
I downloaded "GoogleEarthLinux" from Google's website, but it seems to be an "octet stream" and isn't executable. How do I make it executable...particularly just by double-clicking on it?

Thanks

---

### Post by Therion on 2009-03-28
See this tutorial:  [http://tombuntu.com/index.php/2009/03/20/how-to-install-google-earth-5-on-ubuntu/](http://tombuntu.com/index.php/2009/03/20/how-to-install-google-earth-5-on-ubuntu/)



EDIT:  If you get it installed and then Googleearth "crashes" almost immediately after you start it (common issue), do the following...

Go to /home/googleearth and find the file:  **libcrypto.so.0.9.8**

Rename the file to:  OLDlibcrypto.so.0.9.8 or libcrypto.so.0.9.8.bak and try running Googleearth again.

---

### Post by Delta28 on 2009-03-28
Try reading more about it on Google if you still can't figure it out come back here and ask...I really don't want to pile him up with work but Dr Small would be the best person to ask he is my cousin.

---

### Post by hyper_ch on 2009-03-28
I'd add medibuntu repos and add googleearth from there... but then, that's just me :)

---

### Post by rich1939 on 2009-03-28
> **Therion said:**
> See this tutorial:  [http://tombuntu.com/index.php/2009/03/20/how-to-install-google-earth-5-on-ubuntu/](http://tombuntu.com/index.php/2009/03/20/how-to-install-google-earth-5-on-ubuntu/)

EDIT:  If you get it installed and then Googleearth "crashes" almost immediately after you start it (common issue), do the following...

Go to /home/googleearth and find the file:  **libcrypto.so.0.9.8**

Rename the file to:  OLDlibcrypto.so.0.9.8 or libcrypto.so.0.9.8.bak and try running Googleearth again.

I renamed the file **libcrypto.so.0.9.8.bak**, but google earth still crashes. I ran it in a terminal and got the following:

```

Warning: Unable to create prefs directory '/home/richard/.googleearth'. File exists.
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
...
Xlib:  extension "GLX" missing on display ":0.0".

```

...And then **stacktrace from glibc**

Any other suggestions? What the heck is "GLX"?

---

### Post by rich1939 on 2009-03-28
> **hyper_ch said:**
> I'd add medibuntu repos and add googleearth from there... but then, that's just me :)

Could you tell me what/where is **medibuntu repos**? I'm not familiar with that.

Thanks

---

### Post by ibuclaw on 2009-03-28
[Medibuntu]("http://www.medibuntu.org/") is a Third Party buntu Repository which hosts several non-free packages mostly focused around media/home entertainment.

Documentation of how to add it is available on the [Ubuntu Wiki.]("https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories")

Once setup, to install Google Earth:
```
sudo apt-get install googleearth
```

Regards
Iain

---

### Post by hyper_ch on 2009-03-28
or have a look at my signature for repo generator :)

---

