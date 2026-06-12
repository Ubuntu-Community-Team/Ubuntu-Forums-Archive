---
title: "Making File System not accessible"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by niko123 on 2009-03-20
Hello all,

I was wondering if i could make the File System Folder...not accessible. I am one of the System administrator at my university, And very proud that i made an AWESOME image that i will be placing in a lab.

But i had a few questions:

1) How can i make the File System not accessible only to the user?
** i know that they are not able to change/edit anything because they don't have the root passwd, but still. Wont hurt to ask :P

2) Is there a way to remove "Places" from the Main menu?
**I have removed the "System" tab...By going to System>Pref>main Menu. But there not way from there to hide that tab..?!?!

Any suggestions would be GREATT!!

Thanks

---

### Post by LowSky on 2009-03-20
Sorry you cant get rid of system that way, just unlcik both option.

the reason you cant is becaue that is were shutdown is on a normal gnome install.

and no you cant block the file system entirely, as the normal user need to be able to access their files formt he home folder.. sorry no way out of that.

But as you said they cant touch anything thats it important

---

### Post by niko123 on 2009-03-20
Ohh ok ok I see i see, thanks for that response. Learned something new.

Would you by any chance know if i am able to hide the "connect to server" OR "NetworK" icon that is there under "Places"...i just KNOW people are going to use that option is i am not able to hide it...

Please do let me know

Thanks

---

### Post by niko123 on 2009-03-21
Anyone please *bump

---

### Post by linuxisevolution on 2009-03-21
By using the menu editor (right click menus, click edit menus) and click system and then uncheck the boxes on the left to hid everything except the shutdown option in the system menu.

The places menu cannot be removed, but you *CAN just remove the whole menu and just make launchers to the applications you need. For instance, right click the taskbar, click add to panel, and click custom app launcher. Name it something, give it an icon, and put "nautilus" as the command without quotes. This will open the file browser when clicked. Good luck. :)

---

