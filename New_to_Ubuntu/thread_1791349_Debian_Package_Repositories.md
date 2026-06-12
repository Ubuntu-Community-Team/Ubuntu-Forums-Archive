---
title: "Debian Package Repositories"
date: 2011-06-26
forum: New to Ubuntu
---

### Post by JohnBonne on 2011-06-26
[FONT=Georgia]First I went to the install guide I intend to use[/FONT]: [http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html#2](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html#2) and I found an apt-get guide I have used in Ubuntu before. At least the apt-get command is there. I would like to know if these sources are good to use in ubuntu. They have a strong base of followers. 

There are these commands there and I have never seen them in the forums. This got me to wondering if I have missed something or have just come upon something which will help me to keep my systems running?

```

#Local Mirror  deb ftp://ftp.us.debian.org/debian/ stable main contrib non-free  deb-src ftp://ftp.us.debian.org/debian/ stable main contrib non-free   #Security Updates  deb ftp://ftp.us.debian.org/debian-security/ stable/updates main contrib non-free  deb-src ftp://ftp.us.debian.org/debian-security/ stable/updates main contrib non-free

```

---

### Post by Bachstelze on 2011-06-26
Those are the Debian repositories. In general, the Ubuntu repositories contain the same packages, but compiled for Ubuntu, so you should not need to modify anything in your sources.list. Just proceed to the next step.

---

