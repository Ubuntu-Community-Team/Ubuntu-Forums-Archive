---
title: "uninstall program in wine without the wine application uninstaller"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by nachos99 on 2009-03-02
im having trouble uninstalling a program in wine.  when i use the wine app uninstaller_uninstall_remove in the program setup, it just keeps reinstalling it.  

ive looked through past threads but it seems the answer for uninstalling a program in wine is run "$ wine uninstaller" in terminal and go through the wine app uninstaller.

is there a way to get rid of a program without going through the wine app uninstaller?

thank you.

---

### Post by Panzor on 2009-03-02
Yes, just delete the files made in the Program Files directory. I'm pretty sure that's the only place that an installer (usually) touches. Anything else it touches is probably minimal and not worth digging through.

To clarify, I'm talking about /home/user/.wine/drive_c/Program\ Files/

---

### Post by nachos99 on 2009-03-02
ive deleted the files in the .wine/drive_c/program files but the program still shows up under applications_wine_programs_...

when i run the wine app uninstaller again, the program is still there also.

---

### Post by nachos99 on 2009-03-02
ok.  deleting the files in ~/.config/menus/applications-merged for residual menu entries took care of the menu entry.

however, the program still shows up in the wine app uninstaller.

any advice on how to get it out of there?

thanks in advance.

---

### Post by nachos99 on 2009-03-02
problem solved.  thanks very much for your suggestions.  i put in all the terminal commands below and it seems to have cleared out everything.

i did...


5. Uninstalling applications

5.1. How do I uninstall Windows applications?

Wine has its own built-in uninstaller - the equivalent of Windows' "Add/Remove Programs" function for running standardized uninstallers. In recent versions, a shortcut has been added to Wine's menu, along with a shortcut to winecfg.

Note that Wine does not fully implement everything required to cleanly uninstall all applications. Some uninstallers might not function at all. To remove all programs installed under Wine, remove the ~/.wine directory:

rm -rf $HOME/.wine

Also the uninstaller does not remove menu and desktop entries. To remove all Wine-created menu entries run the following commands

rm -f $HOME/.config/menus/applications-merged/wine*
rm -rf $HOME/.local/share/applications/wine
rm -f $HOME/.local/share/desktop-directories/wine*
rm -f $HOME/.local/share/icons/????_*.xpm

---

