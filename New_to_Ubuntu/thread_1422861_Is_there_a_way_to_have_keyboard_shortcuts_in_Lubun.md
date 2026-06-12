---
title: "Is there a way to have keyboard shortcuts in Lubuntu"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by theweasel2345 on 2010-03-05
I just want to have Ctrl+T as my Terminal shortcut but I dont know how with the Lubuntu distro

---

### Post by patchwork on 2010-03-05
check out xbindkeys, I don't believe LXDE comes with a default shortcut option like Gnome.

---

### Post by curiousgeorgej on 2010-07-08
To see what keyboard shortcut bindings are currently set, and to add more without using xbindkeys, you can dig through the following file and edit it:

/home/<user>/.config/openbox/lxde-rc.xml

I imagine you can figure it out just fine, but for a quick start, at least on PC hardware,
A- means "Alt+" 
C- means "Ctrl+"
S- means "Shift+"
W- means the "Windows" key
so, for example, C-A-T is ctrl+alt+"t", which runs a terminal window.

I found the meat of this information (and a bit more) here, on the lxde forums: [http://forum.lxde.org/viewtopic.php?f=8&t=457](http://forum.lxde.org/viewtopic.php?f=8&t=457)

There might be even more on the openbox forums, but I'm happy with this solution.

Cheers,
~George J.

---

### Post by urukrama on 2010-07-09
As curiousgeorgej said, you don't need xbindkeys for this. Openbox itself can manage keybindings. You might find the official documentation useful as well: [http://openbox.org/wiki/Help:Bindings](http://openbox.org/wiki/Help:Bindings)

Please note that if you use LXDE, you will need to edit the lxde-rc.xml file, and not the rc.xml file that Openbox normally uses and that will be referred to in most documentation.

To launch a terminal with the keybindings Ctrl T, you would add the following to your (lxde-)rc.xml in the <keyboard> section:

```
<keybind key="C-t">
    <action name="execute">
        <command>urxvt</command>
      </action>
  </keybind>
```

Replace *urxvt* with whatever terminal you prefer to use.

You might also be interested in this post I wrote some time ago: [http://urukrama.wordpress.com/2008/07/22/my-openbox-keybindings/](http://urukrama.wordpress.com/2008/07/22/my-openbox-keybindings/)

---

### Post by nshram on 2010-08-20
Hello,

I have been using Lubuntu on a P3 700.
I need to remap some shortcuts.
But nothing works:

1. commented out the keybindings in /home/<user>/.config/openbox/lubuntu-rc.xml
2. renamed above file to lxde-rc.xml

what gives?

---

### Post by Gaygerbil on 2010-10-09
It seems to me the keyboard shortcut support for Lubuntu/LXDE is a joke. You can't use custom commands? And that's if I could get it to actually work, I haven't been able to get anything to work, i got the GUI to display but it doesn't change any of the keys.

Perhaps I need to log in and out but or restart but I'm just not gonna bother with it.

EDIT:

In Lubuntu 10.10 they seem to be working a lot better now, it was a lil try doing the config for the keys but it works now at least.

---

### Post by Culip on 2010-10-18
I modified "lubuntu-rc" instead of "lxde-rc" in the same directory, and it worked.

---

### Post by iluii on 2010-11-06
strange when I tried opensuse 11.3 lxde and modified "lxde-rc" it did nothing. In Lubuntu, however, only "lubuntu-rc" , mentioned by culip, was present and modifying it worked like a charm

thanks! keeping lubuntu since suse and the massive headaches it gave me were just not for me!

---

### Post by hoover67 on 2010-11-16
you may have to run 

openbox --reconfigure

to have openbox reload the configuration file after you've made changes to it. 

HTH,

Uwe

---

### Post by domu on 2011-01-25
Anyway, Lubuntu 10.10 is set up already with CTRL+ALT+T to open a terminal (mine was anyway...)

You can check the keyboard shortcuts already set up by looking at the output of:

grep -A 2 "<keybind" ~/.config/openbox/lubuntu-rc.xml

---

### Post by kakashi_12 on 2011-10-26
Why can't I edit the volume on mine.
 
<keybing key="XF86AudioRaise Volume">
<action name="Execute">
<command>amixer -q sset Master 3%-</command>
</action>
<keybind>
 
Which line do I edit? I tried editting the top line and that did not work.
I even ran the cmd openbox --reconfigure afterwards

---

### Post by taghawi on 2012-06-22
There is a nice graphical tool for it: obkey:
[https://code.google.com/p/obkey/](https://code.google.com/p/obkey/)

Installation:
1. Download the tar file:
[https://code.google.com/p/obkey/downloads/list](https://code.google.com/p/obkey/downloads/list)

2. unpack it

3. run it:
./obkey ./path_to_your/rc.xml file.


davoud

---

