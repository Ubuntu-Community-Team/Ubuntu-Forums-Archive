---
title: "Commands Help"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by CJWW1989 on 2009-09-18
Every time I try and add a launcher (say on a dock or my taskbar) I am always asked about a command, an executable file. I have no idea where there are. I simply looking to make a documents, terminal, system monitor, and swiftfox application shortcut. Drag and drop doesn't seem to work on Xubuntu either. Thanks.

---

### Post by anystupidname1 on 2009-09-18
Is "add this launcher to panel" not an option when you right click on menu items? It is in Ubuntu. If not, you can specify the command you want to run for example: "xfce4-terminal.wrapper" or "/usr/bin/xterm"
The full path is probably not even necessary... You can use top or htop to determine what the executable name is of what you are currently running. You can find a full path to something using "whereis", example: whereis xterm

Hope that helps...

---

### Post by apmcd47 on 2009-09-18
If you know what the program is chances are just the name will suffice, e.g. *thunar* for the XFCE File manager. If it doesn't, then open a terminal window and type:
```
type thunar
```(again I use thunar for the example). Then paste the result in the appropriate window (assuming it found the program).

You mention drag and drop does not work. Presumably you are trying to drag apps out of the main menu? Try looking in */usr/share/applications*. You will find *.desktop* files in there. Find the one you want to transfer to the launcher panel and look for the  *Exec=*line.

Andrew

---

### Post by CJWW1989 on 2009-09-18
Thanks guys but I actually solved it myself. If you open the file manager, under "Go" and "Find Location" (or press Ctrl+L) it will give you the file path and then you can just cd to that. Thanks again.

---

### Post by CJWW1989 on 2009-09-18
However, I can only add executable files. Any idea how I add a path, say like Documents or File System?

---

### Post by HereInOz on 2009-09-18
Right click on the desktop and select Create Launcher.  In the Create Launcher dialog box, select the type as Location, then in the Location box, type the location in the format of file:///home/username/subfolder  etc.

Don't forget the 3 forward slashes.

Then you can drag that launcher to the top panel.

---

