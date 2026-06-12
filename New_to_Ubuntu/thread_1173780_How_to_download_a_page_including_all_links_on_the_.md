---
title: "How to download a page including all links on the page"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by zelalem on 2009-05-30
Hi all, I am wondering if there is a tool to download a page and its associated pages. Like a manual could have an outline with its chapters and subchapters having a link on the main page. So i am looking for a tool that can download the manual including the different chapters and sub-chapters in one instruction. I hope there is a tool for this.

Thank you.

---

### Post by kpkeerthi on 2009-05-30
```

wget -r http://www.website.com

```

You can control how deep (default is 5) you want the pages downloaded using the -l (lowercase L) option. Suppose you only need first 2 levels of [http://www.website.com](http://www.website.com), you would do:

```

wget -r -l2 http://www.website.com

```

For more information see 
```
man wget
```

EDIT: There is also a GUI wrapper for wget. Google **gwget**.

---

### Post by zelalem on 2009-05-30
Hi Kpkeerthi[COLOR=Black][]("http://ubuntuforums.org/member.php?u=123376")[/COLOR], thank you for your prompt response. I tried the command but because i am behind a proxy it gives me an error. How do i specify my user name and password when i issue the command. BTW, is there a tool (like download manager in windows) that i can use in ubuntu? 

407 Proxy Authentication Required
2009-05-30 11:47:34 ERROR 407: Proxy Authentication Required.


Thank you again for your help.

Zelalem

---

### Post by kpkeerthi on 2009-05-30
Did you check the man page for proxy authentication?

---

### Post by zelalem on 2009-05-30
No, in fact the following is what I got:

Resolving wwwproxy.xx.xx.xx... 145.xxx.xxx.xxx, 145.xxx.xxx.xxx, 145.xxx.xxx.xxx, ...
Connecting to wwwproxy.xxx.xxx.xx|145.xxx.xxx.xxx|:3000... connected.
Proxy request sent, awaiting response... 407 Proxy Authentication Required
2009-05-30 11:47:34 ERROR 407: Proxy Authentication Required.

I changed my proxy name and address above. So, I wanted to know how I can insert my username and password in the request line so that the proxy can authenticate me to get the page.

Thanks again.

BTW, how about a tool (with graphical user interface). Don't you know any tool that does this work?

---

### Post by kpkeerthi on 2009-05-30
```

--proxy-user=user
--proxy-password=password
    Specify the username user and password password for authentication on a proxy server. 

```

```
man wget
```

---

### Post by bobin on 2009-05-30
ucan download a firefox addon called flashgot.it does everything u wanted.

---

### Post by zelalem on 2009-05-30
Hi Bobin, that is what I was looking for. A tool that I can use like download manager in windows. I will download it and try it. Thank you for your help. 

Thank you Kpkeerthi as well for your help.

Cheers,

---

### Post by Hated On Mostly on 2009-05-30
Is this what you are looking for?

[http://www.httrack.com/](http://www.httrack.com/)

The package is in the repositories and can be installed through Synaptic or Add/Remove.

---

