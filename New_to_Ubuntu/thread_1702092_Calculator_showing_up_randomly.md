---
title: "Calculator showing up randomly"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by Viva on 2011-03-07
Once in a while on my computer, several windows of gcalc tool are showing up automatically with random text written in the input boxes. I can't do anything else during this period because I completely lose control of my keyboard. I looked at the log file and it's showing this
```
Mar  7 21:26:40 ubuntu kernel: [  396.297379] atkbd serio0: Use 'setkeycodes 6d <keycode>' to make it known.
Mar  7 21:26:42 ubuntu kernel: [  398.599154] atkbd serio0: Unknown key pressed (translated set 2, code 0x6d on isa0060/serio0).
Mar  7 21:26:42 ubuntu kernel: [  398.599161] atkbd serio0: Use 'setkeycodes 6d <keycode>' to make it known.
Mar  7 21:26:42 ubuntu kernel: [  398.648245] atkbd serio0: Unknown key released (translated set 2, code 0x6d on isa0060/serio0).
Mar  7 21:26:42 ubuntu kernel: [  398.648252] atkbd serio0: Use 'setkeycodes 6d <keycode>' to make it known.
Mar  7 21:26:42 ubuntu kernel: [  398.696647] atkbd serio0: Unknown key pressed (translated set 2, code 0x6d on isa0060/serio0).
Mar  7 21:26:42 ubuntu kernel: [  398.696653] atkbd serio0: Use 'setkeycodes 6d <keycode>' to make it known.
Mar  7 21:26:42 ubuntu kernel: [  398.765100] atkbd serio0: Unknown key released (translated set 2, code 0x6d on isa0060/serio0).
Mar  7 21:26:42 ubuntu kernel: [  398.765106] atkbd serio0: Use 'setkeycodes 6d <keycode>' to make it known.
```

This error is repeated numerous times.

I'm also attaching a screenshot of my desktop while this is happening.

---

### Post by aeiah on 2011-03-07
most likely issue is that you've got a shortcut set up for the calc in some odd manner. some keyboards have a calculator button, and perhaps your OS is mistaking some button or combination for this one? 

are they any keyboard shortcuts assigned to the calc?

---

