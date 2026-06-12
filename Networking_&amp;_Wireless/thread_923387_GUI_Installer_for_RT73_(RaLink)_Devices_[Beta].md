---
title: "GUI Installer for RT73 (RaLink) Devices [Beta]"
date: 2008-09-18
forum: Networking &amp; Wireless
---

### Post by Kiefer Rodriguez on 2008-09-18
**RT73 Driver GUI Installer**
Okay so it's taken me just over, erm, six months to update what started out as a simple install script to install wireless devices from the RT73 RaLink chipset, but it's finally been updated. I actually re-wrote this entire thing over a few days off, hence why it's in Beta stage- I **am** expecting bugs and errors, so bare with me on this one guys. Details are as follows.

**Language:** Python (GTK 2.X GUI)
**Version:** 0.5.2 Beta
**Author:** Kiefer Rodriguez

It's pretty simple, download the attached zipfile's (the script, *and* the SerialMonkey driver, both attached), and follow the instructions provided (check out the README), if you're not sure what you're supposed to enter in to a certain field, click the '?' button next to said field and that should get you back on track. Time for some screenshots..

[IMG]http://c.imagehost.org/0643/rt73guiinstaller1.jpg[/IMG]
[IMG]http://c.imagehost.org/0889/rt73guiinstaller2.jpg[/IMG]

And heres the source for your viewing pleasure (to actually use the installer, you need to download the attached ZIP file, not just grab the source)

```
########################
# name:    RT73 GUI Based Installer     #
# ver:            0.5 Beta                                 #
# author:    Kiefer Rodriguez                     #
# license:    GPL                                             #
# description: A GUI based Installer #
#                            for the RT73 RaLink    #
#                            chipset. GTK based.  #
########################

#!/usr/bin/env python

import pygtk
pygtk.require('2.0')
import os
import gtk        

class MainInstallerWindow:
    VERSION = "v0.5 Beta"
    def display_help_dialog(self, widget, event="clicked", data=None):
        if widget == self.button_ifaceq:
            self.label_help.set_text("This field requires the interface name of the wireless device you wish to install\n" \
                                                            "the RT73 drivers under, by default it should be 'wlan0' or 'ath0', if you have a pre-existing\n" \
                                                            "wireless device installed, it may by default be 'wlan1' or 'ath1'.")
            self.help_title = "Interface Help"
        elif widget == self.button_package_managerq:
            self.label_help.set_text("This field requires the name of your default package manager, if your using a Debian based system\n" \
                                                        "e.g. Ubuntu, Kubuntu, Edubuntu, or Xubuntu then your package manager, by default is 'apt-get'.\n" \
                                                        "If the install fails due to the package manager, you may use an alternative package manager, check\n" \
                                                        "your distrobution documentation to find out which one.")
            self.help_title = "Package manager Help"
        elif widget == self.button_essidq:
            self.label_help.set_text("This field requires the name of your access point you plan to connect to by default, e.g. 'our_internet'.")
            self.help_title = "Access Point ESSID Help"
        elif widget == self.button_wepkeyq:
            self.label_help.set_text("This field requires your WEP key used to authenticate with your access point, it can be of any length and\n" \
                                                                    "either HEX or ASCII, remember that ASCII keys must be prefixed with 's:' (without the quotes).")
            self.help_title = "WEP Key Help"
        elif widget == self.button_tarballq:
            self.label_help.set_text("This field requires the FULL path to the tarball ('filename.tar[.gz]') containing the SerialMonkey drivers, most likely\n" \
                                                            "named 'rt73-cvs-daily.tar.gz'.")
            self.help_title = "Driver Tarball Help"
        self.help_dialog.show()
    def toggle_wep(self, widget, event="toggled", data=None):
        if self.checkbox_usewep.get_active():
            self.entry_wepkey.set_text(self.wephistory)
            self.entry_wepkey.set_editable(True)
        else:
            self.wephistory = self.entry_wepkey.get_text()
            self.entry_wepkey.set_text("-WEP Disabled-")
            self.entry_wepkey.set_editable(False)
    def main(self):
        gtk.main()
    def delete_event(self, widget, event, data=None):
        return False
    def destroy_event(self, widget, data=None):
        gtk.main_quit()
    def show_about(self, widget, event="clicked", data=None):
        self.output.set_justification(gtk.JUSTIFY_CENTER)
        self.output_buffer.set_text("\n\n\n\nRT73 Chipset GUI Installer "+self.VERSION+"\n\n" \
                                                            "Lead Programmer (GUI & Core)\t\tKiefer Rodriguez\n" \
                                                            "Based on the RT73 driver manual install guide by Diepruis" \
                                                            "\n\nhttp://thelinuxnewb.blogspot.com\n")
    def start_install(self, widget, event="clcked", data=None):
        self.button_okay.set_sensitive(False)
        self.button_cancel.set_sensitive(False)
        self.button_loadtb.set_sensitive(False)
        self.output.set_justification(gtk.JUSTIFY_LEFT)
        self.output_buffer.set_text("Commencing install..")
        self.output_buffer.insert(self.output_buffer.get_end_iter(),"\n*    Copying driver tarball to /usr/src..")
        os.system("sudo cp"+self.entry_tbpath.get_text()+" /usr/src")
        self.pb_install.set_fraction(0.02)
        self.pb_install.set_text("Installing | 2%")
        self.output_buffer.insert(self.output_buffer.get_end_iter(),"\n*    Unpacking driver tarball contents to /usr/src..")
        os.system("sudo tar -xvzf /usr/src/*.tar.gz")
        self.pb_install.set_text("Installing | 5%")
        self.pb_install.set_fraction(0.05)
        if self.checkbox_internet.get_active()==False:        
            self.output_buffer.insert(self.output_buffer.get_end_iter(), "\n*    Please confirm your distrobution's LiveCD is inserted")
            self.output_buffer.insert(self.output_buffer.get_end_iter(),"\n*    Gathering required header files from CD, this may take a while..")
            os.system("sudo apt-cdrom add")
            self.output_buffer.insert(self.output_buffer.get_end_iter(),"\n*    Added CD-Rom to sources list, now updating list..")
            os.system("sudo aptitude update")
            self.output_buffer.insert(self.output_buffer.get_end_iter(),"\n*    Installing headers..")
            os.system("sudo aptitude install build-essential linux-headers-`uname -r`")
        else:
            self.output_buffer.insert(self.output_buffer.get_end_iter(),"\n*    Installing headers..")
            os.system("sudo" + self.entry_package_manager.get_text() +" install build-essential linux-headers-`uname -r`")
        self.pb_install.set_fraction(0.15)
        self.pb_install.set_text("Installing | 15%")
        self.output_buffer.insert(self.output_buffer.get_end_iter(),"\n*    Compiling RT73 module..")
        os.system("cd /usr/src/rt73-*/Module && sudo make")
        self.pb_install.set_fraction(0.20)
        self.pb_install.set_text("Installing | 20%")
        self.output_buffer.insert(self.output_buffer.get_end_iter(),"\n*    Correcting file size issue..")
        os.system("sudo strip -S rt73.ko")
        self.pb_install.set_fraction(0.22)
        self.pb_install.set_text("Installing | 22%")
        self.output_buffer.insert(self.output_buffer.get_end_iter(),"\n*    Installing module..")
        os.system("sudo make install")
        self.pb_install.set_text("Installing | 35%")
        self.pb_install.set_fraction(0.35)
        self.output_buffer.insert(self.output_buffer.get_end_iter(),"\n*    Bringing down wireless device..")
        os.system("sudo ifconfig" + self.entry_iface.get_text() + "  down")
        self.pb_install.set_fraction(0.42)
        self.pb_install.set_text("Installing | 42%")
        self.output_buffer.insert(self.output_buffer.get_end_iter(),"\n*    Removing obsolete RaLink modules..")
        os.system("sudo modprobe -r rt73usb")
        self.pb_install.set_fraction(0.45)
        self.pb_install.set_text("Installing | 45%")
        os.system("sudo modprobe -r rt2570")
        self.pb_install.set_fraction(0.50)
        self.pb_install.set_text("Installing | 50%")
        os.system("sudo modprobe -r rt2500usb")
        self.pb_install.set_fraction(0.52)
        self.pb_install.set_text("Installing | 52%")
        os.system("sudo modprobe -r rt2x00lib")
        self.pb_install.set_fraction(0.60)
        self.pb_install.set_text("Installing | 60%")
        self.output_buffer.insert(self.output_buffer.get_end_iter(),"\n*    Making a backup of /etc/modprobe.d/blacklist to your /home directory..")
        os.system("sudo cp /etc/modprobe.d/blacklist ~/blacklist.backup")
        self.pb_install.set_fraction(0.65)
        self.pb_install.set_text("Installing | 65%")
        os.system("sudo cp /etc/modprobe.d/blacklist ./rt73-blacklist.temp")
        self.output_buffer.insert(self.output_buffer.get_end_iter(),"\n*    Opening /etc/modprobe.d/blacklist..")
        m    odprobe = file("rt73-blacklist.temp", 'a')
        self.pb_install.set_fraction(0.67)
        self.pb_install.set_text("Installing | 67%")
        self.output_buffer.insert(self.output_buffer.get_end_iter(),"\n*    Writing to /etc/modprobe.d/blacklist..")
        modprobe.write("# Added by RT73 Installer\nblacklist rt2570\nblacklist rt73usb\nblacklist rt2500usb\nblacklist rt2x00lib\n#END.")
        self.pb_install.set_fraction(0.70)
        self.pb_install.set_text("Installing | 70%")
        os.system("sudo cp rt73-blacklist.temp /etc/modprobe.d/blacklist && rm -rf rt73-blacklist.temp")
        self.pb_install.set_fraction(0.75)
        self.pb_install.set_text("Installing | 75%")
        self.output_buffer.insert(self.output_buffer.get_end_iter(),"\n*    Closing blacklist..")
        modprobe.close()
        self.pb_install.set_fraction(0.77)
        self.pb_install.set_text("Installing | 77%")
        self.output_buffer.insert(self.output_buffer.get_end_iter(),"\n*    Deleting temp files..")
        os.system("sudo rm -rf rt73-blacklist.temp")
        self.pb_install.set_fraction(0.80)
        self.pb_install.set_text("Installing | 80%")
        self.output_buffer.insert(self.output_buffer.get_end_iter(),"\n*    Making sure the driver was installed correctly..")
        os.system("sudo modprobe -v rt73")
        self.pb_install.set_fraction(0.85)
        self.pb_install.set_text("Installing | 85%")
        self.output_buffer.insert(self.output_buffer.get_end_iter(),"\n*    Bringing up device..")
        os.system("sudo ifconfig" + self.entry_iface.get_text() +" up")
        self.pb_install.set_fraction(0.87)
        self.pb_install.set_text("Installing | 87%")
        self.output_buffer.insert(self.output_buffer.get_end_iter(),"\n*    Configuring new device..")
        os.system("sudo iwconfig" + self.entry_iface.get_text() +" essid" + self.entry_essid.get_text())
        self.pb_install.set_fraction(0.90)
        self.pb_install.set_text("Installing | 90%")
        if self.checkbox_usewep.is_active():
            os.system("sudo iwconfig" + self.entry_iface.get_text() +" key" + self.entry_wepkey.get_text())
            os.system("sudo iwconfig" + self.entry_iface.get_text() +" key on")
        self.pb_install.set_fraction(0.95)
        self.pb_install.set_text("Installing | 95%")
        self.output_buffer.insert(self.output_buffer.get_end_iter(),"\n*    Running dhclient..")
        os.system("sudo dhclient" + self.entry_iface.get_text())
        self.output_buffer.insert(self.output_buffer.get_end_iter(),"\nInstall complete, you should now be able to access the internet.\nIf not consult the " \
                                                                                                                        "README included with this program.")
        self.pb_install.set_fraction(1)
        self.pb_install.set_text("Installation Complete | 100%")
        self.button_okay.set_sensitive(True)
        self.button_cancel.set_sensitive(True)
        self.button_loadtb.set_sensitive(True)
    def file_ok_sel(self, w):
        self.path_tarball =  self.filew.get_filename()
        self.entry_tbpath.set_text(self.path_tarball)
        self.filew.hide()
    def pick_tarball(self, widget, event="clcked", data=None):
        self.filew.show()
    def __init__(self):
        # Set up window
        self.window = gtk.Window(gtk.WINDOW_TOPLEVEL)
        self.window.set_title("RT73 Driver Install")
        # Set up basic signal handlers
        self.window.connect("delete_event", self.delete_event)
        self.window.connect("destroy", self.destroy_event)
        # Set up layout
        self.mainvbox = gtk.VBox(False, 8)
        self.window.add(self.mainvbox)
        self.window.set_border_width(10)
        self.box_iface = gtk.HBox(False, 3)
        self.box_package_manager = gtk.HBox(False, 3)
        self.box_essid = gtk.HBox(False, 3)
        self.box_wepkey = gtk.HBox(False, 3)
        self.box_buttons = gtk.HBox(False, 95)
        self.box_internet = gtk.HBox(False, 3)
        self.box_tb = gtk.HBox(False,3)
        self.box_write_interface = gtk.HBox(False, 1)
        self.box_output = gtk.HBox(False,1)
        self.box_getdata = gtk.HBox(False, 2)
        self.box_ventry = gtk.VBox(True,2)
        self.box_vlabel = gtk.VBox(True,2)
        self.box_tbentry = gtk.HBox(True, 2)
        self.box_progress = gtk.HBox(False,1)
        self.mainvbox.pack_start(self.box_getdata)
        self.box_getdata.pack_start(self.box_vlabel)
        self.box_getdata.pack_start(self.box_ventry)
        self.box_vlabel.pack_start(self.box_iface)
        self.box_vlabel.pack_start(self.box_package_manager)
        self.box_vlabel.pack_start(self.box_essid)
        self.box_vlabel.pack_start(self.box_wepkey)
        self.box_vlabel.pack_start(self.box_tb)
        self.mainvbox.pack_start(self.box_internet)
        self.mainvbox.pack_start(self.box_write_interface)
        self.mainvbox.pack_start(self.box_output)
        self.mainvbox.pack_start(self.box_progress)
        self.mainvbox.pack_start(self.box_buttons)
        # Input boxes
        self.entry_iface = gtk.Entry(max=5)
        self.entry_package_manager = gtk.Entry()
        self.entry_essid = gtk.Entry()
        self.entry_wepkey = gtk.Entry()
        self.entry_tbpath = gtk.Entry()
        self.entry_iface.set_text("wlan0")
        self.entry_package_manager.set_text("apt-get")
        self.entry_essid.set_text("my_wireless")
        self.entry_wepkey.set_text("0123456789")
        self.entry_tbpath.set_text("/home/you/rt73-cvs-daily.tar.gz")
        # Text labels
        self.label_iface = gtk.Label("Interface name")
        self.label_package_manager = gtk.Label("Package manager")
        self.label_essid = gtk.Label("ESSID")
        self.label_wepkey = gtk.Label("WEP key")
        self.label_tarball = gtk.Label("Path to SerialMonkey tarball  ")
        self.label_help = gtk.Label("Error Occured, Could not locate Help strings.")
        self.help_title = "Help"
        # Buttons
        self.button_cancel = gtk.Button("", gtk.STOCK_CANCEL)
        self.button_okay = gtk.Button("Start Install")
        self.button_loadtb = gtk.Button("",gtk.STOCK_OPEN)
        self.button_ifaceq = gtk.Button("  ?  ")
        self.button_package_managerq = gtk.Button("  ?  ")
        self.button_essidq = gtk.Button("  ?  ")
        self.button_wepkeyq = gtk.Button("  ?  ")
        self.button_tarballq = gtk.Button("  ?  ")
        self.button_dialog_okay = gtk.Button("", gtk.STOCK_OK)
        self.button_about = gtk.Button("About")
        # Other widgets
        self.checkbox_write_interface = gtk.CheckButton("Set up /etc/network/Interfaces file")
        self.checkbox_usewep = gtk.CheckButton("Use WEP")
        self.checkbox_internet = gtk.CheckButton("Other active internet connection")
        self.filew = gtk.FileSelection("Choose Drivar tarball")
        self.filew.connect("destroy", self.destroy_event)
        self.filew.ok_button.connect("clicked", self.file_ok_sel)
        self.filew.cancel_button.connect("clicked", lambda w: self.filew.hide())
        self.filew.set_filename("rt73-cvs-2008XXXXXX")
        self.checkbox_usewep.set_active(True)
        self.checkbox_write_interface.set_active(True)
        self.output = gtk.TextView()
        self.output.set_editable(False)
        self.output.set_cursor_visible(False)
        self.output.set_wrap_mode(gtk.WRAP_WORD)
        self.output_buffer = self.output.get_buffer()
        self.output.set_justification(gtk.JUSTIFY_CENTER)
        self.output_buffer.set_text("\n\n\n\nRT73 Chipset GUI Installer "+self.VERSION+"\nBy Kiefer Rodriguez\n\n-Important-\nIf you do not have a pre-existing" \
                                                            " internet connection (ethernet etc).\nPlease ensure your LiveCD is in the drive and spinning BEFORE you start the install.\n\n-Disclaimer-" \
                                                            "\n"  \
                                                            "This program wil modify system files, and while the author has made every\neffort to ensure a safe install, such can not "  \
                                                            "be guaranteed. By activating\nthe install process you agree that the author is in no way liable or responsible\nfor any damage " \
                                                            "or harm caused as a result of running this program.")
        self.output.set_size_request(300, 380)
        self.output.modify_base(gtk.STATE_NORMAL, gtk.gdk.color_parse("black"))
        self.output.modify_text(gtk.STATE_NORMAL, gtk.gdk.color_parse("white"))
        self.output_iter = self.output_buffer.get_end_iter()
        self.help_dialog = gtk.Dialog(title=self.help_title ,parent=self.window, )
        self.pb_install = gtk.ProgressBar()
        self.pb_install.set_text("Waiting to start install | 0%")
        self.pb_install.set_fraction(0)
        # Pack containers
        self.box_iface.pack_start(self.button_ifaceq, False, False, 0)
        self.box_iface.pack_start(self.label_iface, False, False, 0)
        self.box_package_manager.pack_start(self.button_package_managerq, False, False, 0)
        self.box_package_manager.pack_start(self.label_package_manager, False, False, 0)
        self.box_essid.pack_start(self.button_essidq, False, False, 0)
        self.box_essid.pack_start(self.label_essid, False, False, 0)
        self.box_wepkey.pack_start(self.button_wepkeyq, False, False, 0)    
        self.box_wepkey.pack_start(self.label_wepkey, False, False, 0)
        self.box_ventry.pack_start(self.entry_iface)
        self.box_ventry.pack_start(self.entry_package_manager)
        self.box_ventry.pack_start(self.entry_essid)
        self.box_ventry.pack_start(self.entry_wepkey)
        self.box_buttons.pack_start(self.button_cancel)
        self.box_buttons.pack_start(self.button_about)
        self.box_buttons.pack_start(self.button_okay)
        self.box_internet.pack_start(self.checkbox_internet)
        self.box_internet.pack_start(self.checkbox_usewep)
        self.box_write_interface.pack_start(self.checkbox_write_interface)
        self.box_tb.pack_start(self.button_tarballq, False, False, 0)
        self.box_tb.pack_start(self.label_tarball, False, False, 0)
        self.box_ventry.pack_start(self.box_tbentry)
        self.box_tbentry.pack_start(self.entry_tbpath)
        self.box_tbentry.pack_start(self.button_loadtb)
        self.box_output.pack_start(self.output)
        self.formbox = gtk.VBox(False, 0)
        self.help_dialog.action_area.pack_start(self.formbox)
        self.formbox.pack_start(self.label_help)
        self.formbox.pack_start(self.button_dialog_okay, False, False, 0)
        self.box_progress.pack_start(self.pb_install)
        # Signal connections
        self.button_loadtb.connect("clicked",self.pick_tarball)
        self.button_cancel.connect("clicked",lambda w: self.filew.destroy())
        self.button_dialog_okay.connect("clicked", lambda w: self.help_dialog.hide())
        self.button_ifaceq.connect("clicked", self.display_help_dialog)
        self.button_wepkeyq.connect("clicked", self.display_help_dialog)
        self.button_essidq.connect("clicked", self.display_help_dialog)
        self.button_package_managerq.connect("clicked", self.display_help_dialog)
        self.button_tarballq.connect("clicked", self.display_help_dialog)
        self.checkbox_usewep.connect("toggled", self.toggle_wep)
        self.button_okay.connect("clicked", self.start_install)
        self.button_about.connect("clicked", self.show_about)
        # Draw everything
        self.button_about.show()
        self.box_progress.show()
        self.pb_install.show()
        self.formbox.show()
        self.label_help.show()
        self.button_dialog_okay.show()
        self.box_tbentry.show()
        self.box_getdata.show()
        self.box_ventry.show()
        self.box_vlabel.show()
        self.button_ifaceq.show()
        self.button_package_managerq.show()
        self.button_essidq.show()
        self.button_wepkeyq.show()
        self.button_tarballq.show()
        self.output.show()
        self.box_output.show()
        self.entry_tbpath.show()
        self.label_tarball.show()
        self.button_loadtb.show()
        self.box_tb.show()
        self.box_write_interface.show()
        self.checkbox_write_interface.show()
        self.checkbox_usewep.show()
        self.checkbox_internet.show()
        self.box_internet.show()
        self.button_okay.show()
        self.button_cancel.show()
        self.box_buttons.show()
        self.label_iface.show()
        self.label_package_manager.show()
        self.label_essid.show()
        self.label_wepkey.show()
        self.entry_iface.show()
        self.entry_package_manager.show()
        self.entry_essid.show()
        self.entry_wepkey.show()
        self.mainvbox.show()
        self.box_iface.show()
        self.box_package_manager.show()
        self.box_essid.show()
        self.box_wepkey.show(
        self.window.show()
        # Misc variables
        self.wephistory = "0123456789"
if __name__ == "__main__":
    x = MainInstallerWindow()
    x.main()

```I am aware that the 'Configure /etc/network/Interfaces' option is not working, it will be patched in the coming days. Feedback/problems can either be posted here (suggested) or emailed to me, at *kiefer [dot] rodriguez [at] gmail [dot] com*

[B]Changelog
[/B][INDENT]
**0.5.2**  *Fixed *.is_active() bug.*
**0.5.1** *Fixed syntax error relating to Modprobe*
**0.5**    *Fixed WEP History bug (resetting to default on install)*
**0.4**    *Added help functions and basic support for file location dialog*
**0.3.1** *Rewrote GUI*
**0.3**    *Wrote all callback functions and skel. GUI*
**0.2**    *Mapped out basic GTK 2.0 GUI, fixed known bugs.*
**0.1***Rewrote entire script, basic command set.*
[/INDENT]-Kiefer

---

### Post by Bobski on 2008-09-18
That looks awesome. It is a shame that I installed my wireless driver yesterday using the diepruis method this is based on.

---

### Post by zszafran on 2008-09-18
Awesome job, looks great. Thanks for the effort.

---

### Post by Kiefer Rodriguez on 2008-09-18
Heh thanks for the kind words.

---

### Post by Foret on 2008-09-20
Mmm... Doesnt work. System: Fresh install of Ubuntu 8.04 with all possible updates. Here is console message: 

> soir@ub-soir:~/&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;/RT73_GUI_ Installer$ ls
README  rt73install.py
soir@ub-soir:~/&#1056;&#1072;&#1073;&#1086;&#1095;&#1080;&#1081; &#1089;&#1090;&#1086;&#1083;/RT73_GUI_ Installer$ sudo python rt73install.py 
  File "rt73install.py", line 126
    m	odprobe = file("rt73-blacklist.temp", 'a')
            ^
SyntaxError: invalid syntax


Or is it some kind of hands mutation? ;)

PS: care for newbies is great so thx anyway

---

### Post by McScruff on 2008-09-20
> **Foret said:**
> Mmm... Doesnt work. System: Fresh install of Ubuntu 8.04 with all possible updates. Here is console message: 



Or is it some kind of hands mutation? ;)

PS: care for newbies is great so thx anyway

I have the same problem

---

### Post by Kiefer Rodriguez on 2008-09-21
> **McScruff said:**
> I have the same problem

Wow, I see what's causing the problem, basic syntax error, why didn't Python pick up on it and spit out a nasty error? Oh well, just patched it- cheers guys.

---

### Post by papaj on 2008-09-24
big thanks from an old dog trying to learn new tricks

---

### Post by nepaliketa on 2008-09-26
> **Kiefer Rodriguez said:**
> Heh thanks for the kind words.

I am a newbie to UBUNTU and I am trying to install RT73 Ralink driver and your installer seems to be quite a good thing to first install. However, I have not been able to proceed beyond the download. WIll you be able to help?

Many thanks 
nepaliketa

---

### Post by escipio on 2008-09-28
Hi Kiefer,

nice and extraordinary job. Congratulations.
I was going to test it but I use WPA. I saw that your application is only for WEP. Is there any way of using it with WPA?

Thank you in advance.

Toni.

---

### Post by gnusci on 2008-09-28
Hi Kiefer, That is a great job, I did install my RT73 with the all bash script that BTW worked out just fine. But, I am happy that new people can use this gem installer.

---

### Post by Kiefer Rodriguez on 2008-09-29
First off guys, thanks for all the feedback. Sorry I havent been as active as I would have liked, was a bit busy with work :).

> Hi Kiefer,

nice and extraordinary job. Congratulations.
I was going to test it but I use WPA. I saw that your application is only for WEP. Is there any way of using it with WPA?

Thank you in advance.

Toni.

Toni, yes there is a way- it shouldnt be too hard. First run the installer specifying that you will not use WEP (you wont be connected after install at this point, no need to worry) then I suggest using wpa_supplicant (a good guide on this can be found [[COLOR="Blue"]**here**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=263136")). Let me know how you go, and good luck :)

> I am a newbie to UBUNTU and I am trying to install RT73 Ralink driver and your installer seems to be quite a good thing to first install. However, I have not been able to proceed beyond the download. WIll you be able to help?

Many thanks 
nepaliketa

nepaliketa,
Thanks for the feedback, by 'proceed beyond the download' do you mean you can not access the attached files from my post? if you could clarify what your having problems with, I'll be more than happy to help :)

---

### Post by DarKat on 2008-10-09
Hi Kiefer, 
i'm using your installer but when it arrives at 90%, it tell me:

```
cd: 1: can't cd to /usr/src/rt73-*/Module
strip: 'rt73.ko': No such file
nake: *** No rule to make target 'install'. Stop.
sudo: ifconfigwlan0: command not foun
FATAL: Module rt2570 not found.
FATAL: Module rt73 not found.
sudo: ifconfigwlan0: command not found
sudo: iwconfigwlan0: command not found
Traceback (most recent call last):
  File "rt73install.py", line 156, in start install
    if self.checkbox_usewep.is_active():
AttributeError: 'gtk.CheckButton' object has no attribute 'is_active
```

HELP! :D

---

### Post by Kiefer Rodriguez on 2008-10-10
> **DarKat said:**
> Hi Kiefer, 
i'm using your installer but when it arrives at 90%, it tell me:

```
cd: 1: can't cd to /usr/src/rt73-*/Module
strip: 'rt73.ko': No such file
nake: *** No rule to make target 'install'. Stop.
sudo: ifconfigwlan0: command not foun
FATAL: Module rt2570 not found.
FATAL: Module rt73 not found.
sudo: ifconfigwlan0: command not found
sudo: iwconfigwlan0: command not found
Traceback (most recent call last):
  File "rt73install.py", line 156, in start install
    if self.checkbox_usewep.is_active():
AttributeError: 'gtk.CheckButton' object has no attribute 'is_active
```

HELP! :D

DarKat,
Thanks for your reply, I've fixed that little bug - redownload the attached updated version (0.5.2) from the original post :D.

---

### Post by Kiefer Rodriguez on 2008-10-10
Also, 
Ignore these messages in the output,
```
FATAL: Module <module> not found.
```
Thats the installer blacklisting modules that dont exist, which is good :).

---

### Post by nisarmail@hotmail.com on 2008-10-11
Hi,
I'm super noob at Ubuntu and linux in general. I'm trying to get this install done but its failing. Its got to be something that i am doing wrong. I've never installed anything in ubuntu before but when i run the install, i seem to get to 65% install and it then crashes out on me. Dunno what i'm doing wrong.... maybe you can help...
I've downloaded both attachements. Both are in /home/nisar (my login)
I open a terminal window and type "python tr73install.py"
This brings up your driver installer.
I leave the "interface name" and "package manager" as it. I assume they are correct for ubuntu which i downloaded a few days ago from ubunu web site.
I change the essid to the name of my wireless lan.
I untick "use wep" as my wireless is wpa at the moment.
I change the serialmonkey tarball path to /home/nisar/rt73-cvs-daily.tar.gz
I put my original ubuntu cd in my cdrom drive, let it spin up then hit "Start Install"
The install starts but fails at 65%....

This is where i am stuck.
I post the terminal window below to help....

nisar@PackardBell:~$ python rt73install.py
sudo: cp/home/nisar/rt73-cvs-daily.tar.gz: command not found
tar: /usr/src/*.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
sh: sudoapt-get: not found
cd: 1: can't cd to /usr/src/rt73-*/Module
strip: 'rt73.ko': No such file
make: *** No rule to make target `install'. Stop.
sudo: ifconfigwlan0: command not found
FATAL: Module rt2570 not found.
Traceback (most recent call last):
  File "rt73install.py", line 126, in start_install
    modprobe = file("rt73-blacklist.temp", 'a')
IOError: [Errno 13] Permission denied: 'rt73-blacklist.temp'

Any help would be grateful.....
I'm trying to move into the linux scene but these problems keep putting me off.... i'm sure they are simple errors which i just don't see due to being a linux noob.

---

### Post by Kiefer Rodriguez on 2008-10-12
> **nisarmail@hotmail.com said:**
> Hi,
I'm super noob at Ubuntu and linux in general. I'm trying to get this install done but its failing. Its got to be something that i am doing wrong. I've never installed anything in ubuntu before but when i run the install, i seem to get to 65% install and it then crashes out on me. Dunno what i'm doing wrong.... maybe you can help...
I've downloaded both attachements. Both are in /home/nisar (my login)
I open a terminal window and type "python tr73install.py"
This brings up your driver installer.
I leave the "interface name" and "package manager" as it. I assume they are correct for ubuntu which i downloaded a few days ago from ubunu web site.
I change the essid to the name of my wireless lan.
I untick "use wep" as my wireless is wpa at the moment.
I change the serialmonkey tarball path to /home/nisar/rt73-cvs-daily.tar.gz
I put my original ubuntu cd in my cdrom drive, let it spin up then hit "Start Install"
The install starts but fails at 65%....

This is where i am stuck.
I post the terminal window below to help....

nisar@PackardBell:~$ python rt73install.py
sudo: cp/home/nisar/rt73-cvs-daily.tar.gz: command not found
tar: /usr/src/*.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
sh: sudoapt-get: not found
cd: 1: can't cd to /usr/src/rt73-*/Module
strip: 'rt73.ko': No such file
make: *** No rule to make target `install'. Stop.
sudo: ifconfigwlan0: command not found
FATAL: Module rt2570 not found.
Traceback (most recent call last):
  File "rt73install.py", line 126, in start_install
    modprobe = file("rt73-blacklist.temp", 'a')
IOError: [Errno 13] Permission denied: 'rt73-blacklist.temp'

Any help would be grateful.....
I'm trying to move into the linux scene but these problems keep putting me off.... i'm sure they are simple errors which i just don't see due to being a linux noob.

nisarmail,
Try running the installer as root,
```
sudo python rt73install.py
```
For more info, see,
```
man sudo
```
We were all new once, give Linux a chance - im sure youll find it a rewarding experience. :)

---

### Post by nisarmail@hotmail.com on 2008-10-14
Ok, thanks for the advice...
As Linux is so new, the simple things like running as root etc is new to me. I remember the days of DOS o/s and knowing all the dos commands and not wanting to move over to windows as i found dos much more stable.... lol... looks like its started again for me with linux.
I'll try your advice and see how it goes. I will post my results later on as i'm at work at the moment.
If only linux had simple installers like windows.... lol!!! 
On a side note, why is linux installations so much more complicated? I would think that a app or driver could be made to run off an installation in a similar way to how windows installs work. Sorry if its a stupid question but i really only know windows at the moment and i won't learn anything without asking.

Thanks :)

---

### Post by Kiefer Rodriguez on 2008-10-14
> **nisarmail@hotmail.com said:**
> Ok, thanks for the advice...
As Linux is so new, the simple things like running as root etc is new to me. I remember the days of DOS o/s and knowing all the dos commands and not wanting to move over to windows as i found dos much more stable.... lol... looks like its started again for me with linux.
I'll try your advice and see how it goes. I will post my results later on as i'm at work at the moment.
If only linux had simple installers like windows.... lol!!! 
On a side note, why is linux installations so much more complicated? I would think that a app or driver could be made to run off an installation in a similar way to how windows installs work. Sorry if its a stupid question but i really only know windows at the moment and i won't learn anything without asking.

Thanks :)

While it is hardly my place to explain, Linux doesnt have much of a graphical installer base (with the exception of programs like *aptitude* etc) due to its roots as a more complicated, command line based system - we are only now starting to see this influx of contributions involving graphical installers, or thats my two cents anyway. You'll soon see how terminal based commands (e.g. *apt-get*) are more convenient, and at times - easier. Just my two cents.
-Kiefer

---

### Post by moebb on 2008-10-19
hey..

it is good idea to make a prog for the problem with rt73 + ubuntu :-D

i have just a view questions :

whats up with the rt73 driver from this page? is it installable with you installer? could you add a function to install the rt2750 driver? 

do you know the program airdriver-ng?

h**p://homepages.tu-darmstadt.de/~p_larbig/wlan/



greetz & thx moebb

---

### Post by Kiefer Rodriguez on 2008-10-20
> **moebb said:**
> hey..

it is good idea to make a prog for the problem with rt73 + ubuntu :-D

i have just a view questions :

whats up with the rt73 driver from this page? is it installable with you installer? could you add a function to install the rt2750 driver? 

do you know the program airdriver-ng?

h**p://homepages.tu-darmstadt.de/~p_larbig/wlan/



greetz & thx moebb

moebb,
Thanks for your reply. I'll take a look in to extending the installer to cover other Ralink drivers, a working guide to installing the driver manually comes in handy - it means i can just grab all the commands and go from there (a command set). Yes I know of the entire aircrack-ng suite (as well as aircrack-ptw), why do you ask? (a possible option to patch the driver? :))

- Kiefer

---

### Post by weaver4 on 2008-11-17
Will this work on 8.10?  Or is it needed in version 8.10 at all?

---

### Post by Kiefer Rodriguez on 2008-11-19
The installer should have no problem on 8.10, but has not been officially tested.
Good luck, let me know how it works out :)

Kiefer

---

### Post by pdc124 on 2008-11-23
from my gentoo days I tend to put my own scripts in /usr/local/

when I do this with your installer it fails to  

os.system("sudo cp "+self.entry_tbpath.get_text()+" /usr/src")
                ^^^^^^
needs a space in it  for it to find the path correctly.
I think it also fails to find the downloaded  tarball becaseu it then asked me to put a CD in 

ive got this though 

paul@paul-desktop:~$ ls -la /usr/src/
total 324
drwxrwsr-x  4 root src    4096 2008-11-23 17:39 .
drwxr-xr-x 11 root root   4096 2008-07-01 21:51 ..
drwxr-xr-x 20 root root   4096 2008-11-15 18:14 linux-headers-2.6.24-21
drwxr-xr-x  6 root root   4096 2008-11-15 18:14 linux-headers-2.6.24-21-generic
-rw-r--r--  1 root src  309535 2008-11-23 17:39 rt73-cvs-daily.tar.gz
paul@paul-desktop:~$

and its unzipped stuff into 

paul@paul-desktop:/usr/src$ ls  -la /usr/local/ | grep rt
drwxr-xr-x  4 32042 32043   4096 2008-09-18 15:35 rt73-cvs-2008091809
-rw-r--r--  1 paul  paul  309535 2008-11-23 17:21 rt73-cvs-daily.tar.gz
-rw-r--r--  1 root  root   18441 2008-11-23 17:39 rt73install.py
paul@paul-desktop:/usr/src$          

sorry not a python programmer ( perl and java ;-) 
so cant really help further

---

### Post by wzwilliam on 2008-12-02
Hi there. When i try to install the application that's what i got:

```
Traceback (most recent call last):
  File "rt73install.py", line 13, in <module>
    import pygtk
ImportError: No module named pygtk

```

any ideas?

---

### Post by blueshead on 2008-12-02
I;m a n00b to Ubuntu.. Just installed 8.10 on a Dell XPS M1210.. My intel antenna worked out of the box with Network Manager but my Ralink RT73 Quicky Jr.USB would not show. I installed Rutilt Wlan Manager. And the Ralink showed and is working . Very well I might add. So were the drivers in 8.10? And before I tried Rutilt.. I did find and d/l the drivers.. but could not install.. I'm terminal challenged.. But it seems up and running now...

---

### Post by educarrega on 2008-12-13
In Ubuntu 8.10, not complete the install, see the errors:

cd: 1: can't cd to /usr/src/rt73-*/Module
strip: 'rt73.ko': No such file
make: *** No rules to proccess the target `install'.  Stop.
sudo: ifconfigwlan0: command not found
FATAL: Module rt2570 not found.
FATAL: Module rt73 not found.
sudo: ifconfigwlan0: command not found
sudo: iwconfigwlan0: command not found
sudo: iwconfigwlan0: command not found
sudo: iwconfigwlan0: command not found
sudo: dhclientwlan0: command not found

Why?

---

### Post by bfo on 2008-12-17
I made slight change in the code, so that ```

sudo: ifconfigwlan0: command not found
sudo: iwconfigwlan0: command not found
sudo: iwconfigwlan0: command not found
sudo: iwconfigwlan0: command not found
sudo: dhclientwlan0: command not found
```
lines don't appear any more. Improved archive attached.
Thanks Kiefer, good job!

---

### Post by cribology on 2008-12-31
Noob problems

I get the message
python: can't open file 'rt73_install.py' [Errno 2] No such file or directory

What am I not doing I read something about opening a command line and directing it to the folder with the rt73_install.py included but

1) How do I open a command line (is this the same as the terminal?

2) How do I direct it to the correct folder? (currently the folder is on my desktop)

I am using Linux Mint 6 installed on a USB drive.

---

### Post by tommasoa on 2009-03-06
I'm a newbie in linux and in ubuntu.
I installed Ubuntu 7.04 in my old iMac G3.
I ran the installer, but it stop at 65% and it tell me:

Commencing install..
*	Copying driver tarball to /usr/src..
*	Unpacking driver tarball contents to /usr/src..
*	Please confirm your distrobution's LiveCD is inserted
*	Gathering required header files from CD, this may take a while..
*	Added CD-Rom to sources list, now updating list..
*	Installing headers..
*	Compiling RT73 module..
*	Correcting file size issue..
*	Installing module..
*	Bringing down wireless device..
*	Removing obsolete RaLink modules..
*	Making a backup of /etc/modprobe.d/blacklist to your /home directory..
*	Opening /etc/modprobe.d/blacklist..


In Terminal, it tell me:

xassenn@ubuntu:~$ python rt73_install.py
sudo: cp/home/xassenn/rt73-cvs-daily.tar.gz: command not found
tar: /usr/src/*.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
sh: sudoapt-get: not found
cd: 1: can't cd to /usr/src/rt73-*/Module
strip: 'rt73.ko': No such file
make: *** No rule to make target `install'.  Stop.
sudo: ifconfigwlan2: command not found
Traceback (most recent call last):
  File "rt73_install.py", line 126, in start_install
    modprobe = file("rt73-blacklist.temp", 'a')
IOError: [Errno 13] Permission denied: 'rt73-blacklist.temp'



What can I do?
Sorry for my bad english, I'm from Italy.
Thanks
T.

---

### Post by ayyappa1 on 2009-04-06
Hi All,
Noob to ubuntu as well as linux. know the basics but no shortforms pls...

Please find the errors below. I still see a installation complete(100%) on the RT73 Driver install tool but when i open mozilla(google) no internet. Any help is greatly appreciated. Special thanks to kiefer and others involved in developing this tool. Appreciate your kindness in helping the noobs by preparing a tool. Hats off to you. Hurdles in using linux scare off the noobs like me but guys like you give us some good reasons to try linux. OS: Ubuntu 8.10

I have 2 NICs: and my ifconfig shows eth0, eth1 and lo

These are my values:
interface name: eth0
package manager: apt-get
essid: BELL123
WEP key: s:12345678901234567890123456
path: /home/sunny/downloads/rtinstall-0.5.2.tar.gz

#sudo python RT73_GUI_Installer_0.5.2

make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /usr/src/rt73-cvs-2008031322/Module/rtmp_init.o
/usr/src/rt73-cvs-2008031322/Module/rtmp_init.c: In function &#8216;KillThreads&#8217;:
/usr/src/rt73-cvs-2008031322/Module/rtmp_init.c:185: error: implicit declaration of function &#8216;kill_proc&#8217;
/usr/src/rt73-cvs-2008031322/Module/rtmp_init.c: In function &#8216;LoadFirmware&#8217;:
/usr/src/rt73-cvs-2008031322/Module/rtmp_init.c:1590: warning: assignment discards qualifiers from pointer target type
make[2]: *** [/usr/src/rt73-cvs-2008031322/Module/rtmp_init.o] Error 1
make[1]: *** [_module_/usr/src/rt73-cvs-2008031322/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
rt73.ko failed to build!
make: *** [module] Error 1
strip: 'rt73.ko': No such file
make: *** No rule to make target `install'.  Stop.
sudo: ifconfigeth0: command not found
FATAL: Module rt2570 not found.
FATAL: Module rt73 not found.
sudo: ifconfigeth0: command not found
sudo: iwconfigeth0: command not found
sudo: iwconfigeth0: command not found
sudo: iwconfigeth0: command not found
sudo: dhclienteth0: command not found


Issue resolved:

Solution:

Install WUSB54GC on Ubuntu 8.10 (Intrepid Ibex) for rt73 chipset

The WUSB54GC adapter can be connected to the system now.

Go to :
[http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=8&t=4926](http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=8&t=4926)


and click on rt73 to download rt73-cvs-daily.tar.gz

I downloaded this file on a windows machine and transferred the file to the linux machine with a pen drive /media/sunny

cd /usr/src
sudo cp /media/sunny/rt73-cvs-daily.tar.gz .
sudo gunzip rt73-cvs-daily.tar.gz
sudo tar - xvf rt73-cvs-daily.tar
cd rt73-cvs-2009040610/Module
sudo make
sudo make install
sudo ifconfig wlan0 down
sudo modprobe -r rt73usb
sudo modprobe -r rt2570
sudo modprobe -r rt2500usb
sudo modprobe -r rt2x00lib
gksu gedit /etc/modprobe.d/blacklist (if you are using Ubuntu)
kdesu kate /etc/modprobe.d/blacklist (if you are using Kubuntu)

Add the following lines to the text file:

# Blacklist rt73usb, as it is a non-functional beta module which conflicts with the working rt73 module.
blacklist rt73usb
# Blacklist rt2570, as it causes conflicts with rt73
blacklist rt2570
# Other modules that break rt73
blacklist rt2500usb
blacklist rt2x00lib

save and exit

sudo modprobe -v rt73

sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid YOUR_NETWORK_NAME_HERE
sudo iwconfig wlan0 key YOUR_WEP_KEY_HERE_OR_"off"_FOR_NO_KEY
sudo dhclient wlan0

sample for the above:

sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid BELL123
sudo iwconfig wlan0 key 12345678901234567890123456
sudo dhclient wlan0

(my network name is BELL123 and i use 104- / 128-bit WEP: 26 digit key(WEP key and Network key are the same)

Your internet should connect now. Make sure your mozilla browser is not set in offline mode: To bring it to online mode: start mozilla and click on file and uncheck work offline

To automate this process:

gksu gedit /etc/network/interfaces (if you are using Ubuntu)
kdesu kate /etc/network/interfaces (if you are using Kubuntu)

add the following lines: 

auto wlan0
iface wlan0 inet dhcp
pre-up ifconfig wlan0 up
pre-up iwconfig wlan0 essid YOUR_ESSID
pre-up iwconfig wlan0 key 12345678901234567890123456

save and exit

sample for the above:
pre-up iwconfig wlan0 essid BELL123
pre-up iwconfig wlan0 key WEP_KEY_OR_"OFF"_IF_YOU_HAVE_NONE

at the #prompt:
sudo aptitude purge network-manager

Reboot

and internet should automatically be up.

All credits to diepruis. I'm a noob and trying to help other noobs to setup WUSB54GC

Reference:
[http://ubuntuforums.org/showthread.php?t=400236&highlight=wusb54gc](http://ubuntuforums.org/showthread.php?t=400236&highlight=wusb54gc)

---

### Post by JacobK on 2009-04-21
```
jacob@jacob-laptop:~$ python Install_rt73_drivers.py
Ralink rt73: Driver Installer - by Kiefer Rodriguez.
Traceback (most recent call last):
  File "Install_rt73_drivers.py", line 19, in <module>
    log = file("rt73-logfile", 'w')
IOError: [Errno 13] Permission denied: 'rt73-logfile'

```

Thats what I get, it won't work here. I already tried it once, but it wasn't working. When i'm near to the router i've got a slow connection, but when I'm somewhere else in house I haven't got any connection. So I wanted to try this, to see if I can get a better connection.

But the first time I tried it I used it in the terminal, but how can I use the GUI?

---

### Post by arce on 2009-05-03
Will this work for Ubuntu 9.04?

Also whats different from yours and this one

[http://ubuntuforums.org/showthread.php?t=848445&highlight=diepruis](http://ubuntuforums.org/showthread.php?t=848445&highlight=diepruis)

I am very new to Ubuntu sorry for the questions.

---

### Post by colli012 on 2009-05-27
I tried the serialmonkey link and it no longer provides a file to download.  Many of the serialmonkey links provided in the forums no longer work.  I downloaded 9.04 and can not get my WUSB54GC to work or RT73 drivers to load.  If the link below had worked, would this have worked for 9.04?  Thanks


Install WUSB54GC on Ubuntu 8.10 (Intrepid Ibex) for rt73 chipset
The WUSB54GC adapter can be connected to the system now.
Go to :
[http://rt2x00.serialmonkey.com/phpBB...php?f=8&t=4926]("http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=8&t=4926")
and click on rt73 to download rt73-cvs-daily.tar.gz

8/2/09 - I finally gave up on using wireless with Ubuntu 9.04

---

### Post by Manksman on 2009-07-06
I have the same problem, the folk at serialmonkey seem to imply that the "legacy" files are no longer needed because it will work plug and play, but it has utterly defeated me.

---

### Post by cariboo on 2009-07-06
I'm not on the computer I have a WUA-1340 connected to, but the device is detected and the module is loaded on boot. I would check to see if the driver is loaded:

```
lsmod | grep rt73
```

It should be loaded. I found a problem getting to work properly as network manager said it was unmanaged. To repair that problem rmeove network-manager-gnome and install gnome-network-admin. Once it is installed, go to Syatem-->Administration-->Network, click the unlock button, enter your password and select your device. Fill in the info as needed, and click the close button. Your networking will restart and you should be able to connect.

Gnome-network-admin will only show a small bar graph in the notification area with no other indicaors. I use wifi-radar to see what ap are availabe.

Gnome-network-admin and wifi-radar are in the repositories.

---

### Post by JMTHHH on 2009-09-14
What does it mean when it says make sure your Live CD is in and spinning.  What is a Live CD.  I'm new to this so sorry if its something really obvious.

---

### Post by handrew on 2009-09-14
(I don't know if this thread is still valid or active anymore, nevertheless I'll chance it and post my problem here.



HELP needed with RT73(RT2571W) Wireless Lan Linux Driver

Hi,

I've just bought a USB wireless LAN adapter.(Zioncom WL0123)it uses the RT2571W driver by RALINK. I need to understand how to install the diver so that it can operate with my new computer. The CD that comes with the device has the Linux driver files BUT it is in a format which needs to be complied. I haven't got the skills (yet) to figure out how to render these files into a usable and installed driver. I have 9.04 ubuntu installed.

There are 2 directories, one called "WPA_Supplicant-0.5.8" the other called Module. Within each directory there is a 'read me' file. The following are the read-me file listed in their entirety. If someone would be kind enough to post a simple step by step of how to compile this I would be grateful. Surely there must be a .deb package out there for the RALINK RT73 USB wireless adapter???? THAT would be too easy, right 
Looking forward to your replies....

*****************************************************************

RT73 a/b/g STA driver interface with WPA Supplicant

Ralink Tech Corp.

*****************************************************************



Q0. Contents:

-----------------------

defconfig

driver.h

driver_ralink.c

driver_ralink.h

drivers.c

events.c

Makefile

wpa_supplicant.c

wpa_supplicant_i.h

README

wpa_supplicant_example.conf





Q1. How to compile

-----------------------

The driver interface was developed on wpa_supplicant v.0.5.8.

You can install the WPA Supplicant Free Edition development from website.



[http://hostap.epitest.fi/wpa_supplicant/](http://hostap.epitest.fi/wpa_supplicant/)



After download the package then go to wpa_supplicant directory

Follow the steps..



1.) Copy file "driver_ralink.c" and "driver_ralink.h" we provide to wpa_supplicant directory.

1.1.) Copy files driver.h, events.c, wpa_supplicant.c, wpa_supplicant_i.h we provide to wpa_supplicant directory.

2.) Set driver_ralink configuration as y in the "defconfig" or update to the "defconfig" we provide::



# Driver interface for Ralink rt73 driver

CONFIG_DRIVER_RALINK=y



3.) Add wpa_driver_ralink_ops() into wpa_supplicant_drivers() in file "drivers.c" 

or update to the file "drivers.c" we provide:: 



#ifdef CONFIG_DRIVER_RALINK

extern struct wpa_driver_ops wpa_driver_ralink_ops; /* driver_ralink.c */

#endif /* CONFIG_DRIVER_RALINK */

:

:

struct wpa_driver_ops *wpa_supplicant_drivers[] =

{ 

#ifdef CONFIG_DRIVER_RALINK

&wpa_driver_ralink_ops,

#endif /* CONFIG_DRIVER_RALINK */ 

}



4.) Edit the "Makefile" or update to the "Makefile" we provide::



ifdef CONFIG_DRIVER_RALINK

CFLAGS += -DCONFIG_DRIVER_RALINK

OBJS_d += driver_ralink.o

endif



5.) type $cp defconfig .config

6.) Compile the source code using 'make' command.





Q2. How to start wpa_supplicant

--------------------------------

1.) First start rt73 driver.



2.) Edit/Create a configuration file of wpa_supplicant.

-a) Set your work directory of wpa_supplicant for sockets

ctrl_interface = YOUR_WORK_PATH



-b) Set YOUR_OPENSC_PATH if need be. (e.g. generate certificates)

opensc_engine_path =/YOUR_OPENSC_PATH/engine_opensc.so

pkcs11_engine_path =/YOUR_OPENSC_PATH/engine_pkcs11.so

pkcs11_module_path =/YOUR_OPENSC_PATH/opensc-pkcs11.so



-c) Set network configuration. (e.g. WPA/EAP-TTLS)



*** refer to wpa_supplicant.conf in details or related documents ***



3.) Manually start wpa_supplicant, 

type $./wpa_supplicant -c your_config_file -i rausb0 -D ralink



turn on debug mode,

type $./wpa_supplicant -c your_config_file -i rausb0 -D ralink -d



Notes:

1.) wpa_supplicant 0.5.8 can not compiler with Redhat Enterprise Linux 5 

kernel 2.6.18-8.el5xen. Update Redhat Enterprise Linux 5 kernel to

current version (kernel-xen-2.6.18-8.1.15.el5xen) can solve it.
_______________________________________________________________________________

* README

*

* Ralink Tech Inc.

* 

* [http://www.ralinktech.com](http://www.ralinktech.com)

*



=======================================================================

ModelName:

===========

RT73(RT2571W) Wireless Lan Linux Driver





=======================================================================

Driver lName:

===========

rt73





=======================================================================

Supporting Kernel:

===================

linux kernel 2.4 and 2.6 series. 

Tested in Redhat 7.3 or later.





=======================================================================

Description:

=============

This is a linux device driver for Ralink RT73 a/b/g WLAN Card.





=======================================================================

Contents:

=============

Makefile.4 : Makefile for kernel 2.4 series

Makefile.6 : Makefile for kernel 2.6 series

*.c : c files

*.h : header files





=======================================================================

Features:

==========

This driver implements basic IEEE802.11. Infrastructure and adhoc mode 

with open or shared or WPA-PSK or WPA2-PSK authentication method. 

NONE, WEP, TKIP and AES encryption. 





=======================================================================

Build Instructions: 

====================

1> $tar -xvzf RT73_Linux_STA_Drv_x.x.x.x.tar.gz

go to "./RT73_Linux_STA_Drv_x.x.x.x/Module" directory.



2> $cp Makefile.4 ./Makefile # [kernel 2.4]

or

$cp Makefile.6 ./Makefile # [kernel 2.6]



3> [kernel 2.4]

$chmod 755 Configure

$make config # config build linux os version



4> $make all # compile driver source code

4.1> $make install



5> $cp rt73.bin /etc/Wireless/RT73STA/ # copy firmware



6> $dos2unix rt73sta.dat

$cp rt73sta.dat /etc/Wireless/RT73STA/rt73sta.dat 

# !!!check if it is a binary file before loading !!! 



7> $load 

#[kernel 2.4]

# $/sbin/insmod rt73.o

# $/sbin/ifconfig rausb0 inet YOUR_IP up



#[kernel 2.6]

# $/sbin/insmod rt73.ko

# $/sbin/ifconfig rausb0 inet YOUR_IP up





=======================================================================

CONFIGURATION: 

====================

RT73 driver can be configured via following interfaces, 

i.e. (i)"iwconfig" command, (ii)"iwpriv" command, (iii) configuration file

(iv)RaConfig



i) iwconfig comes with kernel. 

ii) iwpriv usage, please refer to file "iwpriv_usage.txt" for details.

iii)copy configuration file "rt73sta.dat" to /etc/Wireless/RT73STA/rt73sta.dat.

iv) RaConfig is utility for rt73.



Note: 



Configuration File : rt73sta.dat

---------------------------------------

# Copy this file to /etc/Wireless/RT73STA/rt73sta.dat

# This file is a binary file and will be read on loading rt.o module.

#

# Use "vi -b rt73sta.dat" to modify settings according to your need.

# 

# 1.) set NetworkType to "Adhoc" for using Adhoc-mode, otherwise using Infrastructure

# 2.) set Channel to "0" for auto-select on Infrastructure mode

# 3.) set SSID for connecting to your Accss-point.

# 4.) AuthMode can be "WEPAUTO", "OPEN", "SHARED", "WPAPSK", "WPA2PSK", "WPANONE"

# 5.) EncrypType can be "NONE", "WEP", "TKIP", "AES"

# for more information refer to the Readme file.

# 

# The word of "[Default]" must not be removed

[Default]

CountryRegion=0

CountryRegionABand=7

WirelessMode=0

SSID=AP350

NetworkType=Infra

Channel=0

AuthMode=OPEN

EncrypType=NONE

DefaultKeyID=1

Key1Type=0

Key1Str=0123456789

Key2Type=0

Key2Str=

Key3Type=0

Key3Str=

Key4Type=0

Key4Str=

WPAPSK=abcdefghijklmnopqrstuvwxyz

TxBurst=0

PktAggregate=0

TurboRate=0

WmmCapable=0

AckPolicy=0;0;0;0

BGProtection=0

IEEE80211H=0

TxRate=0

RTSThreshold=2347

FragThreshold=2346

PSMode=CAM

TxPreamble=0

AdhocOfdm=0

FastRoaming=0

RoamThreshold=70



-----------------------------------------------

syntax is 'Param'='Value' and describes below. 



1. CountryRegion=value 

value

0: use 1 ~ 11 Channel

1: use 1 ~ 13 Channel

2: use 10, 11 Channel

3: use 10 ~ 13 Channel

4: use 14 Channel

5: use 1 ~ 14 Channel

6: use 3 ~ 9 Channel

7: use 5 ~ 13 Channel



2. CountryRegionABand=value 

value 

0: use 36, 40, 44, 48, 52, 56, 60, 64, 149, 153, 157, 161, 165 Channel

1: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 124, 128, 132, 136, 140 Channel

2: use 36, 40, 44, 48, 52, 56, 60, 64 Channel

3: use 52, 56, 60, 64, 149, 153, 157, 161 Channel

4: use 149, 153, 157, 161, 165 Channel

5: use 149, 153, 157, 161 Channel

6: use 36, 40, 44, 48 Channel

7: use 36, 40, 44, 48, 52, 56, 60, 64, 100, 104, 108, 112, 116, 120, 124, 128, 132, 136, 140, 149, 153, 157, 161, 165 Channel

8: use 52, 56, 60, 64 Channel

9: use 34, 38, 42, 46 Channel

10: use 34, 36, 38, 40, 42, 44, 46, 48, 52, 56, 60, 64 Channel



3. SSID=value 

value

0~z, 1~32 ascii characters.



4. WirelessMode=value

value 

0: 11b/g mixed, 

1: 11b only, 

2: 11a only, //Support in RfIcType=1(id=RFIC_5226) or RfIcType=3(id=RFIC_5225) 

3: 11a/b/g mixed, //Support in RfIcType=1(id=RFIC_5226) or RfIcType=3(id=RFIC_5225)

4: 11g only 



5. TxRate=value

value

0: Auto //WirelessMode=0~4 

1: 1 Mbps //WirelessMode=0 or 1 or 3

2: 2 Mbps //WirelessMode=0 or 1 or 3

3: 5.5 Mbps //WirelessMode=0 or 1 or 3

4: 11 Mbps //WirelessMode=0 or 1 or 3

5: 6 Mbps //WirelessMode=0 or 2 or 3 or 4

6: 9 Mbps //WirelessMode=0 or 2 or 3 or 4

7: 12 Mbps //WirelessMode=0 or 2 or 3 or 4

8: 18 Mbps //WirelessMode=0 or 2 or 3 or 4

9: 24 Mbps //WirelessMode=0 or 2 or 3 or 4

10: 36 Mbps //WirelessMode=0 or 2 or 3 or 4

11: 48 Mbps //WirelessMode=0 or 2 or 3 or 4

12: 54 Mbps //WirelessMode=0 or 2 or 3 or 4



6. Channel=value

value

depends on CountryRegion or CountryRegionABand



7. BGProtection=value

value

0: Auto 

1: Always on 

2: Always off



8. TxPreamble=value

value

0: Preamble Long

1: Preamble Short 

2: Auto



9. RTSThreshold=value

value

1~2347 



10. FragThreshold=value

value 

256~2346



11. TxBurst=value

value

0: Disable

1: Enable



12. NetworkType=value 

value 

Infra: infrastructure mode

Adhoc: adhoc mode



13. AdhocOfdm=value

value

0: WIFI mode (1,2,5.5,11 mbps rates) 

1: b/g mixed, (1,2,5.5,11,6,9,12,18,24,36,48,54 mbps rates)

2: 11g only, (6,9,12,18,24,36,48,54 mbps rates) 

3: 11a only, (6,9,12,18,24,36,48,54 mbps rates)



14. AuthMode=value

value

OPEN For open system 

SHARED For shared key system 

WEPAUTO Auto switch between OPEN and SHARED

WPAPSK For WPA pre-shared key (Infra)

WPA2PSK For WPA2 pre-shared key (Infra)

WPANONE For WPA pre-shared key (Adhoc)

WPA Use WPA-Supplicant

WPA2 Use WPA-Supplicant



15. EncrypType=value

value

NONE For AuthMode=OPEN 

WEP For AuthMode=OPEN or SHARED 

TKIP For AuthMode=WPAPSK or WPA2PSK or WPANONE 

AES For AuthMode=WPAPSK or WPA2PSK or WPANONE 



16. DefaultKeyID=value

value

1~4



17. Key1=value

Key2=value

Key3=value

Key4=value

value

10 or 26 hexadecimal characters eg: 012345678

5 or 13 ascii characters eg: passd

(usage : "iwpriv" only)



18. Key1Type=vaule

Key2Type=value

Key3Type=vaule

Key4Type=vaule

value

0 hexadecimal type

1 assic type

(usage : reading profile only)



19. Key1Str=value

Key2Str=value

Key3Str=vaule

Key4Str=vaule

value

10 or 26 characters (key type=0)

5 or 13 characters (key type=1)

(usage : reading profile only) 



20. WPAPSK=value 

value

8~63 ASCII or 

64 HEX characters



21. PSMode=value

value

0: CAM Constantly Awake Mode

1: Max_PSP Max Power Savings

2: Fast_PSP Power Save Mode



22. IEEE80211H=value

value

0: Disable

1: Enable Spectrum management

(This field can be enable only in A band)



23. FastRoaming=value

value

0: Disable

1: Enable Fast Roaming



24. RoamThreshold=value

vale

61 ~ 89



This value is a absolute threshold in dBm.

The condition to roam when receiving Rssi less than (-1*value).



// ////////////////////// 

// No Support !!!

// /////////////////////

// PktAggregate, 

// TurboRate, 

// WmmCapable, 

// AckPolicy

// /////////////////////



MORE INFORMATION

=================================================================================

If you want for rt73 driver to auto-load at boot time:

A) choose rausb0 for first RT73 WLAN card, rausb1 for second RT73 WLAN card, etc.



B) go to "./RT73_Linux_STA_Drv_x.x.x.x/Module" directory.

$make install



NOTE:

if you use dhcp, 

add this line

BOOTPROTO='dhcp'

in the file ifcfg-rausb0 .





*C) To ease the Default Gateway setting, 

add the line

GATEWAY=x.x.x.x 

in /etc/sysconfig/network



D) When build for SUSE, please unmark the part for SUSE in Makefile.



E) When build for Mandriva 2007.1, please unmark the part for Mandriva in Makefile.

You have to remove the module pre-loaded by Mandriva 2007.1 before

you can load our rt73sta module.

Edit this file /lib/modules/`uname -r`/build/.kernelrelease before "4> make all"

Change it to 2.6.17-13mdv (should be the same as "uname -r" value)

Follow "Build Instructions: 4> and 4.1>" then the driver should be loaded correctly on boot up.

---

### Post by Sezmeralda on 2009-11-17
> **educarrega said:**
> In Ubuntu 8.10, not complete the install, see the errors:
 
cd: 1: can't cd to /usr/src/rt73-*/Module
strip: 'rt73.ko': No such file
make: *** No rules to proccess the target `install'. Stop.
sudo: ifconfigwlan0: command not found
FATAL: Module rt2570 not found.
FATAL: Module rt73 not found.
sudo: ifconfigwlan0: command not found
sudo: iwconfigwlan0: command not found
sudo: iwconfigwlan0: command not found
sudo: iwconfigwlan0: command not found
sudo: dhclientwlan0: command not found
 
Why?
 
 
I have almost exactly the same, but with extra lines as below:
 
> 
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
rt73.ko failed to build!
make: *** [module] Error 1
strip: 'rt73.ko': No such file
make: *** No rule to make target `install'.  Stop.
sudo: ifconfigwlan0: command not found
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Module rt2570 not found.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Module rt2x00lib is in use.
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
FATAL: Module rt73 not found.
sudo: ifconfigwlan0: command not found
sudo: iwconfigwlan0: command not found
sudo: iwconfigwlan0: command not found
sudo: iwconfigwlan0: command not found
sudo: dhclientwlan0: command not found

 
After the above has appeared in the terminal the computer I have no options to search for wireless networks,  and no wireless signal strength is indicated.
 
I have a new install of 9.10 64-bit, and no other connection to the internet.  I am trying to install a WUSB54GC USB adaptor.  The router is an N-type router but there is a Vista laptop with G which connects no problems.

---

### Post by Sezmeralda on 2009-11-17
Cancel my last, the above problem has not stopped the computer from recognising the card, I just seem to have WPA/WEP issues.  Thanks for the installer, it's been an experience!

---

### Post by Love2MeetU on 2009-12-04
I don't really understand any of this stuff, just picking up things here and there. I tried to use the rt73 installer, but maybe I'm doing something wrong because there didn't seem to be a .sh file to find.

---

### Post by Topher_G on 2010-01-02
I am VERY new to Ubuntu but wanted to give it a try.

I actually spent some time putting UNR 9.10 on my Netbook and, after a while, through the help of the information contained in various forums and websites, I figured out how to make it work -so far so good,

Now, however, I just did a fresh install of 9.10 on my desktop and I am having trouble with the Linksys Compact Wireless G Network Adapter.

It would appear that the GUI Installer for RT73 should fix this, but I can't get it to run (no GUI) - At this time I don't have Internet on the desktop, just on the Netbook; so I downloaded files to flash drive and can't figure out how to make them work - any help getting this done would be much appreciated.

Thanks -

---

### Post by Topher_G on 2010-01-02
I am VERY new to Ubuntu but wanted to give it a try.

I actually spent some time putting UNR 9.10 on my Netbook and, after a while, through the help of the information contained in various forums and websites, I figured out how to make it work -so far so good,

Now, however, I just did a fresh install of 9.10 on my desktop and I am having trouble with the Linksys Compact Wireless G Network Adapter.

It would appear that the GUI Installer for RT73 should fix this, but I can't get it to run (no GUI) - At this time I don't have Internet on the desktop, just on the Netbook; so I downloaded files to flash drive and can't figure out how to make them work - any help getting this done would be much appreciated.

Thanks -

---

### Post by lescrooge on 2010-07-17
Would someone kindly explain to me how to obtain this ellusive installer.
TVM

---

### Post by FUJIM0 on 2010-09-19
Question from a new user, any known issues with the GUI Installer and Ubuntu 10.04.1 LTS (Lucid Lynx)? Just curious, I know almost nothing about linux but I'm trying to be a windows convert... :)
 
 
 
Fuji.....

---

### Post by widodox on 2011-12-15
Good Job... Tks very much..

---

