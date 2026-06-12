---
title: "The Cairo-Dock Repositories"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by Roger Allott on 2010-01-06
For the past couple of days I've been getting an error message from Update Manager, as follows:

```
W: Failed to fetch http://repository.cairo-dock.org/ubuntu/dists/karmic/Release.gpg  Could not resolve ‘repository.cairo-dock.org’

W: Failed to fetch http://repository.cairo-dock.org/ubuntu/dists/karmic/cairo-dock/i18n/Translation-en_GB.bz2  Could not resolve ‘repository.cairo-dock.org’

W: Some index files failed to download, they have been ignored, or old ones used instead.
```

Has Cairo-Dock changed the location of its deb repository? If so, to what? Or is it just that Cairo-Dock has a (temporary) server problem?

---

### Post by howefield on 2010-01-06
Looks like a server problem.

Open a terminal and type whois cairo-dock.org

You'll see one of the entries as follows

Status : PENDING DELETE RESTORABLE

Not exactly sure what that means, but doesn't look too terrific.

(I added spaces either side of the colon, to stop it turning into a emoticon)

---

### Post by Roger Allott on 2010-01-06
So, has Cairo-Dock just shut up shop? Does anyone know? Were there any warnings of it?

---

### Post by corncob on 2010-01-06
I'm not familiar with this but here is what I get:
> corncob@eeebox:~$ whois cairo-dock.org
NOTICE: Access to .ORG WHOIS information is provided to assist persons in 
determining the contents of a domain name registration record in the Public Interest Registry
registry database. The data in this record is provided by Public Interest Registry
for informational purposes only, and Public Interest Registry does not guarantee its 
accuracy.  This service is intended only for query-based access.  You agree 
that you will use this data only for lawful purposes and that, under no 
circumstances will you use this data to: (a) allow, enable, or otherwise 
support the transmission by e-mail, telephone, or facsimile of mass 
unsolicited, commercial advertising or solicitations to entities other than 
the data recipient's own existing customers; or (b) enable high volume, 
automated, electronic processes that send queries or data to the systems of 
Registry Operator or any ICANN-Accredited Registrar, except as reasonably 
necessary to register domain names or modify existing registrations.  All 
rights reserved. Public Interest Registry reserves the right to modify these terms at any 
time. By submitting this query, you agree to abide by this policy. 

Domain ID:D149892966-LROR
Domain Name:CAIRO-DOCK.ORG
Created On:23-Nov-2007 00:46:16 UTC
Last Updated On:05-Jan-2010 04:16:30 UTC
Expiration Date:23-Nov-2010 00:46:16 UTC
Sponsoring Registrar:Key-Systems GmbH (R51-LROR)
Status:HOLD
Status:AUTORENEWPERIOD
Status:PENDING DELETE RESTORABLE
Registrant ID:P-2609230
Registrant Name:Teddy Perrin
Registrant Street1:26 bis rue aumone vieille
Registrant Street2:
Registrant Street3:
Registrant City:Aix-en-provence
Registrant State/Province:
Registrant Postal Code:13100
Registrant Country:FR
Registrant Phone:+6.66013822
Registrant Phone Ext.:
Registrant FAX:
Registrant FAX Ext.:
Registrant Email:ted.1@free.fr
Admin ID:P-2609230
Admin Name:Teddy Perrin
Admin Street1:26 bis rue aumone vieille
Admin Street2:
Admin Street3:
Admin City:Aix-en-provence
Admin State/Province:
Admin Postal Code:13100
Admin Country:FR
Admin Phone:+6.66013822
Admin Phone Ext.:
Admin FAX:
Admin FAX Ext.:
Admin Email:ted.1@free.fr
Tech ID:P-2609230
Tech Name:Teddy Perrin
Tech Street1:26 bis rue aumone vieille
Tech Street2:
Tech Street3:
Tech City:Aix-en-provence
Tech State/Province:
Tech Postal Code:13100
Tech Country:FR
Tech Phone:+6.66013822
Tech Phone Ext.:
Tech FAX:
Tech FAX Ext.:
Tech Email:ted.1@free.fr
Name Server:NS2.VIROENFORCE.COM
Name Server:NS1.VIROENFORCE.COM
Name Server: 
Name Server: 
Name Server: 
Name Server: 
Name Server: 
Name Server: 
Name Server: 
Name Server: 
Name Server: 
Name Server: 
Name Server: 
DNSSEC:Unsigned


corncob@eeebox:~$ 

I see its turning : and D or P into emoticons.

---

### Post by fabounet on 2010-01-06
Well it seems the domain name has expired, and the one who registered it once ago didn't warn us (for any reason).

We are now in the registration process, but it may take up to 2 weeks.
A temporary name will probably be used (I don't have all the details yet).

So the name cairo-dock.org is not directly accessible at the moment. This affects the forum, the wiki, the repository, and the themes.


PS : please delete the personnal information of the whois command, it's not nice to have one's phone and address exposed on a forum.

---

### Post by howefield on 2010-01-06
> **fabounet said:**
> Well it seems the domain name has expired,...

Wow, such a basic error.

You are in "good" company though. Microsoft has been known to commit such mistakes.

---

### Post by matttbe on 2010-01-06
@ Fabounet : it's now ok there : [http://cairo-dock.vef.fr/]("http://cairo-dock.vef.fr/") :)
But only for the website...

I will write a message on CD forum !

---

### Post by SirGe on 2010-01-06
The web site and the wiki appear to be up at [http://cairo-dock.vef.fr/]("http://cairo-dock.vef.fr/"). The repos are not available at this address, though :(

Thanks for the updates, fabounet and everyone else - I was getting a little worried...

---

### Post by fabounet on 2010-01-07
there is a PPA for Cairo-Dock :
launchpad.net/cairo-dock
it holds both the stable release and the development one.

---

### Post by D1Knight on 2010-01-07
> **fabounet said:**
> there is a PPA for Cairo-Dock :
launchpad.net/cairo-dock
it holds both the stable release and the development one.
fabounet, I am currently unable to download themes via Cairo-Dock. :( Is this related to the issue with domain name?:? Peace.:)

**Disregard** I just saw your post up above.:oops:

---

### Post by fabounet on 2010-01-07
some news about it.
seems we'll have to wait 3 weeks to regain our domain :-(

meanwhile, the site is available here :
[cairo-dock.vef.fr]("cairo-dock.vef.fr")

and to get the themes in the dock, use this command :

```
cairo-dock -oS http://themes.vef.fr
```
or if some applets are invisible :
```
cairo-dock -oiS http://themes.vef.fr
```
or if your card doesn't support the OpenGL :
```
cairo-dock -cS http://themes.vef.fr
```

---

### Post by onyxwolf on 2010-01-07
:mad::confused::frown:](*,)[-(:cry::evil: people suck!!!

---

### Post by D1Knight on 2010-01-07
> **fabounet said:**
> some news about it.
seems we'll have to wait 3 weeks to regain our domain :-(

meanwhile, the site is available here :
[cairo-dock.vef.fr]("http://cairo-dock.vef.fr")

and to get the themes in the dock, use this command :

```
cairo-dock -oS themes.vef.fr
```or if some applets are invisible :
```
cairo-dock -oiS themes.vef.fr
```or if your card doesn't support the OpenGL :
```
cairo-dock -cS themes.vef.fr
```
fabounet, I thank you kindly for the commands.:D Hopefully next time you shall be given a fair amount of time, before the domain is about to expire or at least given a date of when renewal is due for the domain.;) I appreciate you. Have a great week/end!:)Peace.

---

### Post by fabounet on 2010-01-08
the latest rev on the BZR trunk now includes the temporary themes server address, so if you're running this version you don't need to specify the address.

---

### Post by fabounet on 2010-01-09
the server has ben reorganized (what we did i a hurry in the first days was becoming a mess)
so now you can have the themes in the dock with
```
cairo-dock -S http://themes.cairo-dock.vef.fr
```

sorry for the troubles, hope everything goes back to normal soon !

---

### Post by Tapas Pain on 2010-03-02
So, I don't know if this is the right question to ask or not, but what about the repositories?  Do I delete the old cairo-dock link
[http://repository.cairo-dock.org/ubuntu](http://repository.cairo-dock.org/ubuntu)
from my software source?  Or just declick it?
Do I change it to something else?

Also, just out of curiosity, can someone tell me how you manage to paste the terminal outputs into your forum post (I'm guessing you do more than a simple copy and paste but I have no idea what).
Thanks.

---

### Post by SirWeazel on 2010-03-02
Tapas, I can answer one of your questions. The old link has changed. you need to change it to: 
[http://repository.glx-dock.org/ubuntu](http://repository.glx-dock.org/ubuntu)

So, basically your changing it from ".cairo-dock.org" to ".glx-dock.org".
The gaphical way to change it: System>administration>software sources>other software tab>find the cario dock repository, click edit and change the URL:
Then cario dock will update, there has been a couple updates lately.

I don't know the answer to your second question since i've never had to do it before. I hope this helps.

---

### Post by Tapas Pain on 2010-03-04
> **SirWeazel said:**
> Tapas, I can answer one of your questions. The old link has changed. you need to change it to: 
[http://repository.glx-dock.org/ubuntu](http://repository.glx-dock.org/ubuntu)

So, basically your changing it from ".cairo-dock.org" to ".glx-dock.org".
The gaphical way to change it: System>administration>software sources>other software tab>find the cario dock repository, click edit and change the URL:
Then cario dock will update, there has been a couple updates lately.

I don't know the answer to your second question since i've never had to do it before. I hope this helps.

Thanks a lot.  I'm getting the updates now.  Appreciate it.

---

### Post by Roger Allott on 2010-03-04
> **Tapas Pain said:**
> 
Also, just out of curiosity, can someone tell me how you manage to paste the terminal outputs into your forum post (I'm guessing you do more than a simple copy and paste but I have no idea what).
Thanks.

It's simple copy and paste, but note that you cannot use the keyboard shortcuts of Ctrl-c and Ctrl-v. Instead, right-click on the text you want to copy and select 'Copy' from the dropdown list. For pasting, place your cursor where you want to insert the text in your clipboard, right-click, and select 'Paste' from the dropdown list.

---

