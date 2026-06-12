---
title: "[SOLVED] download all images in a web page"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by sazan on 2008-12-08
can anyone tell me how i can download all the imgaes that are present in a web page.. 
is there any firefox addon for this ...???

---

### Post by tbroderick on 2008-12-08
DownThemAll! extension will do it.

[https://addons.mozilla.org/en-US/firefox/addon/201](https://addons.mozilla.org/en-US/firefox/addon/201)

---

### Post by adobrakic on 2008-12-08
I just used to save the webpage as a file on my desktop, and it saved all of the images like that.

Then just delete everything else.

But if DTA works fine, then use that. :D

---

### Post by sazan on 2008-12-08
saving a page is a gud idea, but i hav to save lot of images from lot many sites, so i dont want any html files alongwith.. only d images.. 

i added DTA, but still not able to use it properly for my purpose.. 
can you tell me how i can configure it to download all the images directly to a folder.. ?


thanks in advance

---

### Post by glotz on 2008-12-08
Might be of interest [http://www.squarefree.com/pornzilla/](http://www.squarefree.com/pornzilla/) and for single images [https://addons.mozilla.org/en-US/firefox/addon/614](https://addons.mozilla.org/en-US/firefox/addon/614)

---

### Post by sazan on 2008-12-08
i dont want a single image in a folder but all the images in a web site...

anyone .... !!!!!!!!!!

---

### Post by kpkeerthi on 2008-12-08
```

wget -r -A gif,jpg,png http://www.myfavoritewebsite.com

```

man [wget]("http://linux.die.net/man/1/wget")
Add -l <depth>, -l 10 will fetch images 10 level deep. Default is 5.

---

### Post by sazan on 2008-12-08
problem solved.. DTA was very helpful.. cud download all images in my folder.. thank you everyone for your support.. 

:guitar:

---

### Post by Dedoimedo on 2008-12-08
Hello,

ScrapBook is also very handy. Allows you to choose the depth of links to follow for downloads.

[https://addons.mozilla.org/en-US/firefox/addon/427](https://addons.mozilla.org/en-US/firefox/addon/427)

Dedoimedo

---

