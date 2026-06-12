---
title: "adding gpg key file?"
date: 2010-12-13
forum: New to Ubuntu
---

### Post by Mazehero55 on 2010-12-13
I need to add a gpg key file for a repository I added to my sources.list, but I need to do it from the terminal. I've googled but can't find out what I need, anyone got any ideas? I'm sure it's just a command or two.

Thanks

---

### Post by plucky on 2010-12-14
> **Mazehero55 said:**
> I need to add a gpg key file for a repository I added to my sources.list, but I need to do it from the terminal. I've googled but can't find out what I need, anyone got any ideas? I'm sure it's just a command or two.

Thanks

Try ```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys DB141E2302FDF932
``` where you substitute DB141E2302FDF932 for the key that you need for your repository.


Good Luck

---

