---
title: "openbox issues"
date: 2010-04-28
forum: New to Ubuntu
---

### Post by dzon65 on 2010-04-28
Hi guys.
Since I'm increasingly intrested in openbox,decided to give it a run like this:minimal/openbox/gnome-panel(autohide,website shortcuts),thunar and all kinds of leightweight stuff.Now,I installed jockey gtk as well since I'm used to use it ubuntu,lxde whatever.However,I wanted to install the 185 version driver and a window pops up telling me I'm not allowed to do this (?).So,I installed it through synaptics but even if it should be installed,it hasn't (gradients issue whatever).Now,when I try jockey again,it tells me that a version of it is already installed.What would be a good way to install this driver?
Second prob.There is no logout/shutdown window.(see screenshot)I do have this in my slitaz pc's.How can I get this.
Third prob.This gtk theme's been used in all of my previous setups using the murrine engine.I've installed several engines now but still,it doesn't apply correctly.
Thanks in advance.

---

### Post by dzon65 on 2010-04-28
Ok,got the driver installed.Envyng worked better.
Edit:where can I find additional language packs?

---

### Post by dzon65 on 2010-04-29
Okay.The driver's working,he pixbuf gtk engine solved the gtk theme issue.But still haven't found how to have a shutdown/logout.....window.

---

### Post by dzon65 on 2010-04-29
Found a nice solution on the arch forum.With this,no more problems.Thread solved.

---

### Post by Mark76 on 2010-04-29
Can I just say I hope that's not you in your avatar :shock:

---

### Post by dzon65 on 2010-04-29
Wouhaha,no,hardly.My previous one was the same dude in a far too small boat.

---

### Post by kerry_s on 2010-04-29
> **dzon65 said:**
> Found a nice solution on the arch forum.With this,no more problems.Thread solved.

hey, do you got that background in that screenshot?
if so, can you attach or put link to?

---

### Post by dzon65 on 2010-04-29
Kerry,just a sec,have to look it up.I'll post it wright away.

---

### Post by dzon65 on 2010-04-29
Forgotten it's the background for my youtube style.Anyway:[http://img64.imageshack.us/img64/20/newstatic.png](http://img64.imageshack.us/img64/20/newstatic.png)
As you can see,it's png,it's not so big.

---

### Post by dzon65 on 2010-04-29
BTW kerry.I use gnomepanel in this OB setup.I use the toppanel as autohide menu (left).But everytime I log in,it shows in the center of my desktop.Tried adding a sleepfactor to the autostart.sh but doesn't help.
And,still haven't figured out how to edit the etc/sudoers file.For that shutdown/logout window.

---

### Post by Mark76 on 2010-04-29
That shutdown menu is awesome :D

---

### Post by dzon65 on 2010-04-29
If I could only get it to work!Stuck with visudo/sudoers file.
[http://www.mediafire.com/?zoe2kgi3n2n](http://www.mediafire.com/?zoe2kgi3n2n)

---

### Post by kerry_s on 2010-04-29
thanks for the pic, got it on the desktop, but hmm...don't feel right. :(

sudoers, in terminal:

**sudo visudo**

put-> **your-name ALL=NOPASSWD: /sbin/shutdown,/sbin/reboot**


see pic for how mine looks "owner" is me.

---

### Post by dzon65 on 2010-04-29
I put in this but doesn't do much.# yourUserName ALL=(ALL) NOPASSWD:/sbin/shutdown

import os
import gtk
import gtk.glade
import pygtk
import sys

# Class Commands
class Commands:
        
    def logout(self):
        os.system("/usr/bin/killall openbox")
    
    def reboot(self):
        os.system("/usr/bin/sudo shutdown -r now")
    
    def shutdown(self):
        os.system("/usr/bin/sudo shutdown -h now")
        
# Class Shutdown gui
class ShutdownGui(Commands):
    
    def __init__(self):
        self.gladefile = sys.path[0] + "/shutdown_gui.glade"
        self.wTree = gtk.glade.XML(self.gladefile)
        self.ShutdownBox = self.wTree.get_widget("ShutdownBox")
        self.set_button_signals()
    
    def show(self):
        self.ShutdownBox.show_all()

    def set_button_signals(self):
        button_dictonary = {"on_LogoutButton_clicked"   : self.on_logout,
                    "on_RebootButton_clicked"   : self.on_reboot,
                    "on_ShutdownButton_clicked" : self.on_shutdown,
                    "on_CancelButton_clicked"    : self.on_cancel}
        self.wTree.signal_autoconnect(button_dictonary)
    
    def on_logout(self, data):
        self.logout()
    
    def on_reboot(self, data):
        self.reboot()
    
    def on_shutdown(self, data):
        self.shutdown()
    
    def on_cancel(self, data):
        gtk.main_quit()()
        

# Main Program
def main():
    shutbox = ShutdownGui()
    shutbox.show()
    gtk.main()

# Script Trick
if __name__ == "__main__":
    main()
    sys.exit(0)

---

### Post by kerry_s on 2010-04-29
so all you need is the shutdown, do it like this:

```
your-name ALL=NOPASSWD: /sbin/shutdown
```

---

### Post by dzon65 on 2010-04-29
Like this?If so,how do I save this?

---

### Post by dzon65 on 2010-04-29
Kerry,it's okay,got it to work.
Thanks for all the replies.
Kind regards,J.

---

### Post by kerry_s on 2010-04-29
> **dzon65 said:**
> Like this?If so,how do I save this?

yeap, press enter to leave a empty line under it.
press-> ctrl+x
then-> y
then-> enter

---

### Post by dzon65 on 2010-04-29
Getting used to openbox.Really like it.exept for gnome-panel/utils no gnome,lxde,xfce.....and fast.

---

### Post by kerry_s on 2010-04-29
> **dzon65 said:**
> Getting used to openbox.Really like it.exept for gnome-panel/utils no gnome,lxde,xfce.....and fast.

the more you play with it the easier it gets, it's just a matter of learning what go's where to get what you want.

i was bored, so i swapped lxpanel for xfce4-panel, so i'm running openbox+nautilus+xfce4-panel+gnome-main-menu in a lxsession, even went ahead an gave it the gnome look, talk about your bastard of a system. :lolflag:

---

### Post by dzon65 on 2010-04-30
Héhé.I like bastard sytems,they turn out to give birth to the nicest.Downloaded slitaz mini,just openbox,firefox and a packagemanager (15mb).Gonna set it up as a total openbox system to run it on an old pc.See what it gives.My biggest concern is that as far as I know,gnome panel is the only panel/dock that supports website shortcuts.I simply hate adding a bookmark toolbar to my browser or go through the bookmark menu.And that one is not available in the slitaz repos.The laptop I'm on wright has 2Gb ram and some 160Gb storage so I could install a full ubuntu but stick with a minimal/openbox.Like you said,once you know how to run things......
Oh,btw,edited that background a little,turns out "cool".Makes the menu/windows kinda fly.

---

