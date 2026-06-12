---
title: "Ubuntu Software Center Crashed, What should I do?"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by Isyaltut on 2010-10-15
I just tried to install opera deb file, and since in Ubuntu 10.10 it's not handle by gdebi anymore, instead Ubuntu sofware center take over. The problem is it keeps showing applying changes and then just crash, poof. 

Well, first thing i do is run sudo dpkg --configure -a to repair potentially broken packages. I thought all will be well, but it turns out it's not. When I try to install gimp through the terminal it shows " The package opera needs to be reinstalled, but I can't find an archive for it." I attach screenshot below. Now what should I do, because whenever i tried to install new program or update it kept showing me this message?

[ATTACH]172500[/ATTACH]

---

### Post by Isyaltut on 2010-10-15
Nevermind, just solved it with sudo dpkg -i opera.deb

---

