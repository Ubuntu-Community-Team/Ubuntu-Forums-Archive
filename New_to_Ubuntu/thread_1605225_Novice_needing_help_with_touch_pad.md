---
title: "Novice needing help with touch pad"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by theTemest on 2010-10-25
Proficient user of Windows and now trying my hand at Linux/Ubuntu. Have the manual and will learn this stuff over time. It's difficult to ask for help as any advice is in a language I'm not familiar. But there is one thing that if corrected would make my life easier during this learning period.
My right hand got destroyed in an accident and typing with it is a pain. Therefore, I almost always use a mouse. But when I do type the touch pad is always engaged in some manner and ruins what has been typed. I've looked online and can find no method that is universally accepted as the best way to deactivate the touchpad when the USB mouse is active. Is there a simple method to deactivate the touch pad? I tried removing the Synaptic package but the touch pad is apparently independent of Synaptic. 
 
Any help and advice is welcomed.

---

### Post by Jeanke on 2010-10-25
Hi,

I'm not sure if (and how) you could automatic disable the touchpad when a USB mouse is connected.
However, under System -> Preferences -> Mouse -> Touchpad you should have an option to disable the touchpad while typing (at least it is in Ubuntu 10.10, I'm not sure if it is also there in 10.04). There is also an option to disable "clicking" with the touchpad, then you can only use the buttons.

Note: did you uninstall the "Synaptic Package Manager"? This software has nothing to do with the touchpad. It is used to install/uninstall software in Ubuntu (similar to "Ubuntu Software Center").

---

### Post by Verbeck on 2010-10-25
try this: 
run **gconf-editor **(alt+F2 should bring up the run dialogue)
go to **desktop>gnome>peripherals>touchpad**
uncheck the box next to "**touchpad_enabled**"

---

### Post by theTemest on 2010-10-25
> **Jeanke said:**
> Hi,

I'm not sure if (and how) you could automatic disable the touchpad when a USB mouse is connected.
However, under System -> Preferences -> Mouse -> Touchpad you should have an option to disable the touchpad while typing (at least it is in Ubuntu 10.10, I'm not sure if it is also there in 10.04). There is also an option to disable "clicking" with the touchpad, then you can only use the buttons.

Thanks for responding.
It might be a 10.04 issue because there are no options for the touchpad, only the mouse. 
No I did not remove the Package Manager. It was a synaptic package that I removed but made no difference as I do not have a synaptic device.
Thanks for the effort.

---

### Post by theTemest on 2010-10-25
> **Verbeck said:**
> try this: 
run **gconf-editor **(alt+F2 should bring up the run dialogue)
go to **desktop>gnome>peripherals>touchpad**
uncheck the box next to "**touchpad_enabled**"

When unchecked, the Touchpad should be disabled. Right? And I noticed a key in config editor “disable_while_typing” was checked [True]. I restarted the computer and the settings remained, but the Touchpad is alive and well.  [I had to type this in OpenOffice because breathing on the Touchpad kept erasing everything I typed]. This really is ridiculous. Possible bug with Lucid??
Any other ideas? 
Thanks for your trying.

---

### Post by pelastikbintang on 2010-10-25
Menu>System>Preferences>Mouse>Touchpad

there should be a box there saying disable touchpad while typing..hope this will help you..btw..u should tick the box

---

### Post by theTemest on 2010-10-25
> **pelastikbintang said:**
> Menu>System>Preferences>**Mouse>Touchpad**

there should be a box there saying disable touchpad while typing..hope this will help you..btw..u should tick the box

That's probably the most frustrating thing. Even though there is a Touch pad, it does not display in the Mouse Preferences.:cry: Many have suggested this and why Touch pad is not available there, I have no idea.
Tick the box??

---

### Post by theTemest on 2010-10-25
The system began to freeze periodically. With the touchpad issue and now freezing up I downloaded 10.10 Meerkat and ran it from a USB thumb drive. 10.10 allows settings for the touch pad to be done in the mouse preferences and it works beautifully. Jeanke is correct....the touchpad issue is one with 10.04. I don't have that must invested in Lucid that I'm going to format that partition and install 10.10.
Thanks to everyone for your responses. I really appreciate your efforts.

-Mark

---

