---
title: "Installing Apps"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by gibxam on 2009-03-14
I have noticed that depending on where you read, some sources will say to install apps using ```
sudo apt-get install appname 
``` while others will say to go to the download web page of the specific app and then save it to your disk and then compile it using ./configure make ext..

-What is the difference between these two methods?
-Does using sudo apt-get install appname automatically do all the compiling for you?
-Why does using sudo apt-get install appname automatically put (or install?) files in /usr/share/doc/ ?
-Are these the only files that are installed or are there more files that are installed other places? I ask this because after doing the sudo apt-get install method I navigate to /usr/share/doc/specificapp I see files that are different then if I save an app to my disk.

Overall I think I'm just mixing up my terminology and just pretty confused in general. I hope my questions were specific enough, its very possible that I am not being clear in what I am asking; if this is the case please let me know and I will try to rephrase.

Thank you as always,

---

### Post by hyper_ch on 2009-03-14
with apt-get install you fetch precompiled software form repositories. By default you only have ubuntu repositories but there are also third party ones that provide more software (have a look at my generator).

Basically, only add repositories to your sources list that you trust.

Have a read here:  [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by gibxam on 2009-03-14
Why would the files in /usr/shar/doc/appname be different then if I were to save the .gz file to my disk though?

Also does using the repositories automatically install to /usr/shar/doc/appname or can this be adjusted or are there other files in different places?

---

### Post by hyper_ch on 2009-03-14
you know what /usr/share/doc is for?

---

### Post by ugm6hr on 2009-03-14
If you need to ask this question, I would strongly advise using apt (or derivatives) to install.

Compiling using source (often tar.gz files) is easy enough, but can leave you with dependency problems (i.e. non-working installation) and an inability to uninstall if you don't know what you are doing.

---

### Post by theozzlives on 2009-03-14
I would recommend  repositories first, then a *.deb file if there is one before compiling.

---

### Post by zvacet on 2009-03-14
> while others will say to go to the download web page of the specific app and then save it to your disk and then compile it

This is good in case that you don´t have app in repos and you can not find deb package anywhere else.But in most cases repos are enough.

---

