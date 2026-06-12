---
title: "software management system - failure"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by michaeltobin on 2008-12-12
This comes up when i open any package manager or add/remove, not sure what ive done? Any suggestions?

This is what comes up when i type in terminal
tobin@tobin-laptop:~$ sudo apt-get update
E: Type ‘sudo’ is not known on line 1 in source list /etc/apt/sources.list.d/winff.list
tobin@tobin-laptop:~$ 




**This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.**

:confused:

---

### Post by jgoguen on 2008-12-12
Please post the output of this command:

```
cat /etc/apt/sources.list.d/winff.list
```

Also, please tell us what version of Ubuntu you are using.

---

### Post by 2hot6ft2 on 2008-12-12
winff is not in the repos as far as I know. I installed it from a package on their site. It's not major. But it shouldn't be there. I'm on the other pc which doesn't have it so can't check that file right now.

---

### Post by Duck2006 on 2008-12-12
If you can open Synaptic Package Manager look to see if you have Broken Packs if you do you can fix them there.
Click edit and then "fix broken packages"

---

### Post by drs305 on 2008-12-12
> **2hot6ft2 said:**
> winff is not in the repos as far as I know. I installed it from a package on their site. It's not major. But it shouldn't be there. I'm on the other pc which doesn't have it so can't check that file right now.

If you didn't do it, the site must have installed the repository reference - winff.list

If you don't need that repository, you can remove this file, and the associated error message, with:
```

sudo rm /etc/apt/sources.list.d/winff.list

```

You can probably also untick it in Synaptic, Settings, Repositories, Third Party.

---

### Post by 2hot6ft2 on 2008-12-12
Just checked the pc which has winff and it has no such file either. So I would have to agree delete it as it doesn't belong there.

---

### Post by 2hot6ft2 on 2008-12-12
The OP must have been told that they could install it by using the command line and created it in the process. I got it as the solution for a issue from an admin of the ultimate site so I knew it wasn't adding anything like that.

---

### Post by jgoguen on 2008-12-12
The page for WinFF provides directions to create that file.  It seems like the file was created wrong, so rather than just deleting it (and leaving the OP with no way to install through Synaptic) I think the contents should be checked to make sure there's no errors.  If there are, then fixing the file is the best way to go IMO, so the OP can use Synaptic (or apt-get, or aptitude...) to install and update WinFF.

If you install from the package from their site, the file the OP mentioned wouldn't be there, but it's created if you follow their directions for using the package manager.

---

### Post by michaeltobin on 2008-12-12
> **jgoguen said:**
> Please post the output of this command:

```
cat /etc/apt/sources.list.d/winff.list
```

Also, please tell us what version of Ubuntu you are using.
output as follows;

tobin@tobin-laptop:~$ cat /etc/apt/sources.list.d/winff.list
cat: /etc/apt/sources.list.d/winff.list: No such file or directory
tobin@tobin-laptop:~$

---

### Post by 2hot6ft2 on 2008-12-12
> **jgoguen said:**
> The page for WinFF provides directions to create that file.  It seems like the file was created wrong, so rather than just deleting it (and leaving the OP with no way to install through Synaptic) I think the contents should be checked to make sure there's no errors.  If there are, then fixing the file is the best way to go IMO, so the OP can use Synaptic (or apt-get, or aptitude...) to install and update WinFF.

If you install from the package from their site, the file the OP mentioned wouldn't be there, but it's created if you follow their directions for using the package manager.

Exactly. I'm curious as to what's in it.

---

### Post by michaeltobin on 2008-12-12
> **drs305 said:**
> If you didn't do it, the site must have installed the repository reference - winff.list

If you don't need that repository, you can remove this file, and the associated error message, with:
```

sudo rm /etc/apt/sources.list.d/winff.list

```

You can probably also untick it in Synaptic, Settings, Repositories, Third Party.
thanks, i used this code to remove it and synaptic now works, thanks for your help, problem solved

---

### Post by jgoguen on 2008-12-12
I'm very curious how that file ended up empty... but at least it's working for you now :)

---

