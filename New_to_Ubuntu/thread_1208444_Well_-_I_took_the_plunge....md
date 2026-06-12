---
title: "Well - I took the plunge..."
date: 2009-07-09
forum: New to Ubuntu
---

### Post by IHeequ5i on 2009-07-09
I installed Jaunty last night on my desktop, overwriting my Fedora install completely. I've also installed all the security updates.

It was painless.

Tonight, I will be playing with sound and video and making sure everything works the way I need it to. I'll also be installing Basket, Wine, Dosbox, and all the other apps I need. 

The only reason I keep Windows XP around is for those games (and a very few applications) that I can't run under Linux or haven't found replacements for.

So - does anyone know of a good HTML editor that will allow me to edit files on my host's server directly the way MS Front Page does?  I've used Seamonkey for editing local files and then upload them with Filezilla - but I'd really like to be able to modify my website "on the fly".

Oh, and one more silly question: I have a couple of old (pre OS X) Macintosh games. Is there anything like Wine around that will let me run old Mac games on Linux?

---

### Post by random turnip on 2009-07-09
For the mac version of Wine thing, sadly not, as far as i know one doesn't exist, you won't find many people saying that mac programs are worth running either, so i guess it'll be a while till one comes out, lol.

Have you considered trying to run front page with wine?
Could work.

---

### Post by demosthene1 on 2009-07-09
For HTML editing I like to use Seamonkey Composer, though I don't use the Seamonkey browser much. Just install Seamonkey from the repos. You might like it. It is an alternative I don't see mentioned very much.

You can set Seamonkey up in prefrences so that it opens with Composer, not the Seamonkey browser.

---

### Post by alexlafreniere on 2009-07-09
I would find out if you're web host allows shell access through SSH, and if so, just tunnel into your server, and open your HTML files with whatever text editor or IDE you prefer by issuing something like:

```
gedit yourFile.html
```

In case you can't tell, I really like gedit, it is a very powerful editor if you throw in enough plugins, and I love it's syntax highlighting.

---

### Post by boblemur on 2009-07-09
id say the easiest thing to do would be to just mount the ftp folder (if your using ftp) inside ubuntu and then edit them as if they were any other files on your computer with the editor your already using.


try this link:
[http://www.compdigitec.com/labs/2008/12/07/mount-a-ftp-share-in-ubuntu-as-a-folder/](http://www.compdigitec.com/labs/2008/12/07/mount-a-ftp-share-in-ubuntu-as-a-folder/)

---

### Post by asmoore82 on 2009-07-09
[SIZE="5"]+1[/SIZE] for using Gnome's VFS "Places -> Connect to Server"

and/or for maximum efficiency ... Grsync!

you could keep a working copy of all of the files locally for editing/testing and only sync them up to the server as needed.

---

