---
title: "use urllib2 to open url"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by sparkyro on 2011-02-04
Let me start off saying im new to python.
 
with that in mind.. I have created a class (my_url) which creates a url for me.
 
now im trying to use 
f = o.open(my_url) 
data = f.read() 
to open this url and display the sourse code
 
the error message im getting is:
 
Traceback (most recent call last):
File "C:\Users\Chris\Desktop\Python\untitled-29.py", line 62, in <module>
f = o.open(my_url)
File "C:\Python27\lib\urllib2.py", line 384, in open
protocol = req.get_type()
AttributeError: url instance has no attribute 'get_type'
 
Is there anyway urllib will use a class for a full url ??

---

### Post by robsoles on 2011-02-12
Welcome to UF, sorry I'm going to refer you elsewhere because python is not specifically an Ubuntu 'problem'.

[http://www.python.org/doc//current/howto/urllib2.html](http://www.python.org/doc//current/howto/urllib2.html)

---

