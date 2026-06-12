---
title: "switch user list to username field"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by tocleora on 2010-07-12
Is there a way to switch from the user list to a username field?

I'm sure this question has been asked before, I did do a search but I didn't find anything specifically related to this so sorry if I missed an important sticky or something.  Thanks in advance!

---

### Post by Penguin Guy on 2010-07-12
I think you're going to have to be a bit more specific.

---

### Post by tocleora on 2010-07-12
Ok in the latest version you have a list of usernames, you select the username it prompts you for a password. Similar to this:

[img]http://effiejayx.files.wordpress.com/2009/10/ubuntu-10-04-karmic-koala-login-screen.jpg[/img]

What I want is for it to be just the username text box again, like this:

[img]http://i39.tinypic.com/6hhis1.jpg[/img]

That doable?

---

### Post by JustinR on 2010-07-12
Hi!

Hit ALT + F2 and type "gconf-editor".

In gconf-editor click Apps > gdm> Simple-greeter

Right click the key that says "disable_user_list" and click "Set as Mandatory".

Restart your computer and the user list should be gone.

---

### Post by sisco311 on 2010-07-12
You have to change the value of the key as user gdm.

Disable the list: 
```
sudo -u gdm gconftool-2 --set --type boolean /apps/gdm/simple-greeter/disable_user_list true
```

Enable the list: 
```
sudo -u gdm gconftool-2 --set --type boolean /apps/gdm/simple-greeter/disable_user_list false
```

---

### Post by tocleora on 2010-07-12
Great, thanks so much!

---

