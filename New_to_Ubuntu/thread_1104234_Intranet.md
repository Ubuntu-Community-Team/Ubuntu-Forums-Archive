---
title: "Intranet"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by Django1200 on 2009-03-23
I have recently set up a pc on my home network with ubuntu 8.10. I successfully installed LAMP and went to [http://localhost](http://localhost) to make sure that Apache is working. It is. However, I have three questions relating to this that I would appreciate help with.

1) How do I set up the addresses within my network so that this server is always at the same place so I can direct my other computers to find the intranet?

2) How do I ensure that the page is only an internal phenomenon and won't be available to outside users. (I want this to be a true intranet and don't want it available from the web)

3) I had a friend code the actual page for me and he did it in shtml. Will there be any issues with simply dropping index.shtml in /var/www in place of the index.html that is already there?

By the way, I can't say how amazing this community has been to me. I've only ever used linux casually before this and was a little hesitant to be a total noob after so many years with windows. Anyways, I appreciate any input you can provide

---

### Post by dacorr on 2009-03-23
1) How do I set up the addresses within my network so that this server is always at the same place so I can direct my other computers to find the intranet?

*I believe you need to set the IP to static (Network in system menu.) on Ubuntu where Apache is running, then typing its IP in a browser will allow other machines to access it.*

2) How do I ensure that the page is only an internal phenomenon and won't be available to outside users. (I want this to be a true intranet and don't want it available from the web)

*As long as the router does not forward incomming port 80 to the Apache host it should be fine. when you access the web you go out on port 80.*

3) I had a friend code the actual page for me and he did it in shtml. Will there be any issues with simply dropping index.shtml in /var/www in place of the index.html that is already there?

*I dont think so, the only thing i can think of is the order in which it looks up index.###, i.e index,htmle, index.php that kind of thing so i would rename the index.html to somthing like index_bk.html so the webserver will ignore it.*

Dac

---

