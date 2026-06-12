---
title: "Run executable without prompt"
date: 2010-10-19
forum: New to Ubuntu
---

### Post by Papa.Coen on 2010-10-19
Hi,

I've got an executable text file that starts an application (Java .jar file). Each time I double click it, the system prompts me if I want to run or open it ("..." is an executable text file.).

Is it possible to somehow prevent/disable this prompt and execute this file at once?

Thanks in advance.

---

### Post by coffeecat on 2010-10-19
You could create a launcher. For a launcher on the desktop, right-click on the desktop > Create Launcher. On the panel, right-click > Add to panel > Custom Application Launcher. For somewhere in the main menu, right-click on the main menu > edit menus and add an item. You need to include the full path to the shell script in the command field.

---

### Post by yetiman64 on 2010-10-19
> **Papa.Coen said:**
> Hi,

I've got an executable text file that starts an application (Java .jar file). Each time I double click it, the system prompts me if I want to run or open it ("..." is an executable text file.).

Is it possible to somehow prevent/disable this prompt and execute this file at once?

Thanks in advance.

In any nautilus window, Edit > Preferences > Behaviour Tab, "Executable Text Files" section, click the top option.

Edit: note that this will cause **any** executable text file such as shell scripts to automatically execute (if permissions include execute), which may be undesirable in some instances. Remember whenever you use this option that it is set.

---

