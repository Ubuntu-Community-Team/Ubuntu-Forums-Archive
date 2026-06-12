---
title: "Bluetooth locking up Hardy (8.04)"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by xt0rt on 2008-05-15
New Ubuntu user here, please bear with me. I installed Hardy on my HP Pavilion dv9500t the other day. Got all my hardware working almost out of the box, which was very encouraging.

Today, I bought myself one of the new Samsung Glide phones. I managed to get both devices to recognize each other, but when I attempt to pair the devices in order to send files my entire Ubuntu installation hangs. The caps lock button starts blinking, seemingly mocking me. Only way I have found to get out of this is a hard reboot.

I've been searching through the forums hoping it wouldn't come to this, but I have been unable to find any solution. I don't really know what to be looking for in my logs either, so if this information will help resolve the problem I may need a little guidance...

Any help here would be greatly appreciated.

---

### Post by hermes0710 on 2008-05-16
For a start point, can you post the output of "dmesg" command (run it in a terminal) ?

<alt>+F2 then type gnome-terminal. In the terminal execute:
```
dmesg
```

---

### Post by xt0rt on 2008-05-16
hermes0710,

Thank you very much for the response. dmesg outputs a large amount of information... more than my terminal buffer will allow it looks like.

Is there something I should be looking for in specific? Or can I clear this log somehow and then immediately trigger the lockup?

I appreciate the help!

---

### Post by hermes0710 on 2008-05-16
My mistake... Since your system hangs no good can come from the dmesg after the reboot. Anyway, have you tried ctrl+alt+F1 when it hangs in order to change to console mode? Or even ctrl+alt+backspace in order to restart the gui?

---

### Post by xt0rt on 2008-05-16
No I have not, and I was unaware that I could do such a thing. Perhaps I can kill the hanging process this way? I'm about to leave for work, but will definitely try this when I return.

Please subscribe to this thread, as I'll probably be working on this feverishly until I find a solution. Nobody should have to pay for ring tones or wallpaper, not to mention put up with crappy manufacturer software!

---

### Post by hermes0710 on 2008-05-16
I am already subscribed, good luck

PS>I agree with you on not paying for ring tones etc.

---

### Post by xt0rt on 2008-05-17
A bit of an update here...

I think this might be related to some other problems I've started having, particularly the GUI locking up during startup.

I'm going to reinstall (no big deal, I expected this), using a guide I found for my specific laptop. If I do end up running into this same problem, we can take it from there. I will be sure and post updates as I go along here.

---

