---
title: "Make ctrl and alt pressed without a keyboard?"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by ehalls on 2010-01-02
Hi there,

I want to be able to rotate the desktop cube with my touch screen, when I am not able to access the keyboard (my laptop is in tablet mode). Is there a way (some script or program) that holds ctrl and alt for one second or two so I can initiate rotate cube by drawing my finger over the screen?

---

### Post by iWolf on 2010-01-02
Im not sure about that, You're most likely to find that info with the Ubuntu Developers @ irc.freenode.net Channel #ubuntu-devel

---

### Post by Methuselah on 2010-01-02
I do not have compiz installed but have you checked the cube keybindings in CCSM (compiz config settings manager).
I'm pretty sure you should be able to configure which keys or mouse buttons rotate the cube.

I know it has a ScreenEdge option that can tie actions to when the cursor is at the edge of the screen.
[http://wiki.compiz.org/CCSM#Screen_Edges](http://wiki.compiz.org/CCSM#Screen_Edges)

Would it be suitable to rotate the cube when you move your hand to the ScreenEdge?

---

### Post by ehalls on 2010-01-02
> **Methuselah said:**
> I do not have compiz installed but have you checked the cube keybindings in CCSM (compiz config settings manager).
I'm pretty sure you should be able to configure which keys or mouse buttons rotate the cube.

I know it has a ScreenEdge option that can tie actions to when the cursor is at the edge of the screen.
[http://wiki.compiz.org/CCSM#Screen_Edges](http://wiki.compiz.org/CCSM#Screen_Edges)

Would it be suitable to rotate the cube when you move your hand to the ScreenEdge?
  Yes, i have checked the settings in ccsm, I can't do it with the screen edge. It is almost imposable to touch the screen edge with the finger, and pretty hard with the pen.

---

### Post by Jenkins1 on 2010-01-02
Go to Compiz and you can remove the ctrl+alt key bindings and have it just to a mouse button. just found out! If you go System > administration > conpizconfig settings 
find rotate cube (click it ) 
click bindings
click where it says <ctrl><altbutton one then click the green coloured ctrl and alt keys untill they are grey then you can assign it to only one mouse button it can't be a normal cliking button as that confuses things. 

Edit: found a mouse it works!!!!!!

---

### Post by falconindy on 2010-01-02
Use a program that allows you to create gestures, like Easystroke.

---

### Post by ehalls on 2010-01-02
> **Jenkins1 said:**
> Go to Compiz and you can remove the ctrl+alt key bindings and have it just to a mouse button. just found out! If you go System > administration > conpizconfig settings 
find rotate cube (click it ) 
click bindings
click where it says <ctrl><altbutton one then click the green coloured ctrl and alt keys untill they are grey then you can assign it to only one mouse button it can't be a normal cliking button as that confuses things. 

Edit: found a mouse it works!!!!!!

Yes, that works very well, but keep in mind that I am only using the finger, I can't use the mouse.

---

### Post by ehalls on 2010-01-02
> **falconindy said:**
> Use a program that allows you to create gestures, like Easystroke.

I haven't found a way to have easystroke hold alt and ctrl. Easystroke only presses and releases buttons...

---

### Post by Jenkins1 on 2010-01-02
> **ehalls said:**
> Yes, that works very well, but keep in mind that I am only using the finger, I can't use the mouse.

Can you not use a button on a pen I think a finger might not be possible.

---

### Post by Marlonsm on 2010-01-02
> **Jenkins1 said:**
> Can you not use a button on a pen I think a finger might not be possible.

Don't quote me on that, but isn't it possible to make a touch with 2 fingers work like another mouse button?

---

### Post by Jenkins1 on 2010-01-02
> **Marlonsm said:**
> Don't quote me on that, but isn't it possible to make a touch with 2 fingers work like another mouse button?

It is possible on a mouse pad I have two finger scrolling enabled.

---

### Post by sisco311 on 2010-01-02
```
sudo apt-get install xautomation
```

```
xte "keydown Control_L" "keydown Alt_L" "sleep 2" "keyup Control_L" "keyup Alt_L"

```

EDIT:

> **falconindy said:**
> Use a program that allows you to create gestures, like Easystroke.

+1 for easystroke.

---

### Post by ehalls on 2010-01-02
> **sisco311 said:**
> ```
sudo apt-get install xautomation
``````
xte "keydown Control_L" "keydown Alt_L" "sleep 2" "keyup Control_L" "keyup Alt_L"

```EDIT:



+1 for easystroke.

Thanks! Exactly what I have been looking for :)

---

