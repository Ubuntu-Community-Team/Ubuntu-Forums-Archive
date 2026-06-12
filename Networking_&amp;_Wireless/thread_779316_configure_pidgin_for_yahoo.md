---
title: "configure pidgin for yahoo"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by rohan.modi on 2008-05-02
some one plz help me out to configure pidgin for yahoo
i m able to configure it for gmail using xmpp
how can i do the same for yahoo
i.e. the connect port
connect server

i m using hostel lan and we do have a proxy server here

---

### Post by superprash2003 on 2008-05-02
doesnt it work with the default settings?

---

### Post by rohan.modi on 2008-05-03
Do U Mean To Use Yahoo Instead Of Xmpp
If It So Then Also No Result With The Japan Server And Without It Also
There Is No Default Valu For Server In Xmpp For Yahooo
For Gmail It Is Talk.google.com

---

### Post by superprash2003 on 2008-05-04
i use pidgin.. and i use Yahoo.it doesnt use the japan server..pager server is scs.msg.yahoo.com .. Japan Pager server is cs.yahoo.co.jp ..pager port is 5050 ..File transfer server is filetransfer.msg.yahoo.com ..Japan filetransfer server is filetransfer.msg.yahoo.co.jp ..file transfer port is 80  ..

---

### Post by rohan.modi on 2008-05-05
Man Its Not Working, The Settings U Provide R Default And Over Proxy Server Doesn't Allow Port 5050
Is There Any Other Way Such As Using Xmpp ?????
I M Using Port 443 For G Mail In Xmpp

---

### Post by ben2talk on 2009-04-15
I solved this by using Windows software running Windows XP in a virtualbox.

It seems not worth the effort trying to make Pidgin work. At least Microsoft software appears to be able to connect - thank you Microsoft.

---

### Post by rohan.modi on 2009-04-15
thnx for the comment but i have  configured it already

---

### Post by dejyx on 2009-07-01
rohan.modi,

Can you plz tell the house how you succeded in connecting to your yahoo messanger using pidgin

---

### Post by MCode151 on 2009-07-01
This is an old thread, they now have a simple wizard/drop down choice of type 'yahoo' under 'manage accounts'. However, as discussed in [http://ubuntuforums.org/showthread.php?p=7539933](http://ubuntuforums.org/showthread.php?p=7539933) and noted in
[http://developer.pidgin.im/wiki/ChangeLog](http://developer.pidgin.im/wiki/ChangeLog) there was a v13 > v15/16 Yahoo! protocol change.

From [http://ubuntuliving.blogspot.com/2009/06/problems-logging-on-to-yahoo-from.html](http://ubuntuliving.blogspot.com/2009/06/problems-logging-on-to-yahoo-from.html):
> this is an excellent move, as it should make their server software simpler (speak one less protocol, one less auth scheme, etc.) and reduce their support load (fewer client versions to deal with). Where it became a problem for us is that at the same time, they started requiring protocol version 15 clients to speak the version 15 authentication scheme, which we never implemented. Since we still spoke version 13's authentication, this cut us off entirely.

More details from [http://theflamingbanker.blogspot.com/2009/06/some-clarification-on-yahoo-issues.html](http://theflamingbanker.blogspot.com/2009/06/some-clarification-on-yahoo-issues.html):
> The specific problem that affected us is the authentication mechanism. Yahoo Messenger 6 used a spectacularly complicated password obfuscation method to "encrypt" the password as it was being sent over the wire to Yahoo's servers. Back in 2004 when we were preparing our 0.79 release, Cerulean Studios, the creators of the Trillian client, were kind enough to implement this authentication mechanism for us. As part of this change, we began to identify to the Yahoo servers as Yahoo Messenger 6. This was all fine and well.

The real problem came relatively recently. At some point in our recent history, which I honestly don't feel like tracking down now, we started identifying as Yahoo Messenger 7. At some point after that we again updated to identify as Yahoo Messenger 8. Both of these changes were related to file transfer and other feature enhancements. When we made these changes, however, we never updated our authentication code. This means we were claiming to speak Yahoo Protocol version 15 but we authenticated the same way protocol version 13 clients do. Even this worked for quite some time.

[B]Pidgin 2.5.5 is the version in ubnuntu 8/9 production repositories.
YIM issue is fixed in Pidgin 2.5.7/.8 which is available in PPA/main/dev[/B]
[B]
--->>> Directions for installing 2.5.8: [http://pidgin.im/download/ubuntu](http://pidgin.im/download/ubuntu)
[/B]
Or visual guides:
[http://www.kabatology.com/06/22/pidgin-2-5-7-for-ubuntu-fixes-yahoo-login-issues](http://www.kabatology.com/06/22/pidgin-2-5-7-for-ubuntu-fixes-yahoo-login-issues)
[http://news.softpedia.com/news/How-to-Fix-Yahoo-problem-in-Pidgin-114754.shtml](http://news.softpedia.com/news/How-to-Fix-Yahoo-problem-in-Pidgin-114754.shtml)
[http://ubuntumanual.org/posts/188/pidgin-fails-to-connect-to-yahoo-issue-solved](http://ubuntumanual.org/posts/188/pidgin-fails-to-connect-to-yahoo-issue-solved)

If you don't want to use the new version (though I can't see a good reason not to), some servers aren't upgraded yet [http://blog.mypapit.net/2009/06/solving-pidgin-yahoo-messenger-problem.html](http://blog.mypapit.net/2009/06/solving-pidgin-yahoo-messenger-problem.html) or [http://www.celticwolf.com/useful-information/faqs/26-pidgin-yahoo](http://www.celticwolf.com/useful-information/faqs/26-pidgin-yahoo) but the number is probably dwindling fast.

---

### Post by chau maau on 2009-08-08
[FONT="Comic Sans MS"]
hi frnz
if you want 2 configure pidgin for yahoo
do following things :-
1)  click on Accounts then Manage Accounts.
2)  click on Add button.
3)  select YAHOO as a protocol.
4)  write your Username in username column.
     (only username, not domain 
         for ex. if your username is [email]abc@yahoo.com[/email], write only abc)
5)  write your yahoo password in Password column.
 
thts all my frnz...
donn do anything else...
njoy...!!!
:popcorn:
[/FONT]

---

### Post by jozey on 2010-06-02
> **chau maau said:**
> [FONT="Comic Sans MS"]
hi frnz
if you want 2 configure pidgin for yahoo
do following things :-
1)  click on Accounts then Manage Accounts.
2)  click on Add button.
3)  select YAHOO as a protocol.
4)  write your Username in username column.
     (only username, not domain 
         for ex. if your username is [email]abc@yahoo.com[/email], write only abc)
5)  write your yahoo password in Password column.
 
thts all my frnz...
donn do anything else...
njoy...!!!
:popcorn:
[/FONT]

why i can't use this setting on pidgin 2.6.5???

---

