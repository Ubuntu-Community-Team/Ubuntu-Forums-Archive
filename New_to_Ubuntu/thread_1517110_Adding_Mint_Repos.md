---
title: "Adding Mint Repos?"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by AndyP79 on 2010-06-24
Hi Ya'll, Just wondering if anyone here has tried to add the Mint Repos to Ubuntu? I have been using Mint for some time, but some of the great new things going on in Ubuntu have me switching back. I love the new look and social bits and pieces, but need back some of the user friendly items of Mint. Things like right click and choose open as root, and the codecs, besides, I have found myself customizing my Mint to look like Ubuntu. Any thoughts on this?

---

### Post by Crazedpsyc on 2010-06-24
I thought they added that to Karmic and mint just got it (the right-click part) but now that I look, the tool is /usr/bin/mintdesktop, which contains
> 
#!/usr/bin/python

import os

os.system("/usr/lib/linuxmint/mintDesktop/mintDesktop.py")




/usr/lib/linuxmint/mintDesktop/mintDesktop.py contains:
> 
#!/usr/bin/env python

try:
    import os
    import commands
    import sys
    import string
    import pygtk
    pygtk.require("2.0")
    import gtk
    import gtk.glade
    import gettext
except Exception, detail:
    print detail
    sys.exit(1)


# i18n
gettext.install("mintdesktop", "/usr/share/linuxmint/locale")

# i18n for menu item
menuName = _("Desktop Configuration Tool")
menuGenericName = _("Gnome Settings")
menuComment = _("Fine-tune Gnome settings")

class MintDesktop:
    """MintDesktop - Makes the best out of your Gnome desktop..."""

    def __init__(self):
        
        self.gladefile = '/usr/lib/linuxmint/mintDesktop/mintDesktop.glade'
        self.wTree = gtk.glade.XML(self.gladefile, "main_window") 
        self.wTree.get_widget("main_window").set_title(_("Desktop Configuration Tool"))
        self.wTree.get_widget("main_window").connect("destroy", gtk.main_quit)
        self.wTree.get_widget("button_cancel").connect("clicked", gtk.main_quit)
        self.wTree.get_widget("button_ok").connect("clicked", self.applyChanges)

        # i18n
        self.wTree.get_widget("label3").set_text(_("Desktop Items"))
        self.wTree.get_widget("label5").set_text("Gnome Compositing")
        self.wTree.get_widget("checkbox_computer").set_label(_("Computer"))
        self.wTree.get_widget("checkbox_home").set_label(_("Home"))
        self.wTree.get_widget("checkbox_network").set_label(_("Network"))
        self.wTree.get_widget("checkbox_trash").set_label(_("Trash"))
        self.wTree.get_widget("checkbox_volumes").set_label(_("Mounted Volumes"))
        self.wTree.get_widget("checkbox_compositing").set_label("Gnome compositing")        
        
        # Get the current configuration
        confComputer = commands.getoutput("gconftool-2 --get /apps/nautilus/desktop/computer_icon_visible")
        if (confComputer == "true"):
            self.wTree.get_widget("checkbox_computer").set_active(1)
        confHome = commands.getoutput("gconftool-2 --get /apps/nautilus/desktop/home_icon_visible")
        if (confHome == "true"):
            self.wTree.get_widget("checkbox_home").set_active(1)
        confNetwork = commands.getoutput("gconftool-2 --get /apps/nautilus/desktop/network_icon_visible")
        if (confNetwork == "true"):
            self.wTree.get_widget("checkbox_network").set_active(1)
        confTrash = commands.getoutput("gconftool-2 --get /apps/nautilus/desktop/trash_icon_visible")
        if (confTrash == "true"):
            self.wTree.get_widget("checkbox_trash").set_active(1)
        confVolumes = commands.getoutput("gconftool-2 --get /apps/nautilus/desktop/volumes_visible")
        if (confVolumes == "true"):
            self.wTree.get_widget("checkbox_volumes").set_active(1)
        confCompositing = commands.getoutput("gconftool-2 --get /apps/metacity/general/compositing_manager")
        if (confCompositing == "true"):
            self.wTree.get_widget("checkbox_compositing").set_active(1)
                    

    def applyChanges(self, widget): 
        computer_selected = self.wTree.get_widget("checkbox_computer").get_active()
        if (computer_selected == True):
            os.system("gconftool-2 --type bool --set /apps/nautilus/desktop/computer_icon_visible true")
        else:
            os.system("gconftool-2 --type bool --set /apps/nautilus/desktop/computer_icon_visible false")
        
        home_selected = self.wTree.get_widget("checkbox_home").get_active()
        if (home_selected == True):
            os.system("gconftool-2 --type bool --set /apps/nautilus/desktop/home_icon_visible true")
        else:
            os.system("gconftool-2 --type bool --set /apps/nautilus/desktop/home_icon_visible false")
        
        network_selected = self.wTree.get_widget("checkbox_network").get_active()
        if (network_selected == True):
            os.system("gconftool-2 --type bool --set /apps/nautilus/desktop/network_icon_visible true")
        else:
            os.system("gconftool-2 --type bool --set /apps/nautilus/desktop/network_icon_visible false")
        
        trash_selected = self.wTree.get_widget("checkbox_trash").get_active()
        if (trash_selected == True):
            os.system("gconftool-2 --type bool --set /apps/nautilus/desktop/trash_icon_visible true")
        else:
            os.system("gconftool-2 --type bool --set /apps/nautilus/desktop/trash_icon_visible false")
                
        volumes_selected = self.wTree.get_widget("checkbox_volumes").get_active()
        if (volumes_selected == True):
            os.system("gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible true")
        else:
            os.system("gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible false")        
                
        compositing_selected = self.wTree.get_widget("checkbox_compositing").get_active()
        if (compositing_selected == True):
            os.system("gconftool-2 --type bool --set /apps/metacity/general/compositing_manager true")
        else:
            os.system("gconftool-2 --type bool --set /apps/metacity/general/compositing_manager false")
        
        gtk.main_quit()        
        sys.exit(0)    
            
if __name__ == "__main__":
    MintDesktop()
    gtk.main()


hope this helps some!

---

### Post by philinux on 2010-06-24
Right click open as root. Instal nautilus-gksu

---

### Post by AndyP79 on 2010-06-24
???? Sorry, I have no clue what either of these posts want me to do. I mean, I know about install gksu, but then what? What does that do? And the first post? uhhh...sorry, I am lost on that.

---

### Post by marshmallow1304 on 2010-06-24
Post #3 refers to the package [nautilus-gksu]("apt://nautilus-gksu"), which will provide an "Open as root" option in the right-click menu in nautilus.

Most codecs are installed easily and nearly automatically upon trying to open the file for which the codec is required.

---

### Post by stmiller on 2010-06-24
In ubuntu, just add this to get the good stuff:

[http://medibuntu.org/](http://medibuntu.org/)

And then also doing this one command will install all codecs and stuff you need:
```

sudo apt-get install ubuntu-restricted-extras

```

No need to add mint, unless you want their themes and artwork.

---

### Post by AndyP79 on 2010-06-24
hmmm...okay, cool thanks for the thoughts, help and hints. 
Thanks Again

---

### Post by Crazedpsyc on 2010-06-28
To get some extra good stuff including open as root, install ubuntu-tweak here: [http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
It also does lots of other stuff that I find useful, so hve fun

---

### Post by elnetotaca on 2011-02-24
First we want to add the Mint repo by creating a new file in /etc/apt/sources.list.d/ called mint.list:
sudo nano /etc/apt/sources.list.d/mint.list

Paste in the following line:
deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) isadora main

Press Ctrl+X to close Nano and save the file.
Install the GPG key for the repo:
sudo apt-key adv &#8211;recv-key &#8211;keyserver keyserver.ubuntu.com 0FF405B2

Next run aptitude update, and install some Mint packages:
sudo aptitude update; sudo aptitude install mint-translations mint-common mintmenu

---

### Post by elnetotaca on 2011-02-24
1

---

