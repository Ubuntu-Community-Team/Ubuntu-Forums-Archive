---
title: "google earth and flash player..."
date: 2011-08-16
forum: New to Ubuntu
---

### Post by werty2010 on 2011-08-16
when i enable and try to view certain things in google earth like youtube and cousteau videos, it gives me this message:
```

....
Viewing this content requires Adobe Flash player, but it is not installed.
...

```

Flash player, at least on firefox, works great.
some help to figure this out?

---

### Post by sanderd17 on 2011-08-16
The problem is that the Linux version of Google Earth is in fact the same as the Windows version, with Wine packed inside it.

So Google Earth is searching for Flash inside the Wine installation of that program. But there is no Flash inside that Wine installation. 

This is what the reason for the problem is, but I don't know how you can solve it. Maybe there is no sollution with the Linux version of Google Earth. 

It may be possible to install the Windows version Google Earth inside Wine and also install Flash inside Wine. But I never tried it, and Wine can always be tricky.

---

### Post by haqking on 2011-08-16
mmm

You mean when you click on a youtube marker and view the video ?

Works fine for me.

I am running 10.10 meerkat with flash aid recenlty but recently upgraded to the Flash11 beta from adobe for 64 bit which works great.

Google earth has always workd including youtube.

My google earth version details are as follows.
 
  5.1.3533.1731
   Build Date
  Nov 11, 2009
   Build Time
  4:39:12 pm
   Renderer
  OpenGL
   Operating System
  Linux (2.6.35.0)
   Video Driver
  NVIDIA Corporation
   Max Texture Size
  8192x8192
   Server
  kh.google.com

---

### Post by oldos2er on 2011-08-16
I would love to know how you got it to work. Filed this bug [http://bit.ly/n0vdU2](http://bit.ly/n0vdU2) but all Google says is flash isn't supported on Linux.

---

### Post by werty2010 on 2011-08-16
> **oldos2er said:**
> I would love to know how you got it to work. Filed this bug [http://bit.ly/n0vdU2](http://bit.ly/n0vdU2) but all Google says is flash isn't supported on Linux.

+1

haqking if you or anyone else actually made it work please post a link/some info for the rest of us

---

### Post by haqking on 2011-08-16
> **werty2010 said:**
> +1

haqking if you or anyone else actually made it work please post a link/some info for the rest of us

i havent dont anything other than a standard install.

Actually i just went to Google page to download latest version.  which is version 6.

I have both versions installed now, google 6 gives me the flash plugin message.

My previous version stilll works fine though ;-)

---

