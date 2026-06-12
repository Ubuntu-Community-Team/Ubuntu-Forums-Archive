---
title: "Unblocking Facebook"
date: 2011-01-03
forum: New to Ubuntu
---

### Post by toomanymatts on 2011-01-03
Hi all

So I live in a country where the government intermittently blocks out Facebook.

There are some MacOS workaround instructions that I have come across that I was hoping someone could translate to Linuxese for me...

> in terminal, paste this 

sudo /Applications/TextEdit.app/Contents/MacOS/TextEdit /private/etc/hosts

When the notepad appears, paste this whole thing below beneath line 127.0.0.1 localhost

153.16.15.71 [www.facebook.com](www.facebook.com)
153.16.15.71 [www.login.facebook.com](www.login.facebook.com)
153.16.15.71 facebook.com
153.16.15.71 login.facebook.com
153.16.15.71 apps.facebook.com
153.16.15.71 upload.facebook.com
153.16.15.71 graph.facebook.com
153.16.15.71 register.facebook.com
153.16.15.71 vi-vn.connect.facebook.com
153.16.15.71 vi-vn.facebook.com
153.16.15.71 static.ak.connect.facebook.com
153.16.15.71 developers.facebook.com
153.16.15.71 error.facebook.com
153.16.15.71 channel.facebook.com
153.16.15.71 upload.facebook.com
153.16.15.71 register.facebook.com
153.16.15.71 bigzipfiles.facebook.com
153.16.15.71 pixel.facebook.com
153.16.15.71 upload.facebook.com
153.16.15.71 register.facebook.com
153.16.15.71 bigzipfiles.facebook.com
153.16.15.71 pixel.facebook.com

Then save.

Any help greatly appreciated. 

Matt

---

### Post by overdrank on 2011-01-03
Sorry but this is not supported in the forums. Circumventing restriction Thread closed.

---

