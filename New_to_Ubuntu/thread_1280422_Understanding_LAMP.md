---
title: "Understanding LAMP"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by mortalapeman on 2009-10-02
Hi, i'm new to linux and have been intrigued by all the opensource stuff that is out there. I had no idea. I am currently interested in web development, but i am not looking to use my CPU as a server. I only want to develope a website using AMP and whatever text editor, i have a book with tutorials and such, but i can't figure out how to start. I have all 3 applications downloaded with both my PHP5 working and apache working. I have not configured the bin address in the apache config file and i ahve done nothing to MySQL since i can't seem to find a consistent help article on how to configure everything.

My question is, where do i go from here? Is there a good article i've been missing? I don't know how to save php files in thee www folder without using the terminal, and that's the only way i've been able to figure out how to display whatever php i've written. I feel like there is probably a better way xD

Any comments or help would be appreciated.

---

### Post by ad_267 on 2009-10-02
To answer your question about saving in /var/www, the easiest way I found was just to create a folder for web development in my home directory and then create a symbolic link to that from /var/www.

eg:
```
mkdir ~/webdev
sudo ln -s ~/webdev /var/www/dev
```

Then you can go to [http://localhost/dev](http://localhost/dev) to see your stuff, and easily edit files from your home directory. There are other ways, but that's the easiest way I know.

As for where to start, I started by playing around with some basic content management systems. [SNews]("http://snewscms.com/") was pretty easy to understand and change stuff in. If you play around with that for a bit you should be able to figure out how to make your own stuff. Other than that just use google to find some php+MySQL tutorials.

---

### Post by lovinglinux on 2009-10-02
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

