---
title: "Servers"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by Poltergiest on 2010-10-10
I am trying to learn how to run, and maintain a web site using a server that I would set up my self in my home, or a building close to my home any one know where I can get this information, Im thinking about using Ubuntu Server Edition but I know literally nothing about servers and how URL's are tied to each server?

---

### Post by drdos2006 on 2010-10-10
Here is a HOWTO which I found comprehensive and invaluable.
> 
Are you using the most current version of this how-to?
Version numbers are located @ top right of this page. Latest versions are available at my homepage [http://woodel.com](http://woodel.com)
Under the Solutions tab
Setting up a Linux Server, Start to Finish, using Webmin. By Kevin Elwood


regards

---

### Post by jnorthr on 2010-10-10
you could start your reading here: [https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

It's for ubuntu 8.04 but most of it should still apply to 10.10.

---

### Post by Poltergiest on 2010-10-11
Thank you, Your help is much appreciated. Any one else who has more information on the matter I would appreciate it. I'm trying to learn as much as possible.

---

### Post by mastablasta on 2010-10-11
if you only want a webserver (website) with some space for your data it is not cost effective (usually) to run it from home. it is far more cheaper and easier to rent the service.
 
however if you plan on using it as familly server or somehting liek that where everyone would store data, then that is a different story.

---

### Post by iMisspell on 2010-10-11
To help you get started, test and learn; you could always install VirtualBox on your current system then install a server in that as a virtual machine.

---

### Post by amjjawad on 2010-10-11
> **Poltergiest said:**
> I am trying to learn how to run, and maintain a web site using a server that I would set up my self in my home, or a building close to my home any one know where I can get this information, Im thinking about using Ubuntu Server Edition but I know literally nothing about servers and how URL's are tied to each server?

I'm also very interested in this. I'm looking for another PC or laptop at the moment so that I can use my current PC as a server. 

Maybe this will help you for basic understanding:
[http://en.wikipedia.org/wiki/Server_(computing)]("http://en.wikipedia.org/wiki/Server_%28computing%29")

Also, I was wondering if I'm going to build a website and use my own server at home, I think I still have to pay to publish that page on the Internet, right?

---

### Post by QLee on 2010-10-11
[QUOTE=amjjawad]...
Also, I was wondering if I'm going to build a website and use my own server at home, I think I still have to pay to publish that page on the Internet, right?[/QUOTE]
You're going to have to check the terms of service of your contract with your ISP, often they do not include allowing a web server on residential service, they might be blocking port 80 to your gateway. In any case, if you get much traffic, they are likely to notice. This is aside of the issues of DNS, if you don't have a static IP address. I suggest you check what you can legally do with your connection with your ISP before you go to much trouble.

---

### Post by amjjawad on 2010-10-11
> **QLee said:**
> You're going to have to check the terms of service of your contract with your ISP, often they do not include allowing a web server on residential service, they might be blocking port 80 to your gateway. In any case, if you get much traffic, they are likely to notice. This is aside of the issues of DNS, if you don't have a static IP address. I suggest you check what you can legally do with your connection with your ISP before you go to much trouble.

Thanks a lot for the reply.
What I'm so sure about is I don't have a Static IP. I think I need an IP address in order to have a Web Server (not sure).
Also, I'm very sure that my greedy ISP will charge me for that and I think I have to go through them. I really hate that feeling specially when I don't have another ISP provider to go to.

So, looks like it's a dead end. However, I was just trying understand more about this :)

---

### Post by HereInOz on 2010-10-11
If you want to build a web server, check out Falco's How To:

[http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-2](http://www.howtoforge.com/perfect-server-ubuntu-10.04-lucid-lynx-ispconfig-2)

But you are going to need a static IP address and you are going to need to know how to set up DNS records for the site.  

Have fun.  It is (eventually) worth the effort.

---

### Post by QLee on 2010-10-11
[QUOTE=amjjawad]... I was just trying understand more about this :)[/QUOTE]
Good, then you will want to research a bit about dynamic DNS service too.

Here is one provider, there are others. As always, google is your friend.
[http://www.dyndns.com/](http://www.dyndns.com/)

---

### Post by SeijiSensei on 2010-10-11
One low-cost option is to rent a virtual server at someplace like [www.linode.com](www.linode.com).  You can run a 512MB server for $20/month, and they don't require a contract.  You'll get a publicly available IP as well.  Ubuntu 10.04 is one of the supported Linux distributions.  (Not affiliated with Linode; just a happy customer.)

---

### Post by amjjawad on 2010-10-11
> **QLee said:**
> Good, then you will want to research a bit about dynamic DNS service too.

Here is one provider, there are others. As always, google is your friend.
[http://www.dyndns.com/](http://www.dyndns.com/)

Thank you again :)
I'll do some research later because I'm busy with something else at the moment. I saw this thread and couldn't resist :) I've always wanted to have a server at home whether it's a family server or any kind of servers but didn't have the chance to have it or build it. This thread reminded me of an old wish :)

I think the main problem is the static IP which I can't change ... perhaps I have to pay to my ISP and I hate that, they're thieves. Never mind :)

Thanks again!

---

