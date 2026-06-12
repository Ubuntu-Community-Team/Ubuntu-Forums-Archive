---
title: "Webpage Viewing problem"
date: 2010-03-06
forum: New to Ubuntu
---

### Post by nns2006 on 2010-03-06
I am trying to access this [web page]("http://www.panchjanya.com/dynamic/modules.php?name=Content&pa=showpage&pid=367&page=5") it is written in Hindi Language. At first I was not able to see the web page correctly (for me its first time !!).Then I downloaded the fonts given for download and moved them to [HTML]/usr/share/fonts[/HTML], I was hoping this would solve my problem but despite doing this I am still not able to see the web page correctly. 

Please help.
Thanks in advance.

---

### Post by arochester on 2010-03-06
> I am still not able to see the web page correctly Can you either provide a screenshot so we can see what you mean, or can you explain what the problem with the website is?

---

### Post by Greenwidth on 2010-03-06
There is a Hindi version of Firefox here:
[http://www.mozilla.com/en-US/firefox/all.html](http://www.mozilla.com/en-US/firefox/all.html)

---

### Post by nns2006 on 2010-03-06
> **arochester said:**
> Can you either provide a screenshot so we can see what you mean, or can you explain what the problem with the website is?


I am attaching the screenshot of the webpage. It should be in Hindi but is in not so.

---

### Post by nns2006 on 2010-03-06
I am not looking for HIndi version of firefox . I am just not able to read the webpage that is written in Hindi despite installing the fonts they have provided.

---

### Post by houseworkshy on 2010-03-06
It looks a mess to me too, as does it's source.  I'm not a hindi speaker however, [http://in.jagran.yahoo.com/](http://in.jagran.yahoo.com/) and other sites look, to me, ok.  If they look ok to you too then I assume that it is the fault of the site and not your system.

---

### Post by nns2006 on 2010-03-06
> **houseworkshy said:**
> It looks a mess to me too, as does it's source.  I'm not a hindi speaker however, [http://in.jagran.yahoo.com/](http://in.jagran.yahoo.com/) and other sites look, to me, ok.  If they look ok to you too then I assume that it is the fault of the site and not your system.

Others sites are great .I am attaching the screenshot for the other Hindi webpage.

---

### Post by wojox on 2010-03-06
Where did you download the fonts from? 

These are what you need:

DVW-TTSurekh

DV-TTSurekh

Try refreshing your font cache:

```
fc-cache -fv
```

---

### Post by prenoob on 2010-03-06
> **nns2006 said:**
> Others sites are great .I am attaching the screenshot for the other Hindi webpage.Yes, that's fine isn't it?  I can't help but I can see quite a few Russian characters in the "text" on the problem page.  Possibly, that gives you some way to track down the problem.

---

### Post by Rolie on 2010-03-06
I can resolve the problem for 90% when switching to Hindi manually (using the View > Encoding menu in Firefox). 10% of the characters still do not look Hindi to me.

You could try to also install the package ttf-indic-fonts, if you didn't do so already.

---

