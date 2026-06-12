---
title: "how to browse files on website using terminal"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by baha'a on 2010-03-05
hi guys 

I can surf the web from terminal using text web browsers like links2 or w3m and I can download files using wget but isn't there any way to browse a website files like I browse files on my computer using terminal, I mean can't I enter a website and see the files it contains and then download the one I like through wget or some thing like that.
it would be nice to be able to do it from command line
thanks for any help :)


I posted this thread in tips and tutorials forum but it should me a message I couldn't read and it was starting with thanks for posting but...
and I waited but the thread wasn't there I don't know why so sorry for posting it again :)

---

### Post by ubudog on 2010-03-05
Only if the website allows it.

---

### Post by doas777 on 2010-03-05
well, when you browse a page or file online, you are always downloading it, you just don;t realize it. so no, there is not way to do that with http, unless someone has created a server side app for it, that navigates for you and just sends you renders of the output. this is how most web servers show directory listings if configured to do so. you will probably have to use a differant protocol if you want to browse and manipulate files without downloading them first. common examples include (s)ftp, SCP/RCP, webDav, ms fpse, etc.

---

### Post by baha'a on 2010-03-05
well thanks but I don't want to manipulate the files or view them I just want the terminal to tell me that "this page of the web sites contains those files"
well I first got the idea when I was browsing a thread in my collage forum that the mod has put in it the lectures of the subject and the lectures were in rar files so I found out that if I gave wget (for example) the exact path of a file it would download it for me so I thought that if I could tell the terminal to show me the files uploaded on the page so I could tell wget to get me the files.

sorry for talking a lot ;)

---

### Post by doas777 on 2010-03-05
no prob man. i wish I had a better answer, but page rendering is a client side activity, and http handlers don't do things like 'ls'. if the server is configured to allow directory browsing (which is rare, as it is a security issue), it will render a page that appears to show directory information, and send it down to the client. 

one way to get what you want, is to download a page you can see, and parse its source for links. that would at least get you links to all the content linked from that page, but it will be tricky for javascript redirects (so it won't work for all sites) and you still have to go through all the links to see if they are what you are looking for. I done stuff like this before, but it can be a pain.

---

### Post by Kulgan on 2010-03-05
Agreed, it's annoying.

For a reliable, pain-free solution you would have to have access via FTP, SSH or similar.

---

### Post by baha'a on 2010-03-05
thanks guys 
it would really be a nice thing if I could do it
I think but I leave it now and I'll get back to it when I have the knowledge
because using command line in linux is really great ;)

---

