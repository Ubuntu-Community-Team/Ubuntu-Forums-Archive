---
title: "login problem"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by mary79 on 2009-08-10
hello everyone. I would be really thankful if anyone can answer my question. I'm using ubuntu. The problem is that I changed the language, from english to greek, then I log out, and now I can't log in 'cause my password is in english. How can I change the language?? Please help!

---

### Post by mikewhatever on 2009-08-10
Try a keyboard shortcut like Alt+Alt. Isn't there a way to switch to another keyboard layout in GDM?

---

### Post by tom66 on 2009-08-10
Log in using recovery mode. Select 'root shell'. Execute these commands:

```

km us
sudo startx

```

"km us" sets your keyboard to US. I don't know if this will work though because GDM/GNOME might set their own keymaps... 

"sudo startx" starts the X server.

---

### Post by unutbu on 2009-08-10
tom66, what is "km"? It is not on my default Intrepid installation...

---

### Post by mary79 on 2009-08-10
nai mono pou kai thn entolh thn grafei me ellhnikous xarakthres



> **tom66 said:**
> Log in using recovery mode. Select 'root shell'. Execute these commands:

```

km us
sudo startx

```"km us" sets your keyboard to US. I don't know if this will work though because GDM/GNOME might set their own keymaps... 

"sudo startx" starts the X server.

---

