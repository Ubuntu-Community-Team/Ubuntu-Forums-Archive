---
title: "installing komodo editor"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by bindu arya on 2009-09-29
How to install komodo editor manually?

---

### Post by zeroseven0183 on 2009-09-29
Hi! I'm not familiar with Komodo Edit but looking at Google search results, I found this page : [Useful Ubuntu: Installing Komodo Edit 5]("http://usefulubuntu.blogspot.com/2009/03/installing-komodo-edit-5.html")

There you have the instructions, just replace the directories to which you extract the files.

I've tested it and works good. By the way, a desktop shortcut is created.

---

### Post by zeroseven0183 on 2009-09-29
So to summarize what I did,

1. download the file from [Komodo Edit website]("http://downloads.activestate.com/Komodo/releases/5.2.1/Komodo-Edit-5.2.1-4108-linux-libcpp6-x86.tar.gz")
2. open a Terminal and type
 ```
tar zxvf /home/username/Desktop/Komodo-Edit-5.2.1-4108-linux-libcpp6-x86.tar.gz
```Note: The directory will depend where you downloaded the file. I assume you know that.
3. still on Terminal, type
 ```
cd /home/username/Komodo-Edit-5.2.1-4108-linux-libcpp6-x86
```4. To install, type
 ```
sh install.sh
```5. to finalize
 ```
sudo ln -s ""/home/username/Software/Komodo-Edit-5/bin/komodo" /usr/local/bin/komodo
```I basically did what the poster in the [blog post]("http://usefulubuntu.blogspot.com/2009/03/installing-komodo-edit-5.html") instructed so the credit goes to him.

I hope that helps.

---

### Post by bindu arya on 2009-09-30
> **zeroseven0183 said:**
> Hi! I'm not familiar with Komodo Edit but looking at Google search results, I found this page : [Useful Ubuntu: Installing Komodo Edit 5]("http://usefulubuntu.blogspot.com/2009/03/installing-komodo-edit-5.html")

There you have the instructions, just replace the directories to which you extract the files.

I've tested it and works good. By the way, a desktop shortcut is created.

thanx..
its working..

---

### Post by bindu arya on 2009-09-30
[quote=zeroseven0183;8023827]So to summarize what I did,

1. download the file from [Komodo Edit website]("http://downloads.activestate.com/Komodo/releases/5.2.1/Komodo-Edit-5.2.1-4108-linux-libcpp6-x86.tar.gz")
2. open a Terminal and type
 ```
tar zxvf /home/username/Desktop/Komodo-Edit-5.2.1-4108-linux-libcpp6-x86.tar.gz
```Note: The directory will depend where you downloaded the file. I assume you know that.
3. still on Terminal, type
 ```
cd /home/username/Komodo-Edit-5.2.1-4108-linux-libcpp6-x86
```4. To install, type
 ```
sh install.sh
```5. to finalize
 ```
sudo ln -s ""/home/username/Software/Komodo-Edit-5/bin/komodo" /usr/local/bin/komodo
```I basically did what the poster in the [blog post]("http://usefulubuntu.blogspot.com/2009/03/installing-komodo-edit-5.html") instructed so the credit goes to him.

I hope that helps.

---

### Post by bindu arya on 2009-09-30
> **bindu arya said:**
> [quote=zeroseven0183;8023827]So to summarize what I did,

1. download the file from [Komodo Edit website]("http://downloads.activestate.com/Komodo/releases/5.2.1/Komodo-Edit-5.2.1-4108-linux-libcpp6-x86.tar.gz")
2. open a Terminal and type
 ```
tar zxvf /home/username/Desktop/Komodo-Edit-5.2.1-4108-linux-libcpp6-x86.tar.gz
```Note: The directory will depend where you downloaded the file. I assume you know that.
3. still on Terminal, type
 ```
cd /home/username/Komodo-Edit-5.2.1-4108-linux-libcpp6-x86
```4. To install, type
 ```
sh install.sh
```5. to finalize
 ```
sudo ln -s ""/home/username/Software/Komodo-Edit-5/bin/komodo" /usr/local/bin/komodo
```I basically did what the poster in the [blog post]("http://usefulubuntu.blogspot.com/2009/03/installing-komodo-edit-5.html") instructed so the credit goes to him.

I hope that helps.


thanx..
its working..

---

### Post by dblv on 2010-06-03
Good Morning,
I have trouble installing Komodo Edit on ubuntu 10.4
when I write : ./install.sh I have this message :
./INSTALLDIR/lib/python/bin/python2.6: 1: Syntax error: word unexpected (expecting ")")

What is the problem ?

(Excuse me for my bad English, I'm just a poor French !!)

---

### Post by vol7ron on 2010-09-18
> **zeroseven0183 said:**
> So to summarize what I did,
...
I basically did what the poster in the [blog post]("http://usefulubuntu.blogspot.com/2009/03/installing-komodo-edit-5.html") instructed so the credit goes to him.

I hope that helps.

There's no "basically" about it, you did as the blog post said.

---

