---
title: "Docky = black part of screen"
date: 2010-11-02
forum: New to Ubuntu
---

### Post by XeonBloomfield on 2010-11-02
Welcome

How to "repair" Docky, when it does something like on the picture?
[[IMG]http://img9.imageshack.us/img9/6080/screenshot26t.th.png[/IMG]](http://img9.imageshack.us/img9/6080/screenshot26t.png)

Regards, XeonBloomfield.

---

### Post by fatality_uk on 2010-11-02
You need to enable 3D/Compiz / Visual  from System->Preferences->Appearence and then the Visual Effects tab.

---

### Post by Brandel Valico on 2010-11-02
Tip: If you have an ATI or an Intel card, you  should try without OpenGL first, because their drivers are not yet  perfect. 
You need to turn on compositing. For instance, you can run Compiz or  xcompmgr.  
If you're using XFCE or KDE, you can just enable compositing in the  window manager options. 
If you're using Gnome, you can enable it in Metacity in this way : 
 Open gconf-editor, edit the key  '/apps/metacity/general/compositing_manager' and set it to 'true'.

---

### Post by XeonBloomfield on 2010-11-02
@fatality_uk:
I enabled "Normal" Visual Effects in Apperance Menu.

After it, black space was smaller.

@Brandel Valico:
I set this key to true, restarted and now it`s under down Gnome Panel (of course I attach picture):
[[IMG]http://img198.imageshack.us/img198/8769/screenshot27j.th.png[/IMG]](http://img198.imageshack.us/img198/8769/screenshot27j.png)

---

### Post by fatality_uk on 2010-11-02
If you click on "Anchor" icon on Docky then select "Intellihide" from the dock configuration.

---

### Post by XeonBloomfield on 2010-11-02
@fatality_uk:
Great !
Thank you for your answers.

Problem solved.

---

### Post by fatality_uk on 2010-11-02
No problem. Please mark this thread as solved by using the **Thread Tools** menu.

---

### Post by XeonBloomfield on 2010-11-02
Ok, I marked it as SOLVED.

---

### Post by Brandel Valico on 2010-11-03
Glad to hear you got it working.

---

