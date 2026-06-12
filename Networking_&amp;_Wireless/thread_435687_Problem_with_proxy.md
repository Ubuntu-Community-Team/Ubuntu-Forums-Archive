---
title: "Problem with proxy"
date: 2007-05-07
forum: Networking &amp; Wireless
---

### Post by Ximarx on 2007-05-07
I'm deprived of hope. Please help me.

Internet connection in my campus go through squid proxy server and require authentication against proxy using username and password.

Internet connection works only with firefox by setting networking preference. I can't access internet using any different application. wget, apt, lynx... don't work.

I tried setting export http_client=http://username:password@proxy_address:port in /etc/bash.bashrc... nothing
I tried setting proxy configuration in System->preference->proxy........ nothing
i tried setting /etc/apt/apt.conf too, but i don't have any success.

---

### Post by beatbros on 2007-05-25
hi,
you can use this post for wget configuration


[http://ubuntuforums.org/showthread.php?p=2717116#post2717116](http://ubuntuforums.org/showthread.php?p=2717116#post2717116)


bye

---

