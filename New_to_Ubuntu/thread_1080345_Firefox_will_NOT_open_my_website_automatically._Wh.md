---
title: "Firefox will NOT open my website automatically. Why not?"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by suomalainen on 2009-02-25
Ubunteros,

I have a small web server (500GB) that I use for development purposes.

I copied to the correct directory the files:

index.htm
index_files

When I launch Firefox, I get the following message PLEASE SEE ATTACHED PICTURE.

So, as you can see the only possible option is to save the htm file to desktop.

When I do and double click on it the only thing that appears is web page and no graphics. Only the text of the web page appears.

HOWEVER,

When I open Windows XP and launch Explorer and type the very same URL the page opens FLAWLESSLY! In windows XP I also tested Opera browser and Apple Safari browser. They too open my web page Flawlessly.

I also have Firefox for Windows XP. Here I get message:

You have chosen to open:

index.htm

Which is a html document

What should Firefox do with this file:

Open with:  (here you use program to open file)
Save File:


When I choose the option to open with FireFox the same thing happens as in Ubuntu. I get a page only with the text of the web site and nothing more.

There is a difference using Firefox in XP and Ubuntu. Here  the difference is that in XP I'm given two choices. 1) open 2) save. In Ubuntu I can only save file.

So my question is this, based on the documentation I have offered, How can I configure Firefox to open my index.htm file and display my website.

As I mentioned, Explorer, Opera and Apple can do this first time without problems. Only Ubuntu Firefox isn't working.

What can I do?

Thank you and regards!

---

### Post by rustutzman on 2009-02-25
It doesn't sound like apache is running. What happens with this command?

```
sudo /etc/init.d/apache2 restart
```

---

### Post by suomalainen on 2009-02-25
Rustutzman,

The message I got based on your command is:

sudo: /etc/init.d/apache2: command not found

Does this help?

---

### Post by rustutzman on 2009-02-25
If you open a browser and type in localhost what happens? You should get a page with "It works!"

Have you installed apache? You might want to check out this thread:

[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")

Russ

---

### Post by suomalainen on 2009-02-25
Rustutzman,


Attached is a pic of the message I got.

How do I install Apache?

Thank you

---

### Post by Doug11 on 2009-02-25
> **suomalainen said:**
> Rustutzman,


Attached is a pic of the message I got.

How do I install Apache?

Thank you
You can install it through synaptic!

---

### Post by rustutzman on 2009-02-25
Follow the instructions in this link:
[https://help.ubuntu.com/community/ApacheMySQLPHP]("https://help.ubuntu.com/community/ApacheMySQLPHP")
You need to scroll down a little on that page for your system.

Russ

---

### Post by suomalainen on 2009-02-25
Thank you for the advice and suggestions.

I got a stupid question so I hope you don't laugh too hard......

Why exactly do I want to install Apache? I'm asking this because I'm under the impression that I can just type a url to a web site and then it pop's up.

I guess I'm confused because Explorer. Opera and Safari worked straight away without and modifications. Only the XP and ubuntu versions of FireFox aren't working for me.

I would appreciate any background info or clarification you have to provide.

Thanks very much!!!

---

### Post by suomalainen on 2009-02-25
P.S.

I'm running Ubuntu 8.04 LTS and Firefox version 3.0.6 if that helps you...

---

### Post by rustutzman on 2009-02-25
Opening the page in a web browser is much different than having it served to you through a web server. Right now you have no web server, That's what apache is. If you're going to do any web development you will need the web service running to do any real testing.

Russ

---

### Post by suomalainen on 2009-02-25
Russ,

What then is the difference here? I mean Explorer, Opera and Safari can open the url with no issue. The page opens normally lika any other website I go to.

Only Firefox complains......

Adding that I need to install an Apache webserver futher complicates the matter for me. What is it that I'm missing here????

Thanks for your feedback!

---

### Post by suomalainen on 2009-02-25
P.S.

I already have a webserve. I just want to view pages normally.

As I mentioned, I can see these pages without issue using Explorer, Opera and Safari. Only Firefox produces undesirable effects.

What can I do to open these web pages normally????

---

### Post by rustutzman on 2009-02-25
To view them normally you need to open them from a web server. If this is for development what language are you going to be using? PHP, Javascript, Java, Ruby? You won't be able to do any of these without testing on an actual web server. The scripts won't run. You might as well just create the documents in OO Writer.

Russ

---

### Post by suomalainen on 2009-02-25
I already have a web server!

I have two files these are:

index.htm
index_files


I uploaded them to Godaddy and I can view them just fine! No problem!

I also have my own web server at home.

I put these two very same files into the folder where they are suppose to go. Explorer, Opera and Safari can open these pages on my web server just fine. No problem.

If I use firefox for either XP or Ubuntu then these pages will not open. I noted the precise problem at the beginning of this post.

Do you have any idea as to what I can do so that Firefox can open my web pages?

---

