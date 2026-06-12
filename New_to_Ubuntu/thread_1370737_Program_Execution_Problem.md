---
title: "Program Execution Problem"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by beegary on 2010-01-02
I have recently installed Tangarine and Wine
However when I click on any of the associated icons in the menu's nothing happens?

I installed tangerine using terminal
I installed wine using the software centre

Have I done something wrong? I have installed other software since this problem and they execute without any issues.
I am using Karmic

---

### Post by Methuselah on 2010-01-02
It is possible for some programs not to work well with wine while others work almost perfectly.
Tangerine might be one of that does not work at all.

If you are curious you can do something like the below in a Terminal

```

cd ~/.wine/drive_c/Program\ Files/...
wine Tangerine.exe

```
[I'm assuming the program is called Tangerine.exe and is somewhere under Program Files...you'd have to know the right path/names]

Then Tangerine will spit out error messages in the terminal.
These probably won't be much use to you anyway.

---

### Post by beegary on 2010-01-02
Sorry i do not think i was clear in my post.....

I have installed Wine, it appears in the Applications list in Karmic, but when i select any of its icons, like preferences or start program etc. nothing happens.

I have also installed Tangarine (which is a DAAP media server i think) it appears in System -Preferences but when i select Tangarine media sharing - again nothing happens?

Should I try to re-install? Is there a way of running the programs via terminal to see what is happening?
I have tried to execute them via Gnome-do but still nothing happens

---

### Post by beegary on 2010-01-02
I just tried this...
```

wine NOTEPAD
wine: '/home/bee' is not owned by you, refusing to create a configuration directory there
```


so I chowned my home directory, but am still getting the error???

---

### Post by Methuselah on 2010-01-02
Type 

```
winecfg
```

in a Terminal.

If wine is installed it should start the wine configuration program.
If not, you should get some kind of error.

---

### Post by beegary on 2010-01-02
```
bee@ubuntu:~$ winecfg
wine: '/home/bee' is not owned by you, refusing to create a configuration directory there

```I have tried to chown /home/bee, it doesnt give an error but the owner always remains as root?
Thanks for your help so far........

not sure if I should have done this but...

[code]bee@ubuntu:~$ sudo winecfg
wine: created the configuration directory '/home/bee/.wine'
Failed to create secure directory: Permission denied
Failed to create secure directory: Permission denied
bee@ubuntu:~$ fixme:system:SetProcessDPIAware stub!
fixme:iphlpapi:NotifyAddrChange (Handle 0x7eb4d9b8, overlapped 0x7eb4d99c): stub
fixme:shell:DllCanUnloadNow stub
wine: configuration in '/home/bee/.wine' has been updated.[code]

---

### Post by Methuselah on 2010-01-02
Is your Ubuntu username bee?
Try

```

sudo chown bee /home/bee

```

It's strange that you do not own your home directory.
All your permission problems arise from this.

---

### Post by beegary on 2010-01-02
Yea I thought it was strange!
I have tried to chown but it doesnt seem to have any affect???


It might have something to do with me mounting an nfs share as my home directory?
I have this line in my fstab:
/dev/sda3 /home/bee ntfs-3g defaults,locale=en_GB.UTF-8 0

---

### Post by beegary on 2010-01-02
I have posted this as a new thread, im not sure f thatviolates forum etiquette but I have a more specific idea of the question now.......
[http://ubuntuforums.org/showthread.php?p=8599250#post8599250](http://ubuntuforums.org/showthread.php?p=8599250#post8599250)

---

### Post by 3rdalbum on 2010-01-02
As for your other problem, Tangerine is indeed broken in Karmic. You might be able to compile a new version.

---

### Post by Methuselah on 2010-01-02
Or are there any PPAs?

---

### Post by 3rdalbum on 2010-01-02
> **Methuselah said:**
> Or are there any PPAs?

Could be, I haven't checked.

---

### Post by beegary on 2010-01-02
> **3rdalbum said:**
> As for your other problem, Tangerine is indeed broken in Karmic. You might be able to compile a new version.

Thank you, is there a way of checking this before install?

---

### Post by beegary on 2010-01-03
> **Methuselah said:**
> Or are there any PPAs?

What does that mean?

---

### Post by Methuselah on 2010-01-03
> **beegary said:**
> What does that mean?

Personal package archive:
[https://help.launchpad.net/Packaging/PPA](https://help.launchpad.net/Packaging/PPA)

I found one for tangerine but I don't know if it is any better than what is packages with Karmic
[https://launchpad.net/~tangerine-developers/+archive/ppa](https://launchpad.net/~tangerine-developers/+archive/ppa)
I guess one could try.

---

### Post by beegary on 2010-01-03
Thank you

---

### Post by firefeather on 2010-02-01
This post might also be relevant to the issue with Tangerine not starting; worked for me:

[http://ubuntuforums.org/showthread.php?t=1319098&p=8484358](http://ubuntuforums.org/showthread.php?t=1319098&p=8484358)

---

