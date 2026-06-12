---
title: "[SOLVED] Permissions denied in folders I wish to write"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by inirini on 2008-12-06
I am trying to set up a webserver, and in folders like /etc/apache2/, /var/www/ and other similar folders. I can access to them and edit folders via sudo -1 and become root that way. But I wish to grant permissions to those folders without going into terminal (as it did not save my work when I tried playing around with the index.html in /var/www. I also have checked some of the tags like 'permission denied' and they have no answers to the problem.

I also tried right clicking on /var/www/ and clicked on the permissions tab, and I need to become root in order to change the permissions. How would I go about doing that in terminal?

Thanks for the help in advance!

Tiffy

---

### Post by MockY on 2008-12-06
Type this in terminal:

```
sudo chmod 777 /var/www/
```

And you will not be bothered again with permissions. However, this is not recommended on a production server.

---

### Post by inirini on 2008-12-06
Thank you, but what do you mean by production server? It sounds like to be used for business. I am using the server for personal use only, so I won't be sharing any of the links or IPs to other people or online. :] 

But, as a precaution, what is the command for setting the permissions back on?

---

### Post by MockY on 2008-12-06
What I meant by production server is if you have your server publicly available. But since you intent to use if for personal use only then it might not matter as much. However, using 777 as a habit is a bad idea.
I do think that chmod 555 will set back the permission as they were before, though I am not 100% sure about that.

Take a look **[here]("http://en.wikipedia.org/wiki/Chmod#Examples")** for more permission examples.

---

