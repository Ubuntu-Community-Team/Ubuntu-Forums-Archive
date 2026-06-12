---
title: "sirius"
date: 2010-05-19
forum: New to Ubuntu
---

### Post by nhovan on 2010-05-19
i am trying to listen to sirius on 10.04 and i have followed the instructions about sipie i found on here and it isnt work. 
i have even tried gxine and the plugin. i can get gxine to pop up when i log into sirius but it isnt playing any sound.

my sipie problem is this:
File "/usr/lib/python2.6/HTMLParser.py", line 108, in feed
    self.goahead(0)
  File "/usr/lib/python2.6/HTMLParser.py", line 148, in goahead
    k = self.parse_starttag(i)
  File "/usr/lib/python2.6/HTMLParser.py", line 226, in parse_starttag
    endpos = self.check_for_whole_start_tag(i)
  File "/usr/lib/python2.6/HTMLParser.py", line 301, in check_for_whole_start_tag
    self.error("malformed start tag")
  File "/usr/lib/python2.6/HTMLParser.py", line 115, in error
    raise HTMLParseError(message, self.getpos())
HTMLParser.HTMLParseError: malformed start tag, at line 100, column 3



and then it just sits. im a n00b so i apologize in advance if this is a dumb question.

---

### Post by nhovan on 2010-05-19
im trying to listen to sirius radio on linux but cant.
i have tried sipie but it isnt working. can anyone help me out?
the error i get when i run sippie is this:

File "/usr/lib/python2.6/HTMLParser.py", line 115, in error
    raise HTMLParseError(message, self.getpos())
HTMLParser.HTMLParseError: malformed start tag, at line 100, column 3


has anyone seen that before?

---

### Post by cariboo on 2010-05-19
Please don't create multiple threads on the same subject, I have merged your two threads.

---

### Post by dummy910 on 2010-06-01
i haven't tried this yet(makes total sense to this tech brain though), but according to another solution posted here on this board for this issue is the following:

in a terminal:
**sudo apt-get install gstreamer0.10-plugins-bad**

---

### Post by darnellearly on 2010-06-04
> **dummy910 said:**
> i haven't tried this yet(makes total sense to this tech brain though), but according to another solution posted here on this board for this issue is the following:

in a terminal:
**sudo apt-get install gstreamer0.10-plugins-bad**


Is this all that needs to be done from a fresh 10.04 install?  or is there more?

---

### Post by sdredwingsfan on 2010-07-05
i'm also having the same issue and tried the gstreamer0.10-plugins-bad but that didn't help either.

---

