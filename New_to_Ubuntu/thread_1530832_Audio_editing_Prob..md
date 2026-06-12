---
title: "Audio editing Prob."
date: 2010-07-14
forum: New to Ubuntu
---

### Post by nnjond on 2010-07-14
Audio editing Prob.

Hi,

Can anyone help me please?
I have a line-in signal showing up on the input level meter in Sound preference, and i can record with Ubuntu&#8217;s Sound Recorder and hear it played back. But i cannot here what is being recorded while it&#8217;s being recorded. It does&#8217;t pass through the sys and out my speakers.

Thanks

---

### Post by HermanAB on 2010-07-14
Sounds like a job for 'tee' and 'sox'.

---

### Post by MiCK.ca on 2010-07-14
Simple:
Need JACK to help you route the signal to your system output. if you have pulseAudio installed look for pulseJack program and there you can record and monitor at the same time...

More involve but better:
install Jack and audacity and use them together to record whatever you put into your input. There are great tutorials for beginners floating around.

good luck

---

### Post by BbUiDgZ on 2010-07-14
depending on what your doing you might want to look here
[http://ubuntustudio.org/](http://ubuntustudio.org/)

---

