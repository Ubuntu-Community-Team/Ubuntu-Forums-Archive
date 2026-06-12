---
title: "Cannot access website in Linux - Can in Windows"
date: 2007-09-25
forum: Networking &amp; Wireless
---

### Post by altonbr on 2007-09-25
My sister needs to access this local teaching website from her Ubuntu laptop but can not: [http://www.kpr.edu.on.ca/redirect_mykpr.php](http://www.kpr.edu.on.ca/redirect_mykpr.php)

I've tried it from my Ubuntu workstation and went to my father's to try on his Ubuntu computer.

None of them seem able to be redirect properly.

I've tried in Ubuntu Gusty (7.10) with IEs4Linux (5.0, 5.5, 6.0), Firefox, Gran Paradisio, Opera and Epiphany just to mix it up an make sure it's not Gecko's problem.

Success only came when I tried it on my other sister's computer who uses Windows XP and Firefox 2.0.0.x

Can everyone try this website with Linux and without it and post what combinations with browsers are working?

At first I figured it was because of PeerGuardian, but that's only installed on my workstation, NOT her laptop, and still didn't work after I stopped it.

Any other suggestions would be appreciated. Having a "WIN32" only system wouldn't make much sense because I know teachers use other machines than Windows... that and it would seem oxymoronic to use PHP and block out Linux, lol.

I was able to find where it redirected to, found it cached in Google and was able to connect then, but only once.

---

### Post by helgman on 2007-09-25
I guess I can access it just fine?

I'm using "GNOME Web Browser 2.18.1" (Epiphany) but I get it just fine in Firefox as well. As you see it redirects to [https://mykpr-du.kprdsb.ca/http/kprecmykpr/](https://mykpr-du.kprdsb.ca/http/kprecmykpr/) so try that one directly to see if you can get it to work?

Regards,
Helgman

---

### Post by Ashlord on 2007-09-25
O_O I tested the site in Lynx and it worked but it gave me an interesting prompt about the common name.

The damn certificate doesn't have any CN. I don't know if that interferes with the settings in your browser but the possibility is there.

```
                                                                  myKPR - Login

                              [mykpr_logo.gif]

                                PLEASE LOGIN

          [img-privacy-lock.gif]
                                 Network Username _________
                                 Network Password ________________
                                                  Login  Reset



Reminder

   Please enter the same network username and password that you use to
   log into your computer when at work.

                 Forgot your Network Password? Click Here!


(Text entry field) Enter text.  Use UP or DOWN arrows or tab to move off.
            Enter text into the field by typing on the keyboard
      Ctrl-U to delete text in field, [Backspace] to delete a character

```

---

### Post by altonbr on 2007-09-25
Thanks helgman and Ashlord. I appreciate it!

No, I don't have any settings blocking certificates however and I can't look at it in Links2. I'll try Lynx right now.

Thanks for your help. At least now I know it's not Linux (unless it's Gusty's fault).

I'll try LiveHTTPHeaders (the Firefox plugin) to see if it gives me any clues.

---

### Post by altonbr on 2007-09-25
LiveHTTPHeaders result:

> [http://www.kpr.edu.on.ca/redirect_mykpr.php](http://www.kpr.edu.on.ca/redirect_mykpr.php)

GET /redirect_mykpr.php HTTP/1.1
Host: [www.kpr.edu.on.ca](www.kpr.edu.on.ca)
User-Agent: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.6) Gecko/20070919 Ubuntu/7.10 (gutsy) Firefox/2.0.0.6
Accept: text/xml,application/xml,application/xhtml+xml,text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5
Accept-Language: en-us,en;q=0.5
Accept-Encoding: gzip,deflate
Accept-Charset: ISO-8859-1,utf-8;q=0.7,*;q=0.7
Keep-Alive: 300
Connection: keep-alive
Referer: [http://www.kpr.edu.on.ca/](http://www.kpr.edu.on.ca/)
Cookie: PHPSESSID=23ad2b6a1440fd8b3f0621bdc1f921cd

HTTP/1.x 302 Found
Date: Tue, 25 Sep 2007 18:06:34 GMT
Server: Apache/2.2.3 (Unix) PHP/4.4.4 mod_ssl/2.2.3 OpenSSL/0.9.7e-p1
X-Powered-By: PHP/4.4.4
Location: [https://mykpr-du.kprdsb.ca](https://mykpr-du.kprdsb.ca)
Content-Length: 28
Keep-Alive: timeout=15, max=100
Connection: Keep-Alive
Content-Type: text/html; charset=ISO-8859-1
----------------------------------------------------------

> #request# GET [http://www.kpr.edu.on.ca/favicon.ico](http://www.kpr.edu.on.ca/favicon.ico)
#request# GET [http://www.kpr.edu.on.ca/redirect_mykpr.php](http://www.kpr.edu.on.ca/redirect_mykpr.php)
GET /redirect_mykpr.php
#request# GET [https://mykpr-du.kprdsb.ca/](https://mykpr-du.kprdsb.ca/)

---

