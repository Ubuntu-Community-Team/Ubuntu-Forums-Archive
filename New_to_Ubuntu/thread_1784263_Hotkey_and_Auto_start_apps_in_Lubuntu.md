---
title: "Hotkey and Auto start apps in Lubuntu"
date: 2011-06-16
forum: New to Ubuntu
---

### Post by eb3ha4el on 2011-06-16
I installed Lubuntu 11.04
and it seems that there is no pre-installed hotkey software nor auto start software in lubuntu by default. 

So I wonder either how I can configure these manually by myself, 
or what light-weighted software would do this.

Primary use for hotkey is volume control
(I'm using Netbook and I believe it does not have volume control key on keyboard by default)

Anyone please?
thanks

---

### Post by jtarin on 2011-06-16
See if[ this ]("http://locutusweb.asw15.org/index.php/topic,80.0.html")can get you "started" in the right direction.

---

### Post by eb3ha4el on 2011-06-16
> **jtarin said:**
> See if[ this ]("http://locutusweb.asw15.org/index.php/topic,80.0.html")can get you "started" in the right direction.



Thanks, that works perfectly.
What about Hotkey binding? 

I want to control volume through
my keyboard, not hovering my mouse over it and click to control..

---

### Post by jtarin on 2011-06-16
You can use[ Ubuntu Tweaks]("http://ubuntu-tweak.com/")
or
[This if it is still available in the repositories.]("http://www.ubuntugeek.com/keylaunch-a-utility-for-binding-commands-to-a-hot-key.html")

---

### Post by kerry_s on 2011-06-17
> What about Hotkey binding? 


[http://ubuntuforums.org/showthread.php?t=1422861](http://ubuntuforums.org/showthread.php?t=1422861)

---

### Post by eb3ha4el on 2011-06-17
Thank you very much you all..
I'm configuring hotkey manually, however, I cannot figure out
what command it is when I adjust volume..

Anyone know what command I should put in? (Volume up and Volume down)


Also, is it necessary to do following? (giving space)
```

<Keybind key="C-]">
 <action name="execute">
  <command> 
```

instead of (not giving space)

```
<Keybind key="C-]">
<action name="execute">
<command> 
```


Why so?

---

### Post by XP1 on 2011-12-11
Might be helpful to take a look at this:

Help:Bindings - Openbox Wiki:
[http://openbox.org/wiki/Help:Bindings#Key_bindings](http://openbox.org/wiki/Help:Bindings#Key_bindings)


> **eb3ha4el said:**
> Thank you very much you all..
I'm configuring hotkey manually, however, I cannot figure out
what command it is when I adjust volume..

Anyone know what command I should put in? (Volume up and Volume down)When I look in ~/.config/openbox/lubuntu-rc.xml, at line 347, this is what I see:
```
    <!-- Keybinding for Volume management -->
    <keybind key="XF86AudioRaiseVolume">
      <action name="Execute">
          <command>amixer -q sset Master 3%+</command>
      </action>
    </keybind>

    <keybind key="XF86AudioLowerVolume">
      <action name="Execute">
          <command>amixer -q sset Master 3%-</command>
      </action>
    </keybind>

    <keybind key="XF86AudioMute">
      <action name="Execute">
          <command>amixer -q sset Master toggle</command>
      </action>
    </keybind>
```Maybe it will help?

> **eb3ha4el said:**
> Also, is it necessary to do following? (giving space)
```

<Keybind key="C-]">
 <action name="execute">
  <command> 
```

instead of (not giving space)

```
<Keybind key="C-]">
<action name="execute">
<command> 
```


Why so?This is XML, so spacing should not matter to the program. However, spacing is helpful for human readability.

---

