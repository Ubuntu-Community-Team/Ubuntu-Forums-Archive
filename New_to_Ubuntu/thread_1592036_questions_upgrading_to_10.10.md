---
title: "questions upgrading to 10.10"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by cap10Ibraim on 2010-10-10
I'm running Ubuntu 10.04 and wasn't planning to upgrade but the 10/10/10 10:10:10 is really special , so if I upgrade : 
- concerned about wine and windows apps ? 
- concerned about the manually added PPAs ?
- I removed Open-office will the upgrade manager reinstall it ? 
- Does the upgrade manager take care of removing old useless packages ? ( F-spot will be removed ?)

---

### Post by mikewhatever on 2010-10-10
A heavily customized system (such as yours) may fail to upgrade. I'd remove all third party repositories and reinstall the ubuntu-desktop package.

---

### Post by thunk77 on 2010-10-10
> **cap10Ibraim said:**
> I'm running Ubuntu 10.04 and wasn't planning to upgrade but the 10/10/10 10:10:10 is really special , so if I upgrade : 
- concerned about wine and windows apps ? 
- concerned about the manually added PPAs ?
- I removed Open-office will the upgrade manager reinstall it ? 
- Does the upgrade manager take care of removing old useless packages ? ( F-spot will be removed ?)

Upgrades on any OS are always painful, and Ubuntu is no exception to that rule.

First of all you should backup your home directory and any data you want to keep.

Your Wine installation and Windows applications will likely not be affected, but be prepared to do some tweaking to get some apps to the desired state.

Manually added PPA's should be disabled when upgrading and after the upgrade you will have to alter the lines in your sources.list so as to point to the right Ubuntu release (e.g. Lucid -> Maverick).
Alternate solution to this would be to remove any third party repositories and then add them again after the upgrade

If you removed OpenOffice I assume you also removed a package named ubuntu-desktop. This package is required to ensure a smooth upgrade and it is tied to OpenOffice (among other things!), so yes you will probably have to reinstall it and then remove it again.

The update manager takes care of obsolete packages, so yes F-Spot will be removed and it will be replaced with Shotwell.

Some Info: [http://www.ubuntu.com/desktop/get-ubuntu/upgrade](http://www.ubuntu.com/desktop/get-ubuntu/upgrade)

Regards

---

### Post by cap10Ibraim on 2010-10-10
thanks for the advice guys :guitar: as a result i'll not upgrade 
not now at least

---

### Post by irv on 2010-10-10
For the record: I have a Dell Inspiron 1521 laptop running a Win7 and Ubuntu. I did the upgrade from 10.04 to 10.10 and I am using 26Gig of disk space for Ubuntu, which means I have a lot of stuff loaded. It took awhile, but all went well, and everything seems to be running OK. I also did a fresh install on a Dell 1505 laptop, and it went even better. Much faster. I have a extra HD for the 1521, which I plan on doing a fresh install of Win7 and Ubuntu 10.10 64 bit, but I plan on doing this later on.

---

### Post by Yan_Suryana on 2010-10-10
I just install 10.10 and found that root can't run gedit, it was ok with 10.04 or 10.10 beta . .

Please advise . .

---

### Post by irv on 2010-10-10
> **Yan_Suryana said:**
> I just install 10.10 and found that root can't run gedit, it was ok with 10.04 or 10.10 beta . .

Please advise . .

My gedit works. I am using 10.10. Maybe just try removing it and re-installing it again. Maybe it got broke during the install. Did you do an update or a clean install? I did an update.

---

### Post by Yan_Suryana on 2010-10-11
> **irv said:**
> My gedit works. I am using 10.10. Maybe just try removing it and re-installing it again. Maybe it got broke during the install. Did you do an update or a clean install? I did an update.

Thanks for the reply, I did a clean install because my 10.10 beta hung up after I installed ManDVD . I'll try to re-install it again soon .

---

### Post by Yan_Suryana on 2010-10-11
> **irv said:**
> My gedit works. I am using 10.10. Maybe just try removing it and re-installing it again. Maybe it got broke during the install. Did you do an update or a clean install? I did an update.

Still can't use gedit under root after re-Download and re-Install 10.10
It's ok if I login as a user other than root, but if I do su and type root's password, I can't use gedit and gave me library error etc.

It was ok with 10.10 beta, 10.04 or the version before or other Linux . .

---

### Post by irv on 2010-10-11
> **Yan_Suryana said:**
> Still can't use gedit under root after re-Download and re-Install 10.10
It's ok if I login as a user other than root, but if I do su and type root's password, I can't use gedit and gave me library error etc.

It was ok with 10.10 beta, 10.04 or the version before or other Linux . .

If it gives you the Library name thats missing, try to install it. Also try 
> sudo geditat the command prompt.

---

### Post by irv on 2010-10-11
> **irv said:**
> For the record: I have a Dell Inspiron 1521 laptop running a Win7 and Ubuntu. I did the upgrade from 10.04 to 10.10 and I am using 26Gig of disk space for Ubuntu, which means I have a lot of stuff loaded. It took awhile, but all went well, and everything seems to be running OK. I also did a fresh install on a Dell 1505 laptop, and it went even better. Much faster. I have a extra HD for the 1521, which I plan on doing a fresh install of Win7 and Ubuntu 10.10 64 bit, but I plan on doing this later on.

OK, last night I put a 250 Gib hard drive in my Inspiron 1521, did a wipe and installed Win7 64bit and Ubuntu 10.10 64bit, and it went without a hitch. It took about 45 minutes to install Win7 and under a half hour to install Ubuntu. Win7 did not find the right 64 bit video driver so I had a lower resolution. Ubuntu looked great (found the right video driver). I still had to have the network cable plugged in when I did the install because I need to load the wifi driver. Now all I need to do is pull all my file over to it and find the right Win7 drivers and it's done.

---

### Post by Yan_Suryana on 2010-10-11
> **irv said:**
> If it gives you the Library name thats missing, try to install it. Also try 
at the command prompt.

sudo gedit works fine.

anyway, how do I re-intall the library ?

Thanks a Lot . .

---

### Post by irv on 2010-10-11
> **Yan_Suryana said:**
> sudo gedit works fine.

anyway, how do I re-intall the library ?

Thanks a Lot . .

Goto System>Administration> Synaptic Package Manager and type in the name of the Library: select it and mark it for install. Then Apply the changes and that it. You can also do it from the command prompt by typing
> sudo apt-get install name-of-package 
You will be asked for your password and then it will install it.
When you do this make sure you don't have the package manager open or you will get an error.

---

### Post by Yan_Suryana on 2010-10-12
> **irv said:**
> Goto System>Administration> Synaptic Package Manager and type in the name of the Library: select it and mark it for install. Then Apply the changes and that it. You can also do it from the command prompt by typing

You will be asked for your password and then it will install it.
When you do this make sure you don't have the package manager open or you will get an error.

Thanks you very much Irv . .
I'll try it soon . .

---

