---
title: "How to Install Certain Applications"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by wyaeiga on 2010-06-26
Hi all!

First of all, complete Linux/UNIX n00b here so sorry if this question is really lame and/or stupid.

I was wondering how to install certain applications as you can tell from the title. Now I know Ubuntu is helpful enough most of the time with instructions on what to type into terminal (e.g. sudo apt-get and whatnot) and other times all you really have to do is press a few buttons, but when those two options aren't available, what do you do?

I've been trying to install this screengrabbing application called Gyazo and the download page is [here]("http://yaa.no-ip.org/~yaa/diary/20071108.html#p04"), but when I go to the actual download link, it just directs me to another page of code. What do I do from that point?

Thanks in advance!

~wya

---

### Post by Groodles on 2010-06-26
> **wyaeiga said:**
> Hi all!

First of all, complete Linux/UNIX n00b here so sorry if this question is really lame and/or stupid.

I was wondering how to install certain applications as you can tell from the title. Now I know Ubuntu is helpful enough most of the time with instructions on what to type into terminal (e.g. sudo apt-get and whatnot) and other times all you really have to do is press a few buttons, but when those two options aren't available, what do you do?

I've been trying to install this screengrabbing application called Gyazo and the download page is [here]("http://yaa.no-ip.org/%7Eyaa/diary/20071108.html#p04"), but when I go to the actual download link, it just directs me to another page of code. What do I do from that point?

Thanks in advance!

~wya

The page of code is a bash script (that I'm guessing requires Ruby/Rails to be installed as well).

You could copy the entire page of code, paste it into a file.  chmod the file to +x and you're away.  However, running scripts from a unknown source is NOT recommended.

---

### Post by jfreak_ on 2010-06-26
Hmm I don't know the language in the link , but anyway shutter (search in Ubuntu software centre) takes screenshots well.

---

### Post by wyaeiga on 2010-06-26
> **Groodles said:**
> You could copy the entire page of code, paste it into a file.  chmod the file to +x and you're away.  However, running scripts from a unknown source is NOT recommended.

Dumbfounded. Mostly just the chmod the file to the +x part, not sure what that really means D:

> **jfreak_ said:**
> Hmm I don't know the language in the link , but anyway shutter (search in Ubuntu software centre) takes screenshots well.

Thanks for the recommendation! I wanted Gyazo originally because it's super quick. It's literally just summon GNOME Do, launch Gyazo, drag for screenshot, uploaded automatically. I used to take screenshots the same way on Windows with Launchy + Gyazo.

I guess shutter will have to suffice for now.

---

### Post by werecatomega on 2010-06-26
you want to take screenshots? there is already the "Take Screenshot" app in the Applications tab

---

### Post by Paddy Landau on 2010-06-26
Where possible, I would recommend that you stick with installing programs through Ubuntu Software Centre or Synaptic Package Manager. That way, you have a greater likelihood of compatibility -- and it's so much easier.

Experiment with gnome-screenshot (Accessories > Take Screenshot). You can use Gnome-Do to launch it.

---

### Post by Tyke91 on 2010-06-26
hitting the print screen button will also automatically start gnome screenshot.


about chmodding something executable, it's REALLY not recommended that you install software unless you know exactly what it does. chmod is a very handy tool, and you can learn more about it (and *nix permissions in general) here: [http://catcode.com/teachmod/](http://catcode.com/teachmod/)

the link that your site points to ([http://yaa.no-ip.org/~yaa/ddata/gyazo](http://yaa.no-ip.org/~yaa/ddata/gyazo)) is a ruby script which looks like it sets up an install directory for the gyazo program and then downloads it from their website (tho my ruby skill really sucks, so I could be wrong and it could be the actual source code behind Gyazo... it seems like gyazo takes whatever is selected on screen, converts it to a png file and then uploads it to their own server and provides you with a link)

personally I use imgshack for all of my free file hosting (my home network is a little bit complicated with one router I own and one router I don't own, and I really don't want to mess around with my own server at the moment heh)

anyway good luck!

---

### Post by mapes12 on 2010-06-26
Hope you've solved this by now but for future reference:-

[http://amitech.50webs.com/installing/index.php.html](http://amitech.50webs.com/installing/index.php.html)

---

