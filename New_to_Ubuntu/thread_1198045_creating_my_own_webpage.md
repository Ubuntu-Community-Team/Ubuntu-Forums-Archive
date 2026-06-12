---
title: "creating my own webpage"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by thomz92 on 2009-06-26
is it true that i can make my own webpage for free? i was reading (skimming) Linux: The Complete Reference and it said something about apache web servers, etc etc, but i only understood the part where it said that i could make my system into a fully functional website :) so...im wondering, how?? (in simple terms, plz)

by the way, idk if this helps any but there is no /var/www/html directory on my computer

---

### Post by cariboo on 2009-06-26
You have to install apache and associated apps, there are not installed by default. IF you would like to install Apache2, Mysql, Php5, go to System-->Administration-->Synaptic Package Manager-->Edit-->Mark Packages by Task, and select the LAMP server from the menu.

---

### Post by Papa-san on 2009-06-26
What would you suggest as being the minimum system resources for doing something like this?

---

### Post by theozzlives on 2009-06-27
> **thomz92 said:**
> is it true that i can make my own webpage for free? i was reading (skimming) Linux: The Complete Reference and it said something about apache web servers, etc etc, but i only understood the part where it said that i could make my system into a fully functional website :) so...im wondering, how?? (in simple terms, plz)

by the way, idk if this helps any but there is no /var/www/html directory on my computer

Depends, you may have to pay your ISP for a static IP, and a registrar for a domain name (if you want one).

---

### Post by Papa-san on 2009-06-27
Very true! If your IP changes, nobody will be able to find your site until all the links are updated. However, like with my cable account, my 'variable IP' has been the same for 8 years now...

---

### Post by rushikesh988 on 2009-06-27
I got a easy way to do this, just crate the webpages cointaining the link having targets in file trasfer protocol

 

that will open the home directory in browser


and yes  I have that book too ...

---

### Post by mgranet on 2009-06-27
> **Papa-san said:**
> What would you suggest as being the minimum system resources for doing something like this?

Depends on what you plan on doing with it. If you plan on putting up something more substantial than spider food, it will need to be a multi-core system with lots of ram.

---

### Post by Papa-san on 2009-06-27
Thanks...
I guess I just need to just be spider-bait for now! lol

---

### Post by rushikesh988 on 2009-06-27
hey can anybody tell me what does this spider mean  on UBUNTU FORUMS MAIN PAGE when it shows the total online member and guests

---

### Post by diwas on 2009-06-27
> **rushikesh988 said:**
> hey can anybody tell me what does this spider mean  on UBUNTU FORUMS MAIN PAGE when it shows the total online member and guests
Yes, exactly...what does it mean?

---

### Post by mgranet on 2009-06-27
[http://en.wikipedia.org/wiki/Web_spider](http://en.wikipedia.org/wiki/Web_spider)

---

### Post by cariboo on 2009-06-27
They are basically indexing bots from the different search engines. 

This really isn't helping the op, lets get back on topic.

---

### Post by lisati on 2009-06-27
> **rushikesh988 said:**
> hey can anybody tell me what does this spider mean  on UBUNTU FORUMS MAIN PAGE when it shows the total online member and guests

> **cariboo907 said:**
> They are basically indexing bots from the different search engines. 

This really isn't helping the op, lets get back on topic.

1. The arachnids might be something to be aware of when having your own web page. Once the OP's website is up and running it might pay to have something like a robots.txt file to politely tell some of the archnids where to go. (No, I haven't set it up myself, it's just something I'm aware of which might be useful to know about when I finally get round to setting up a replacement for my geocities sites)
2. Something else that might be worth looking into is a service like no-ip which can help with the setting up of domains.

---

### Post by rushikesh988 on 2009-06-27
> **lisati said:**
> 1. The arachnids might be something to be aware of when having your own web page. Once the OP's website is up and running it might pay to have something like a robots.txt file to politely tell some of the archnids where to go. (No, I haven't set it up myself, it's just something I'm aware of which might be useful to know about when I finally get round to setting up a replacement for my geocities sites)
2. Something else that might be worth looking into is a service like no-ip which can help with the setting up of domains.

thanks , It helped me to understand the concept of the SPIDER

---

### Post by kixome on 2009-06-27
If you are going to host a website that gets alot of traffic, do not host it on your own PC/network unless you have some rediculously fast connection. If it is just for a few ppl to see, then it will be fine.

---

### Post by balachandarlinks on 2009-06-27
> **cariboo907 said:**
> You have to install apache and associated apps, there are not installed by default. IF you would like to install Apache2, Mysql, Php5, go to System-->Administration-->Synaptic Package Manager-->Edit-->Mark Packages by Task, and select the LAMP server from the menu.
You can install php,mysql and apache with a single command
          
             > $ sudo apt-get install lamp-server^

---

### Post by thomz92 on 2009-06-27
ok, so after i run

$sudo apt-get install lamp-server^

i have all the necessary stuff. then what? srry i dont understand all that stuff about spiders, static IP addresses, domain names, file transfer protocols, etc so very simple language would be helpful :) thank ya

and yes, it IS going to be for just a few people.

---

### Post by cariboo on 2009-06-27
Have a look at this [howto]("http:///www.brennan.id.au/index.html"), it gives you an overview of what you need to serve web pages. The article is a little old, but most of the principles still apply.

---

### Post by thomz92 on 2009-06-27
wow. maybe i'll stick with google sites. this looks a little bit too complicated for me. by the way, does anyone have a site that they made this way? can you send me the link?

---

### Post by tet3 on 2009-06-27
I'd say that learning how to host your own site on your local Ubuntu machine is a great learning excercise, but not very practical. Your machine has to be on an connected to the Internet all the time for the site to be up, for one thing. Along with needing to either get a static IP from your ISP or configure a dynamic IP solution like dyndns.com.

There are lots of easy-to-use content management systems like Drupal and Wordpress that you can install on your local Ubuntu machine to learn and then transfer that knowledge to hosting them for very little cost at some place like Dreamhost, or my favorite for low-bandwidth sites, [http://nearlyfreespeech.net](http://nearlyfreespeech.net).

---

### Post by Old_Grey_Wolf on 2009-06-27
Install LAMP using the instructions located at [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP). The important part to get started is the command ```
sudo tasksel install lamp-server
```

After installing LAMP, ask questions at the Ubuntu Forum for Server Platforms:  [http://ubuntuforums.org/forumdisplay.php?f=339](http://ubuntuforums.org/forumdisplay.php?f=339).

Also, check to see if your ISP allows you to run a server. Many ISPs will not allow you to do that without violating your contract.

I have a website; however, my ISP provides a free website hosting service. I use their free service. It is limited to about 1.5 GB of storage though.

I read through instructions, tutorials, and guides just as you have. I thought it was to complicated for me; however, I gave it a try. I thought it was going to take me all weekend to get it working. It was running and in use in less than an hour with the help of people on this forum. When my children were living at home, going to school, and working, I set up a message board using LAMP. It was only available on my LAN with about 8 or 9 computers on it. The limitation to LAN rather than WAN was for security and privacy reasons. Everyone could post their class schedules, work schedules, constantly changing email address and phone numbers, etc.

Give it a go. If you enjoy trying something new, you will have fun doing it.

---

### Post by Terry of Astoria on 2009-06-27
If you just want a web site cheap then please take the advice given above and set up an account at a web hosting company - it's much easier and way more secure for your home computer. 
  Although linux is inherently easy to keep secure, you will need a bit more experience and/or knowledge than the average Desktop user to keep your server secure. 
  But don't let me stop you. Just please be aware of the security issue of running a web server on your home box. What I did was to set up another computer besides my main Desktop. I used it as a "sandbox" to play in with PHP programs and various content management systems like Wordpress. 
  Good luck. Either way you go I encourage you to give it your best shot.

---

