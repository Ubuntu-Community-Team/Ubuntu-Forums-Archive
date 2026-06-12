---
title: "how do i change the Xserver settings?"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by super kim on 2009-08-19
bad title i know sorry.

i am using jaunty 9.04
i have an 8 button mouse that is working as standard. the wheel has 2 axis and they all scroll the correct way.
i would like to set the thumb (Button 8 ) and the wheel (Button 2) to do different things in different programs.

now the thumb button will go back (Alt_Left) in firefox and seems to do nothing in nautilus. i would like this to copy (Control_c) in every instance except in the "eye of gnome" image viewer where i would like it to load the previous image in the directory (Alt_Left) and fire fox should  go back (Alt_Left)
the wheel button opens a link in a new tab in firefox and in nautilus (Control_t). in the image viewer it will pan when an image is zoomed or larger than the window like the left mouse button does, i want this to paste (Control_v) in all instances except the image viewer where i would like this to advance to the next image in the directory (Alt_Right). and firefox where it should go forward (Alt_Right)

the X Input can handle these combinations since they are only using keyboard modifiers not multiple key presses.
There should be no reason to install any extra software (imwheel) since it is evident that the X is already mapping different keycode combinations to different programs.

all i want to do is edit the current set up to do this:
```

Button 1    leftclick
Button 2    wheelclick    for nautilus (37, 55) for firefox (64, 113) for image viewer (64, 113)
Button 3    rightclick
Button 4    wheelup
Button 5    wheeldown
Button 6    wheelleft
Button 7    wheelright
Button 9    thumb        for nautilus (37, 54) for firefox (64, 114) for image viewer (64, 114)

keycode  37 = Control_L NoSymbol Control_L NoSymbol Control_L
keycode  54 = c C c C cent copyright
keycode  55 = v V v V leftdoublequotemark leftsinglequotemark

keycode  64 = Alt_L Meta_L Alt_L Meta_L Alt_L Meta_L
keycode 113 = Left NoSymbol Left NoSymbol Left
keycode 114 = Right NoSymbol Right NoSymbol Right
```

---

### Post by super kim on 2009-08-19
would i need to make an fdi for the mouse to respond as i want?

i don't know how to make one, but i have started reading and if i did need an fdi for the mouse would it be like this?:
```
<?xml version="1.0" encoding="ISO-8859-1"?>
    <deviceinfo version="0.2">
    <device>
     <match key="info.product" string="Microsoft Microsoft Wireless Optical Mouse? 1.00">
      


     </match>
    </device>
   </deviceinfo>

```

but it would need options in there im thinking but i just don't know, i'm sure there is someone out there who does i think the lame thread title doesn't help its only had 3 view in 1 hour

---

### Post by super kim on 2009-08-21
:popcorn: free pop corn to anyone who can help:popcorn:

---

### Post by perce on 2009-08-21
A while ago Linus complained not to be able to change the behaviour of his mouse in Gnome: [http://www.desktoplinux.com/news/NS8745257437.html]("http://www.desktoplinux.com/news/NS8745257437.html") so good luck

---

### Post by super kim on 2009-08-21
> **perce said:**
> A while ago Linus complained not to be able to change the behaviour of his mouse in Gnome: [http://www.desktoplinux.com/news/NS8745257437.html](http://www.desktoplinux.com/news/NS8745257437.html) so good luck

i found that i can change the buttons using btnx.

gnome will allow you to set up a multi button mouse easily and with gui!!

btnx allows you to specify how the x server deals with your button clicks. my mouse now does exactly what i want it to do.
imwheel allows you to fiddle a bit more. i did not need to use this in the end a btnx can map key grabs like Control_C (copy) or Alt_Left (back in firefox/nautilus/image viewer)

if you are trying to set up your multi button mouse my advice is to install btnx first, if you want more then imwheel will probably do the rest.

---

