---
title: "Google Talk with Pidgin - &quot;not authorized&quot;"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by Envergure on 2008-09-03
I can't use my Google Talk account with Pidgin!

I go Accounts > Manage, then click Add

I enter my data:
Protocol = Google Talk
Screen Name = "Envergure94"
Domain = "gmail.com"
Resource = "Home"
Password = "sweetpeas"
Local alias = (nothing)

I click "Save," it connects to the server and tells me i'm "not authorized."  The "Protocol" field has changed to "XMPP".


btw that isn't my real name or password xD


.

---

### Post by Cope57 on 2008-09-03
Try this

Protocol: **XMPP**
Username: Envergure94
Domain: gmail.com
Resource: Home
Password: ************
Local alias: Envergure (or whatever)

If that is not working try [Google Talk Help]("http://www.google.com/support/talk/bin/topic.py?topic=1191")
There is a link near the bottom that says
[I'm having trouble accessing the Talk network using Pidgin on Linux]("http://www.google.com/support/talk/bin/answer.py?answer=47934&topic=13038")

If you're using Pidgin on Linux to access the Google Talk network, and are seeing an error message stating:

    server does not use any supported authentication method

your version of Pidgin was not compiled with SSL support. Please visit [http://developer.pidgin.im/wiki/FAQssl](http://developer.pidgin.im/wiki/FAQssl) for instructions on compiling with SSL.

Go to 
13) [Ubuntu Feisty (7.04) and Gusty (7.10)]("http://developer.pidgin.im/wiki/FAQssl#UbuntuFeisty7.04andGusty7.10")

And possibly find the answer.

---

### Post by Envergure on 2008-09-03
No, that's not it, it just says "Not Authorized".

Maybe i've got my account info wrong.

Here's another idea:  My Google Talk account has existed for all of half an hour now, so maybe something at their end hasn't been updated yet?

---

### Post by vishzilla on 2008-09-03
What are your Advanced settings?
I have the following options set
Use GSSAPI for authentication **checked**
Connect port: 5222
Connect server: talk.google.com

---

### Post by Envergure on 2008-09-03
Nevermind!  It was the login info after all :)

I must have mistyped my password when i created the account.

It would have helped if Pidgin were more specific than "not authorised".

Admins, you may delete this thread if you like, as far is i'm concerned.

---

### Post by paraselixir on 2008-12-30
Pidgin is working well for my gmail and yahoo account 
but when i am configuring it for aother XMPP ....then it simply gives
"not authorised message"?


I have entered following data-

Protocol = XMPP
Screen Name = paras.shah
Domain = xyz.com
Resource = Home
Password = **********
local alias = paras

in advance settings
haven't checked any option

Connect port : 5222
Connect Server: talk.google.com
file tansfer proxies: proxy.jabber.com
and I have used Gnome proxy settings.....

can anyone help?

---

### Post by SanskritFritz on 2008-12-30
Gtalk requires SSL to be turned on, despite of this description:
[http://www.google.com/support/a/bin/answer.py?hl=en&answer=49147](http://www.google.com/support/a/bin/answer.py?hl=en&answer=49147)

---

### Post by paraselixir on 2008-12-30
what should I do

---

### Post by paraselixir on 2008-12-30
I have done the same thing even checking the Require SSL/TLS button 
in the advance tab I am getting the same error....
"Not authorized"
and in the debug window error is

ficate for talk.google.com
(13:54:29) jabber: XML parser error for JabberStream 0x98c00f8: Domain 1, code 5, level 3: Extra content at the end of the document

---

### Post by SanskritFritz on 2008-12-30
> **paraselixir said:**
> I have done the same thing even checking the Require SSL/TLS button 
in the advance tab I am getting the same error....
"Not authorized"
and in the debug window error is

ficate for talk.google.com
(13:54:29) jabber: XML parser error for JabberStream 0x98c00f8: Domain 1, code 5, level 3: Extra content at the end of the documentDo you have a space at the end of the domain name?

---

### Post by studo77 on 2008-12-30
I am having the same problems.

Either i get a "read error" or "cannot connect to server".

Have been through many settings. My msn and facebook is doing fine. 

It is google talk which is giving me troubles.

If i use prot 5222 i get the server connect error. If i use port 443 i get the read error. Other options i cannot tell apart.

And yes i have been through my info, it is correct. It has been checked for the last month or so, and four times while writing this.

Oh, and starting from terminal i get this:
error: 0 is wrong flag id


EDIT:
I got it working. Not entirely sure why. But this helped.

I found that i had quite some forwarding on the router, removed them all. To start over. Read som infos, and most did not help.

But a little down in this i found something that worked:
[http://groups.google.com/group/3rd-Party-Clients/browse_thread/thread/d1dd627a180e9abf/1aa39d42f1d83550?q=Pidgin&pli=1]("http://groups.google.com/group/3rd-Party-Clients/browse_thread/thread/d1dd627a180e9abf/1aa39d42f1d83550?q=Pidgin&pli=1")


This works for me:
Force old (port 5223) SSL: Checked
Allow plaintext auth over unencrypted streams: Un-Checked
Connect Port: 443   <---!!!
Connect Server: talk.google.com
Proxy type: Use Global Proxy Settings


My guess is that i had forwarding of 443 and not 5223, although i can't see why it should matter. Now there is none.

---

### Post by paraselixir on 2008-12-30
sanskrit>>>>>>>>>>>>>>>>

no I dont have any space after that.....

studo77>>>>>>>>>>>>>>

I tried every single options that is possibe.....
and I got three types of error...

SSL handshake failed -- port 5222 and [force old...]checked
Read error  -- taking port 443
Not Authorized--for any other combination

Write error -- taking port 423

---

### Post by studo77 on 2008-12-30
paraselixir:
How about port forwarding? I removed all mine.

With the 443, did you check "Force...5223"

And lastly, Pidgin could really use some useable/informative error messages.

---

### Post by khc on 2008-12-31
see if [http://developer.pidgin.im/wiki/Protocol%20Specific%20Questions#WhycantIlogontomyGoogleTalkGoogleAppsaccountanymore](http://developer.pidgin.im/wiki/Protocol%20Specific%20Questions#WhycantIlogontomyGoogleTalkGoogleAppsaccountanymore) helps

---

### Post by jdoggman on 2009-02-03
I was able to right-click on an unauthorized contact and "re-authorize" the individual.  Everything seems to be back to normal..... for now

---

### Post by redders on 2009-03-28
> **paraselixir said:**
> I have done the same thing even checking the Require SSL/TLS button 
in the advance tab I am getting the same error....
"Not authorized"
and in the debug window error is

ficate for talk.google.com
(13:54:29) jabber: XML parser error for JabberStream 0x98c00f8: Domain 1, code 5, level 3: Extra content at the end of the document

Try leaving all the other settings as default, and changing domain from gmail.com to googlemail.com ... worked for me.

---

### Post by Steve White on 2012-06-07
Hi, this issue came up again for me recently.

Situation was:  I had been using Pidgin for my Google Chat client successfully for some time.  I had been told about Google Talk, and fiddled with the settings for that.

At this point, my Pidgin ceased to work for Google Chat, giving always the "not authorized" message.

I tried everything, I do believe, looking through all the advice at Google, and on various forums.  Nothing helped.  Even moving my ~/.pidgin directory and re-creating the account failed.

Finally, it occurred to me it might have to do with this business of giving Google my phone number for a 2-step authorization.  Seems nowadays they have "application-specific passwords", and these can be made only with the 2-step authorization thing.  I don't like it, there's some notice about asking me every 60 days or something.  Anyway.

I gave them the number, they SMS'ed me a code, with which I generated an application-specific password using the Google page, put that in my Pidgin account for Google Chat, and now I can log in again.

I still don't know what Google Talk had to do with it.  I tried to turn it off, but don't really know what I was doing.

Cheers!

---

