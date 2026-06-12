---
title: "what are &quot;Buttons 1 -9&quot;"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by enri2 on 2009-03-27
ok  the magnifier  has  shift + super+ button 4 to zoom in. What does button 4 mean ? what key is it? 

super is the windows logo button right??

---

### Post by boof1988 on 2009-03-27
I gave incorrect information it seems.

Previous information removed by boof1988.

---

### Post by mgmiller on 2009-03-27
Button 1 is the regular left click button
Button 2 is the middle mouse button (or press down on scroll wheel)
Button 3 is the regular right click button
Button 4 is the scroll up on the wheel
Button 5 is the scroll down on the wheel
Button 6 is the left side button (usually the "back" button)
Button 7 is the right side button (usually the "forward" button)

That's all I have on my mouse.  To discover what buttons yours are do the following:

Open a terminal
Applications > Accessories > Terminal

enter the following command:
```
xinput list
```
It will return all the keyboard, mouse, etc settings, my mouse is:
  "Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)"

Next, to see what the buttons do, enter the following command in terminal:
xinput test "name of mouse"

in my case I would enter:
```
xinput test "Microsoft Microsoft 5-Button Mouse with IntelliEye(TM)"
```

In the window that results, as you click each button, the number will appear.  Be careful, as if you move the mouse, you will get a long scrolling line of text that makes it difficult to interpret the results.

If that happens, just close and reopen the terminal and repeat the xinput test command.

Have fun...

---

