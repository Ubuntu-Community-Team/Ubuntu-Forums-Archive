---
title: "sudo apt-get autoremove --purge &lt;package_name&gt; question"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by mikodo on 2010-04-25
Hello everyone,

```
sudo apt-get autoremove --purge <package_name>
```
Will this command remove the package with its' dependencies and associated configuration files, but not remove any** similarly **needed dependencies, for other packages?

Thank you.

---

### Post by mikodo on 2010-04-25
Hi, never mind responding about this. I found in the forums, too many instances of people losing needed dependencies for other packages when using apt-get autoremove, (for multiple reasons). I don't want to risk making a mistake and removing a needed dependency, so I don't think I'll use it.

Thanks.

---

### Post by Linuxforall on 2010-04-25
This one removes config files, not dependencies as thats handled by autoremove only if no other programs are linked to it and the command is sudo apt-get --purge remove <package>

---

### Post by mikodo on 2010-04-25
Thanks.

---

