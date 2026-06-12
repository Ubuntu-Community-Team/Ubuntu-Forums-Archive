---
title: "NO address bar in Nautilus"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by kalimojo on 2011-06-10
i have NO address bar in Nautilus. Any ideas ?

---

### Post by kalimojo on 2011-06-10
**Configuration**

 Nautilus can be configured to display the location bar for only a specific window, or for all windows. 
 
**Session Configuration**

 To display the location bar for only the current session, simply push Ctrl+L.  Other open windows will not be affected, and newly opened windows will continue to use the pathbar. You can switch back to the pathbar by pressing ESC while the cursor is on the location bar. 
 
**Permanent Configuration**

 To always display the location bar, a setting must be changed in GConf.  Get to a [command-line]("https://help.ubuntu.com/community/UsingTheTerminal#Starting%20a%20Terminal") and enter  
gconf-editorAlternatively, the gconf-editor may be available in your menu through  

[LIST]
[*]Applications -> System Tools -> Configuration Editor 
[/LIST]
Once GConf Editor is open, double-click the **apps** folder.  Scroll down and find the **nautilus** folder, double-click it, and then choose the **preferences** folder.  On the right side, check the box beside the **always_use_location_entry**  option.  This will immediately change all open Nautilus windows, as  well as any newly opened Nautilus windows, to always use the location  bar.  If you want to undo this change, simply un-check the box you  previously checked.

---

