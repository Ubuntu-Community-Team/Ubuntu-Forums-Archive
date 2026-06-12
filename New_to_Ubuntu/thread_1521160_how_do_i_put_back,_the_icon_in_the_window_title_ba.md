---
title: "how do i put back, the icon in the window title bar? the one on the left"
date: 2010-06-30
forum: New to Ubuntu
---

### Post by opendevlite on 2010-06-30
is this possible?

i dont see the application icon of every window, opened

how?

thanks

---

### Post by Seanlol on 2010-06-30
> **opendevlite said:**
> is this possible?

i dont see the application icon of every window, opened

how?

thanks

I'm having a hard time understanding your problem. Are you saying that the button in the bottom left corner that takes you to the desktop (and back to where you were) is missing?

---

### Post by hackerseraph on 2010-06-30
> **opendevlite said:**
> is this possible?

i dont see the application icon of every window, opened

how?

thanks

I am so confused right now... Usually there is a folder called 128x128 where resizable pngs are put, eliminating the need to a bunch of different icon sizes for things like docks, menubars, title bars, etc.

---

### Post by ankspo71 on 2010-06-30
Do you mean the menu button on the opposite side of the minimize, maximize and close window buttons?

using your keyboard, press Alt-F2
type gconf-editor in the run dialog, then press enter.
when the gnome configuration editor opens, navigate to:
apps > metacity > general > button layout
Then type in the following entry...
menu:maximize,minimize,close

The ":" separates the left and right side. You can arrange them in any order too.
Hope that helps.

---

### Post by opendevlite on 2010-06-30
ankspo71: yes thats what i meant

thanks, i got it fix

thanks to you, all for helping

:)

---

