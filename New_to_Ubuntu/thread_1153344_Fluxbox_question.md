---
title: "Fluxbox question"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by zigmo on 2009-05-08
I installed fluxbox via synaptic package manager in KDE and restarted in a fluxbox session.
So far, so good.
The right-click menu seemed to give me access to whatever I needed (so far).
At some point, I clicked on an image via Nautilus and it became my desktop image. Ever since then, the right-click menu now shows:

[INDENT]create folder ...
create launcher ...
create document >
clean up by name
keep aligned
paste (grayed out)
change desktop background[/INDENT]

1) What did I do?
2) How can I revert?
3) What's a good link for general fluxbox info/tutorials?

Thanks.

---

### Post by Pjotrovitz on 2009-05-08
The problem is that nautilus has taken control of your desktop. You can start it with the --no-desktop option to prevent this. There is also a setting in gconf-editor you can use (search for show_desktop in gconf-editor)

---

### Post by Pjotrovitz on 2009-05-08
..oh, and [http://www.fluxbox.org/](http://www.fluxbox.org/) is good for info.

---

### Post by bodhi.zazen on 2009-05-08
I put a bunch of fluxbox how to's here :

[http://community.fluxbuntu.org/index.php?&board=18.0](http://community.fluxbuntu.org/index.php?&board=18.0)

---

### Post by zigmo on 2009-05-08
Thanks for the suggestions, links and info. This post refers to one of my work computers.
At home, I'm running Xubuntu and just loaded fluxbox. I got it to run, but it doesn't sense my wifi card. I'm going to check out the sites you posted and see if I can figure out why.

---

### Post by kansasnoob on 2009-05-08
> **bodhi.zazen said:**
> I put a bunch of fluxbox how to's here :

[http://community.fluxbuntu.org/index.php?&board=18.0](http://community.fluxbuntu.org/index.php?&board=18.0)

That's awesome!

I was going to add that Mint's treatment of Fluxbox is the best I've seen recently if someone just wants a simple desktop to surf and mail:

[http://www.linuxmint.com/blog/?p=724](http://www.linuxmint.com/blog/?p=724)

---

### Post by bodhi.zazen on 2009-05-08
> **kansasnoob said:**
> That's awesome!

I was going to add that Mint's treatment of Fluxbox is the best I've seen recently if someone just wants a simple desktop to surf and mail:

[http://www.linuxmint.com/blog/?p=724](http://www.linuxmint.com/blog/?p=724)

Best I have seen hands down is March :

[http://marchlinux.wikidot.com/](http://marchlinux.wikidot.com/)

[[IMG]http://marchlinux.wdfiles.com/local--resized-images/screenshots/screen0-2.jpg/thumbnail.jpg[/IMG]]("http://marchlinux.wdfiles.com/local--files/screenshots/screen0-2.jpg")

<click image for larger view>

---

### Post by zigmo on 2009-05-10
So, I got wifi to work by adding ```
nm-applet &
``` to my fluxbox config.
Thanks for the all the other suggestions.
March Linux appears to be an entirely different distro from ubuntu - yes?
Mint is just a fluxbox gui for xubuntu - why does it require an entire installer CD? When I originally installed fluxbox, I just loaded it and set it as my session.

---

