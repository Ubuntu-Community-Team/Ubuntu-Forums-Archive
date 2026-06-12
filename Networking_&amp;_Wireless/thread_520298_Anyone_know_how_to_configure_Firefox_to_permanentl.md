---
title: "Anyone know how to configure Firefox to permanently accept Gmail HTTPS certificate?"
date: 2007-08-08
forum: Networking &amp; Wireless
---

### Post by kevdog on 2007-08-08
How do I import gmail's openssl certificate into firefox.  I went through the command line and downloaded the certs:

openssl s_client -showcerts -connect gmail.com:443

I tried importing the resultant certificates into firefox, but this didnt exactly work.  Any suggestions?? Im tired of the popup box when visiting [https://gmail.com](https://gmail.com), and want to avoid MIM attacks.

---

### Post by Damiel on 2007-08-08
Can you access Gmail over HTTPS directly with [https://mail.google.com](https://mail.google.com) ?

---

### Post by noob12 on 2007-08-08
That's the recommended thing.  Bookmark it. It won't help to download their cert.  The problem is the mismatch between the name and the url, which will always cause a warning.

---

### Post by kevdog on 2007-08-08
Thanks for the suggestions.  I was hoping there was another way other than typing the long URL :) :
[https://mail.google.com](https://mail.google.com)

---

### Post by noob12 on 2007-08-08
Yeah, but it's called the Bookmark Toolbar.

---

### Post by kevdog on 2007-08-08
*****Damn Bookmark Toolbar --- Hate all those toolbars cluttering my screen:)

---

