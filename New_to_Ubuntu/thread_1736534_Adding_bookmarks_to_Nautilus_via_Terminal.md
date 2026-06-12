---
title: "Adding bookmarks to Nautilus via Terminal"
date: 2011-04-22
forum: New to Ubuntu
---

### Post by mkhaytman on 2011-04-22
Hi guys, first off let me thank everyone who develops and posts here. This site has been an invaluable resource in the few weeks that I've been using linux so far. :P

Now to the topic at hand: I've searched pretty extensively and have not found instructions on how to do this (probably because it was way easier through the GUI), but I need to add a bookmark/shortcut to Nautilus using command line ([Here's an example of what I'm talking about, in case I'm not being clear]("http://imgur.com/zQWNe")). 

I'm running 10.04.2, and in case you are wondering why I don't just do it through GNOME, it's because I am trying to set up a bash script to automate a new install as much as possible, as I will be installing linux on dozens of computers at work in the near future.

Thanks in advance for your help![IMG]http://imgur.com/zQWNe[/IMG][IMG]http://imgur.com/zQWNe[/IMG]

---

### Post by doas777 on 2011-04-22
bookmarks are stored in the file ~/.gtk-bookmarks in 
'file:///<Path/to/file/or/folder> <BookmarkName>' format.
here is mine:
```

User@Lucid:~$ cat ~/.gtk-bookmarks
file:///home/User/Documents
file:///home/User/Downloads
file:///home/User/Comics Comics

```

---

### Post by mkhaytman on 2011-04-22
Exactly what I was looking for, thanks!

---

### Post by mkhaytman on 2011-04-28
Adding a quick note in case anyone else has this issue in the future. 
I was having trouble getting the bookmarks with spaces in the file directory to work properly. Even using \ to escape the space, the file would use that space as the divider between the file name and the bookmark name. This would create broken links as the part of the directory after the space was instead part of the bookmark name. 
To solve this I had to use "%20" instead of "\ " to indicate a space in the file directory. Works like a charm now.

---

### Post by oldfred on 2011-04-28
I have two scripts I run. One to update mounts & links and another to install apps. I have desktop & laptop and often reinstall Ubuntu alpha, beta  etc, so I want to make it as easy as possible. So I look for anything that may apply even if I do not use it immediately. So one more note in my update script. Thanks.

---

