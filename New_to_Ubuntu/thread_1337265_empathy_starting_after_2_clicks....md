---
title: "empathy starting after 2 clicks..."
date: 2009-11-25
forum: New to Ubuntu
---

### Post by Findarato on 2009-11-25
Hello everyone,

I feel very stupid asking this question, but I haven't been able to find the answer anywhere on the net.

Since the upgrade to 9.10, I have been trying out empathy and am having one ****** problem :(  => I have it placed in my quickstart bar, but I have to click it twice for the program to open. On the first click, the program is running, but it's only on the second click that the "conctacts" window is opened. I am REALLY annoyed by this and can't seem to find a configuration for it anywhere, even though I am sure there must be somewhere.

Could you please help me by telling me how I can simply have the "contact" list opened by default when I start the program ?

Thank you very much and have a nice day,

Findarato

---

### Post by Findarato on 2009-11-26
no1 has the answer to this one ?

---

### Post by Findarato on 2009-11-27
wow, is this so complicated that no1 knows the answer ? :(

---

### Post by anders_c_ on 2009-11-27
having the same problem, if i shutdown the computer with the contact list open it will come up in one click next time i start it, its the same with rhythmbox when using tray-icon and "owns main window". Usually these things are configurable through gconf-editor but i havent looked around there yet.

---

### Post by drs305 on 2009-11-27
As anders_c said, with Empathy it appears to be a function of whether or not the contact list was open when Empathy closed the last time. If the window was closed on last shutdown, the first "start" begins the app, the second displays the Contact List. The app is running after the first click, and you can probably find the icon on your top panel.

The setting in gconf-editor is /apps/empathy/ui/main_window_hidden. You can set it to *true* and Empathy will open with the Contact List window displayed,

To enable the window, you can run:
```
gconftool-2 -t boolean -s /apps/empathy/ui/main_window_hidden false
```

The quirk is that if you close the Contact Window, it changes the gconf-setting and the *next* time Empathy starts it will again not display the Contact List until you open Empathy twice or click on the icon in the panel.

The **really simple** way is to drag an Empathy or Rhythmbox shortcut to the panel and just double-click it quickly. It should open up the Contact List for you.

The **truly one-click obsessive way** to get true "one-click" access *for Empathy* would be to make a script and put it on the panel so that gconf-editor sets the value to *true* and then opens the app:

my_empathy.sh
```

#!/bin/bash
gconftool-2 -t boolean -s /apps/empathy/ui/main_window_hidden false
empathy

```
Make it executable with:
```
chmod +x my_empathy.sh
```

The default icon is /usr/share/icons/hicolor/48x48/apps/empathy.png

Don't ask me to justify Empathy's behavior.  ;-)

---

### Post by Findarato on 2009-11-27
> **drs305 said:**
> As anders_c said, with Empathy it appears to be a function of whether or not the contact list was open when Empathy closed the last time. If the window was closed on last shutdown, the first "start" begins the app, the second displays the Contact List. The app is running after the first click, and you can probably find the icon on your top panel.

The setting in gconf-editor is /apps/empathy/ui/main_window_hidden. You can set it to *true* and Empathy will open with the Contact List window displayed,

To enable the window, you can run:
```
gconftool-2 -t boolean -s /apps/empathy/ui/main_window_hidden false
```

The quirk is that if you close the Contact Window, it changes the gconf-setting and the *next* time Empathy starts it will again not display the Contact List until you open Empathy twice or click on the icon in the panel.

The **really simple** way is to drag an Empathy or Rhythmbox shortcut to the panel and just double-click it quickly. It should open up the Contact List for you.

The **truly one-click obsessive way** to get true "one-click" access *for Empathy* would be to make a script and put it on the panel so that gconf-editor sets the value to *true* and then opens the app:

my_empathy.sh
```

#!/bin/bash
gconftool-2 -t boolean -s /apps/empathy/ui/main_window_hidden false
empathy

```
Make it executable with:
```
chmod +x my_empathy.sh
```

The default icon is /usr/share/icons/hicolor/48x48/apps/empathy.png

Don't ask me to justify Empathy's behavior.  ;-)

Wow... Thanks a lot for the pointers, at least I see where the problem is coming from. 

How can the ubuntu team have decided to replace pidgin when the very simple things as a one-click launcher aren't even functionnal yet ? :(. I must say i am having a very hard time understanding the logic of having to click twice :P

=> My solution for the moment : Stay with Pidgin :P

---

