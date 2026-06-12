---
title: "Ctrl key moves cursor or display to top in certain cases"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by Paddy Landau on 2010-10-26
I have a bizarre effect with the Ctrl key that makes things very frustrating.

In certain cases, when I press the Ctrl key (e.g. I'm about to press Ctrl-V to paste), I get an unexpected and unwanted side-effect.

There are two cases specifically:

[LIST]
[*]In Open Office Writer, when typing in a note (Insert > Comment). I position my cursor within the note where I want to paste, press Ctrl-V, and it pastes at the start of the note. Or if I just press Ctrl and let go, the cursor is back at the start of the note.
[/LIST]

[LIST]
[*]I use GMail in Firefox. If I'm editing a Contact with a very long note, when I press Ctrl, the note jumps back to the start. In this case, the cursor remains in the right place, although of course it's no longer visible. Editing and viewing long notes is highly frustrating, e.g. when I press Ctrl-Tab to switch between tabs.
[/LIST]
Do you know how to stop this odd behaviour with the Ctrl key? Does anyone else reading this have the same problem?

Linux: Ubuntu Lucid 10.04
Open Office: 3.2.1
Firefox: 3.6.11

TIA

---

### Post by Paddy Landau on 2011-10-31
I have (finally) discovered the answer.

It is the attribute in Assistive Technologies that highlights the position of the control key.

Assistive Technologies > Mouse Accessibility > Accessibility > General > Locate Pointer > Show position of pointer when the Control key is pressed.

If this is checked, it leads to this bizarre behaviour with the Control key.

Rather use ccsm > Accessibility > Show mouse. Not as convenient, but it works.

---

### Post by anewguy on 2011-10-31
Great to know, as this will definitely help in those times when it is driving some of us mad trying to figure out what the heck is going on!

Thanks!!

Dave ;)

---

