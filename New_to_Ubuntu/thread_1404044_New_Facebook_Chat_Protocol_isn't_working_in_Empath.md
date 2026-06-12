---
title: "New Facebook Chat Protocol isn't working in Empathy"
date: 2010-02-11
forum: New to Ubuntu
---

### Post by dirtlamb5 on 2010-02-11
So apparently Facebook recently allowed support for Jabber and XXMP protocols (via [http://www.omgubuntu.co.uk/2010/02/facebook-chat-in-pidgin-empathy-with-no.html](http://www.omgubuntu.co.uk/2010/02/facebook-chat-in-pidgin-empathy-with-no.html)). I tried this in Empathy with william.w.rieger (which is what's in my Facebook url) and my Facebook password, but it didn't work. Any ideas?

---

### Post by Temposs on 2010-02-11
Lots of people using both Pidgin and Empathy are having issues with this right now. I think there may be problems with Facebook's chat server. I'd say give it a day and try it again.

---

### Post by bytor4232 on 2010-02-11
I am having no problems with connecting under Pidgin, but I couldn't get Empathy to connect at all.

Has anyone successfully connected Empathy?

---

### Post by leandromartinez98 on 2010-02-11
One important thing is that you need a facebook USERNAME. 

Meaning: You can have a Facebook account WITHOUT a username. This was
my case. In that case, you probably log into facebook by using as
username an e-mail address.

In that case, you need to create a USERNAME in facebook before trying
to configure Empathy. For doing so, edit your Account settings in
Facebook, create the username, and logout and login from your Facebook
account. 

Then you can configure Empathy using as 

Account type:  Jabber
Login ID:     [email]facebookusername@chat.facebook.com[/email]
Password:     Your facebook password
Server: chat.facebook.com

Everything else can be set as default.

This has worked for me. I'm using it. It took me a while to notice
that I had a facebook account without a facebook username.

It is working well for me in Empathy.

---

### Post by ElSlunko on 2010-02-11
What the above user said could be the issue. Not trying to assume that you don't know the difference between your email address & your facebook username, might just be a simple error. Any progress today?

---

### Post by thedondj on 2010-02-11
I have the same problem, can log in fine with pidgin but empathy gives me an "Authentication Error".

There are screenshots of it working for someone else here [http://www.theopensourcerer.com/2010/02/11/using-facebook-xmpp-chat-on-ubuntu/]("http://www.theopensourcerer.com/2010/02/11/using-facebook-xmpp-chat-on-ubuntu/")

---

### Post by tom.swartz07 on 2010-02-11
Make sure you have SSL turned off. I had that problem, as mine had it enabled by default.

---

### Post by Temposs on 2010-02-11
Also, make sure when you click "Add" in Empathy, that you then select "Reuse existing account". I kept choosing "Create new account" and it was giving an authentication error. Kudos to the comments on this blog post:

[http://www.theopensourcerer.com/2010/02/11/using-facebook-xmpp-chat-on-ubuntu/](http://www.theopensourcerer.com/2010/02/11/using-facebook-xmpp-chat-on-ubuntu/)

The comment by Paul Tansom is what fixed it for me. Now I have facebook chat on Empathy :-)

---

### Post by muyisco on 2010-02-11
i got mine to work after logging out of facebook and logging back in. i think this should work. source: [http://www.theopensourcerer.com/2010/02/11/using-facebook-xmpp-chat-on-ubuntu/comment-page-1/#comment-12445](http://www.theopensourcerer.com/2010/02/11/using-facebook-xmpp-chat-on-ubuntu/comment-page-1/#comment-12445)

---

### Post by durand on 2010-02-11
Getting a 503 error in pidgin. That might be your problem too.

---

### Post by Rami-L on 2010-02-11
> **muyisco said:**
> i got mine to work after logging out of facebook and logging back in. i think this should work. source: [http://www.theopensourcerer.com/2010/02/11/using-facebook-xmpp-chat-on-ubuntu/comment-page-1/#comment-12445](http://www.theopensourcerer.com/2010/02/11/using-facebook-xmpp-chat-on-ubuntu/comment-page-1/#comment-12445)
that was the problem -now working

---

### Post by dirtlamb5 on 2010-02-11
> **Temposs said:**
> Also, make sure when you click "Add" in Empathy, that you then select "Reuse existing account". I kept choosing "Create new account" and it was giving an authentication error. Kudos to the comments on this blog post:

[http://www.theopensourcerer.com/2010/02/11/using-facebook-xmpp-chat-on-ubuntu/](http://www.theopensourcerer.com/2010/02/11/using-facebook-xmpp-chat-on-ubuntu/)

The comment by Paul Tansom is what fixed it for me. Now I have facebook chat on Empathy :-)

Thanks, that got it working for me. The only annoying issue now is that I can't seem to put the new Facebook contacts into any Empathy groups...

---

### Post by NightHawk_UK on 2010-02-11
I found the following that worked for me:

Create a Google Talk account.

  Login ID: [EMAIL="fbusername@chat.facebook.com"]fbusername@chat.facebook.com[/EMAIL]
Password: fb_password

Server: chat.facebook.com
    Port: 5222

Only 'Enabled' should be ticked.

Empathy connected straight away using this for me.

Then i found I could only send but not receive messages so i added a Jabber account (reuse existing) with all the same as above and it connected properly, i then removed the Google Talk account and it works perfectly now.

---

### Post by leandromartinez98 on 2010-02-11
> **NightHawk_UK said:**
> I found the following that worked for me:

Create a Google Talk account.

  Login ID: [EMAIL="fbusername@chat.facebook.com"]fbusername@chat.facebook.com[/EMAIL]
Password: fb_password

Server: chat.facebook.com
    Port: 5222

Only 'Enabled' should be ticked.

Empathy connected straight away using this for me.

Then i found I could only send but not receive messages so i added a Jabber account (reuse existing) with all the same as above and it connected properly, i then removed the Google Talk account and it works perfectly now.

The google-talk had nothing to do with it working. The reuse account thing is related to the Facebook account. You have to reuse your existing Facebook account, not create a new facebook account. That is why people is having problems, there is a confusion (I had it) between the Empathy account and the service account, in this case the Facebook one.

---

### Post by NightHawk_UK on 2010-02-11
Yeah i understand that but for some reason the Jabber (reuse) wasnt working, then i read someone got it working with google-talk, so i tried that but it wouldnt receive so i remade the Jabber account and it worked that time so i thought i would let people know.

---

### Post by meho_r on 2010-02-14
Oh man, I have another problem. I managed to connect with both Pidgin and Empathy, can see friends log in and out, etc. But the moment I send them a message, they get disconnected (not to mention that message didn't manage to go through, and they cannot see me at all). Anyone experience the same?

---

### Post by dirtlamb5 on 2010-02-15
> **meho_r said:**
> Oh man, I have another problem. I managed to connect with both Pidgin and Empathy, can see friends log in and out, etc. But the moment I send them a message, they get disconnected (not to mention that message didn't manage to go through, and they cannot see me at all). Anyone experience the same?

I haven't experienced this problem before...does it happen in both Empathy and Pidgin?

---

### Post by meho_r on 2010-02-17
Yes, both of them. I've found people had [similar problems](http://getsatisfaction.com/facebook/topics/facebook_chat_doesnt_work_for_me_for_the_past_3_months_or_so) with FB chat, not Pidgin's or Empathy's fault. After doing the most stupid step I can remember I've ever done for making things work, i.e. creating a new list from FB chat as suggested by a poster on that link (to whom I own a big: thanks), I could finally see my friends and chat with them using facebook pidgin plugin and/or jabber. Problem solved, I hope.

---

### Post by rjbgbo on 2010-02-17
go create an existing account
:p

---

### Post by meho_r on 2010-02-17
> **rjbgbo said:**
> go create an existing account
:p

OK, there may be even worse situations, I guess :)

---

### Post by rjbgbo on 2010-02-17
Sorry my English translated on Google, but adding contacts between networks and network jabber chat.facebook.org could not get information that possibility has to be real.
As I spoke in a chat, only the possibility that Facebook turn to your contact list.

---

### Post by froggontherocks on 2010-03-20
Thank you this was driving me crazy. The reuse existing account was my issue guess it just made since to create new account but i was wrong. Thanks again for this post it was most helpfull

> **Temposs said:**
> Also, make sure when you click "Add" in Empathy, that you then select "Reuse existing account". I kept choosing "Create new account" and it was giving an authentication error. Kudos to the comments on this blog post:

[http://www.theopensourcerer.com/2010/02/11/using-facebook-xmpp-chat-on-ubuntu/](http://www.theopensourcerer.com/2010/02/11/using-facebook-xmpp-chat-on-ubuntu/)

The comment by Paul Tansom is what fixed it for me. Now I have facebook chat on Empathy :-)

---

### Post by aeon.flux on 2010-05-01
i think that the problem is, that facebook.com is changing its page, chat and everything too fast, so you can't login with messenger that is not up to date. no?

---

### Post by durand on 2010-05-01
It works in Pidgin. Their protocol is just standard xmpp, I think.

---

### Post by crjackson on 2010-05-01
It works fine. You just have to assign yourself an actual user name and wait for FB to provision the name.  After anywhere from 1 to 30 min. you should be able to use the chat.

It works flawless on 12 systems here, it's not Empathy.

---

### Post by greenjumper on 2010-05-02
> **leandromartinez98 said:**
> One important thing is that you need a facebook USERNAME. 

Meaning: You can have a Facebook account WITHOUT a username. This was
my case. In that case, you probably log into facebook by using as
username an e-mail address.

In that case, you need to create a USERNAME in facebook before trying
to configure Empathy. For doing so, edit your Account settings in
Facebook, create the username, and logout and login from your Facebook
account. 

Then you can configure Empathy using as 

Account type:  Jabber
Login ID:     [email]facebookusername@chat.facebook.com[/email]
Password:     Your facebook password
Server: chat.facebook.com

Everything else can be set as default.

This has worked for me. I'm using it. It took me a while to notice
that I had a facebook account without a facebook username.

It is working well for me in Empathy.

Seems to have worked for me! Thanks!

---

### Post by joelpedersen on 2010-05-04
I used my [email]username@chat.facebook.com[/email] instead of just my username alone in the facebook protocol in empathy.  When I used the username alone it failed to authenticate, but when I added chat.facebook.com it got on fine!

J

---

### Post by LeftWIngPenguin on 2010-06-02
Hope it's okay that I jump in here with another question, but I'm encountering a confusing issue with Facebook. I can enter my user name and password into Empathy, and it connects and populates my list of friends online, but I cannot send an IM to them. Double clicking does nothing and when I right click the option to Chat is available, but clicking it does nothing.

Chat works fine for my MSN account, so I'm not sure what's going on with Facebook in particular.

Anyone else encounter this issue before?

---

### Post by Lamellama on 2010-12-16
> **leandromartinez98 said:**
> One important thing is that you need a facebook USERNAME. 

Meaning: You can have a Facebook account WITHOUT a username. This was
my case. In that case, you probably log into facebook by using as
username an e-mail address.

In that case, you need to create a USERNAME in facebook before trying
to configure Empathy. For doing so, edit your Account settings in
Facebook, create the username, and logout and login from your Facebook
account. 

Then you can configure Empathy using as 

Account type:  Jabber
Login ID:     [email]facebookusername@chat.facebook.com[/email]
Password:     Your facebook password
Server: chat.facebook.com

Everything else can be set as default.

This has worked for me. I'm using it. It took me a while to notice
that I had a facebook account without a facebook username.

It is working well for me in Empathy.

Thanks dude, I didn't realise there was a difference.

---

### Post by egelon on 2011-06-06
First of all I would like to say Hi to everybody since this is my very first post to this forum :)
I've been using Ubuntu for a few months now, and I can say I like it a lot more than MS Win.
Anyway back on the topic:
I've also been trying to use the facebook chat through Empathy, but so far it kept giving me errors about not being able to log in. I tried the proposed fix about using [email]username@chat.facebook.com[/email], but that didn't work as well.
However I was just able to get the chat to work FINALLY :)

Here's what I did:

I went to Facebook -> Account -> Account settings -> Username
and set myself up a username

[B]Then I _logged out_ of facebook

[/B]After that I logged in again, this time using my new username instead of my e-mail

Then I deleted my old facebook chat account from Empathy (the one that didn't work), and tried to set up a new facebook chat account with my new user name and the old password

And what do you know- the chat actually connected and now it works!

If you are already logged in to Facebook via an e-mail address Empathy doesn't seem to connect to the chat service, EVEN if you already set up a username.
I guess the whole problem was that first you have to log in to Facebook using a username instead of an email address, and THEN try to set up a chat account. It didn't seem to make sence to me at first (and still doesn't :)), However my Empathy chat works now.

So try this fix and see if it works
CHeers:popcorn:

---

### Post by Aneesh John on 2011-06-27
Thank you for your information. Now facebook chat is working for me too with your tips.

---

### Post by amarendra on 2011-09-11
> **egelon said:**
> First of all I would like to say Hi to everybody since this is my very first post to this forum :)
I've been using Ubuntu for a few months now, and I can say I like it a lot more than MS Win.
Anyway back on the topic:
I've also been trying to use the facebook chat through Empathy, but so far it kept giving me errors about not being able to log in. I tried the proposed fix about using [EMAIL="username@chat.facebook.com"]username@chat.facebook.com[/EMAIL], but that didn't work as well.
However I was just able to get the chat to work FINALLY :)

Here's what I did:

I went to Facebook -> Account -> Account settings -> Username
and set myself up a username

[B]Then I _logged out_ of facebook

[/B]After that I logged in again, this time using my new username instead of my e-mail

Then I deleted my old facebook chat account from Empathy (the one that didn't work), and tried to set up a new facebook chat account with my new user name and the old password

And what do you know- the chat actually connected and now it works!

If you are already logged in to Facebook via an e-mail address Empathy doesn't seem to connect to the chat service, EVEN if you already set up a username.
I guess the whole problem was that first you have to log in to Facebook using a username instead of an email address, and THEN try to set up a chat account. It didn't seem to make sence to me at first (and still doesn't :)), However my Empathy chat works now.

So try this fix and see if it works
CHeers:popcorn:

Hey, thanks. Don't know why this weird behaviour but logging in and logging out solved the issue. Although I use my username only for logging but just did it again :-)

---

### Post by noletolucas on 2011-09-15
Empathy + Ubuntu 11.04 + Facebook = BUGGY!!!

Doesnt work for me either!

---

