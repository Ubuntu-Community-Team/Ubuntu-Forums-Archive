---
title: "Theme question/problem"
date: 2009-06-22
forum: New to Ubuntu
---

### Post by Gp. on 2009-06-22
I've got Ubuntu looking how I like it but theres one problem.
How come in places like the update manager and synaptic manager, the progress bar and whatnot does not match the theme. Instead it uses some kind of default, generic looking themeset.

See attachments. The grey stripy one is my theme's style, and the other is what the update manager loading looks like.

---

### Post by Thingymebob on 2009-06-22
Because your running these with sudo, so uses root users theme settings (default)

to make it match, you'd need to theme su's settings the same as your own, I haven't tried but am guessing entering
```
sudo gnome-appearance-properties
```in a terminal would open up the appearance preference dialog as su.

---

### Post by billgoldberg on 2009-06-22
It because your root user doesn't use the themes specified in /home

That is easily fixed by copying those theme files in /home/.icons and /home/.themes to the ones in /root/.icons and /root/.themes

---

### Post by Sealbhach on 2009-06-22
Hi, try this, it should get your theme to look the same in Synaptic:

sudo ln -sf /home/your-user/.themes /root/.themes

Change "your-user" to whatever your username is.

.

---

### Post by billgoldberg on 2009-06-22
> **Sealbhach said:**
> Hi, try this, it should get your theme to look the same in Synaptic:

sudo ln -sf /home/your-user/.themes /root/.themes

Change "your-user" to whatever your username is.

.

Don't forget the icons, sealbhach :p

```
sudo ln -s /home/user/.themes /root/.themes && sudo ln -s /home/user/.icons /root/.icons
```

Change user to your username.

---

### Post by Sealbhach on 2009-06-22
> **billgoldberg said:**
> Don't forget the icons, sealbhach :p

```
sudo ln -s /home/user/.themes /root/.themes && sudo ln -s /home/user/.icons /root/.icons
```Change user to your username.

Oh, yeah, the icons. 

By the way, I got that tip from looking at this weird blog...

[http://linuxowns.wordpress.com/2008/05/13/make-synpatic-package-manager-use-gtk-theme/#comments](http://linuxowns.wordpress.com/2008/05/13/make-synpatic-package-manager-use-gtk-theme/#comments)


.

---

### Post by SunnyRabbiera on 2009-06-22
Yeh this is common as the administration account doesnt use the same files as the main user, even on Ubuntu with the root user disabled there is still administrative stuff there.

---

