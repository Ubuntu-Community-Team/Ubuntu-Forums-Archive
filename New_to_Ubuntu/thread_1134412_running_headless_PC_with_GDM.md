---
title: "running headless PC with GDM"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by tricia56 on 2009-04-23
I have setup my desktop as headless to serve my media.  I am using x360mediaserve for music and ushare for movies.  I am still attaching the monitor at times whilst I fine tune all of this.

My question (I think!) is that most guides about headless media servers I have read talk about turning off GDM but I have not and it is not causing me a problem. Is that going to be a problem and in what way?   What exactly does GDM do apart from taking the username and password - which I have set to automatically do on the headless PC - is there some other reason for it? 

It is a mystery.

tricia

---

### Post by crjackson on 2009-04-23
> **tricia56 said:**
> I have setup my desktop as headless to serve my media.  I am using x360mediaserve for music and ushare for movies.  I am still attaching the monitor at times whilst I fine tune all of this.

My question (I think!) is that most guides about headless media servers I have read talk about turning off GDM but I have not and it is not causing me a problem. Is that going to be a problem and in what way?   What exactly does GDM do apart from taking the username and password - which I have set to automatically do on the headless PC - is there some other reason for it? 

It is a mystery.

tricia

It shouldn't hurt anything. The only reason I can give for removing it is that it is useless for some server configurations and it uses extra resourses.

---

### Post by cariboo on 2009-04-23
IF you leave gdm enabled when running headless, the max resolution you will get is 800X600. Which may not be to good if you intend to use remote desktop to access it.

---

### Post by tricia56 on 2009-04-23
Okay, thanks for the replies.  I think I will leave it as it is.

---

