---
title: "wget woes no images while mirroring a website"
date: 2010-03-15
forum: New to Ubuntu
---

### Post by jernord on 2010-03-15
Hi,
Ive been trying to download a website for offline browsing. The site is dynamic so I am using Wget. Based on other posts I have used this command:

wget -r -p -l 2 [http://website.com]("http://website.com/")

This command downloads the site, renames the php and other files to html and basically seems to do everything I need except download the image files. There are links to the online images in the pages that Wget stores, but Im hoping it can be coaxed to download the images as well. 

Any suggestions would be welcome.



[]("http://website.com/")

---

### Post by andrewc6l on 2010-03-16
It could be that the website has a robots.txt that blocks images from being transferred. wget has a way around it, but it's usually considered poor form to use it on an unsuspecting server:
[http://www.gnu.org/software/wget/manual/wget.html#Robot-Exclusion](http://www.gnu.org/software/wget/manual/wget.html#Robot-Exclusion)

---

