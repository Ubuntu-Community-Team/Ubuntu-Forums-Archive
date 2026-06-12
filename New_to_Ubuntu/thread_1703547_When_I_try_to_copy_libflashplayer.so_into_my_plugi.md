---
title: "When I try to copy libflashplayer.so into my plugins folder to get flash, I cant."
date: 2011-03-09
forum: New to Ubuntu
---

### Post by defested on 2011-03-09
I try to copy this file "libflashplayer.so" into "usr/lib/chromium-browser/plugins" and it gives me an error saying that I am not the owner and I am unable to do so.

How to I remedy this?

---

### Post by oldos2er on 2011-03-09
Use "sudo" ```
sudo cp libflashplayer.so /usr/lib/chromium-browser/plugins
``` for example.

Or you can just copy it to ~/.mozilla/plugins and Chromium should find it.

---

### Post by wep940 on 2011-03-10
oldos2er:   LOVE the avatar - any idea if she's still alive?

---

### Post by oldos2er on 2011-03-10
Oops--changed my avatar. As far as I know, P. D. is still around. [http://en.wikipedia.org/wiki/Phyllis_Diller](http://en.wikipedia.org/wiki/Phyllis_Diller)

---

