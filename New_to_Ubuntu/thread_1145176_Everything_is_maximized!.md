---
title: "Everything is maximized!"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by basics on 2009-05-01
Hi,

When I start anything on my 9.04 system every window is maximized. i hate it. 

It is not only Firefox but even synaptic or any folder on the system.

Its not compiz. I checked.

---

### Post by 3rdalbum on 2009-05-01
You don't, by any chance, have Maximus installed and running?

---

### Post by basics on 2009-05-01
No I do not. 

I think it is in some setting on my system. I just don't know where.

---

### Post by Dark Aspect on 2009-05-01
> **basics said:**
> I think it is in some setting on my system. I just don't know where.

Does you system settings under appearance preferences look like this? This is default.

[IMG]http://img18.imageshack.us/img18/4666/ubuntusdefault.png[/IMG]

---

### Post by pastalavista on 2009-05-01
Run gconf-editor and open apps/same-gnome. Uncheck the 'maximized' box if it is checked. That's just the obvious cause of your problem. I hope it's that simple.

---

### Post by basics on 2009-05-01
> **pastalavista said:**
> Run gconf-editor and open apps/same-gnome. Uncheck the 'maximized' box if it is checked. That's just the obvious cause of your problem. I hope it's that simple.

Would you please give me more details?

I have never done this before. I opened gconf-editor but I don't know where to do anything.

thanks

---

### Post by Spiritous on 2009-05-01
Press ALT + F2 And type "gconf-editor"

Then open Apps >>> Same Gnome >>> and if "Maximized" is checked in the box, uncheck

---

### Post by xpod on 2009-05-01
> Would you please give me more details?

I have never done this before. I opened gconf-editor but I don't know where to do anything.

thanks

To use gconf-editor you can use either the terminal or ALT-F2 and type in 
```
gconf-editor
```

There is no "maximized" option in mine though i`ve just noticed.
The only thing looking kinda relevant is a custom height & width option.

---

### Post by pastalavista on 2009-05-01
Here's how it looks...

---

### Post by xpod on 2009-05-01
> Here's how it looks... 

Ahhh.....Gconf-editor seems to have eaten my "maximized" option then.
[ATTACH]111997[/ATTACH]

Oh well.

---

### Post by basics on 2009-05-01
> **pastalavista said:**
> Run gconf-editor and open apps/same-gnome. Uncheck the 'maximized' box if it is checked. That's just the obvious cause of your problem. I hope it's that simple.


It was unchecked.

Everything is the same...

---

### Post by jwaclawsky on 2009-05-02
I believe I have the same problem. See my thread titled "Is window size default changeable?" (last post 5 days ago). I tried a number of things that people suggested but I still have the same problem as you....sigh  And as you know, it is very annoying. You can see when opening a new window the new window attempts to open up at its old smaller size and then something takes over a drives the window to full screen size. Help anyone would be appreciated!  Thanks

---

### Post by gcbzzzz on 2009-05-02
SOLUTION!!!

first, how to reproduce:
1. install 9.04 net book edition
2. change desktop mode to Standard (that netbook stuff sux)
3. open anything, say, xterm

expected: xterm is NOT maximized

what really happens: xterm is maximized


work around (the fix):
run 'gconf-editor'
navigate on the left to '/apps/maximus/'
select on the right 'no_maximize' and uncheck.

---

### Post by jwaclawsky on 2009-05-02
This is the same advice as on my previous thread, which didn't work then either. When I go to maximus using the configuration editor there is NO statement called 'no_maximize' to uncheck.  Just three statements exist there. They are:

binding    <Ctrl><Alt>f

execute_class [Totem, Wfica_Seamless, Ktuberling, Gnometris,Cheese,Kwordquiz,Gnome-terminal,XTerm, NC   
 
undecorate  - with an unchecked box 

Again, any help would be appreciated. Thanks!

---

### Post by basics on 2009-05-02
Is there a way to set ubuntu back to all of its basic defaults?

I don't mind doing that.

please help

---

