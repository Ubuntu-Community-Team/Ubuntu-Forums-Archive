---
title: "My Grub - is this message ok?"
date: 2010-04-09
forum: New to Ubuntu
---

### Post by listerdl on 2010-04-09
Hi I have a dual boot ubuntu 9.10 and Windows 7 that works great. No issues.

I was wondering though, when I boot, the grub menu says this:

Linux, Ubuntu 2.6.31-21 Generic
Linux, Ubuntu 2.6.31-21 Generic (Recovery Mode)
Linux, Ubuntu 2.6.31-20 Generic
Linux, Ubuntu 2.6.31-20 Generic (Recovery Mode)
Linux, Ubuntu 2.6.31-18 Generic
Linux, Ubuntu 2.6.31-18 Generic (Recovery Mode)
Linux, Ubuntu 2.6.31-17 Generic
Linux, Ubuntu 2.6.31-17 Generic (Recovery Mode)
Linux, Ubuntu 2.6.31-15 Generic
Linux, Ubuntu 2.6.31-15 Generic (Recovery Mode)
Linux, Ubuntu 2.6.31-15 Generic
Linux, Ubuntu 2.6.31-14 Generic
Windows 7 Loader

Is it ok? - I mean these all look like different versions?

thanks?

---

### Post by mikewhatever on 2010-04-09
Indeed, different kernel versions. When the kernel is updated, the older versions are retained, but you can always remove them if not needed. They don't do any harm, other then taking up disk space. Anyway, to do that, you can search for 'linux-image' in synaptic package manager, and remove all but the latest version. Do not remove the latest version! If you prefer CLI, run the following commands:

```

sudo apt-get purge linux-image-2.6.31-14-generic linux-image-2.6.31-15-generic linux-image-2.6.31-17-generic linux-image-2.6.31-18-generic linux-image-2.6.31-20-generic

sudo apt-get --purge autoremove

```

The boot menu will get updated in the process.

---

### Post by Didius Falco on 2010-04-09
What Mike said, except I always leave the 2 latest versions of the kernel installed, just in case.

I'm a belt & suspenders type, but being that way keeps my butt from hanging in the breeze if my belt fails. :lolflag:

---

### Post by listerdl on 2010-04-09
OK cool thanks

Im very scared to delete the kernel i am using....

Basically I MUST leave the TOP TWO right?

I.e. the 

[I]Linux, Ubuntu 2.6.31-21 Generic
Linux, Ubuntu 2.6.31-21 Generic (Recovery Mode)[/I]

And then add these for being removed using terminal?

[I]Linux, Ubuntu 2.6.31-20 Generic
Linux, Ubuntu 2.6.31-20 Generic (Recovery Mode)
Linux, Ubuntu 2.6.31-18 Generic
Linux, Ubuntu 2.6.31-18 Generic (Recovery Mode)
Linux, Ubuntu 2.6.31-17 Generic
Linux, Ubuntu 2.6.31-17 Generic (Recovery Mode)
Linux, Ubuntu 2.6.31-15 Generic
Linux, Ubuntu 2.6.31-15 Generic (Recovery Mode)
Linux, Ubuntu 2.6.31-15 Generic
Linux, Ubuntu 2.6.31-14 Generic[/I]

T H A N K S

---

### Post by wobin77 on 2010-04-09
The ones you listed are the same kernel version. One is just the 'recovery-mode'. 
I would suggest keeping the 2.6.31-20 aswell. Just in case anything goes wrong, you can still boot the older version.

---

### Post by Mykk on 2010-04-09
> **listerdl said:**
> OK cool thanks

Im very scared to delete the kernel i am using....

Basically I MUST leave the TOP TWO right?

I.e. the 

[I]Linux, Ubuntu 2.6.31-21 Generic
Linux, Ubuntu 2.6.31-21 Generic (Recovery Mode)[/I]

And then add these for being removed using terminal?

[I]Linux, Ubuntu 2.6.31-20 Generic
Linux, Ubuntu 2.6.31-20 Generic (Recovery Mode)
Linux, Ubuntu 2.6.31-18 Generic
Linux, Ubuntu 2.6.31-18 Generic (Recovery Mode)
Linux, Ubuntu 2.6.31-17 Generic
Linux, Ubuntu 2.6.31-17 Generic (Recovery Mode)
Linux, Ubuntu 2.6.31-15 Generic
Linux, Ubuntu 2.6.31-15 Generic (Recovery Mode)
Linux, Ubuntu 2.6.31-15 Generic
Linux, Ubuntu 2.6.31-14 Generic[/I]

T H A N K S

No, personally i would leave a few more.

IE:

[I]Linux, Ubuntu 2.6.31-21 Generic
Linux, Ubuntu 2.6.31-21 Generic (Recovery Mode)[/I]
[I]Linux, Ubuntu 2.6.31-20 Generic
Linux, Ubuntu 2.6.31-20 Generic (Recovery Mode)
Linux, Ubuntu 2.6.31-18 Generic
Linux, Ubuntu 2.6.31-18 Generic (Recovery Mode)
Linux, Ubuntu 2.6.31-17 Generic


[/I]

---

### Post by da burger on 2010-04-09
It is recommended that you keep 2 kernels in case something goes wrong. You have only kept one kernel and the recovery mode that uses that kernel.

Linux, Ubuntu 2.6.31-21 Generic
Linux, Ubuntu 2.6.31-21 Generic (Recovery Mode)
Linux, Ubuntu 2.6.31-20 Generic
Linux, Ubuntu 2.6.31-20 Generic (Recovery Mode)

In other words keep those four.

---

### Post by mikewhatever on 2010-04-09
> **listerdl said:**
> OK cool thanks

Im very scared to delete the kernel i am using....

Basically I MUST leave the TOP TWO right?

I.e. the 



So use the commands I posted, they don't include the latest kernel. I should have also mentioned, the first command removes the specified kernel versions, and the second removes the dependencies, headers and what not.
If not sure, you could run the commands with the '-s' flag, which stands for 'simulate'. The output will show what's going to happen.

---

### Post by codemaniac on 2010-04-09
To remove the entries(not the kernels) only from the boot menu all you need to do is make a custom file in the directory /etc/grub.d and add the entries you want be shown in the grub menu..:)

---

### Post by orkyahaalhai on 2010-04-09
personnaly  i would recommend keeping the latest and the oldest ( or the last one which worked with total stability ) . Well even having only one kernal version is ok , but  you never know!!
 

 Keep a second one for may day .

---

### Post by zengzhangsong on 2010-04-09
Don't worry!Your computer grub is OK,when you update your Ubuntu,the menu will be crate,I have install the Ubuntu8.04 and Windows7.I have the same problem!:-P

---

### Post by Didius Falco on 2010-04-09
> **listerdl said:**
> OK cool thanks

I'm very scared to delete the kernel i am using....

Basically I MUST leave the TOP TWO right?

I.e. the 

[I]Linux, Ubuntu 2.6.31-21 Generic
Linux, Ubuntu 2.6.31-21 Generic (Recovery Mode)[/I]

And then add these for being removed using terminal?

[I]Linux, Ubuntu 2.6.31-20 Generic
Linux, Ubuntu 2.6.31-20 Generic (Recovery Mode)
Linux, Ubuntu 2.6.31-18 Generic
Linux, Ubuntu 2.6.31-18 Generic (Recovery Mode)
Linux, Ubuntu 2.6.31-17 Generic
Linux, Ubuntu 2.6.31-17 Generic (Recovery Mode)
Linux, Ubuntu 2.6.31-15 Generic
Linux, Ubuntu 2.6.31-15 Generic (Recovery Mode)
Linux, Ubuntu 2.6.31-15 Generic
Linux, Ubuntu 2.6.31-14 Generic[/I]

T H A N K S

The (Recovery Mode) listings aren't separate kernels, they are just a  different way to boot the kernel that gives you different options you can use in case you run into trouble and need a command line to fix things.

If you open a Terminal window (Menu/Accessories/Terminal) and cut/paste this command:


```
sudo apt-get purge linux-image-2.6.31-14-generic linux-image-2.6.31-15-generic linux-image-2.6.31-17-generic linux-image-2.6.31-18-generic 
```
 
It will remove all the kernels except for linux-image-2-6-31-20-generic and linux-image-2-6-31-21-generic.

It will update your grub listing so the next time you boot, you'll have something like this listed:

```
Linux, Ubuntu 2.6.31-21 Generic
Linux, Ubuntu 2.6.31-21 Generic (Recovery Mode)
Linux, Ubuntu 2.6.31-20 Generic
Linux, Ubuntu 2.6.31-20 Generic (Recovery Mode)
Windows 7 Loader
```Regards,

Didius

---

