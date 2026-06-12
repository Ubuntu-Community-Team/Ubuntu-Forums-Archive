---
title: "ubuntu server 8.10 apache 2.2"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by stonerrob420 on 2009-02-13
Hello! I installed ubuntu server 8.10 then installed ubuntu desktop that way I would have a GUI. everything works good except the apache 2.2 server. I cant unlock the /var/www file to be able to edit the index.html to make the webpage. I also cant put anything into the directory. Any help would be much appreciated.:P

---

### Post by jenkinbr on 2009-02-13
Are you simply trying to copy content to that folder as yourself in nautilus, or are you doing it as root?  Apache, by default, is set up to access files as user 'www' in the group 'www', and your user account doesn't have write permission to that directory by default.

Try running the command ```
gksudo gedit /var/www/index.html
``` and see if you can save changes.

---

### Post by stonerrob420 on 2009-02-13
The code works but what about adding content like gifs and jpegs and such....How do I copy the images to that directory? I've already got a html page written for it but cant copy the images to the folder. Any help would be much appreciated.

---

### Post by theozzlives on 2009-02-13
```
sudo cp origin destination
```

for example test.jpg

```
sudo mkdir /var/www/images
```
```
sudo cp ./test.jpg /var/www/images/
```

---

### Post by mrbiggbrain on 2009-02-13
```
sudo usermod -g www yourusername
``` then youll have full rights to do this with the current user, anytime. remember however anyone using that name will also


EDIT: forgot my sudo

---

### Post by stonerrob420 on 2009-02-13
when I use that code "sudo usermod -g www yourusername" then is gives me this error "usermod: unknown group www". wonder how I overcome this? I am totally lost in how do it. but I did get the apache setup where I could host own my own IP.

---

### Post by raptor2552 on 2009-02-14
the user is www-data not www

---

### Post by stonerrob420 on 2009-02-14
I found a solution to this problem using the gksudo nautilus command. It seems that there has been changes in the ubuntu shell since the last edition. I was able to copy all the files to the directory and now my webpage is up and running. Thanks to everybody for the help I much appreciate it everything. I love this forum....people here are so cool.:P

---

