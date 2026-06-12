---
title: "Unable to Download Package Files"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by Jinty on 2009-02-21
Have just installed Ubuntu 8.10, downloaded updates and some additional apps.

Now downloads stop after one or two files.  Initialy download stated times vary from a few secs to many hours before it stops. I can connect to internet ok.

Can anyone please advise what I should do?

I am a complete beginer.

---

### Post by taurus on 2009-02-21
Maybe change to another server, System -> Administration -> Synaptic Package Manager -> Settings -> Repositories **_or_** System -> Administration -> Software Sources.

---

### Post by Sealbhach on 2009-02-21
Hi,
It could be your download server is not working properly at the moment. 

Try this:

Go to System/Administration/Software Sources in your menu.

In the Download From box, select Other. Then click on Select best Server. This will find the quickest server for your location.


.

---

### Post by MedianMajik on 2009-02-21
> **Jinty said:**
> Have just installed Ubuntu 8.10, downloaded updates and some additional apps.

Now downloads stop after one or two files.  Initialy download stated times vary from a few secs to many hours before it stops. I can connect to internet ok.

Can anyone please advise what I should do?

I am a complete beginer.
Open the Terminal and run

Sudo apt-get upgrade

Copy and paste all the text, including the error that results, into your first post.

edit: Welcome to Linux!

---

### Post by Jinty on 2009-02-21
Apologise if this is not how to reply to answers quickly given to my problem.

I have changed from the UK server to Main Server and this appears to have solved problem.

Many thanks to all who replied.

Jinty

---

### Post by beswatcher on 2009-02-21
Jinty, you and I are both glad that this forum is here. This seems to have fixed my problem also. I'm going to the M.I.T. server now, so now I have to sort through all the updates and try to figure out what to install.

---

