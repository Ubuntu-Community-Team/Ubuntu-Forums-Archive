---
title: "Wordpress - File tries to download instead of open"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by stratodavius on 2010-05-20
Hello, everyone! I am new to Ubuntu and am running 10.04 on my system.  Because I'm new, I fear this is a silly question but I am stumped so I thought I would ask away.

I downloaded Wordpress (along with lamp-server) and set it up making sure every step works from this [how-to reference]("https://help.ubuntu.com/community/WordPress"). I've done everything according to plan and the Web files are located at /var/www/wordpress.

However, when I call up [http://localhost/wordpress](http://localhost/wordpress), both my Web browsers (Firefox and Chromium) download a file instead of calling it.  When I open the downloaded file, it opens gedit with the syntax of the file.  I just want to start the Wordpress config and install.  What gives?

Hopefully this is a Ubuntu issue (stupid user issue) and not a Wordpress issue and I'm posting this in the right place.

This is my first time posting, so I hope this makes sense.  Thanks in advance for any help!

---

### Post by Nythain on 2010-05-20
i would suggest going over some of the steps concerning apache2 part of howto forge's excellent "Perfect Server" guide.

it sounds like either your DirectoryIndex line isnt set right or your mime.types are off.

[http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-2-p6](http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-2-p6)

but icould be entirely wrong here

---

### Post by stratodavius on 2010-05-20
Thanks for the quick response!  I made changes as suggested but am not having luck.  Any other ideas?

---

