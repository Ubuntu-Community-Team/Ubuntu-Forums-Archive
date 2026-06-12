---
title: "Is there any app for right-clicking on a mac?"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by captpicard12 on 2009-08-25
Hi, I was wondering if there is any app I can get that will allow my to right click in intrepid on my powerbook g4?

---

### Post by coldReactive on 2009-08-25
This snippet from a blog I found might help:

> I realized early that Ubuntu is not very usable with a 1-button mousepad. After some searching I found out that F12 (or maybe it was F11, it's not working now) was mapped to right-click. WTF, there is no way in hell I'm using any F key for right-clicking. In OS X I can do it by ctrl-clicking, so I should be able to do it in Linux too. I came across [this posting]("http://ubuntuforums.org/showthread.php?t=193864") about installing mouseemu. I did so, and added to /etc/default/mouseemu:

```
    MID_CLICK="-middle 125 272" # Command key + mouse click
    RIGHT_CLICK="-right 29 272" # Control key + mouse click
```

Once I did that and restarted mouseemu (sudo /etc/init.d/mouseemu stop/start), I was able to right-click with ctrl-click. Yay! But then after realizing that I have to use Alt-Tab instead of Command-Tab to switch windows, I was annoyed further because the Alt key on the Mac is proven to increase the risk of arthritis and why the hell do I have to remember a different keystroke for Linux when Command-Tab works in OS X?

---

### Post by 3rdalbum on 2009-08-26
Yes, use F12 to right-click, and F11 to middle-click.

>> and why the hell do I have to remember a different keystroke for Linux when Command-Tab works in OS X? <<

Whoever wrote that article is obviously forgetting that Linux has been around for longer than OS X :-)

---

