---
title: "need help setting up pan news reader"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by gandaran on 2008-12-05
I'm trying to set up pan news reader, I have added the news server and I can see it downloads thousands of groups and I subscribed some groups but it doest download anything from these groups I have subscribed, what am I missing or doing wrong?
thanks

---

### Post by nhasian on 2008-12-05
i've run into 3 posts about the pan news reader in the last two days.  it must be pretty difficult to setup?  i might have to give it a try.  Do you need your newsreader to do text or you only need it to download binary files?  If its the latter, may i suggest the LottaNZB frontend with HellaNZB?

```
sudo apt-get install lottanzb
```

---

### Post by Michaelg14 on 2008-12-06
Go to "Groups" in the menu and click on "Get new headers in subscribed groups".

---

### Post by gandaran on 2008-12-06
well. thanks for the answers, I started pan this morning and it is working now, don't know why it refused to fetch the headers after installing

---

### Post by Lantash on 2008-12-11
> **nhasian said:**
> i've run into 3 posts about the pan news reader in the last two days.  it must be pretty difficult to setup?  i might have to give it a try.  Do you need your newsreader to do text or you only need it to download binary files?  If its the latter, may i suggest the LottaNZB frontend with HellaNZB?

```
sudo apt-get install lottanzb
```

Sorry for being a little off-topic: I just wanted to say that anyone who's interested in LottaNZB should go to the _[LottaNZB download page]("http://www.lottanzb.org/downloads")_ and grab the Ubuntu package from there. This is because LottaNZB isn't part of Ubuntu's repositories yet, so "sudo apt-get install lottanzb" won't work.

---

