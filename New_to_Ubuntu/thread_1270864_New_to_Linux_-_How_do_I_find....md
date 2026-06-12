---
title: "New to Linux - How do I find..."
date: 2009-09-20
forum: New to Ubuntu
---

### Post by bobsummer45 on 2009-09-20
New to Linux - How do I find a file or a name inside a file.
I know its something with grep but I am not really sure.
Please someone help.

Thanks

---

### Post by mapes12 on 2009-09-20
Hi

I would go Places>Search for files

There are probably other ways to find stuff..............

---

### Post by badger_fruit on 2009-09-20
> **bobsummer45 said:**
> New to Linux - How do I find a file or a name inside a file.
I know its something with grep but I am not really sure.
Please someone help.

Thanks


if you insist on using the terminal, the man pages are usually VERY good places to start; eg "man grep"

Grep (if I recall correctly) allows you to filter the outputs of things such as system commands or the contents of files

```
tail -f /var/log/messages | grep usb
```

or

```
more /path/file | grep sausages
```

would tail the [FONT=Courier New]/var/log/messages[/FONT] file and update automatically but only display the line if something with the phrase "[FONT=Courier New]usb[/FONT]" is found within - or - example 2 will display the[FONT=Courier New] /path/file[/FONT] using "[FONT=Courier New]more[/FONT]" and only show lines with the phrase "[FONT=Courier New]sausages[/FONT]" in.

"find" will find files, use [FONT=Courier New]man find[/FONT] or google "man find" will produce countless pages, here's one I found
[http://unixhelp.ed.ac.uk/CGI/man-cgi?find](http://unixhelp.ed.ac.uk/CGI/man-cgi?find)

Another good resource is [http://www.manpagez.com/](http://www.manpagez.com/)

---

### Post by konqueror7 on 2009-09-20
search a file via,
```
locate <filename>
```
and search a name in a file,
```
cat <filename> | grep <keyword>
```

my above suggestion are based on what i understand from your post, hope it helps!

---

