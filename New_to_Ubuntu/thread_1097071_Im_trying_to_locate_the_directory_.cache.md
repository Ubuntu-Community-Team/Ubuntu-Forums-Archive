---
title: "Im trying to locate the directory /.cache/"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by feesgo on 2009-03-15
Im trying to locate the directory /.cache/  where is /.cache/ ?

Im trying to to edit the auto generated XFCE menu with the menu editor

The instructions to do this says:

# cp ~/.cache/xfce4/desktop/menu-cache-name-of-the-generated-file.xml ~/.config/xfce4/desktop/menu2.xml

  # cd ~/.config/xfce4/desktop/

I realize that "/.config/" is an abbreviation to refer a directory in my computer.

In my computer  "/.config/" refers to the directories: 

/etc/xdg/

So I think "/.cache/"  is also an abbreviation to refer a directory in my computer.

But what directory?

Where is /.cache/xfce4/desktop/menu-cache-name-of-the-generated-file.xml ?

Thank you very much

---

### Post by tanha on 2009-03-15
> **feesgo said:**
> Im trying to locate the directory /.cache/  where is /.cache/ ?

Im trying to to edit the auto generated XFCE menu with the menu editor

The instructions to do this says:

# cp ~/.cache/xfce4/desktop/menu-cache-name-of-the-generated-file.xml ~/.config/xfce4/desktop/menu2.xml

  # cd ~/.config/xfce4/desktop/

I realize that "/.config/" is an abbreviation to refer a directory in my computer.

In my computer  "/.config/" refers to the directories: 

/etc/xdg/

So I think "/.cache/"  is also an abbreviation to refer a directory in my computer.

But what directory?

Where is /.cache/xfce4/desktop/menu-cache-name-of-the-generated-file.xml ?

Thank you very much

"~/" refers to your home directory, e.g., /home/username
"/.filename" refers to a hidden file. So, in file browser View> Show hidden files
You'll find the find in your home directory, hidden.

---

### Post by egalvan on 2009-03-15
> **feesgo said:**
> Im trying to locate the directory /.cache/  where is /.cache/ ?


The instructions to do this says:

# cp [COLOR="Red"]~[/COLOR]/.cache/xfce4/desktop/menu-cache-name-of-the-generated-file.xml ~/.config/xfce4/desktop/menu2.xml

# cd [COLOR="Red"]~[/COLOR]/.config/xfce4/desktop/

I realize that "/.config/" is an abbreviation to refer a directory in my computer.

In my computer  "/.config/" refers to the directories: 

/etc/xdg/

So I think "/.cache/"  is also an abbreviation to refer a directory in my computer.

But what directory?

Where is /.cache/xfce4/desktop/menu-cache-name-of-the-generated-file.xml ?

Thank you very much

The red [COLOR="Red"]~[/COLOR] is short-hand for your home directory.

an example, mine is....

/home/ernest/.cache

which is the same as 

 [COLOR="Red"]~[/COLOR]/.cache

---

