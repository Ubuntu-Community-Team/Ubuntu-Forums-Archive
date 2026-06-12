---
title: "Web Server File Security"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by jkurtisr32 on 2010-08-11
My first post. Ever:

I'm building a web server to host a site from which people can download files.

[1] I've heard that having a server with [X] running can lead to security issues, so I'm not sure if I want to go with GNOME or not for the server.

[2] I was thinking of keeping the site running on my web server and keeping the available files for the website on my personal PC/server (on the same local network). I want to keep my personal files separate from the site files for security purposes, so would it be a security risk to have the web server pull from my PC/server?

[3] The alternative to the above setup, would be to simply host the website on my PC/server. Would this be less secure than the method outlined in [2]?

All input is appreciated.


Thanks,

Kurt

---

### Post by sandyd on 2010-08-11
> **jkurtisr32 said:**
> My first post. Ever:

I'm building a web server to host a site from which people can download files.

[1] I've heard that having a server with [X] running can lead to security issues, so I'm not sure if I want to go with GNOME or not for the server.
**Yeah, it is, run it without X. However, if you want, you can firewall the ports so that only port 80 is allowed (with the exclusion of some other ports you may need)**

[2] I was thinking of keeping the site running on my web server and keeping the available files for the website on my personal PC/server (on the same local network). I want to keep my personal files separate from the site files for security purposes, so would it be a security risk to have the web server pull from my PC/server?

[3] The alternative to the above setup, would be to simply host the website on my PC/server. Would this be less secure than the method outlined in [2]?
**Host it in a chroot Jail setup**.

All input is appreciated.


Thanks,

Kurt
.

---

### Post by Bachstelze on 2010-08-11
Methinks that you're worrying about security way too much.  You probably don't need entrprise-class security just to share a few files with some people.  Installing Apache on your desktop and putting your files in /var/www will be enough.

---

### Post by jkurtisr32 on 2010-08-12
> **Host it in a chroot Jail setup**.
This is some very cool stuff that I'd never come across before. Thanks a lot.

Thanks to both of you for sending me in the right direction. I'm definitely going to do some more research.

---

### Post by MrWES on 2010-08-12
You might consider installing denyhosts. I have it running on my server.

[http://ubuntuforums.org/showthread.php?t=450853]("http://ubuntuforums.org/showthread.php?t=450853")

Bill

---

