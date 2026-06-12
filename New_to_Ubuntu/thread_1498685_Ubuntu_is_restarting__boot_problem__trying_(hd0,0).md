---
title: "Ubuntu is restarting | boot problem | trying (hd0,0) ntfs5"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by daanial on 2010-06-01
**Dear all**

After long time of installing Ubuntu and switching back to the windows I found last version of Ubuntu absolutely amazing and I used it full time on my laptop.
the only problem I had was with wireless which was disconnecting constantly and yesterday I installed some other drivers and I shut it down.

After some hours when I turned on my computer and in the first page I chose Ubuntu and
instead of going to the second page of showing different types of Ubuntu it wrote:

[B]Trying (hd0,0) ntfs5
[/B]
and then it restarted and its happening constantly ( Ubuntu >> trying (hd0,0) ntfs5 >> restart[B] )

[/B]I really dont know what happened, why this happened and what to do to having my setting and my files in the Ubuntu.

It will be really great if you help me about that.

Thanks in advance for your time.
[B]
Danial


P.s[/B]: I have windows XP on the computer and I tried a lot but I couldn't pause the errors before restarting. It shows something in two lines with word "command" and I tried a lot with Pause and Insert buttons but I couldn't stop the page.

---

### Post by weirdtalk on 2010-06-01
Since it was right after installing a new driver, I would try to boot ubuntu into a older kernel (if you have on in the boot menu), or a rescue mode. If it can then it's probably the drivers fault, if you can't my first guess would be file corruption. Either way let us know. 

Also is it booting to windows okay, or restarting on windows as well?

---

### Post by daanial on 2010-06-01
No. I can not. I even tried one solution for copying c:\wubildr to Ubuntu folder and nothing changed.

Yes. windows is still working fine and I have no problem with that.
Is there any way to save the setting?
What will happen If I install a fresh Ubuntu?

Thanks for your time

---

### Post by weirdtalk on 2010-06-01
Yes you can save settings. Use a live cd to boot and then open the ubuntu partition. you can copy the /home/<user> folder out and that will hold all the user settings. (user settings is almost everything) If you want you can also copy out the /etc folder for system settings. (sometimes useful) then you can do a clean install and restore the settings/files you want.

---

### Post by daanial on 2010-06-01
> **weirdtalk said:**
> you can copy the /home/<user> folder out and that will hold all the user settings. (user settings is almost everything) If you want you can also copy out the /etc folder for system settings. (sometimes useful) then you can do a clean install and restore the settings/files you want.


OK. for making it clear I am repeating it:

I will copy 
 /home/<user>
/etc

to other storage.
I will install a new version and then I will copy them.

I think I will lose the programs I installed but it seems that there is no other way.

Anyway: Thank you!

---

