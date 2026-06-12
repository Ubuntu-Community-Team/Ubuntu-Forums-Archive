---
title: "www-data, what is it?  And is it causing ruby on rails to not work?"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by illDogg on 2009-06-23
K so I'm trying to set up a ruby on rails environment.

I followed the instructions on this page:
[http://www.hackido.com/2009/04/install-ruby-rails-on-ubuntu-904-jaunty.html](http://www.hackido.com/2009/04/install-ruby-rails-on-ubuntu-904-jaunty.html)

I just got ubuntu 9.04 last night so I got a lot of stuff set up.

Anyway ruby seems to basically work and all that except when I try to view pages on the localhost server.  It shows the ruby on rails home page but whatever link I press or when I try to view pages I wrote it says We're sorry but something went wrong.

I feel like I followed all the instructions correctly on the instructions except I wasn't sure what I was doing with the chown www-data thing.  I get what chown does but I'm not sure what www-data is.  Is it a folder I have to create somewhere or is it like some abstract thing of some sort where all data goes through?  I ran that command to do chown

```
sudo chown -R www-data:www-data /var/www/myapp/current/
```and I get no errors but I have no clue what's going on here and whether or not this is what's preventing ruby on rails from working.  I've looked everywhere and no one explains what www-data is.  I can't find it anywhere on disk if it's a folder.

---

### Post by OffAxis on 2009-06-23
in the chown statement all that's it's doing is changing the folder and it's subfolders to be owned by the www-data user and www-data group.

chown = change ownership
-R = Recursively (this folder and it's sub-folders)
www-data:www-data = user:group

did you check the error log for nginx ?
/opt/nginx/logs/

---

