---
title: "Can't type numbers in terminal"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by HarleyDude on 2009-10-14
OK, I am trying to install vlc, it plays audio mp3 but cannot play a video.

Googled help and they said uninstall vlc in terminal and then re-install.

When I copy&paste the command in terminal, it will not allow me to enter numbers which are my password. any help?

---

### Post by Bachstelze on 2009-10-14
Just type your password and press Enter.

---

### Post by marshmallow1304 on 2009-10-14
The terminal does not display anything when you are entering your password.

[http://www.psychocats.net/ubuntu/passwordinterminal](http://www.psychocats.net/ubuntu/passwordinterminal)

---

### Post by tuxxy on 2009-10-14
Its not showing your password characters for security reasons if your using sudo, just tpype them out as normal and hit enter.  Also you may just not have the correct codecs to launch the movies, try installing ubuntu-restricted-extras it includes the popular codecs you need.

```
sudo apt-get install ubuntu-restricted-extra
```

---

