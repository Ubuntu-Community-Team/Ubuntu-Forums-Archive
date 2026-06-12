---
title: "Tkinter Canvas and Snack sound tool kit"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by drsyntax on 2010-02-06
Hello,

I am using Snack sound toolkit to plot the spectrogram of audio files that uses Tkinter canvas.
Here's a piece of code that can do so:
 
```
s = Sound(load='out.wav')
c = SnackCanvas(height=200, width=400)
c.pack()
n=c.create_spectrogram(0, 0, sound=s, height=200, width=400)

```
what i want is to get the spectrogram data, not to draw it, is there a way to get the data before plotting it using Tkinter canvas ??

Thanks,

---

