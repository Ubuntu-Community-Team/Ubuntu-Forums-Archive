---
title: "How can I install gfortran in my Ubuntu 10.04 from outside source?"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by MGTHEBOSS on 2011-02-21
In my Ubuntu I don't have gfortran.I can't install it from Synaptic Package Manager because I see it's not there.I have downloaded gfortran from this link :
[http://gfortran.org/download/i686/](http://gfortran.org/download/i686/)
It was a tar file.I extracted it using Winrar.
But I don't know how to install it in my Ubuntu.Please help.

---

### Post by marl30 on 2011-02-22
> **MGTHEBOSS said:**
> In my Ubuntu I don't have gfortran.I can't install it from Synaptic Package Manager because I see it's not there.I have downloaded gfortran from this link :
[http://gfortran.org/download/i686/](http://gfortran.org/download/i686/)
It was a tar file.I extracted it using Winrar.
But I don't know how to install it in my Ubuntu.Please help.
I just checked Synaptic package manager and it has it there. I'm using 10.10. Then again, I have quite a few third party ppas added. I could provide you with that ppa if only I could find how to know which it's connected to.

---

### Post by Synthetic Sam on 2011-02-22
This package should be available in lucid, try typing this into a terminal:

```
sudo apt-get update && sudo apt-get install gfortran -y
```

If that doesn't work, open synaptic package manager, and check in Settings > Repositories that Main is selected (no reason that it shouldn't be), then try again.  Make sure Synaptic is closed when you try to run the command.

---

### Post by Synthetic Sam on 2011-02-22
> **marl30 said:**
> I just checked Synaptic package manager and it has it there. I'm using 10.10. Then again, I have quite a few third party ppas added. I could provide you with that ppa if only I could find how to know which it's connected to.
Change to view packages by origin using the button at the bottom left of the package manager.  In mine it's in maverick/main (gb.archive.ubuntu.com). When you search for it, if a package has the ubuntu symbol next to it in the list, it's an indication that it's an officially supported package from the ubuntu repos.

---

### Post by marl30 on 2011-02-22
> **Synthetic Sam said:**
> Change to view packages by origin using the button at the bottom left of the package manager.  In mine it's in maverick/main (gb.archive.ubuntu.com). When you search for it, if a package has the ubuntu symbol next to it in the list, it's an indication that it's an officially supported package from the ubuntu repos.
Thanks for this suggestion. And yes, it has the Ubuntu symbol beside it. That means it's in the repository.

---

### Post by deconstrained on 2011-02-22
OP, FFR: use 'apt-cache search'. It even accepts POSIX-style regex, and searches not only the package title but the description as well.

---

### Post by MGTHEBOSS on 2011-02-23
> **Synthetic Sam said:**
> This package should be available in lucid, try typing this into a terminal:

```
sudo apt-get update && sudo apt-get install gfortran -y
```

If that doesn't work, open synaptic package manager, and check in Settings > Repositories that Main is selected (no reason that it shouldn't be), then try again.  Make sure Synaptic is closed when you try to run the command.
Thanks for your help.

---

