---
title: "How can I change (speicifally) the colors for selected text?"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by RKCole on 2010-05-13
Hello, everyone.

**Using Ubuntu 10.04**

I am trying to find out how I can change the colors of selected text on my system.

Due to my eyesight, it is easier for me to view selected text with white lettering on a dark background.  I have tried customizing the Ambiance theme colors for "Selected Items" under the customization dialog in the **Appearance Preferences** application, but this seems to tamper with the theme in its entirety.

Is there any way at all to simply just change the colors of selected text?  For instance, the selected text colors as I highlight text within Firefox appear as black text with a light-brown background.  I would like to make it so that the text is white on a dark blue background.

If anyone has any input on this matter, it would be greatly appreciated.

Thanks in advance.

Take care.

PS:  I sure do miss these forums. :)

---

### Post by RKCole on 2010-05-18
Still no success in this slight dilemma.

Changing the **Selected Items** option under the **Appearance Preferences**-> works for the text highlight color, but the problem with this is that it changes button colors to have a blue background (not a problem) with a very faded text color (which is a problem).

I will keep experimenting and searching for a solution to this, but any suggestions are greatly appreciated.

Thanks very much for any help offered.

Take care

PS: Attached is a screenshot of selected text (how I would like it to be) and the button coloring (which is posing the problem).

---

### Post by kerry_s on 2010-05-18
you have to go straight to the gtkrc file to make those kind of changes. grab a theme folder from "/usr/share/themes", in there you'll find a gtkrc file. just start tweaking that.
i used the clearlooks theme to do a clearlooks-grey theme, it's kinda simple all the colors are at the top so you don't need to mess with the rest of the file.

take your time, it takes patience to get it right.

---

