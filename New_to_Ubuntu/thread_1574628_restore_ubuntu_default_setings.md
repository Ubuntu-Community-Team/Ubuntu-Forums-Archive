---
title: "restore ubuntu default setings"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by uniku on 2010-09-14
Hello every1
i'm new on linux and i'm lost
Smb tell me how to Reset/ ubuntu default setting i mean like was when i've installed it
Thanks in advance

---

### Post by roger_1960 on 2010-09-14
Hi

Why not back up your data and then re-install?

---

### Post by bodhi.zazen on 2010-09-14
> **uniku said:**
> Hello every1
i'm new on linux and i'm lost
Smb tell me how to Reset/ ubuntu default setting i mean like was when i've installed it
Thanks in advance

What setting do you want to restore exactly ?

If all else fails, back up your data, boot to single user, and delete everything in your home directory. Then reboot, log in, and restore your data.

If you are asking about changes to system files, purge and re-install the package(s).

---

### Post by uniku on 2010-09-14
i was doing smth with compiz...and now i have all system up & Down i cant see half of icons etc etc
i was wondering if i can restore it as it was before(i mean like was when i installed)
if not i have to reinstall again from the begin

---

### Post by Rubi1200 on 2010-09-14
Could you please try and be more _specific_ about what you were doing with Compiz?

The more you tell us, the more likely we can offer you solutions.

---

### Post by uniku on 2010-09-14
> **Rubi1200 said:**
> Could you please try and be more _specific_ about what you were doing with Compiz?

The more you tell us, the more likely we can offer you solutions.
As i told i'm new and i'm not sure if i will report the exact problem
i think the only helt is restore all system like it was i mean untouched* clean
Thnx

---

### Post by coffeecat on 2010-09-14
First - there is no system restore utility as you find in Windows.

Second. In theory we could help you to restore the system to its original settings, but that would require quite a bit of detective work, details of what you have and haven't done, what you've installed, and so on. As you are a beginner and unused to Ubuntu, that will take a very long time and may not get you where you want to be.

Third. As others have suggested, you could simply reinstall. This takes less than an hour and you would have the "clean" system you are asking for. Remember to back up your data first and post back if you need any help.

Good luck!

---

### Post by mc4man on 2010-09-14
If you were using Compizconfig Settings Manager (System - Preferences), see screen 1, then open it up and click on the preferences Tab.
Then choose 'reset to defaults' - screen 2

---

### Post by uniku on 2010-09-14
> ** ccoffeeat said:**
> First - there is no system restore utility as you find in Windows.

Second. In theory we could help you to restore the system to its original settings, but that would require quite a bit of detective work, details of what you have and haven't done, what you've installed, and so on. As you are a beginner and unused to Ubuntu, that will take a very long time and may not get you where you want to be.

Third. As others have suggested, you could simply reinstall. This takes less than an hour and you would have the "clean" system you are asking for. Remember to back up your data first and post back if you need any help.

Good luck!
Thanks for help ccoffeecat and all others guys i apreciate that...I will re-install the more easy way :)

---

### Post by uniku on 2010-09-14
[mc4man]("http://ubuntuforums.org/member.php?u=320715")  done that and now is everything ok :)
Thank you very much
Thanks 2 all  & VIVA LINUX :D:D

---

### Post by robalcorn on 2010-09-14
I know this is a little late but this worked for me:

[http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

---

### Post by uniku on 2010-09-15
Thanks to all 
Solved !! :)

---

### Post by 3rdalbum on 2010-09-15
Compiz runs as user, so you can remove your user preferences which are stored in hidden directories in your home folder. Back it all up and then delete it.

---

