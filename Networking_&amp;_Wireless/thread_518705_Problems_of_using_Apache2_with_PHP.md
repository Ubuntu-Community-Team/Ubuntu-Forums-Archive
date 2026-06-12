---
title: "Problems of using Apache2 with PHP?"
date: 2007-08-06
forum: Networking &amp; Wireless
---

### Post by Richardinho on 2007-08-06
Hi!

I've been using PHP with Apache on Windows XP and wanting to set it up on Ubuntu now that I've got this OS installed. However I have read (PHP and MySql 2nd edition, Larry Ullman) that Apache 2 doesn't work properly with PHP. However Apache2 seems to be the only one available in my repository listed in synaptic.  I'm assuming I can find Apache 1 somewhere, but can anyone tell me what good reasons there are for not using Apache 2 with PHP?

---

### Post by Saner on 2007-08-06
It works fine for me.

But I am interested too in this topic, as I am just about to re-install my dedicated box and I was going to install (again) apache2 / php5 / sql5

---

### Post by EndPerform on 2007-08-06
I have Apache2, PHP5 and mysql installed on this box and my home box, and both work perfectly fine.  The edition of the book you have sounds a bit old as I knew there used to be issues when Apache2 first came out, but those problems were solved since then. 

For the record, I installed on Ubuntu and Kubuntu, non-server editions.

---

### Post by Richardinho on 2007-08-06
The source book ('PHP and Mysql' by LarryUllman) was published in 2005, and some of the mysql examples are actually  dated February 2005.On his website, forum, he's pretty adamant about the problems with php and apache2-(yes, I know I should ask there!), although he admits that he doesn't know a great deal about linux which is why I asked here.

If people say they've got it working ok though, who am I to argue!

---

### Post by jonald on 2007-08-07
hello, am very new to ubuntu and php5, my school teaches red hat linux which i can't install in my laptop. so i tried about this ubuntu and installed it finally. but when i was trying to write some html file that calls an php script i got this download manager all the time. and when click open nothing happens. 

is php5 supports firefox? i just want the script to run in a browser and returns the value that i have put in from html form. any help would be appreciated.

yes i installed php5 through get-apt install command including php5-cgi
thanks

---

### Post by hrapasmb on 2007-08-07
Firefox runs on the client side, while PHP is compiled on by the server into some HTML code. Firefox supports HTML - therefore it is "compatible" with all server-side scripting languages.
--------------
Replies go here: [email]hrapasmb@macs.biu.ac.il[/email]

---

