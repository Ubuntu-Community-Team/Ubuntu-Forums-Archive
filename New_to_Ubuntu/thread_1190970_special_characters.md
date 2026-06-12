---
title: "special characters"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by adamogardner on 2009-06-18
How do I make the little circle to denote degrees?

---

### Post by adrianx on 2009-06-18
There is probably more than one way, but this is how I do it (US standard keyboard):

1. System > Preferences > Keyboard
2. Click "Layouts" tab
3. Click "Layout Options..." button
4. Expand "Compose key position"
5. Choose one (I use "Right Win")
6. Click "Close", "Close"

You can now use your "Compose" key described here: [http://en.wikipedia.org/wiki/Compose_key](http://en.wikipedia.org/wiki/Compose_key)

E.g. 
Right_Win o o gives me °
Right_Win ^ e gives me ê
Right_Win , c gives me ç
...

---

### Post by wpshooter on 2009-06-18
hold Alt followed by 0176 on the numeric keypad.

---

### Post by adrianx on 2009-06-18
> **wpshooter said:**
> hold Alt followed by 0176 on the numeric keypad.
I know that works in Windows, but I'm not so sure about Linux... :confused:

---

### Post by geirha on 2009-06-18
On my norwegian layout, I get the ° by hitting Alt Gr+Shift+0 (zero). If you know the unicode number for the symbol (00b0 in this case), you can use Ctrl+Shift+u as well.

When you hit Ctrl+Shift+u, you'll see an underlined _u_, type the unicode number, then hit space to end it, and the sequence will be replaced with the symbol.

<Ctrl><Shift>u00b0<space>

You can ommit starting zeroes, so in this case it's enough with

<Ctrl><Shift>ub0<space>

EDIT: Minor clarification. You don't need to hold down all those keys at the same time. You hit Ctrl+Shift+u at the same time, then release all of them and type in "b0" followed by the space key.

---

### Post by wpshooter on 2009-06-18
> **wpshooter said:**
> hold Alt followed by 0176 on the numeric keypad.

Can someone try this on Ubuntu, I do not have access to my Ubuntu computer right now ?

Thanks.

---

### Post by geirha on 2009-06-18
> **wpshooter said:**
> Can someone try this on Ubuntu, I do not have access to my Ubuntu computer right now ?


Nope, doesn't work in Ubuntu.

---

### Post by adrianx on 2009-06-18
> **wpshooter said:**
> Can someone try this on Ubuntu, I do not have access to my Ubuntu computer right now ?

Thanks.
I have already, it doesn't work. ;) 

The AltGr/Compose method is simpler than having to know the ASCII or Unicode codes. I should know, I sometimes type in Afrikaans. For me, "Right_Win ^ e" is much simpler than remembering Alt+136. (ê)

---

### Post by The Cog on 2009-06-18
The trick: 
<Ctrl><Shift>U B 0 <space>
works nicely - I learned something today.

Also, look at Accessories->Character Map where you can find a wide range of characters, then double-click them to add them to the text field at the bottom, then copy/paste them where you want.

---

