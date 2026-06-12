---
title: "xterm transperant background"
date: 2008-12-20
forum: New to Ubuntu
---

### Post by ja660k on 2008-12-20
is there any way to get this?

i know you can do it with other terminals.
but i would like to know if it is possible with xterm.
because it is my favorite.. for many reasons

---

### Post by cdtech on 2008-12-20
I don't believe "xterm" is capable of background transparancy. I use the ".Xresourses" file to set mine up for color:
```
xterm*font: -*-fixed-medium-r-*-*-18-*-*-*-*-*-iso8859-*
xterm*font1: -*-*-*-*-*-*-2-*-*-*-*-*-*-*
xterm*font2: -misc-fixed-*-r-normal-*-8-*-*-*-*-*-iso8859-*
xterm*font3: -b&h-lucidatypewriter-bold-*-*-*-12-*-*-*-*-*-*-*
xterm*font4: -*-screen-bold-r-normal-*-16-*-*-*-*-*-iso8859-*
xterm*font5: -*-lucidatypewriter-medium-*-*-*-18-*-*-*-*-*-*-*
xterm*font6: -*-lucidatypewriter-medium-*-*-*-20-*-*-*-*-*-*-*
xterm*font7: -dec-terminal-bold-r-normal-*-14-*-*-*-*-*-iso8859-*

XTerm*background: black
XTerm*foreground: white
XTerm*pointerColor: red
XTerm*pointerColorBackground: black
XTerm*cursorColor: navy
XTerm*internalBorder: 3
XTerm*loginShell: true
XTerm*scrollBar: false
XTerm*scrollKey: true
XTerm*saveLines: 1000
XTerm*multiClickTime: 250
```

---

### Post by ja660k on 2008-12-20
yeah i have similar to that in my .xdefaults and yeah i think it is not possible for xterm to be transperant, can you suggest another LIGHTWEIGHT terminal i can use which is very similar to xterm? because i like the different colors..?

nice color's too =)

---

### Post by kerry_s on 2008-12-20
```
sudo apt-get install roxterm
```

---

