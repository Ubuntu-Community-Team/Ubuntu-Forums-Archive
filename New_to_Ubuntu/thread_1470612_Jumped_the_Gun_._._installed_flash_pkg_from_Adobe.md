---
title: "Jumped the Gun . . installed flash pkg from Adobe"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by GregA on 2010-05-03
Since it's been a couple years from my last Ubuntu install, I forgot the overall process to add the "extra-restricted" packages. So I downloaded the latest flash version from Adobe and installed it using their script.  

It works fine, no issues, but now I'm wanting to install the other restricted packages via "sudo apt-get install ubuntu-restricted-extras" . . . . so, my question is, do I need to uninstall flash first?  (e.g., what happens when a package is already installed, will the apt-get command hang and not completed the other package installs?)

Thanks,

Greg

---

### Post by Zayfox on 2010-05-03
Pretty sure it'll detect you've got it installed and skip it, it won't matter either way, but it's not going to hang or mess up if that's what you fear.

---

### Post by tom.swartz07 on 2010-05-03
> **GregA said:**
> Since it's been a couple years from my last Ubuntu install, I forgot the overall process to add the "extra-restricted" packages. So I downloaded the latest flash version from Adobe and installed it using their script.  

It works fine, no issues, but now I'm wanting to install the other restricted packages via "sudo apt-get install ubuntu-restricted-extras" . . . . so, my question is, do I need to uninstall flash first?  (e.g., what happens when a package is already installed, will the apt-get command hang and not completed the other package installs?)

Thanks,

Greg

It'll probably overwrite it, or it will just say that its already there. 

No bigs... If you want you could re-run it afterwards to make sure you have the latest version

---

### Post by ddecator on 2010-05-03
It's recommended that you remove the installed version of Flash just in case. If you used the .deb from Adobe, you can open the Synaptic Package Manager, search for Flash, find which listing for Flash is installed, uninstall it, then install the ubuntu-restricted-extras package.

---

### Post by 3rdalbum on 2010-05-03
Mark ubuntu-restricted-extras for installation, and then unmark flashplayer-installer.

---

### Post by GregA on 2010-05-03
Thanks guys . . . . I'll take some time tomorrow and remove flash first, and then go thru the install of the restricted-extras.  PS,, I'm liking Lucid so far, but it was a much tougher and longer install on my older PC (HP A250N) than Hardy was - - - took almost 2 hours for the install itself, but finally got it done.

---

### Post by mc4man on 2010-05-03
> I'll take some time tomorrow and remove flash first,
There's no need to, ubuntu-restricted-extras is just a bunch of recommends, if something(s) already installed it won't touch it.

If you'd like to see just search u-r-e in synaptic, right click on the package - click on the 'mark recommends for install'
Whatever's greyed out is already installed, ect.

---

