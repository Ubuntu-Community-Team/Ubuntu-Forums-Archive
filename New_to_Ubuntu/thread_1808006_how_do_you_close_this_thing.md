---
title: "how do you close this thing?"
date: 2011-07-19
forum: New to Ubuntu
---

### Post by LHolcomb on 2011-07-19
I've tried everything I can think of I still get this error ,,, how do i get rid of it?


Syntax error on line 231 of /etc/apache2/apache2.conf: Syntax error on line 4 of /etc/apache2/sites-enabled/000-default-ssl: /etc/apache2/sites-enabled/000-default-ssl:35: <email.mysite*:443> was not closed.\n/etc/apache2/sites-enabled/000-default-ssl:4: <email.mysite*:443> was not closed.[http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

---

### Post by Dangertux on 2011-07-19
I am guessing it should be a

```

<VirtualHost>

```So it would be something like this

```

<VirtualHost email.mysite:443>
...
...
...
</VirtualHost>

```Not sure what is in your apache2.conf file, if you post the contents of line 231 I can probably help you.

---

