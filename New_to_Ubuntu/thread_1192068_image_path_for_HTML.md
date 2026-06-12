---
title: "image path for HTML"
date: 2009-06-19
forum: New to Ubuntu
---

### Post by wgregory1227 on 2009-06-19
I am modifying the index.html without issue, but when i try to place an image source; <img src=""> I am not sure what the proper path to my pictures is. I have tried /home/ME/Pictures/IMGNAME.jpg and no go. I used an URL from some page and it worked like a charm so i am left to beleive my path is wrong.

---

### Post by Lord Noxarethor on 2009-06-19
Do you have a local webserver? What do you use? LAMP (XAMPP)?

---

### Post by Joeb454 on 2009-06-19
Where are your pictures located on the system?

Note that both the image, and index.html page need to be on the same system, else it won't find the pictures :) (sounds stupid, but I've caught myself doing it before)

---

### Post by Tibuda on 2009-06-19
Use relative paths. If the image is on the same folder as the html, use <img src="image.png"/>. If it is in a subfolder use <img src="subfolder/image.png"/>. If it is under the website root (/var/www if you are using Apache or Lighttpd), use <img src="/image.png"/>.

---

### Post by jonobr on 2009-06-19
Hello


w3 schools have some really good, slow paced tutorials with great examples that are easy to follow

You should take a lot at that while your working on html

[Here]("http://w3schools.com/html/default.asp") is the HTML section.
theres a lot more really good stuff in there

---

### Post by wgregory1227 on 2009-06-22
You guys are awsome!!! I cant place the file with the same container that the Index.html is in. No permission do save within that directory. I tried going through the terminal to copy and past it using sudo, but i must not be doing something right. It is in my pictures folder. I have installed the LAMP and also GNOME since I am a Linux virgin!

---

### Post by mcduck on 2009-06-22
> **wgregory1227 said:**
> You guys are awsome!!! I cant place the file with the same container that the Index.html is in. No permission do save within that directory. I tried going through the terminal to copy and past it using sudo, but i must not be doing something right. It is in my pictures folder. I have installed the LAMP and also GNOME since I am a Linux virgin!

You'll probably want to do this with graphical tool instead, running "gksudo nautilus" in a terminal will open the file manager as root, allowing you to move the file into /var/www.

But since you are just learning, you might want to have the WWW files in your home instead, making accessing them easier and to avoid needing root permissions to change anything. There are many ways to do this, but the easiest is to simply create a new directory in your home, and then symlink it inside /var/www. (The correct way would be creating the directory, and then creating a new site configuration file in apache's configs, and using a2ensite-command to enable the site. Or enabling apache's userdirs to add personal www directories for every user of the system).

---

### Post by wgregory1227 on 2009-06-22
I was able to achieve what i needed by simply using, 
sudo -s -H (to hold me in root)
cp /file directory /directory destination. 
Thanks again Ubuntu friends!!

---

