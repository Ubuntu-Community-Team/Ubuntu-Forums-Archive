---
title: "Hosting a website from  a server?"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by ericeclifford on 2009-07-07
I have a domain name, and I want to host it from my web server, any tutorials for this, its a 8.04 ubuntu server edition install. I got it up as a web server and ftp server already.

---

### Post by halitech on 2009-07-07
do you have a static IP for the system from your ISP?

---

### Post by jonobr on 2009-07-07
Hello

Could explain more where you are at?
From what you say, you have registered your domain name,
thats good,

Have you associated that with an IP address in your ISPs dns?

Do you have a static IP address for use with your web service?

IF yes, your domain needs to point to that IP address.

When you type in nslookup mywebsite.com for example, the dns hosted by your isp should return your IP address your using for the website.

If your using a dynamic IP address, then you would need to register with a particular service like dynamic dns.
Here your public IP address may change from time to time and a service like dynamic will track those changes.

In either case, how are you getting from your Internet connection to your web server?
Will it be a direct connection?
IF not are you using a internal IP address on your network (i.e. 192.168.1.x addresses)
If your using internal addresses you router will need to port forward web traffic to your web server.
I.e. anything recieved on port 80 forward to host 192.168.x.x


However, first things first, do you have a static or dynamic ip?

---

### Post by ericeclifford on 2009-07-07
Well I am paying for a domain from go daddy.

And I got a dns name from dyndns and that dyndns site has a thing saying It Works!, also my ftp site is the same domain name as well. I have a var/www/index.html in my folder I am guessing that is my it works page.

So do i just set up a alias of some sort so when people go to the go daddy site, just direct it to my domain name, and use web site building software to set up the web page? I am kind of lost :)

edit: its a static IP

---

### Post by halitech on 2009-07-07
if you have a static IP address, there should be a section on the godaddy site where you can enter your IP address and then you will use their DNS servers to point to your IP address. I'm not exactly sure where the setting is but I remember seeing it before.

the other option is to use ZoneEdit to track your IP and enter their DNS settings in go daddy

---

### Post by jonobr on 2009-07-07
+1 with halitech

Also, if you have your website setup and firewall open on port, you could get someone on the internet (like us here) to try and connect to your site via ip.

That should still work and apache once installed, will produce an "It works" page which shows connection to the web server works and your web server came up ok

---

### Post by ericeclifford on 2009-07-08
> **halitech said:**
> if you have a static IP address, there should be a section on the godaddy site where you can enter your IP address and then you will use their DNS servers to point to your IP address. I'm not exactly sure where the setting is but I remember seeing it before.

the other option is to use ZoneEdit to track your IP and enter their DNS settings in go daddy


Ok but I have to make the website somehow correct? do I just buy website developing software that will make it on my linux var/www/index.html and go from there or what?

---

### Post by alexlafreniere on 2009-07-08
Assuming you have your site up and running and you can get to your "It Works!" page from the Internet, you **do not** have to buy web development software. There's plenty of free software out there that in many respects outperforms the pricey proprietary stuff. Almost all content management systems provide a way to produce content in-browser, so you won't be tied to a specific platform. What platform will you be developing on? Do you know HTML/CSS? What kind of website are you developing, just simple HTML, a blog, or a full-fledged web app? Give us some more information so we can help you.

---

### Post by ericeclifford on 2009-07-08
> **alexlafreniere said:**
> Assuming you have your site up and running and you can get to your "It Works!" page from the Internet, you **do not** have to buy web development software. There's plenty of free software out there that in many respects outperforms the pricey proprietary stuff. Almost all content management systems provide a way to produce content in-browser, so you won't be tied to a specific platform. What platform will you be developing on? Do you know HTML/CSS? What kind of website are you developing, just simple HTML, a blog, or a full-fledged web app? Give us some more information so we can help you.

Just html, I think :)

I am a newbie, but am learning :)

---

### Post by listerdl on 2009-07-08
- just to add my two cents - the issues are that you need to of course keep the machine always on, (which can be expensive) and - apparently - home use bandwidth cannot accommodate many people accessing your site. Say you had 100 people accessing the site at the same time, I think you might have problems there......

If the site is to be used for a few people then sure, go for it I reckon.

---

### Post by halitech on 2009-07-08
the other thing to keep in mind, unless you are paying your ISP for a commercial or server package, it may not be legal for you to run a server of any kind on your current account. If you think you will be just getting a few hits a month then you can probably fly under their radar and get away with it but if they catch you it could amount to big fines and your service being terminated.

---

### Post by alexlafreniere on 2009-07-08
> **ericeclifford said:**
> Just html, I think :)

I am a newbie, but am learning :)

If all you're doing is hand-coding HTML pages, then you don't need **any** paid software, period. You can use any old text editor, or if you want extra amenities like syntax highlighting for gedit on Linux (it's installed by default in Ubuntu) and turn on highlighting, or Notepad++ on Windows. They're both free and both have extremely powerful options for any coding you could be doing.

---

### Post by ericeclifford on 2009-07-09
> **alexlafreniere said:**
> If all you're doing is hand-coding HTML pages, then you don't need **any** paid software, period. You can use any old text editor, or if you want extra amenities like syntax highlighting for gedit on Linux (it's installed by default in Ubuntu) and turn on highlighting, or Notepad++ on Windows. They're both free and both have extremely powerful options for any coding you could be doing.

Dont know how to hand code, which is why I need the software.

But I have a google test website up, maybe I will just tell my go daddy domain to go to that for now.

---

### Post by jonobr on 2009-07-09
Hello


If your trying to learn You could try taking a look at [W3 Schools here]("http://www.w3schools.com/html/default.asp")
for the basics on HTML, 

Once you get the basics and learn to create simple web pages,
You can always use the internet for more enhanced learning

so in firefox for example, if you go to a webpage and go
view->source
it will show you the source coding used to produce a web page.
This was very relevant a few years ago, however now, web pages are a lot more complex and have a lot of dynamic content, however, the basics are still there.

---

### Post by Celauran on 2009-07-09
> **jonobr said:**
> 
so in firefox for example, if you go to a webpage and go
view->source
it will show you the source coding used to produce a web page.
This was very relevant a few years ago, however now, web pages are a lot more complex and have a lot of dynamic content, however, the basics are still there.

It's still relevant. You need to understand the basic building blocks before you move on to anything more complex.

---

### Post by jonobr on 2009-07-09
Agreed Celauran, just to clarify, that viewing the source of pages without knowing the building blocks and seeing a lot of other things in there may be intimidating .


Calling it irrelevant was the wrong word...

Cheers

---

### Post by tomcatdad on 2009-07-10
jonobr, you sound like the goto guy. I too am a newby to Ubuntu, I need to expand my skillset, like hosting a website, so...I have Apache 2.2 in my Home folder, but don't understand the install instructions. Can you help?

---

### Post by Cato2 on 2009-07-10
General advice:

- search for an "Ubuntu Apache HOWTO" on how to set up Apache.  Make sure you are keeping your system updated otherwise someone could hack your PC through Apache!  See the last part of [http://kevin.vanzonneveld.net/techblog/article/schedule_automatic_updates_on_ubuntu/](http://kevin.vanzonneveld.net/techblog/article/schedule_automatic_updates_on_ubuntu/) about doing security updates only.

- Having Apache in your Home folder sounds weird - did you download it from somewhere to that folder?  The way to install Apache is (1) read the HOWTO! and (2) go into Synaptic and search for Apache packages and install those.  Synaptic will install the Ubuntu supported Apache package, which is what you want.

- There are quite a few tools that let you edit HTML pages without knowing HTML - some I can think of are Nvu, Kompozer, and Bluefish.  Search for "HTML editor review Ubuntu"

- GIMP is a great graphics editor - if you aren't used to Photoshop it does take time to learn but it's very good.  Find a good tutorial on the web and have a go.  You can also get a lot of free images, buttons, etc, on the web, but you will end up wanting to do some of your own graphics too.

---

### Post by jonobr on 2009-07-10
tomcatdad Just FYI, I posted in your inbox directly, if you go to provate messages you should a response

---

