---
title: "Viewing Url's with a dash (-) in them?"
date: 2011-06-03
forum: New to Ubuntu
---

### Post by DizzyPound on 2011-06-03
Hi, I'm new to this forum so I'm not quite sure where this would go but since I'm a beginner I thought it may seem appropriate.

I want to view a url with a dash/hyphen in it but I can't on Firefox or Chromium
ex: -example.tumblr.com
or: example-.tumblr.com

Is there any way to get around this?

Thank you!

---

### Post by TeoBigusGeekus on 2011-06-03
Can you give us a real url?

---

### Post by DizzyPound on 2011-06-03
Yes of course.


[http://p0keball-.tumblr.com/](http://p0keball-.tumblr.com/)

---

### Post by Chronon on 2011-06-03
According to some quick searching a label in a domain (string delimited by ".") should never begin or end with a hyphen.  I'm not sure where this is codified as a formal rule but because of this firefox probably doesn't consider these valid domain names.

---

### Post by DizzyPound on 2011-06-03
When I was using windows, I was always able to view any url like those on Firefox/Chrome/etc.

Is it just a Ubuntu thing I guess then?

---

### Post by brandlerson on 2011-06-03
Tumblr doesn't allow hyphens at the beginning or end of a URL. Have you tried removing the it? (e.g. [http://p0keball.tumblr.com/](http://p0keball.tumblr.com/))

---

### Post by DizzyPound on 2011-06-03
They did for a long time but then they stopped allowing people to use hyphens there.
Now the only people that can use them are the ones that have kept them from the beginning.

But that's a whole different person if I take out the hyphen.

I figured out how to follow the person but I just can't view her blog/ask questions unfortunately.

---

### Post by Wim Sturkenboom on 2011-06-03
It's not Ubuntu specific; checked it with Firefoefox in Crunchbang Statler and Firefox also complains about the original URL

---

### Post by DizzyPound on 2011-06-03
> **Wim Sturkenboom said:**
> It's not Ubuntu specific; checked it with Firefoefox in Crunchbang Statler and Firefox also complains about the original URL

Does that mean it wouldn't work in Windows as well then? I never had problems there...

---

### Post by brandlerson on 2011-06-03
It works on Safari, Chrome, and Firefox for OS X and Windows 7.

UPDATE: I am unable to "ping" or "traceroute" the url in Linux, error: cannot handle "host." This leads me to believe that the browsers are not at fault.

---

### Post by Wim Sturkenboom on 2011-06-04
> **DizzyPound said:**
> Does that mean it wouldn't work in Windows as well then? I never had problems there...That's not what I said ;) I said it was not specific to Ubuntu.

---

### Post by camurgo on 2011-10-14
> **Wim Sturkenboom said:**
> That's not what I said ;) I said it was not specific to Ubuntu.

As far as I know it's a linux in general problem, which unfortunately persists to this day. 

A very impractical workaround to the problem is adding each and every hyphenated url to /etc/hosts, like this: "174.121.194.34 p0keball-.tumblr.com"

The aforementioned IP is of 'tumblr.com'. But, as all of you can see, very impractical.

---

