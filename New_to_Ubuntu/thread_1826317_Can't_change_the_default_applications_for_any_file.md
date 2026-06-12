---
title: "Can't change the default applications for any file types"
date: 2011-08-16
forum: New to Ubuntu
---

### Post by zirch on 2011-08-16
Hi, I'm new to Linux/Ubuntu. In fact, I have just been using Ubuntu 11.04 for a few weeks.

I wanted to change the default applications for my media file types but I can't. I used the right-click, properties, open-with method, but when I wanted to select another application on the list, an error pops up saying:

Could not set application as the default: Can't create user application configuration folder /home/chris/.local/share/applications: Not a directory

It's not just for media file types; any other file types, I can't change the default applications too.

I tried to use the File Type Manager in Ubuntu Tweak to change the associations, but it wouldn't change either. I found out that I can change it, and works, when I used root permission, but it's only for root. When I fall back to normal user, it's still the same issue.

If it's of any help, I'm using a Wubi-installed version.

Can anybody please help? Thanks in advance.

---

### Post by zirch on 2011-08-17
I have found the solution! Since the error said that the folder "applications" is not a directory, I went to the destination to check out. It seemed that there is a text file named "applications" there. So, I just removed the text file and created a new folder and named it to "applications".

---

