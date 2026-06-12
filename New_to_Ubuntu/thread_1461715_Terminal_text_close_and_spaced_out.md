---
title: "Terminal text close and spaced out"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by Kafubie on 2010-04-24
When I started to customize the font and font sizes for my computer.  It seems that when I opened up the terminal, that the lettering is close or very spaced out.  How can I make it not to do that.  I changed every option to Sans and Sans bold.  If someone that has the default font setup tell me or if you have a font setup that is not screwing the spacing of the terminal.

Thanks
-Nathan

---

### Post by Kafubie on 2010-04-24
[B][U]HALP!
bump[/U][/B]

---

### Post by jrothwell97 on 2010-04-24
What you've done is changed the "monospace" (also called the "fixed-width") font to Sans, which is *not* a monospaced font.

(It's to do with typography: "monospaced" fonts are ones where the characters are all of equal width and height.)

Simply change the fixed width font in your system preferences back to Monospace, which is the default.

---

### Post by Kafubie on 2010-04-24
> **jrothwell97 said:**
> What you've done is changed the "monospace" (also called the "fixed-width") font to Sans, which is *not* a monospaced font.

(It's to do with typography: "monospaced" fonts are ones where the characters are all of equal width and height.)

Simply change the fixed width font in your system preferences back to Monospace, which is the default.

How would I access it,  I went to Appearance Preferences->font.  There is Monochrome-Bestshapes-Best Contrast- Subpixel smoothing.
(I have subpixel smoothing applied)

---

### Post by nitstorm on 2010-04-24
if u want the terminal's font to be same as that of the system's fixed width font, then open up a terminal and Edit->Profile Preferences. Choose to edit the default and then in the general tab of the window that opens up tick the Use the system fixed width font, otherwise set whatever font you like by unchecking it and then selecting the font of your preference.

---

### Post by Kafubie on 2010-04-24
> **nitstorm said:**
> if u want the terminal's font to be same as that of the system's fixed width font, then open up a terminal and Edit->Profile Preferences. Choose to edit the default and then in the general tab of the window that opens up tick the Use the system fixed width font, otherwise set whatever font you like by unchecking it and then selecting the font of your preference.

Thanks a bunch!  For me I had to uncheck the first option that said system's fixed width font.  Now it looks normal!

---

### Post by nitstorm on 2010-04-25
No problemo, that's what communities are for. Please mark this thread solved by using the thread tools option that you see on this page :) 

Cheers mate!

---

