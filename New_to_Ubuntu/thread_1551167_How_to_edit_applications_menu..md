---
title: "How to edit applications menu."
date: 2010-08-11
forum: New to Ubuntu
---

### Post by InfernalAngel on 2010-08-11
uhm 
I did install netbeans 6.9 and now uninstall it for netbeans 6.9.1 (er the update in 6.9 was broken hard since my connection was corrupt 2-3 times during updating process).
uhm somehow after the installation restart the computer(or just reloging) the shortcut in Applications->Programming show a black "?" icon which show the pointer to 6.9 and the shortcut on netbeans 6.9.1 disappear. And I could not delete the item netbeans-6.9 with right click on** applications ->edit menus  **
I did come to the folder /usr/share/applications/ and there is just netbeans-6.9.1.desktop

-rwxr-xr-x 1 root root   271 2010-08-12 08:16 netbeans-6.9.1.desktop.

I did **sudo alacarte **and there was black "?" icon when I click on that icon to do delete then I've got sth like this
> 
Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/Alacarte/MainWindow.py", line 434, in on_item_tree_show_toggled
    self.editor.setVisible(item, False)
  File "/usr/lib/pymodules/python2.6/Alacarte/MenuEditor.py", line 200, in setVisible
    self.__addUndo([self.__getMenu(item), item])
  File "/usr/lib/pymodules/python2.6/Alacarte/MenuEditor.py", line 427, in __addUndo
    data = open(file_path).read()
IOError: [Errno 2] No such file or directory: '/usr/share/applications/netbeans-6.9.desktop'

I did all other things such as reinstall/uninstall thoese netbeans packets but nothing was changed.
I even did remove the /home/username/.local/share/applications folder and relogin be the issue still there ...

is there any solution for this ?

---

### Post by Ozymandias_117 on 2010-08-12
> **InfernalAngel said:**
> uhm 
I did install netbeans 6.9 and now uninstall it for netbeans 6.9.1 (er the update in 6.9 was broken hard since my connection was corrupt 2-3 times during updating process).
uhm somehow after the installation restart the computer(or just reloging) the shortcut in Applications->Programming show a black "?" icon which show the pointer to 6.9 and the shortcut on netbeans 6.9.1 disappear. And I could not delete the item netbeans-6.9 with right click on** applications ->edit menus  **
I did come to the folder /usr/share/applications/ and there is just netbeans-6.9.1.desktop

-rwxr-xr-x 1 root root   271 2010-08-12 08:16 netbeans-6.9.1.desktop.

I did **sudo alacarte **and there was black "?" icon when I click on that icon to do delete then I've got sth like this


I did all other things such as reinstall/uninstall thoese netbeans packets but nothing was changed.
I even did remove the /home/username/.local/share/applications folder and relogin be the issue still there ...

is there any solution for this ?

What do you get with ```
sudo updatedb && locate netbeans | grep desktop
```

---

### Post by InfernalAngel on 2010-08-12
> /usr/local/netbeans-6.9.1/java/config/Modules/org-jdesktop-beansbinding.xml
/usr/local/netbeans-6.9.1/java/modules/org-jdesktop-beansbinding.jar
/usr/local/netbeans-6.9.1/java/modules/locale/org-jdesktop-beansbinding_ja.jar
/usr/local/netbeans-6.9.1/java/modules/locale/org-jdesktop-beansbinding_pt_BR.jar
/usr/local/netbeans-6.9.1/java/modules/locale/org-jdesktop-beansbinding_zh_CN.jar
/usr/local/netbeans-6.9.1/java/update_tracking/org-jdesktop-beansbinding.xml
/usr/local/netbeans-6.9.1/javafx/javafx-sdk/lib/desktop
/usr/local/netbeans-6.9.1/javafx/javafx-sdk/lib/desktop/decora-j2d-rsl.jar
/usr/local/netbeans-6.9.1/javafx/javafx-sdk/lib/desktop/decora-j2d.jar
/usr/local/netbeans-6.9.1/javafx/javafx-sdk/lib/desktop/decora-jsw.jar
/usr/local/netbeans-6.9.1/javafx/javafx-sdk/lib/desktop/decora-ogl.jar
/usr/local/netbeans-6.9.1/javafx/javafx-sdk/lib/desktop/decora-runtime.jar
/usr/local/netbeans-6.9.1/javafx/javafx-sdk/lib/desktop/eula.jar
/usr/local/netbeans-6.9.1/javafx/javafx-sdk/lib/desktop/fxdloader.jar
/usr/local/netbeans-6.9.1/javafx/javafx-sdk/lib/desktop/javafx-anim.jar
/usr/local/netbeans-6.9.1/javafx/javafx-sdk/lib/desktop/javafx-common.jar
/usr/local/netbeans-6.9.1/javafx/javafx-sdk/lib/desktop/javafx-ext-swing.jar
/usr/local/netbeans-6.9.1/javafx/javafx-sdk/lib/desktop/javafx-geom.jar
/usr/local/netbeans-6.9.1/javafx/javafx-sdk/lib/desktop/javafx-io.jar
/usr/local/netbeans-6.9.1/javafx/javafx-sdk/lib/desktop/javafx-sg-common.jar
/usr/local/netbeans-6.9.1/javafx/javafx-sdk/lib/desktop/javafx-sg-swing.jar
/usr/local/netbeans-6.9.1/javafx/javafx-sdk/lib/desktop/javafx-ui-charts.jar
/usr/local/netbeans-6.9.1/javafx/javafx-sdk/lib/desktop/javafx-ui-common.jar
/usr/local/netbeans-6.9.1/javafx/javafx-sdk/lib/desktop/javafx-ui-controls.jar
/usr/local/netbeans-6.9.1/javafx/javafx-sdk/lib/desktop/javafx-ui-desktop.jar
/usr/local/netbeans-6.9.1/javafx/javafx-sdk/lib/desktop/javafx-ui-swing.jar
/usr/local/netbeans-6.9.1/javafx/javafx-sdk/lib/desktop/javafxrt-main.jar
/usr/local/netbeans-6.9.1/javafx/javafx-sdk/lib/desktop/jmc.jar
/usr/local/netbeans-6.9.1/javafx/javafx-sdk/lib/desktop/jogl-awt.jar
/usr/local/netbeans-6.9.1/javafx/javafx-sdk/lib/desktop/jogl-common.jar
/usr/local/netbeans-6.9.1/javafx/javafx-sdk/lib/desktop/libGStreamer.so
/usr/local/netbeans-6.9.1/javafx/javafx-sdk/lib/desktop/libgluegen-rt.so
/usr/local/netbeans-6.9.1/javafx/javafx-sdk/lib/desktop/libjogl_gl2.so
/usr/local/netbeans-6.9.1/javafx/javafx-sdk/lib/desktop/libnativewindow_awt.so
/usr/local/netbeans-6.9.1/javafx/javafx-sdk/lib/desktop/libnativewindow_jvm.so
/usr/local/netbeans-6.9.1/javafx/javafx-sdk/lib/desktop/rt15.jar
/usr/local/netbeans-6.9.1/javafx/javafx-sdk/lib/desktop/script-api.jar
/usr/local/netbeans-6.9.1/javafx/javafx-sdk/lib/desktop/websvc.jar
/usr/local/netbeans-6.9.1/javafx/javafx-sdk/profiles/desktop.properties
/usr/local/netbeans-6.9.1/javafx/javafx-sdk/samples/shared/new_style/images/ico_desktop.gif
/usr/local/netbeans-6.9.1/javafx/javafx-sdk/samples/shared/new_style/images/ico_mobile-desktop.gif
/usr/local/netbeans-6.9.1/platform/config/Modules/org-jdesktop-layout.xml
/usr/local/netbeans-6.9.1/platform/modules/org-jdesktop-layout.jar
/usr/local/netbeans-6.9.1/platform/modules/locale/org-jdesktop-layout_ja.jar
/usr/local/netbeans-6.9.1/platform/modules/locale/org-jdesktop-layout_pt_BR.jar
/usr/local/netbeans-6.9.1/platform/modules/locale/org-jdesktop-layout_zh_CN.jar
/usr/local/netbeans-6.9.1/platform/update_tracking/org-jdesktop-layout.xml
/usr/share/app-install/desktop/netbeans.desktop
/usr/share/applications/netbeans-6.9.1.desktop

uhm sry for this long stuff ... I didn't find the hidden the post function ... so you should read it in full then :)

---

### Post by Ozymandias_117 on 2010-08-12
> **InfernalAngel said:**
> uhm sry for this long stuff ... I didn't find the hidden the post function ... so you should read it in full then :)
See what happens when you try this... ```
sudo touch /usr/share/applications/netbeans-6.9.desktop
``` Then go back to the edit menu and attempt to delete it.

---

### Post by InfernalAngel on 2010-08-12
nothing happen and things till the same...

[http://yfrog.com/nbmenusfixp](http://yfrog.com/nbmenusfixp)

uhm ... it seem like the netbeans-6.9.desktop was not there but somehow the menus application still can list them ... is there by any chances that still cache file, xml, or config file that still remember that ? [IMG]http://img839.imageshack.us/img839/9016/menusfix[/IMG]

---

### Post by InfernalAngel on 2010-08-12
pardon for the ignorance of mine but I don''t know any other ways to pump my thread so :popcorn:

---

### Post by InfernalAngel on 2010-08-12
another pump. I did my google around the net then most of them was point to what I was done already ... really there is no other ways to solved this ???
:) plz help me any guru ... thanks in advance

---

### Post by Stoned on 2010-08-29
Same problem here after removing netbeans 6.8 to install 6.9.1

---

