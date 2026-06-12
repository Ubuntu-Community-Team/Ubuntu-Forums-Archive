---
title: "Using a Repository w/ command line"
date: 2011-08-06
forum: New to Ubuntu
---

### Post by RawAwesome on 2011-08-06
So I'm uber new, and I remember my friend showing me this, but since then I've been using the GUI to do everything and I forgot. So this is my first attempt at going CL.

 So... how do I download things using a repository in a command line?

Thanks!

---

### Post by oldos2er on 2011-08-06
To edit sources.list, ```
sudo nano /etc/apt/sources.list
``` run ```
sudo apt-get update
``` when done editing.

Or you can use the add-apt-repository command ```
man add-apt-repository
``` for more info.

Once you've added a repo and refreshed your sources.list, install a package with ```
sudo apt-get install <package name>
``` As always if you need more info, use *man* ```
man apt-get
```

[https://help.ubuntu.com/community/AptGet/Howto](https://help.ubuntu.com/community/AptGet/Howto)

---

