---
title: "how to download full website!"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by MBG1987 on 2010-04-07
is there a way to download full website to browse it offline?

---

### Post by J V on 2010-04-07
Ehm... I suppose... if you downloaded every link and every link on every link except external links... but the website would still be pretty broken, and if one part didn't work (For example, the externality filter) then you would end up downloading the whole internet...

If you have access to the website, just use ftp :)

---

### Post by undecim on 2010-04-07
If you use wget, you can use the -r option which will go through all the links on the website and download them all. For example, go to a terminal and type

```
wget -r ubuntu.com
```

---

### Post by bapoumba on 2010-04-07
Hmm.. Some site owners may not appreciate you use all their bandwidth to dl their content. Also please check the license of the site.

---

### Post by maverickmeerkat on 2010-04-07
httrack

[http://www.httrack.com/](http://www.httrack.com/)

---

### Post by MBG1987 on 2010-04-07
> **J V said:**
> Ehm... I suppose... if you downloaded every link and every link on every link except external links... but the website would still be pretty broken, and if one part didn't work (For example, the externality filter) then you would end up downloading the whole internet...

If you have access to the website, just use ftp :)
this will be kind of insanity!! i meant just specific website without external links
 
>  just use ftp
how?



> **undecim said:**
> If you use wget, you can use the -r option which will go through all the links on the website and download them all. For example, go to a terminal and type

```
wget -r ubuntu.com
```

but where to find the downloaded website?

---

### Post by undecim on 2010-04-07
> **MBG1987 said:**
> but where to find the downloaded website?

It will be in whatever directory your shell is in when you run the command. If you just opened the terminal, it will show up in your home directory.

Now that I think about it though, it's probably not the best for browsing offline because it doesn't translate links from internet to local addresses...

---

### Post by audiomick on 2010-04-07
If you are just talking about a simple website, and you are using firefox, try
File> save this page

If have done that a number of times for things with a lot of text that I want to read at my leisure (a Wikipedia page, for instance), and have usually been happy.

---

### Post by tom.swartz07 on 2010-04-07
> **audiomick said:**
> If you are just talking about a simple website, and you are using firefox, try
File> save this page

If have done that a number of times for things with a lot of text that I want to read at my leisure (a Wikipedia page, for instance), and have usually been happy.

Instapaper is perfect for just what you are describing also. Its a free web service that you use to parse pages for the text and links for reading later in a format similar to a newspaper.
[http://www.instapaper.com/](http://www.instapaper.com/)
I use it all the time; theres even an iPhone app if youre so inclined

---

### Post by cmcanulty on 2010-04-07
I have used HTTrack in windows and love that it is available in Linux. You can set the options to download however deep internal or external links you want or set it to zero. It is a great program

---

### Post by J V on 2010-04-07
Hmm... Downthemall?

---

### Post by Rasa1111 on 2010-04-07
you can convert an entire webpage into a PDF to view later, 
not exactly what your lookin for i know, 
bit it comes in handy.
its a firefox addon,
[http://www.pdfdownload.org/](http://www.pdfdownload.org/)

 that httrack looks nice to. :) thanks.

edit:
  Just tested the httrack~
it works beautifully!! wow! Many thanks!

---

### Post by durand on 2010-04-07
MBG1987: Listen to the others and use httrack. It's exactly what you need. However, unless it's a popular online site, you really should ask for permission from the owner.

---

