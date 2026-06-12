---
title: "having problem seeing this wabe site (Flash)"
date: 2009-09-12
forum: New to Ubuntu
---

### Post by cosine352 on 2009-09-12
[http://bc.transloc.com/](http://bc.transloc.com/)

This site is about the real time transportation to locate the real time position of buses. It uses flash player I guess. The problem is firefox can not show the GPS locator. I have the latest adobe flash player installed. I am using Ubuntu 9.04. 

any help will be great.
thanks
I can not

---

### Post by wojox on 2009-09-12
That's cool as hell. I wish I was back home in Mass. So you can't see the little balloons moving in real time?

---

### Post by cosine352 on 2009-09-12
> **wojox said:**
> That's cool as hell. I wish I was back home in Mass. So you can't see the little balloons moving in real time?
that is correct

---

### Post by wojox on 2009-09-12
Using Firefox 3.5.2 ?

Paste into the navigation bar:

```
about:plugins
```

And tell me what version of Flash you have.

---

### Post by cosine352 on 2009-09-12
> **wojox said:**
> Using Firefox 3.5.2 ?

Paste into the navigation bar:

```
about:plugins
```

And tell me what version of Flash you have.

I am using Fiefox 3.0.14 and here is the flash player from about:plugins

> Shockwave Flash

    File name: libswfdecmozilla.so
    Shockwave Flash 9.0 r999

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Adobe Flash movie 	swf 	Yes
application/futuresplash 	FutureSplash movie 	spl 	Yes

> Shockwave Flash

    File name: libgnashplugin.so
    Shockwave Flash 9.0 r999. Gnash 0.8.5, the GNU SWF Player. Copyright © 2006, 2007, 2008 Free Software Foundation, Inc.
    Gnash comes with NO WARRANTY, to the extent permitted by law. You may redistribute copies of Gnash under the terms of the GNU General Public License. For more information about Gnash, see [http://www.gnu.org/software/gnash](http://www.gnu.org/software/gnash). Compatible Shockwave Flash 9.0 r999.

MIME Type 	Description 	Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes

---

### Post by wojox on 2009-09-12
Only thing I could suggest is upgrade to Flash 10.0 which is what I have installed. It's in Synaptic Package Manager.

---

### Post by winotree on 2009-09-12
**cosine352**, I'm using Firefox 3.0.14 and the new Flash 10 and I *can see movement* on the website you linked us to.  (It's cool!)  This update should work for you, too.  :D

---

### Post by cariboo on 2009-09-12
I would also suggest you remove gnash, as there may be a conflict between it and flash.

---

### Post by cosine352 on 2009-09-12
thanks guys. nowit is working. I have installed adobe flash 10. I had to remove all other flash to got it working.

---

