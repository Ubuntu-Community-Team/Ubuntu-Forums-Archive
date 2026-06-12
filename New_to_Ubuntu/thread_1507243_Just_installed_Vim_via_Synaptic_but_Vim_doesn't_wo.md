---
title: "Just installed Vim via Synaptic but Vim doesn't work or show"
date: 2010-06-11
forum: New to Ubuntu
---

### Post by adamsiddhi on 2010-06-11
Hello.

I wanted to install **Vim** so I went to **Ubuntu Software Cente**r in **Xubuntu 10.04**. I typed Vim in the search field, it showed up and I pressed 'Install'. It appeared to have successfully installed but when I went to look for it under **Applications** (in the top panel/menu), I could not find it anywhere in **Accessories** (or any of the other sub-categories). I decided to open **/usr/share/applications** to check to see if **Vim** might be there but it was not. Then I decided to go to **Synaptic Package Manager** to see if Vim was marked as installed and it was along with: **vim-common**,** vim-runtime** and **vim-tiny**. I should mention that the **Vim** entry reads:

**vim    2:7.2.330-1ubuntu3       Vi IMproved - enhanced vi editor**
(the installed version is the same as the latest version so i did not write it 2 times)

Also I was able to find Vim in** /usr/bin/** but when I try to execute it, nothing happens. Then I notice it is not an executable and that it is a link to another file which is located at **/etc/alternatives/vim**. When I check that file out it turns out to be another link to **/usr/bin/vim.basic** right back to the **/usr/bin/** directory! So I execute **vim.basic** and predictably nothing happens again. I even try executing **vim.tiny** which is another Vim executable but nothing happens there as well. So it just seems like this installation went bad or something. 

Does anyone know why this happened and how I can actually get to run Vim?

Thanks,
:adam

---

### Post by Eisenwinter on 2010-06-11
Just open a terminal and type "vim" (without the quotes).

To exit the editor press the ESC button, then type in ":q" without the quotes.

EDIT: 

Vim is a console, text user interface (TUI) editor, it is not a graphical editor. You will not be able to run it from the applications menu, or from nautilus.

If you want Vim in graphical mode, get GVim.

---

### Post by adamsiddhi on 2010-06-11
Ok thank you for that clarification :p

---

### Post by gmargo on 2010-06-11
There are multiple vim packagings available.  The **vim** package provides the text-only version.  The **vim-gnome** package provides the graphical+text version tailored for gnome.  The **vim-gtk** package provides another graphical+text version using GTK2.  If you are using a gnome setup, I recommend that you install the **vim-gnome** version.

[http://packages.ubuntu.com/lucid/vim](http://packages.ubuntu.com/lucid/vim)
[http://packages.ubuntu.com/lucid/vim-gnome](http://packages.ubuntu.com/lucid/vim-gnome)
[http://packages.ubuntu.com/lucid/vim-gtk](http://packages.ubuntu.com/lucid/vim-gtk)

---

### Post by -kg- on 2010-06-11
Of course, if you'll note from adamsiddhi's tag, he's using Xubuntu.  I'm sure that Vim will have a version that runs under Xubuntu, as well.  If nothing else, use one of the other versions, like the GTK version.  It (and others) will be available in Synaptic.

---

### Post by adamsiddhi on 2010-06-11
Yes I was able to install Vim and run it by installing and using it's graphical user interface called gVim. Solved! :guitar:

---

