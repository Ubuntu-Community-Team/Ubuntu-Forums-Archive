---
title: "Change default theme for all users"
date: 2009-05-06
forum: New to Ubuntu
---

### Post by tablaboi on 2009-05-06
I created a customized theme (metacity, gtk, icon pack changes). How do I make it so that each new user uses this theme by default, rather than the human theme? 

I've already tried putting the theme in etc/skel, but that doesn't set my new theme as the default theme for new users. 

I was thinking that I could possibly use remastersys to create a new livecd, but delete completely the human theme and other themes built into ubuntu so that only my theme is left. 

Any other suggestions?

---

### Post by fiddler616 on 2009-05-06
> **tablaboi said:**
> 
I was thinking that I could possibly use remastersys to create a new livecd, but delete completely the human theme and other themes built into ubuntu so that only my theme is left. 
I'm afraid I don't have a solution for you, but that (remastering a new Live CD) sounds like an incredibly overcomplicated idea, and I do not recommend it.

---

### Post by mick8985 on 2009-05-06
The gnome config files can be put into a folder called /etc/skel, any new user you create will have those files in there home folder.

Hope that helps

---

### Post by mick8985 on 2009-05-06
thought I'd add the folder you want to put in /etc/skel is .gconf
And you should make your installed theme available in /usr/share/themes and icon theme in /usr/share/icons

---

### Post by tablaboi on 2009-05-07
Thanks! - that's exactly what I needed :KS. 

One more question though - how do I set a default gnome panel background for all users. I set mine to be transparent through a png image, and I want that to be there for all users. However, it looks like that gnome panel settings aren't stored in .gconf - any suggestions? I've already tried sabayon but it's crashing way too much on me.

---

### Post by mick8985 on 2009-05-08
I think it's stored in .gtkrc but .gtkrc changes whenever you change your theme.

---

