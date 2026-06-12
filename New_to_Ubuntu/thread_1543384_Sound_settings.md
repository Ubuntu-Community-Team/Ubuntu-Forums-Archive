---
title: "Sound settings"
date: 2010-08-01
forum: New to Ubuntu
---

### Post by thejakeman on 2010-08-01
When I download a System Sound setup from gnome-look, the file contains a lot of sounds but the only thing I can set in the System>Preferences>Sound dialog box is the alert sound. Are there advanced sound managers available for download anywhere that would enable me to set individual sounds for every type of alert?

Thanks!

---

### Post by jtarin on 2010-08-01
Try doing these as root.
_Here's a possible if you want to try._
You can still change the system sound preferences, but not using a config editor, you will have to do it manually.

Open up a terminal and type:
sudo nautilus
Type in your password and hit enter. This will bring up root's file browser.

On the side, click on 'File System' then, usr > share > sounds > ubuntu > stereo.
These are the sounds the system uses for the login, question, error sounds etc.

Just simply replace the files with your own, making sure that they have the exact same name or else they won't work. They also have to be 'ogg'.
This program will convert the files to ogg for you:
sudo apt-get install soundconverter

If you find the sound you want to use, for this example, the login sound, copy it to your desktop, change the name to 'desktop-login', then, using the root's file browser, drag the file to the ubuntu sounds folder, replacing the original.

---

