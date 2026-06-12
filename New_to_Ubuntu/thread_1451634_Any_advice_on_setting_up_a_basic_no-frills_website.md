---
title: "Any advice on setting up a basic no-frills website(?)"
date: 2010-04-10
forum: New to Ubuntu
---

### Post by Bill Sheppard on 2010-04-10
Hi 
       Total noob to making a website. Any advice appreciated. 
Thanks
Bill

---

### Post by J V on 2010-04-10
[http://drupal.org](http://drupal.org)

---

### Post by new_tolinux on 2010-04-10
> **J V said:**
> [http://drupal.org](http://drupal.org)
If the system is as good as the demo......

> **Not Found**

 The requested URL /drupal/ was not found on this server.
 Additionally, a 404 Not Found error was encountered while trying to use an ErrorDocument to handle the  request.


---

### Post by sigmarhophi on 2010-04-10
Your computer will work perfect to host your own website.  There are many apps and editors for creating basic HTML and several free web hosting apps readily available in the repository. Guessing since you said no-frill website you do not care much about scripting languages, flash, or other.

To get a webserver up and running:

> sudo apt-get install apache2

The base directory for placing all your web site HTML is going to be:

/var/www

Just save your first page as the index.html

If you want others to see your page, you can use many free ip redirection websites like dyndns.org to point to your home computer.

---

### Post by buddyd16 on 2010-04-10
1. I highly recommend you go through the tutorials and read the information at [http://www.w3schools.com/]("http://www.w3schools.com/"), I picked up the basics of css and html there in a couple hours and created my company's website [www.structura-inc.com]("www.structura-inc.com")

2. Create your first site using nothing but a simple text editor and get an idea of how the actual code effects the appearance.

3. After you finish your site run it through a validator [http://www.w3schools.com/site/site_validate.asp]("http://www.w3schools.com/site/site_validate.asp"), I found this very helpful for finding a few random open html tags and a couple tags where I mistakenly placed the "/" in a tag in the wrong spot.

---

### Post by readycarpenter on 2010-04-11
yes drupal is exactly like the demo, but you can re theme it real easy, drupal is my personal choice, see my site below, all drupal, but drupal is not for bginners, but can catch on pretty quick, I was buged by the layout at first, but as I use it more I see why it is the way it is,

also wordpress is very easy many use it, I think it is more popular than drupal because it can be used by so many different skill levels.

thirdly, as posted above, if you are going to install apache on your local pc, then it better be a pretty fast pc, also need alot of other packages like php, mysql, and so forth. It need to be on and pc online for the outside world to see you. lastly if you are a beginner, and you just want a site, say for personal or business... 6.95 per month thats $83 a year [bluehost.com]("http://bluehost.com") is the best deal I have ever been able to find, and I've used alot of web hosts over the last 10 years.
bluehost offer unlimited domains, unlimited bandwidth, unlimited sub.domains, unlimited email account, ald the best part simplescripts, to install unlimited drupal, wordpress, joombla, phpbb, and tons more

my point is if you just want to mess around with a site, try a free one, download and test drupal, then when your ready to commit to a server, look at all the options.

keepin it real since 1976

---

### Post by J V on 2010-04-11
+1 for w3schools, idk where you got that 404, drupal is a head-wrecker for the first day or 3, but after that you will get better and better.

Its open source and used on a huge amount of famous websites (Where I found out about [the onion]("http://onion.com"))

[List]("http://buytaert.net/tag/drupal-sites")

---

### Post by kellemes on 2010-04-11
> **Bill Sheppard said:**
> Hi 
       Total noob to making a website. Any advice appreciated. 
Thanks
Bill

We need more info..
You need to setup a webserver or you already have one? Details please..
What kind of website do you have in mind?

---

### Post by new_tolinux on 2010-04-11
> **J V said:**
> idk where you got that 404
Like I said, in the demo's (link on the top page of the drupal homepage).

Just checked the first one again and yet it works. I guess some user before me broke down the demo, which was corrected during the once-per-x-time automatic reinstall.

---

### Post by florus on 2010-04-11
BlueFish is a decent HTML editor for Linux.
Get Craig Grannell's book, Web Designers Reference, from Amazon. Makes the whole process simple and logical.
Find websites you like and click View>Page Source in your browser. You can then copy chunks of code and modify them in Bluefish to see how they work.
Use CSS to control the appearance of your site, and HTML to provide the content. It seems more complicated at first, but in reality makes the whole process more logical and easy to understand.

---

### Post by Bill Sheppard on 2010-04-12
Thanks all. Much appreciated.

Bill

---

### Post by deepakjoy on 2010-04-13
I would suggest using [XAMPP]("http://www.apachefriends.org/en/xampp.html") as your server. 
Its extremely easy to set up, and comes with MySQL, PHP and Perl preconfigured. 
These would be great for a beginner, while still allowing ample room for growth :)

---

