---
title: "[SOLVED] shares-admin not working correctly"
date: 2008-06-11
forum: Networking &amp; Wireless
---

### Post by underdog512 on 2008-06-11
when I tried to pull up shares-admin everything is faded out. 

when I launch it from terminal.  i get the following output:

(shares-admin:6470): Gtk-WARNING **: Unknown property: GtkComboBox.items


** (shares-admin:6470): CRITICAL **: Unable to lookup session information for process '6470'


I have samba installed.

---

### Post by jetsam on 2008-06-11
I take it you're on Hardy.  

I get the same error messages you do when I launch shares-admin, but it comes up and is usable.  Strangely, the critical error goes away though if I don't launch as root.  

Not sure if it will work, but you could try to launch with just:
```
shares-admin
```
instead of with gksu or sudo.

**Added:**  also, you need to unlock it with the unlock button at the bottom, then your password.

---

### Post by molotov00 on 2008-06-11
Try:

gksu shares-admin

Edit: Looks as though the person above me JUST posted the exact opposite idea. Mine only works with gksu prepended. Otherwise it asks me to install NFS then quietly fails.

---

### Post by underdog512 on 2008-06-11
> **molotov00 said:**
> Try:

gksu shares-admin

Edit: Looks as though the person above me JUST posted the exact opposite idea. Mine only works with gksu prepended. Otherwise it asks me to install NFS then quietly fails.

nope, no joy

here is the output from that code:

(gksu:6543): Gtk-WARNING **: Theme file for default has no name


(gksu:6543): Gtk-WARNING **: Theme file for default has no directories


** (shares-admin:6544): CRITICAL **: Unable to lookup session information for process '6544'
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSS

Could this be related to this bug?
[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/33068](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/33068)

---

### Post by jetsam on 2008-06-11
> Could this be related to this bug?
[https://bugs.launchpad.net/ubuntu/+s...ols/+bug/33068](https://bugs.launchpad.net/ubuntu/+s...ols/+bug/33068)

That's a different issue, I think.  

**shares-admin** was pretty much pulled from Hardy because they re-did the Samba gui.  It's supposed to still be available from a terminal for backwards compatibility reasons, but it isn't working for you for some reason.  Just to add a new twist, it starts for me in Xubuntu Hardy but is pretty much non-functional.  Everything is gray and there's no way to unlock it, similar maybe to your problem.

Some people have been replacing it with system-config-samba, which has similar functionality (although it crashes for me if I look at the help menu).  You can install system-config-samba with **sudo apt-get install system-config-samba**, and run it from the menu **System-->Administration-->Samba**.

The other option is to configure it manually by editing the smb.conf.  If you're just trying to set your workgroup name, it's easy.  Open a terminal and do these commands:
Backup the smb.conf.
```
sudo cp /etc/samba/smb.conf /etc/samba/smb.conf.bak
```
Open the smb.conf in gedit with root permissions:
```
gksu gedit /etc/samba/smb.conf
```
Edit the file in gedit.  Find the line (line 27 in the default file) that says **workgroup = WORKGROUP** and change the WORKGROUP name on the right hand of the equals sign to your workgroup name.  Save the file, and quit gedit.  
Restart samba:
```
sudo /etc/init.d samba restart
```
That should do it.  You can share folders in Nautilus or on the desktop by right clicking on them and selecting "sharing options."

---

### Post by underdog512 on 2008-06-12
Some people have been replacing it with system-config-samba, which has similar functionality (although it crashes for me if I look at the help menu).  You can install system-config-samba with **sudo apt-get install system-config-samba**, and run it from the menu **System-->Administration-->Samba**.

thanks! that worked.

---

### Post by scharkalvin on 2008-12-07
Launching as non-root and then unlocking works for me (using Ubuntu 8.04) but I still get the GTK error messages.  In my case I wanted to use the program to set up NFS shares NOT SMB.  I know all it does it edit /etc/export though.  Is there a GUI tool to set up NFS from the Client side?

---

### Post by freakalad on 2009-07-14
I suspect this issue is unsolved & possibly a bug; detailed [here]("https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/192579/comments/5")

The shares-admin utility shares & changed correlate to settings in /etc/samba/smb.conf

In Nautilus though, when right-clicking on the directory/folder & create the share that way, it does not feature in the shares-admin or smb.conf file. Nor am I able to locate where that share data is stored, but the share is honored & viewable via nautilus network browser

---

### Post by mhmdahmd on 2011-07-03
for me a aways have this annoying message
"invoke-rc.d: unknown initscript, /etc/init.d/samba not foun"
 after running 
sudo system-config-samba
does any one have a solution for it,,
samba is really daunting
thanks very much

---

### Post by endotoxin on 2011-12-14
> **underdog512 said:**
> Some people have been replacing it with system-config-samba, which has similar functionality (although it crashes for me if I look at the help menu).  You can install system-config-samba with **sudo apt-get install system-config-samba**, and run it from the menu **System-->Administration-->Samba**.

thanks! that worked.

Lovely! THIS is the package I've been searching for, ever since I moved to Xubuntu.

---

