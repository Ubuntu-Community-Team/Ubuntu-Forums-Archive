---
title: "NetworkaManager + WEP problem"
date: 2006-08-28
forum: Networking &amp; Wireless
---

### Post by cokhavim on 2006-08-28
Hello,

NetworkManager isn't connecting to my wireless network when I type in my WEP key.  However, wifi works with ifup/down.  Can anyone tell me what's wrong, and how I can fix this?  I really like nm-applet, and I'd rather not give it up.

Thanks.

---

### Post by cokhavim on 2006-08-29
I found a solution: 

network manager for some reason doesn't do well with WEP.  i had to &#8220;connect to other wireless network&#8221; and use the WEP 24/128-bit HEX and enter the password.  then it asked me for a keyring password.  weird.  (from [http://www.ubuntuforums.org/archive/index.php/t-187571.html](http://www.ubuntuforums.org/archive/index.php/t-187571.html))

---

