---
title: "pdf support on chromium"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by hellomoto on 2011-02-27
Hi guys,

I am trying to get pdf support on chromium, (latest release via daily build PPA). Whenever I try to open a pdf I just get "missing plugin". I have tried the extension for viewing pdfs in google docs but it doesn't always open them, and its slow.


I also tried mozpluggin but I couldn't get it to work. 

In firefox I use the adobe plugin but this is the only reason i still have it.  

Is their any other way?

---

### Post by hellomoto on 2011-02-27
Sorry, I thought I had read up on this enough but  i hadn't.

The way to solve this issue is:

install acroread
install mozplugger

edit (as root) /etc/mozpluggerrc


Change the line which reads
```

	define(ACROREAD, [repeat swallow(acroread) fill : acroread -openInNewWindow /a "$fragment" "$file"])

```
to be 
```

	define(ACROREAD, [repeat needs_xembed swallow(acroread) fill : acroread -openInNewWindow /a "$fragment" "$file"])

```

I then tested an embedded pdf and it loaded the plugin.
However the "find" search tool does not work. 
If their is the option to save the pdf, you can then search 
with a pdf reader like evince.

SOURCE: 
[http://www.google.com/support/forum/p/Chrome/thread?tid=543f0c80bace6c42&hl=en]("http://www.google.com/support/forum/p/Chrome/thread?tid=543f0c80bace6c42&hl=en")

---

### Post by smoosh on 2011-03-09
Thank you!! Works perfect for me. An easier way to search is to click the carrot to the right of the non-working search field, and select "Open full reader search." This opens a separate window that you can search through, and it shows the results of the search right in the browser. That way you don't have to download more stuff to clutter up your computer...

Thanks again!

smoosh

---

