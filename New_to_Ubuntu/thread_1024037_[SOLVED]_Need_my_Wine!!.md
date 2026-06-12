---
title: "[SOLVED] Need my Wine!!"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by 2uRcJQ34G1 on 2008-12-28
Hello,

About three days ago I upgraded from Hardy to Intrepid, everything seemed fine. Of all my installed software, those that were incompatible with Intrepid were deleted. The one that remained are working fine.

However, I just installed Wine 1.0.1 from the Add/Remove Applications and I do not see the Wine sub menu in my applications menu. But, I am not only able to run '.exe' files but also run them from the terminal. I tried to go to the menu editor in Systems to see if I can check the Wine program loader menu, but it is not there. Furthermore, I tried to completely uninstall Wine from Synaptic and reinstalled the Wine.

I am still unable to get my GUI menu under Applications. This being said, I am able to see the Wine menu when I run Ubuntu under the Guest account. Can someone please help me solve this dilemma, thanks in advance.

Cheers,
G_G

---

### Post by hyper_ch on 2008-12-28
how do you try to run the .exe files?

---

### Post by billgoldberg on 2008-12-28
So you have wine installed?

What happens when you try to install an application using wine?

Install from the terminal and post the error messages (if any).

If you don't know how to install an .exe installer from the terminal, use this command;

```
wine /path/to/file/application.exe
```

---

### Post by 2uRcJQ34G1 on 2008-12-28
Hi I just installed utorrent and everyhing went smoothly I even got my desktop icon, made it my default client for torrents and when I minimised it, it appears in the top menu bar. And all the while there is still not sign of the menu in Applications.

---

### Post by 2uRcJQ34G1 on 2008-12-28
i run files by right clicking on the .exe file and then clicking Open with "Wine Windows Program Loader"

---

### Post by adobrakic on 2008-12-28
All that seems to have happened is that Wine went missing from your Menu.

Did you right click on Menu and go to 'Edit Menu' and see if Wine is unchecked?

---

### Post by 2uRcJQ34G1 on 2008-12-28
yes, i have done that

---

### Post by 2uRcJQ34G1 on 2008-12-30
[COLOR="Red"]Ok, SOLVED.[/COLOR]
This is for those who were/are struggling with the same problem:

-> Right click on the _Application_s drop down and click on _Edit Menus_ after that click on _Other_ and then click on _Menu Editor_.

-> Close the window.

-> Click on Applications->Other->Menu Editor

-> You should be able to see the Wine sub-menu, check it and all its arteries.

Et voila! You have Wine on your menu.


P.S. Special thanks to my little grey cells for figuring this out.

---

