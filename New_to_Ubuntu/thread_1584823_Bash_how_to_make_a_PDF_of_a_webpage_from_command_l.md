---
title: "Bash: how to make a PDF of a webpage from command line?"
date: 2010-09-29
forum: New to Ubuntu
---

### Post by honeybear on 2010-09-29
Curl does webpage to html

but how to transform this hmtl to pdf frmo command line?

thanks if anyone knwos or good ideas

---

### Post by DaithiF on 2010-09-29
Hi, 
there are lots of possibilities, two such are htmldoc and pisa (and its command line client xhtml2pdf)

```
sudo apt-get install htmldoc
htmldoc --webpage source.htm -f target.pdf

```

```
sudo apt-get install python-pisa
xhtml2pdf source.htm target.pdf
```

---

### Post by honeybear on 2010-10-01
Thanks so much !

edit : 

$ xhtml2pdf reviewemail.html reviewemail2.pdf
Traceback (most recent call last):
  File "/usr/bin/xhtml2pdf", line 5, in <module>
    from pkg_resources import load_entry_point
ImportError: No module named pkg_resources

---

### Post by honeybear on 2010-10-01
```
wget -k --random-wait  -e robots=off --user-agent "Mozilla/5.0 Firefox/3.5.12" http://www.bbc.co.uk/news/world/  -O retrieved.html

I wget http://www.bbc.co.uk/news/world/

but converting the news to pdf is not working :(

[CODE]htmldoc --links --numbered --landscape --continuous retrieved.html -f retrievedtmp.pdf
```

---

