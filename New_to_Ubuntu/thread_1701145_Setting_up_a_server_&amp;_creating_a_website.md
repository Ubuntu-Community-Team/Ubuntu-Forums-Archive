---
title: "Setting up a server &amp; creating a website"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by Dutch70 on 2011-03-06
Hi all, 

 I am creating a website using KompoZer & I'd like to set up a server, which I know absolutely nothing about. I just want to use it to test the website & let a friend be able to access it. Until I put it on a server such as godaddy I've read a lot about it, but don't quite understand. There are too many diff types of servers and ways to set them up. 

Can anyone tell me what kind of server I need to set up & possibly give me some good links or tutorials. I'm just not sure where to start.

Thank you in advance
Dave

---

### Post by maqtanim on 2011-03-06
Sounds like you need a LAMP server. The following link may be help you
[http://www.unixmen.com/linux-distributions/4-ubuntu/1239-install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat](http://www.unixmen.com/linux-distributions/4-ubuntu/1239-install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat)

---

### Post by dionysius on 2011-03-06
Is your site in HTML, PHP, XML, or a combination? 

I ask because if your website is written in PHP, you'd need a LAMPP stack to test your website locally. HTML only requires a browser to check whether it's all done correctly. 

[Apache Friends - LAMPP]("http://www.apachefriends.org/en/xampp.html") - local LAMPP stack install made easy

For what you're trying to do I'd recommend one of the ad-free free webhosts out there. There's [000webhost.com]("http://000webhost.com"), [x10hosting.com]("http://x10hosting.com"), [byethost.com]("http://byethost.com") - most of them give you enough space and bandwidth for average-traffic websites, and come with a range of features. Unless you intend to run an ecommerce site or some other kind of resource hungry website these providers should be more than sufficient for your needs. 

> **maqtanim said:**
> Sounds like you need a LAMP server. The following link may be help you
[http://www.unixmen.com/linux-distributions/4-ubuntu/1239-install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat](http://www.unixmen.com/linux-distributions/4-ubuntu/1239-install-lamp-with-1-command-in-ubuntu-1010-maverick-meerkat)

Though it's perfectly possible to run web services on your own machine, I'm not sure whether the benefits outweigh the risks in this case.

---

### Post by Dutch70 on 2011-03-07
Thanks for all the info Maqtanim & dionysius. 

 It's HTML only I believe. That's part of it I'm not exactly sure what the differences are, or what I should use. I'm going to check out the info you both gave me very carefully before I mark this thread solved. So far I'm leaning toward the sites dionysius gave. 

Thanks again!!! :)

---

### Post by dionysius on 2011-03-07
PHP is intended for dynamic content, and looks like this: 
```
if ( !comments_open($comment_post_ID) ) {
	do_action('comment_closed', $comment_post_ID);
	wp_die( __('Sorry, comments are closed for this item.') );
} elseif ( 'trash' == $status ) {
	do_action('comment_on_trash', $comment_post_ID);
	exit;
} elseif ( !$status_obj->public && !$status_obj->private ) {
	do_action('comment_on_draft', $comment_post_ID);
	exit;
} elseif ( post_password_required($comment_post_ID) ) {
	do_action('comment_on_password_protected', $comment_post_ID);
	exit;
} else {
	do_action('pre_comment_on_post', $comment_post_ID);
}
```

PHP processes variables and user input, is able to make use of databases (MySQL for example) and then presents the output in HTML, displayed in the visitor's browser. 

HTML on the other hand is intended solely for static content: if your page says 
```
<span class="nocomment">Sorry, there are no comments on this item</span>
```
that's what will be displayed in the visitor's browser, regardless of whether you have a database full of comments. 

In other words, PHP is a dynamic language, and HTML a static one. 

If you've made it with Kompozer it's most likely it will be written in HTML. In that case you may want to have a look at seperating content from mark-up, by using CSS. 

Some information:

[CSS3]("http://www.css3.info/") - up to date info on developments in CSS
[Tuxradar's Practical PHP]("http://www.tuxradar.com/practicalphp") - information on PHP, guides, tutorials
[HTML Goodies]("http://www.htmlgoodies.com/") - great website to get familiar with HTML, includes guides and tutorials.

---

### Post by Taamalus on 2011-03-07
> **dionysius said:**
> Is your site in HTML, PHP, XML, or a combination? 
[Apache Friends - LAMPP]("http://www.apachefriends.org/en/xampp.html") - local LAMPP stack install made easy
Sorry to butt-in - I'm new here (and to to Linux) and this post is another key suggestion for myself. I just installed that on my Windows7, excellent, thank you very much. :D

---

### Post by Dutch70 on 2011-03-15
Well, I actually ended up installing LAMP. Still trying to figure it out though. Apparently I have much to learn. 

Thanks everyone for your help and advice. :D

---

