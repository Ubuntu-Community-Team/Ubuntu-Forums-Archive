---
title: "Wordpress problems with Ubuntu"
date: 2009-06-22
forum: New to Ubuntu
---

### Post by Gp. on 2009-06-22
Whenever I make a post on wordpress and I want to upload a photo, it uploads, but there is no image data?
It says it's uploaded, but it doesn't actually upload the data?
When you click to insert the picture into the post, it just shows up as a broken image link)

Ubuntu + Wordpress? Fail.

---

### Post by Christmas on 2009-06-22
Have you tried another browser? Opera or Epiphany maybe (assuming you are using Firefox)

---

### Post by Gp. on 2009-06-24
No I haven't, but Firefox and wordpress was all fine in Windows so why is it any different now if it's still firefox?

---

### Post by kellemes on 2009-06-24
> **Gp. said:**
> Whenever I make a post on wordpress and I want to upload a photo, it uploads, but there is no image data?
It says it's uploaded, but it doesn't actually upload the data?
When you click to insert the picture into the post, it just shows up as a broken image link)

Ubuntu + Wordpress? Fail.

How are you uploading a photo? You're using an extension for this?
Have you checked your webserver's filesize limit?
Have you actually checked if these images are present on the server or not?
Stuff like this often has to do with the permissions of your wordpress-structure, have you double checked? Never hurts to do this ones in a while.

Anyway, this is a Wordpress-specific issue, there community is very active and should be able to provide you the support you need.

---

### Post by Gp. on 2009-06-24
> **kellemes said:**
> How are you uploading a photo? You're using an extension for this?
Have you checked your webserver's filesize limit?
Have you actually checked if these images are present on the server or not?
Stuff like this often has to do with the permissions of your wordpress-structure, have you double checked? Never hurts to do this ones in a while.

Anyway, this is a Wordpress-specific issue, there community is very active and should be able to provide you the support you need.

How are you uploading a photo? You're using an extension for this? Part of wordpresses media uploading system.

Have you checked your webserver's filesize limit? Yes, and irrelevant as it works fine when using windows

Have you actually checked if these images are present on the server or not? Nope, not sure what directory they go to by default

:S

---

### Post by kellemes on 2009-06-25
Maybe I don't understand the situation..
You have setup Wordpress on an Ubuntu based LAMP-server?
When managing WP from a Windows-client all is fine?
But managing from a Ubuntu-client you have this issue?

---

### Post by pyedog on 2010-11-05
Did anyone ever find a solution to this?

I can't figure out what it is that causes the images to fail display in the browser. I've set the permissions manually to 777 but the filenames are green in the terminal and I have no idea what that means.

---

