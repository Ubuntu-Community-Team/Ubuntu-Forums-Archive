---
title: "carnt set up dual monitors"
date: 2010-07-04
forum: New to Ubuntu
---

### Post by jrovduki on 2010-07-04
i need hellp im tryin to set up dual monitor to extend my desktop but when i connect my second monitor both of them will just go black n stay black untill i disconnect it i have tryed everything i can think of i have a foxconn botherbord and 3 gb ram and a ati radeon hd 3400 graphic card im running windows xp and my main monitor is using vga and the over one is using vga to dvi plz hellp

---

### Post by MichealH on 2010-07-04
When they are black on the keyboard blindly use the keys CTRL+ALT+F1

Now Blindly Log in
enter Password

Now blindly excecute:

```
sudo bash
```
```
Xorg -configure
```
```
cp /etc/X11/xorg.conf.new /etc/X11/xorg.conf
```
```
service gdm start
```

And it should work

---

### Post by jrovduki on 2010-07-04
im sorry im new to all this where do i put the codes in ?

---

### Post by MichealH on 2010-07-05
Oh forgot it is ABT! :P

When you press CTRL+ALT+F1 you will be faced with a terminal. Or... You should When you press them blindly (without looking) put in the codes. Have complete trust in your keyboard.

---

