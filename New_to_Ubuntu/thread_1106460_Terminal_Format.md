---
title: "Terminal Format?"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by mjheagle8 on 2009-03-25
how can i format output in the terminal?
thanks in advance for any and all help!

---

### Post by Bachstelze on 2009-03-25
What do you mean by "format"?

---

### Post by DGortze380 on 2009-03-25
> **mjheagle8 said:**
> how can i format output in the terminal?
thanks in advance for any and all help!

You're going to need to be a little more specific.

What are you trying to do?

---

### Post by mjheagle8 on 2009-03-25
okay, how would i change the colors of the text output? or put it in columns (or spacing in any way)?

---

### Post by Chemical Imbalance on 2009-03-25
Edit, Profile Preferences (gnome-terminal)

---

### Post by mjheagle8 on 2009-03-25
i know how to change all the text, but what if i want just one word or phrase to be a different color?

---

### Post by The Cog on 2009-03-25
Google for ansi escape sequences. Your application needs to print and escape character, an open square bracket, a number and the letter m to set the properties of subsequent text.

Try this command as an example:
echo $'\e[1mBold \e[0mPlain \e[31mRed \e[1;31mBoldRed\e[0m'

---

