---
title: "Application for http links -"
date: 2011-08-25
forum: New to Ubuntu
---

### Post by BlinkinCat on 2011-08-25
Hi all,

I occasionally receive emails from trusted sources that have links on their opening page. When I click on link I get the message - "This link needs to be opened with an application  - Choose an application."  

I simply don't know how to proceed - I didn't have this problem in Ubuntu.
Can somebody help please?
Cheers, - :)

---

### Post by SoFl W on 2011-08-25
> **BlinkinCat said:**
> I simply don't know how to proceed - I didn't have this problem in Ubuntu.

What operating system are you using now?  Choose your favorite web browser.  (Does it offer a choice?)

---

### Post by BlinkinCat on 2011-08-25
Xubuntu 11.04  -  Firefox default which is my choice anyhow.

Thunderbird default Email

Thanks SoFI W

---

### Post by fdrake on 2011-08-25
> **BlinkinCat said:**
> Xubuntu 11.04  -  Firefox default which is my choice anyhow.

Thunderbird default Email

Thanks SoFI W

is it a file, or just a link?
try to wget the link and open it with a txt editor to see the source code.

btw it's possible to that the sender has somehow changed the headers of the mail to trick the spam filter make it look like a real email.

---

### Post by BlinkinCat on 2011-08-25
I have just double checked on two other emails with links and the same problem exists - so it definitely seems a problem at my end -

BTW This installation is only one day old.

---

### Post by fdrake on 2011-08-25
> **BlinkinCat said:**
> I have just double checked on two other emails with links and the same problem exists - so it definitely seems a problem at my end -

maybe you are missing some plug-ins in firefox?

---

### Post by BlinkinCat on 2011-08-26
> **fdrake said:**
> maybe you are missing some plug-ins in firefox?

As I said on my last post edit - installation is new - only 1 day old - I can look around firefox without really knowing what I am doing - You wouldn't think it likely there would be a problem there although anything is possible I suppose.

---

### Post by fdrake on 2011-08-26
> **BlinkinCat said:**
> As I said on my last post edit - installation is new - only 1 day old - I can look around firefox without really knowing what I am doing - You wouldn't think it likely there would be a problem there although anything is possible I suppose.
if you don't really know just use a guess session and open the link with the program requested.

---

### Post by BlinkinCat on 2011-08-26
Is that a guest session? - I don't have one set up -
or is it a guess session??????:confused:


Thanks anyway fdrake -

---

### Post by fdrake on 2011-08-26
> **BlinkinCat said:**
> Is that a guest session? - I don't have one set up -
or is it a guess session??????:confused:


Thanks anyway fdrake -

pardon my typing... :P 

in the terminal:

```

/usr/share/gdm/guest-session/guest-session-launch

```
check your emails, logout and login back to you previous session.

if you don't have it installed do

```

sudo apt-get install guest-session

``` & reboot.

---

### Post by BlinkinCat on 2011-08-26
I entered 2nd command - error came back -Unable to locate package guest-session

Unfortunately I have to go out to the Doc's

Will study when I return -

Any further comments appreciated. - :)

---

### Post by BlinkinCat on 2011-08-26
Hi all,

Sorry for double post.

I was fiddling around in my emails when I discovered the problem with links had gone (for now at least) - I can now select links within emails and go to correct address.
I have just created a second Thunderbird account but I can't see how that would effect the outcome.

I would be very interested if someone could explain why I was getting Application error messages - otherwise I will soon mark as solved. (for good I hope!)

Cheers - :)

---

### Post by ofnuts on 2011-08-26
> **BlinkinCat said:**
> Hi all,

I occasionally receive emails from trusted sources that have links on their opening page. When I click on link I get the message - "This link needs to be opened with an application  - Choose an application."  

I simply don't know how to proceed - I didn't have this problem in Ubuntu.
Can somebody help please?
Cheers, - :)You get this kind of message when the server at the other end declares some unusual MIME-type (or just "plain text") for the data it returns from that link. Then your mail client considers that it cannot itself display it, so asks you what app can open it. 

Use wget -S or FireFox with a suitable plugin (such as LiveHTTPHeaders) to check the Content-type returned by the server: 
```
 wget -S www.ubuntuforums.com
--2011-08-26 17:44:40--  http://www.ubuntuforums.com/
Resolving www.ubuntuforums.com... 91.189.94.12
Connecting to www.ubuntuforums.com|91.189.94.12|:80... connected.
HTTP request sent, awaiting response... 
  HTTP/1.1 301 Moved Permanently
  Date: Fri, 26 Aug 2011 15:44:40 GMT
  Server: Apache/2.2.8 (Ubuntu)
  Location: http://ubuntuforums.org/
  Content-Length: 317
  Keep-Alive: timeout=15, max=100
  Connection: Keep-Alive
[I][B]  Content-Type: text/html; charset=iso-8859-1
[/B][/I]Location: http://ubuntuforums.org/ [following]
--2011-08-26 17:44:40--  http://ubuntuforums.org/
Resolving ubuntuforums.org... 91.189.94.12
Reusing existing connection to www.ubuntuforums.com:80.
HTTP request sent, awaiting response... 
  HTTP/1.1 200 OK
  Date: Fri, 26 Aug 2011 15:44:40 GMT
  Server: Apache/2.2.8 (Ubuntu) PHP/5.2.4-2ubuntu5.17 with Suhosin-Patch
  X-Powered-By: PHP/5.2.4-2ubuntu5.17
  Expires: 0
  Cache-Control: private, post-check=0, pre-check=0, max-age=0
  Pragma: no-cache
  X-UA-Compatible: IE=7
  [I][B]Content-Type: text/html; charset=ISO-8859-1
 [/B][/I] X-Cache: MISS from feijoa.canonical.com
  X-Cache-Lookup: MISS from feijoa.canonical.com:8800
  Via: 1.0 feijoa.canonical.com:8800 (squid/2.6.STABLE18)
  Set-Cookie: bbsessionhash=026f28e8ea480e1aa9b5af59b5d0807b; path=/; domain=.ubuntuforums.org; HttpOnly
  Set-Cookie: bblastvisit=1314373480; expires=Sat, 25-Aug-2012 15:44:40 GMT; path=/; domain=.ubuntuforums.org
  Set-Cookie: bblastactivity=0; expires=Sat, 25-Aug-2012 15:44:40 GMT; path=/; domain=.ubuntuforums.org
  Via: 1.0 ubuntuforums.org
  Connection: close
Length: unspecified [text/html]

```

---

### Post by BlinkinCat on 2011-08-26
Thanks for your input ofnuts - As I indicated on my last post problem now seems be be gone.
When I was browsing through my emails I found that all of them with links showed the same application required message. As none of these are now a problem there does not appear to be any need for further action.

I will hope that I don't have any further problems with it - will mark as solved within half an hour unless anyone else can advise why I would get this message on all emails with links.

Cheers and thanks to all - :)

Edit: I thing I did do was clear all rubbish from Thunderbird - not that there was much anyway.

---

