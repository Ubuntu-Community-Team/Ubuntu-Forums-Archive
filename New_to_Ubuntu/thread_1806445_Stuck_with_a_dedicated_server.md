---
title: "Stuck with a dedicated server"
date: 2011-07-17
forum: New to Ubuntu
---

### Post by tjharrison on 2011-07-17
I'm stuck with a Ubuntu 9 server some guy signed my company up for to run a single website off. I'm presently trying to configure the mail server on it but I have absolutely no knowledge of Ubuntu. All it really needs to do is allow a php script to send through gmail.

I've somehow managed to get Apache2 running on this thing, and serving pages but thats about it. I don't think its got anything listening on port 25, if thats any use to anyone.

Any help at all would be appreciated.

---

### Post by terrykiwi83 on 2011-07-17
I suggest Postfix, here is a guide [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

---

### Post by mikejonesey on 2011-07-17
for initial configureation of webserver with mail server, spamassassin and clam for virus filtering i use virtualmin (there is an open source version)... makes life easyer to adjust a whole bunch of websites in one go too...

i would be using postfix but my latest server provider does not support reverse dns!!! a new one to me, so i setup google mail instead as my mail server this time...

---

### Post by tjharrison on 2011-07-17
> **terrykiwi83 said:**
> I suggest Postfix, here is a guide [http://flurdy.com/docs/postfix/](http://flurdy.com/docs/postfix/)

Thanks. Where the tutorial says

> MySQL 			 		First we'll install MySQL 		sudo aptitude install mysql-client mysql-server 		This will prompt you for a root password. 		Choose someting wise and remember it! 		For purpose of this tutorial I will set it to ***rootPASSWORD*** 	
 	**Postfix**

 			 		Then we'll install postfix	 		sudo aptitude install postfix postfix-mysql 		This will prompt you to choose type of email server. 		Select ***internet site*** 		It will also  suggest a server name. Correct this if needed. 	


Would it be okay to install postfix without mysql? I've already set up and configured a mysql server. Would it over-write that installation?

---

