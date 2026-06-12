---
title: "Installing java on ubuntu feisty"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by javame on 2008-12-18
Hi,

I have tried installing java from terminal by giving command as 

sudo apt-get install sun-java6-jre sun-java6-jdk 

but everytime I get the error as couldn't find package or sometimes it displays sun-java-jre6 has no installation candidate.

What does this mean? I have even tried from Add/Remove programs but from their too it doesn't get installed since it gives error as couldn't install from all repository.  I am really stuck at this and not able to find any solution. Whatever I have read on forums it says checking sources.list file I have done that too but still java doesn't get installed.

Moreover I am not able to install any other software such as bluetooth package also dont get installed from Add/Remove Programs.  For this I have even tried changing the server from Software Sources but still no solution.

Any help would be greatly appreciated.

Thanks & Regards
Sunil

---

### Post by overdrank on 2008-12-18
Hi and welcome, you are getting that error as Feisty has reached it end of life. this means that it is not supported. You may wish to install a newer version like Hardy 8.04 or intrepid 8.10. I would suggest Hardy. :)

---

### Post by javame on 2008-12-18
Hi,

Its ubuntu feisty fawn i.e. ubuntu 7.04. I have another system with the same operating system and that system is able to install java with same command i.e sudo apt-get install sun-java6-jre but not on my system.  Is there any problem with sources.list file or something else. 

I have even tried to copy sources.list of that system into my system and then given the command but still the same problem.  What may be the problem that one system is able to install java with the same command while one system is not able to install.

Thanks & Regards
Sunil

---

### Post by LowSky on 2008-12-18
> **overdrank said:**
> Hi and welcome, you are getting that error as Feisty has reached it end of life. this means that it is not supported. You may wish to install a newer version like Hardy 8.04 or intrepid 8.10. I would suggest Hardy. :)

Like he said, fiesty repos don't work any more. NO idea how one machine just updated unless you have another repo or did an upgrade and didn't know it

---

### Post by javame on 2008-12-18
Hi,

Thanks a lot for replying.

Is there any way now to upgrade the repository or I have to install newer version only.  I did tried Update Manager System -> Adminstration -> Update Manager but its not even getting upgrade.

Seems that I have to go for newer version  but if theres any way out then please let me know ASAP.

Thanks & Regards
Sunil

---

### Post by javame on 2008-12-18
Hi,

Thanks a lot for replying.

Is there any way now to upgrade the repository or I have to install newer version only.  I did tried Update Manager System -> Adminstration -> Update Manager but its not even getting upgrade.

Seems that I have to go for newer version  but if theres any way out then please let me know ASAP.

Thanks & Regards
Sunil

---

### Post by overdrank on 2008-12-18
With the system not being up to date then I would say that if there was away it would most likely fail. I would suggest a clean install.

[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

---

### Post by javame on 2008-12-18
Hi,

Clean install of the same version or newer version. Since I dont have newer version and downloading or getting CD will take time.  

If I install the same version and upgrade it then will that help in installng java or not.  If it will give the same error then theres no point in installing it. But anyways I dont have any other option rite now so will try that only.

If this also dont help then will think of getting newer version or will have to switch it to fedora for the time being.

Thanks & Regards
Sunil

---

### Post by overdrank on 2008-12-18
> **javame said:**
> Hi,

Clean install of the same version or newer version. Since I dont have newer version and downloading or getting CD will take time.  

If I install the same version and upgrade it then will that help in installng java or not.  If it will give the same error then theres no point in installing it. But anyways I dont have any other option rite now so will try that only.

If this also dont help then will think of getting newer version or will have to switch it to fedora for the time being.

Thanks & Regards
Sunil
As stated before Feisty is no longer supported so a reinstall of it would not work likely. The only reason I can think of for one system to work and another not, is that the working system has the server install and has longer support but I can not find any documentation of this.

You may try changing your sources list to  Gutsy and upgrading then, but I do not know if this will work and may cause damage.
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
Good luck.

---

