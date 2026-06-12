---
title: "Help with a webhosting server"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by ZJ88 on 2009-11-15
I am a real newbie when it comes to servers. My teacher is letting me borrow her ubuntu server to put up a website for the rest of the year. The problem is I have no idea what I am doing! She has created a user account for me and in my home files there is public_html. SO I figured I should put my index and everything else in there right? but now how do I broadcast that on the web? I am also trying to buy a domain name for it but I have no idea on how to link my server with the domain name or how to do anything. All I can find on the web is a lot of technical jargon on editing the actual server code and installing apache2. All of that should be in place already. Can somebody please help me?

Sorry if this is a double post, I didn't see this forum until after I posted the first one :/

---

### Post by mörgæs on 2009-11-15
If you upload a test file called index.html in the directory public_html, you should be able to see it by typing [http://path_your_teacher_provided/~your_username/](http://path_your_teacher_provided/~your_username/) in the browser. 'Public_html' should not be typed. 

You can not take for granted that an HTML page can be seen on the internet. I guess that you are at school, and then most likely the page is only visible on the intranet.

If you buy a domain, the hosting company will provide their own folder called public_html for you. Use this for everything you want to make visible on the internet. I recommend picking a web host that uses Apache.

---

