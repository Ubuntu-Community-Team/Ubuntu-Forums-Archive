---
title: "long path name in terminal: how to hide ?"
date: 2011-07-28
forum: New to Ubuntu
---

### Post by cosine352 on 2011-07-28
when I change directory then to sub directory ..... sub directory, the path name in the terminal get really long and can be kind of annoying to work with. 
Here is an example

> /home/XXXX/Documents/xxxx/xxxx/xxxxx/XXXX

Does anyone know how to hide this path. 

thanks

---

### Post by lmarmisa on 2011-07-28
Are you referring about how to customize the bash prompt?.

If so, try to change the parameter PS1. This is an example:

```

export PS1="--> "

```

If you wish to make the new prompt permanent, then edit the file **~/.bashrc** and define your preferred value for the parameter PS1 on this file.

---

### Post by cosine352 on 2011-07-28
> **lmarmisa said:**
> Are you referring about how to customize the bash prompt?.

If so, try to change the parameter PS1. This is an example:

```

export PS1="--> "

```

If you wish to make the new prompt permanent, then edit the file **~/.bashrc** and define your preferred value for the parameter PS1 on this file.

thanks. exactly what I was looking for.

---

### Post by bodhi.zazen on 2011-07-28
You can add (or edit) that to ~/.bashrc so you will not need to make that change with every shell.

---

### Post by msandoy on 2011-07-28
I just added a "\n>" at the end of my PS1 in ~/.bashrc. This makes the terminal list the folder information on the line above my prompt, and I have a full line with an ">" at my disposal.

---

