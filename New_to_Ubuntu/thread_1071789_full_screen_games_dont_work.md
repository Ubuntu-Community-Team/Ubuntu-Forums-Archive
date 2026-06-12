---
title: "full screen games dont work"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by libihero on 2009-02-16
many of my full screen games dont work, such as scortched 3D or supertux2.  when it goes to full screen, it just shows random colors on the screen on horizontal lines.  the same happens when i try to run elisa.  is there any driver i need to download??

---

### Post by sumguy231 on 2009-02-16
For starters, what graphics card do you have?

---

### Post by Art3mis on 2009-02-16
Do you have a ATI graphics card?

If yes disable compiz. For some reason it interferes with 3d applications ( I had the same problem until I disabled compiz)


IF YOU HAVE ATI GRAPHICS CARD YOU HAVE TO DIABLE COMPIZ

---

### Post by libihero on 2009-02-16
ya i have ati.  is there any way i can quickly disable compiz without losing any of the saved settings??

---

### Post by sumguy231 on 2009-02-16
You can create a shortcut to 'killall compiz' which should turn it off and then a shortcut to 'compiz --replace' to turn it back on. There is probably a less annoying workaround though.

---

### Post by libihero on 2009-02-16
is that all i have to type in the terminal?  because if it is i dont mind it

---

### Post by libihero on 2009-02-17
i tried the killall compiz, but that didnt work, but when i did compiz --restore, i think that turned it off.  however, the full screen games still didnt work.  it just shows the horizontal jumbled up colors

---

### Post by sumguy231 on 2009-02-17
Sorry, try
```
killall compiz.real && metacity --replace
```
instead, I think that will work. If it does you can create a shortcut on your panel for it by right-clicking, clicking 'add to panel', 'custom application launcher', 'add', and then pasting the command in the dialog there.

Also, I've never owned an Ati card but do you know if you're using the restricted drivers or the open source drivers for it? You'll probably need ATI's closed-source drivers for 3d games to work properly. You should be able to check in the restricted drivers manager in System -> Administration.

---

### Post by libihero on 2009-02-17
it says that it is a propriety driver... is that open source or closed?

---

### Post by sumguy231 on 2009-02-18
That means the same thing as closed source, which is generally the best choice for 3d stuff. I honestly don't know why that's happening, maybe someone who actually owns an Ati card can help you.

---

### Post by libihero on 2009-02-19
bump...

---

### Post by libihero on 2009-02-23
bump

---

### Post by libihero on 2009-02-25
bump...

---

