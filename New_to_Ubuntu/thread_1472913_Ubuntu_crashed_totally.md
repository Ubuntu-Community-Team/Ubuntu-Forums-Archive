---
title: "Ubuntu crashed totally"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by Greblok on 2010-05-04
Hi all you nice people. :)
Hope you can help me again...

I was trying to uninstall Gwibber but think I must have uninstalled something else as well.
Thing is, i uninstalled Gwibber, and beeing to quick, I think I have removed something else that started with gw. :P

Now, Ubuntu starts and goes to the login screen, but I have no choise as to what desktop i wish to use.
When i log in, the standard Ubuntu screen does not show up.
Instead, there is a blue windows, showing an image of a disk, network (or a globe), and something that seems to be a desktop.

After a short while, the screen goes black and the only thing shown is the quickmessaging account logged in with my contacts. Nothing else. 
I have set up a user account for my wife, same thing there.
Nothing but the contacts windows of empathy is shown.

I can get into restore mode, but I have absolutely no idea what to do...
Starting to believe Linux is not for me after all, but I am so sick of Windows.

Any way I can restore my desktop or do I need to reinstall?
If so, I am considering to skip Linux entirely. 
Any help would be greatly appreciated. :)

---

### Post by cgroza on 2010-05-04
Do you have access to a shell? Enter recovery mode, type your username , type your password and hit enter (the password will not show when you type it) and do " sudo apt-get install ubuntu-desktop ". To enter recovery mode hold the Shift key while your computer boots. A menu will appear with some kernels. Highlight the line that says Recovery Mode and hit enter.

---

### Post by Greblok on 2010-05-04
Haha!!
That simple little command did the trick. 

Ok, I still like Ubuntu, but I LOVE you guys in the community.  :)

Thank you sir!
You just saved my night. :)

---

### Post by cgroza on 2010-05-04
You are welcome... Do not uninstall Gwibber as it seems it takes with it some important packages... And please mark this thread as solved....

---

### Post by Greblok on 2010-05-04
> **cgroza said:**
> Do not uninstall Gwibber as it seems it takes with  it some important packages...

Nah, I think it was my mistace, not Gwibber. ;)

> **cgroza said:**
> 
 And please mark this thread as solved...

I believe I did, even before your last reply. ;)

Thanks again! You guys rock.

---

