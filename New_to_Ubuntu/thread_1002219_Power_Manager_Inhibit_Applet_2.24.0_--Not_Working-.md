---
title: "Power Manager Inhibit Applet 2.24.0 --Not Working--"
date: 2008-12-04
forum: New to Ubuntu
---

### Post by Valtiel on 2008-12-04
I recently added the "Power Manager Inhibit Applet 2.24.0" to in one of my user panel bars [taskbars] and last night I came to find out that the applet doesn't work.


As I understand, activating the Power Manager Inhibit Applet, will prevent the computer from activating the screen saver when in idle. Well last night as I was watching Fringe on Hulu, I came to find out that the applet doesn't seem to work at all.

Tonight I decided to do some research on the applet, since I think it is a great feature to have, and on the Help files I ran into the following:

[INDENT]Don't use this applet if you just use GNOME software, instead file a bug to make the application use the Inhibit() and UnInhibit() methods as this should 'just work'.[/INDENT]

**Can anybody tell me what that means?** I would really love for this applet to work.


Moreover, I visited the link on the "about" window and the applet I see on their webpage isn't the one I have.

Here is the link
[http://projects.gnome.org/gnome-power-manager/](http://projects.gnome.org/gnome-power-manager/)


EDIT: I have Ubuntu 8.10 with the latest updates.

---

### Post by Valtiel on 2008-12-05
**bump** Anybody cares to help or comment?


I have searched for the applet on google and I get nothing. All I find is variation of the applets name. Not even on the website listed on the apples "About" says anything about this applet.  

Any help, suggestion or recommendation to something similar to this applet or work around will be greatly appreciated.

---

### Post by mister_pink on 2008-12-05
> **Valtiel said:**
> I recently added the "Power Manager Inhibit Applet 2.24.0" to in one of my user panel bars [taskbars] and last night I can't to find out that the applet doesn't work.


As I understand, activating the Power Manager Inhibit Applet, will prevent the computer from activating the screen saver when in idle. Well last night as I was watching Fringe on Hulu, I came to find out that the applet doesn't seem to work at all.

Tonight I decided to do some research on the applet, since I think it is a great feature to have, and on the Help files I ran into the following:

[INDENT]Don't use this applet if you just use GNOME software, instead file a bug to make the application use the Inhibit() and UnInhibit() methods as this should 'just work'.[/INDENT]

**Can anybody tell me what that means?** I would really love for this applet to work.


I tried using this applet ages ago and also found it didn't work as expected. The stuff about "just gnome software" basically means that in an ideal world you shouldn't have to manually turn the screensaver off, as the programs should do it themselves.

Anyway, my solution to get around this was to write a script that toggles running "gnome-screensaver-command -i". 

You can download my script here: [http://www.srcf.ucam.org/~pjrh2/screeninhib](http://www.srcf.ucam.org/~pjrh2/screeninhib)

Save that somewhere then make it executable, then add a button to your panel that links to it. Works for me, but as ever YMMV.

---

### Post by Valtiel on 2008-12-05
> **mister_pink said:**
> I tried using this applet ages ago and also found it didn't work as expected. The stuff about "just gnome software" basically means that in an ideal world you shouldn't have to manually turn the screensaver off, as the programs should do it themselves.

Anyway, my solution to get around this was to write a script that toggles running "gnome-screensaver-command -i". 

You can download my script here: [http://www.srcf.ucam.org/~pjrh2/screeninhib](http://www.srcf.ucam.org/~pjrh2/screeninhib)

Save that somewhere then make it executable, then add a button to your panel that links to it. Works for me, but as ever YMMV.


Thanks for you help mister_pink, but how would I go about making this file executable?

- Can I save it as .text file or is there more to this part?

- What do I type in the terminal?
ex:

sudo ./The_Name_I_Give_The_File.bin  ????


Sorry, I still trying ot get the hang of this part of Linux

---

### Post by Valtiel on 2008-12-05
any help with this anybody?

---

### Post by mister_pink on 2008-12-06
Save it as is, wherever you like. To make it executable right click it and go to properties, permissions, and tick the box near the bottom. Now double clicking it should bring up a prompt asking if you want to run it - you do. This should now have your screen saver turned off. Run it again to turn it back on. 

To add it to your panel, right click the panel and go on add to panel, then custom app launcher. In the command box click browse and go find the file. You can put whatever you like in the ohter boxes.

Hope that helps.

---

