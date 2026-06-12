---
title: "Problems with photobucket"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by philbeckwith on 2009-11-04
Hi all!

I am using Ubuntu 9.04.  When I use photobucket, I can't see the button to upload files.  I have IcedTea Java Web Browser Plugin installed (as well as shockwave flash, but I don't know if that is necessary).  I have photobucket's instructions about enabling cookies, clearing cookies, enabling javascript, making a new password and so on, but so far nothing has worked.  Can anybody tell me what gives?

Thanks in advance

Philip

---

### Post by edin9 on 2009-11-04
> **philbeckwith said:**
> Hi all!

I am using Ubuntu 9.04.  When I use photobucket, I can't see the button to upload files.  I have IcedTea Java Web Browser Plugin installed (as well as shockwave flash, but I don't know if that is necessary).  I have photobucket's instructions about enabling cookies, clearing cookies, enabling javascript, making a new password and so on, but so far nothing has worked.  Can anybody tell me what gives?

Thanks in advance

Philip

Remove all the Iced Tea stuff and install sun-java6-jre and sunjava6-plugin. In Terminal run; ```
sudo aptitude install sun-java6-jre sun-java6-plugin
```  _**After removing the Iced Tea stuff!**_

---

### Post by philbeckwith on 2009-11-04
Sadly, it didn't work.  Any other ideas (anyone)?

PS: Thanks a lot though!

---

### Post by mechro on 2009-11-05
Are you using adobe-flashplugin Shockwave Flash 10?

---

