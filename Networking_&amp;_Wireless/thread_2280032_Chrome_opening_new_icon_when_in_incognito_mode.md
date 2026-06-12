---
title: "Chrome opening new icon when in incognito mode"
date: 2015-05-27
forum: Networking &amp; Wireless
---

### Post by ericschopper on 2015-05-27
Hi all,

Chrome is working just fine in Ubuntu except for one thing, when I start an incognito window, it opens a new icon in the task bar. Is there any way I can fix this? I am running Ubuntu 14.04 on a Lenovo n500. Thanks for the help:)

---

### Post by ajgreeny on 2015-05-27
I believe that is the way that it is supposed to work; it is certainly so in chromium on Xubuntu 14.04 , and as Chrome is based on chromium it seems likely that you are getting what you should get when you start a new incognito window.

The item in the menu hamburger button actually says "Open a new incognito [COLOR=#ff0000]window[/COLOR]" and that's exactly what it does, rather than just opening a new tab.  That's why you get another window button in some DEs, though I did not think there were any window buttons in unity, so tell us which DE you're using.

---

### Post by kerry_s on 2015-05-27
> **ericschopper said:**
> Hi all,

Chrome is working just fine in Ubuntu except for one thing, when I start an incognito window, it opens a new icon in the task bar. Is there any way I can fix this? I am running Ubuntu 14.04 on a Lenovo n500. Thanks for the help:)

chrome does that in most docks, you have to do the fix.

open the menu editor(main menu) click on internet than chrome

remove "-stable" from the execute line
do the same thing under actions

or

you can copy chrome from /usr/share/applications to ~/.local/share/applications
then edit it with your text editor.

~/.local/share/applications is a hidden directory, press ctrl+h in your home folder to show hidden.

---

### Post by ericschopper on 2015-05-27
chrome does that in most docks, you have to do the fix.

open the menu editor(main menu) click on internet than chrome

remove "-stable" from the execute line
do the same thing under actions

or

you can copy chrome from /usr/share/applications to ~/.local/share/applications
then edit it with your text editor.

~/.local/share/applications is a hidden directory, press ctrl+h in your home folder to show hidden.


Ok thanks for he help, I did what you said in the text editor and now it is fine. Also, chrome works well in docky, so I will probably be using it from now on.


Thanks-eric

---

### Post by kerry_s on 2015-05-28
> Ok thanks for he help, I did what you said in the text editor and now it is fine. Also, chrome works well in docky, so I will probably be using it from now on.


Thanks-eric

i use plank, plank is now included in the 15.04 repo. i'm using ubuntu-mate 15.04.
[https://ubuntu-mate.org/about/](https://ubuntu-mate.org/about/)

---

