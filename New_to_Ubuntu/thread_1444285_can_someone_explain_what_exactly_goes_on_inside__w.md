---
title: "can someone explain what exactly goes on inside  when we double click a file?"
date: 2010-04-01
forum: New to Ubuntu
---

### Post by justutkarsh on 2010-04-01
who forks the associated application with the file.

---

### Post by Diabolis on 2010-04-27
Programming languages do system calls when they want to open a file. The operating system has control over all the processes that are running, but a particular program has control over any files It has opened.

File access is just memory access. By opening a file, a region of memory is assigned temporarily to be read or write by a running process.

---

### Post by ubunterooster on 2010-04-27
> **justutkarsh said:**
> who forks the associated application with the file.
the OS looks at the extension and uses the program set to open that extension by default.
Example: Files with .odt extensions are set to open with Open Office.

I use the [Ubuntu Tweak]("http://ubuntu-tweak.com/") tool to see all the types at once and what opens them.

---

