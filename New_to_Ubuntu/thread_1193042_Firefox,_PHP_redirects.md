---
title: "Firefox, PHP redirects"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by rosstheboss on 2009-06-21
Hi all,

I use a web based email client for my studies, and have never had problems with it before. However, upon trying to log on today, after entering my username and password into the web page, a dialog window from firefox opens up asking me if i want to open or save a file named "redirect.php". Instructing it to open with firefox simply opens another tab and brings up the same dialog, as does saving it then opening it.

While I don't expect anyone to know the specifics of this particular webmail, I don't understand exactly what it's trying to do here, and why firefox can't simply allow itself to be redirected.

Thanks,
Ross

---

### Post by rosstheboss on 2009-06-21
Alright, I've asked other firefox specific questions here before and not had them resolved either. Perhaps this is the wrong forum for such a question.

Any suggestions where else I can inquire about this issue?

---

### Post by konqueror7 on 2009-06-21
what i believe is that the webmail your accessing doesn't have PHP installed, or if its local, you may not have installed PHP.

have you tried accessing the same page with other browsers?

---

### Post by Crunchy the Headcrab on 2009-06-21
Sounds like your client has sloppy php coding.  I don't think that this is a problem with firefox but I don't know enough about how it works on Linux to say.  If it doesn't work in other browsers definitely contact support for your email client.  If it does work in other browsers then it must be firefox.

---

### Post by Wim Sturkenboom on 2009-06-21
I'm quite sure it's not Firefox. I have the same issue with websites occasionally; everything is normal if I try a while later.

From my knowledge:
The server is supposed to process the PHP file; the result will (usually) be a valid html document (this is, the content resembles a html page) that is send to the browser. The browser sees this as html and will display accordingly.
If the server, for whatever reason, does not process the PHP file, the PHP file will be send to the browser as is. The browser does not understand it and will offer to save it or display it.

---

### Post by indytim on 2009-06-21
The webserver is NOT parsing php.  Contact the website owner.

IndyTim

---

### Post by rosstheboss on 2009-06-21
Thanks very much for the help! I neglected to say that it did work on other browsers, but Wim and indytim were right, the problem resolved itself this (Monday) morning. Maybe the server just developed a problem over the weekend that only got resolved when the staff returned this morning.

Ross

---

