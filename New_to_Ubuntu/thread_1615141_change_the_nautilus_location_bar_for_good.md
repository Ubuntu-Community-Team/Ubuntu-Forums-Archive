---
title: "change the nautilus location bar for good"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by audit on 2010-11-06
How do I get a location bar I can type in and change my defaults? 

When I am using Nautilus to find something I would like to be able to type the location right in location bar. There is a way to change this, but I can not remember it and it always reverts to those stupid buttons. I use the terminal way too often just because I can't make those buttons go away.

I despise those buttons and wish them to never return.

---

### Post by holiday on 2010-11-06
> **audit said:**
> How do I get a location bar I can type in and change my defaults? 

When I am using Nautilus to find something I would like to be able to type the location right in location bar. There is a way to change this, but I can not remember it and it always reverts to those stupid buttons. I use the terminal way too often just because I can't make those buttons go away.

I despise those buttons and wish them to never return.

In Nautilus, with your cursor on those "stupid buttons" (I totally agree!) press Ctrl l.

And hope that it works.

---

### Post by TroN-0074 on 2010-11-06
Press Ctrl + L

[http://library.gnome.org/users/user-guide/2.27/nautilus-location-bar.html.en]("http://library.gnome.org/users/user-guide/2.27/nautilus-location-bar.html.en")

---

### Post by audit on 2010-11-06
Well thank you for the response and the link...I guess the programmers of Nautilus thought those button were so clever that they decided allowing us to change the defaults was a waste of their time.

Oh I wish was smart enough to hack Nautilus and change that.

I'll learn to deal with it--in a way it is kind of like Windows Office 7. Which by the way was the reason I switched to OpenOffice and eventually decided to even change operating systems.

---

### Post by kaldor on 2010-11-06
Wrong!

Do what I did. Open a terminal and type "gconf-editor".

Navigate to Apps > Nautilus > Preferences.

Check the "always_use_location_entry" field.

Exit. run "killall nautilus" in terminal. Done :)

---

### Post by holiday on 2010-11-06
> **kaldor said:**
> Wrong!

Do what I did. Open a terminal and type "gconf-editor".

Navigate to Apps > Nautilus > Preferences.

Check the "always_use_location_entry" field.

Exit. run "killall nautilus" in terminal. Done :)

Oh thank you thank you thank you!

---

### Post by kaldor on 2010-11-06
> **holiday said:**
> Oh thank you thank you thank you!

No problem. It was the first thing I got rid of when it became the default a while back. No point; the button to toggle was a better idea.

---

### Post by audit on 2010-11-06
@ kaldor

Thank you; and thank you for reading my post.

---

