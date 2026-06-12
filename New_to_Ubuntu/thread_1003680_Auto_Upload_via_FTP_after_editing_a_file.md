---
title: "Auto Upload via FTP after editing a file?"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by you123456 on 2008-12-06
Hi all, 
i have a question with regards to FTPing files onto a web server. 

I would want to be able to auto upload a file which i have just edited (and saved ) onto my web server via FTP, is this possible? How do i do that?

I understand that dreamweaver has a similar feature where after editing and saving a file, the respective file will be uploaded to a webserver. 

Just wondering if we can do this in gedit or vim ? or any other editors for ubuntu?

Best Regards,
Eugene

---

### Post by cmnorton on 2008-12-06
By auto-upload do you mean an automatic synch program that, for example, detects that you have edited a file and automatically transfers it, or do you mean that a web page editing  program can transmit the file to the web site?

---

### Post by you123456 on 2008-12-06
> **cmnorton said:**
> By auto-upload do you mean an automatic synch program that, for example, detects that you have edited a file and automatically transfers it, or do you mean that a web page editing  program can transmit the file to the web site?

i am refering to both types.

It would be good to know of different alternatives.

So any idea of what can be done to acheive what i have described in the first post?

BEst Regards,
Eugene

---

### Post by birddog165 on 2008-12-06
I use gFTP. When you log into your server, you can write click and edit your files. When you close out the editting app, it'll prompt you to update the file on the server. This has been very successful for me.

---

### Post by you123456 on 2008-12-06
> **birddog165 said:**
> I use gFTP. When you log into your server, you can write click and edit your files. When you close out the editting app, it'll prompt you to update the file on the server. This has been very successful for me.

ok i see.

So i suppose u use gedit as your editing app?

By the way, when you said that "you log into your server, you can write click and edit your files", do u mean that you log into your web server first, and than edit teh file from your web server?

BEst Regards.

---

### Post by birddog165 on 2008-12-06
Yes, I use gedit. When I mean, log in: when you open gFTP it has some boxes on the top where you can type in Hostname, Port, User, Password and then choose FTP, SSH, etc.

Hope this helps.

---

### Post by you123456 on 2008-12-06
> **birddog165 said:**
> Yes, I use gedit. When I mean, log in: when you open gFTP it has some boxes on the top where you can type in Hostname, Port, User, Password and then choose FTP, SSH, etc.

Hope this helps.


Ok great! Thanks dude!

I was thinking if we edit the files directly on the web server would result in greater efficiency ( and less trouble in setting up LAMP on our computers ).

When you edit directly on the web server and auto upload it each time it is changed, does it actually consume a lot of bandwidth?

BEst Regards,
Eugene

---

### Post by birddog165 on 2008-12-07
> **you123456 said:**
> Ok great! Thanks dude!

I was thinking if we edit the files directly on the web server would result in greater efficiency ( and less trouble in setting up LAMP on our computers ).

When you edit directly on the web server and auto upload it each time it is changed, does it actually consume a lot of bandwidth?

BEst Regards,
Eugene

Um, it doesn't take a high amount of bandwith for me because my webpages are small enough and mostly text based. I edit stuff directly on the server because I program a lot with a friend who lives on the other side of my state so it definitely increases efficiency. I'm sorry that I can't give you a better answer, but you might just have to try it out for yourself and see how much bandwith you actually use.

---

### Post by snova on 2008-12-07
Another idea...

I don't know if this is true for Gnome programs (I think it is), but in KDE, you can open the remote file directly with a URL such as 'ftp://server/~user/file'.

---

