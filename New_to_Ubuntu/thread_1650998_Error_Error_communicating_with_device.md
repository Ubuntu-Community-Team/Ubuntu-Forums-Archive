---
title: "Error: Error communicating with device"
date: 2010-12-22
forum: New to Ubuntu
---

### Post by DayLite on 2010-12-22
I was downloading files to my Sony Daily Edition Reader from Calibre. Then I got this message and now it won't work.  What is wrong? I have Calibre 0.6.42


```
 p, li { white-space: pre-wrap; } [Errno 5] Input/output error
  Traceback (most recent call last):
   File "/usr/lib/calibre/calibre/gui2/device.py", line 56, in run
     self.result = self.func(*self.args, **self.kwargs)
   File "/usr/lib/calibre/calibre/gui2/device.py", line 212, in _books
     mainlist = self.device.books(oncard=None, end_session=False)
   File "/usr/lib/calibre/calibre/devices/prs505/driver.py", line 113, in books
     bl = BookList(open(prefix + db, 'rb'), prefix, self.report_progress)
   File "/usr/lib/calibre/calibre/devices/prs505/books.py", line 135, in __init__
     self.document = dom.parse(xml_file)
   File "/usr/lib/python2.6/xml/dom/minidom.py", line 1918, in parse
     return expatbuilder.parse(file)
   File "/usr/lib/python2.6/xml/dom/expatbuilder.py", line 928, in parse
     result = builder.parseFile(file)
   File "/usr/lib/python2.6/xml/dom/expatbuilder.py", line 204, in parseFile
     buffer = file.read(16*1024)
 IOError: [Errno 5] Input/output error
 
```

---

