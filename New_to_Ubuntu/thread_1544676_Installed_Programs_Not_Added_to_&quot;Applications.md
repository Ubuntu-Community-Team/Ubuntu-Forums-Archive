---
title: "Installed Programs Not Added to &quot;Applications&quot; Menu"
date: 2010-08-02
forum: New to Ubuntu
---

### Post by Ron Carson on 2010-08-02
Just started having a problem that after installing applications, they don't appear on the "Applications" menu.  For example, I installed Wine via Synaptic but there is no Wine menu.  How can I fix this problem so that programs are automatically added to the Applications menu?

R

---

### Post by SpockVulcan on 2010-08-02
Right click the menu and then edit menus there should be a check box somewhere in there to do with Wine

---

### Post by Ron Carson on 2010-08-02
> **SpockVulcan said:**
> Right click the menu and then edit menus there should be a check box somewhere in there to do with Wine

Did that and found about 6 "wine" programs and a bunch of other crap.  Deleted them all, removed Wine via synaptic, reinstalled and now have no Wine functionality.  Now what?

I love Ubuntu, but I get frustrated with not knowing how to fix it when broke.

---

### Post by beew on 2010-08-02
Hi,

The same thing happened to me yesterday and I just figured out how to restore the wine menu :)

On the top panel click "Places". Then go to Home/username, where "username" is your login name. Click "view" and check "Show Hidden Files". Then open the folder .config and go to the subfolder "menus". You will find inside   a file called "applications.menu". Open it with gedit and find the entry for WINE. You will see the tag <delete> in several places under the WINE entry, they were created when you deleted the wine menu in the Main Menu. Now delete all these <delete> tags . Save the file and close it. Reboot and you should find those WINE menus back. If not, just open System > Preferences > Main Menu and check the appropriate boxes.

---

### Post by Ron Carson on 2010-08-02
beew, thank you so much for your reply.  I had just found that fix before logging back onto the Ubuntu Forum.  Isn't is so weird that something so obscure cause such a headache!

---

### Post by Ocxic on 2010-08-02
running "killall gnome-panel" from a terminal will re-load the menu and panels, and will usually fix an item not appearing.

---

