---
title: "openbox keyboard shortcuts dont work"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by mjheagle8 on 2009-06-23
i have defined some keyboard shortcuts in openbox (alone) in my rc.xml.  my defined shortcuts are not working, but the other keyboard shortcuts, the defaults (such as show desktop, close window, etc.) are working.  why is this happening? how do i fix it?  
thanks in advance for any and all help or advice.

edit: here is the section that i added that's not working.
```

    <!--My custom keybindings-->
    <keybind key="W-t">
      <action name="Terminal">
        <command>/usr/bin/xfce4-terminal</command>
      </action>
    </keybind>
    <keybind key="C-A-r">
      <action name="Run">
        <command>/usr/bin/xfrun4</command>
      </action>
    </keybind>
    <!--Music Control-->
    <keybind key="C-A-p">
      <action name="Play/Pause">
        <command>/usr/bin/mpc toggle</command>
      </action>
    </keybind>
    <!--END My custom keybindings-->

```

---

### Post by zerothink on 2011-06-17
try ```
openbox --reconfigure
``` as normal user. if shortcuts start to work, it is Ubuntu "stealing" your shortcuts.

---

