---
title: "how to type in hiragana and khanji"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by smalleye86 on 2009-05-16
hi ..i am new to ubuntu and am configuring how to setup the japanese keyboard ..i tried the layouts in the keyboards preferences but it doesnt help...even if i choose the medium as "japan", my keyboard still types in english, i can swich to other languages with the alt+shift shortcut, but with japanese it just doesnt work? could anyone help me?

thanks.

---

### Post by Frantic_Earthling on 2009-05-16
With Synaptic, pull and install "Anthy" and its dependencies (these should come automatically when you mark Anthy for installation).

Once you have done that, you should see a small keyboard appearing in the notification area. By left clicking on it, "Japanese Anthy" should be available as an option.

If nothing appears, log out and log back in.

---

### Post by albinootje on 2009-05-16
> **smalleye86 said:**
> even if i choose the medium as "japan", my keyboard still types in english

By coincidence I just helped a japanese colleague with this last week :)

The keyboard layout is not important, but the important thing is to have "scim" running. 
If that little keyboard applet does not appear (as someone else posted in a comment already), type the following in a terminal :
```

scim -d

```
After that use the right mouse click on that applet to configure it, and use the keyboard shortcut ctrl-space to activate it inside an application (Openoffice,Thunderbird etc.)

See also here :
[http://ubuntuforums.org/showthread.php?t=975144](http://ubuntuforums.org/showthread.php?t=975144)
[https://help.ubuntu.com/community/Japanese_Input_and_Fonts_in_Ubuntu_8.10_using_SCIM](https://help.ubuntu.com/community/Japanese_Input_and_Fonts_in_Ubuntu_8.10_using_SCIM)

---

