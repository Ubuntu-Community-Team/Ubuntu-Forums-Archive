---
title: "[SOLVED] Gourmet Recipe Manager &amp;amp; Python"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-12-15
When I was offered, by the Update Manager, a revision of: Gourmet Recipe Manager, I clicked Install. Then when I tried to import my 'recipes.xml' file (about 4 meg), the program stalled and said:

Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/gourmet/GourmetThreads.py", line 38, in target_func
    self.c.run()
  File "/usr/lib/python2.5/site-packages/gourmet/importers/importer.py", line 393, in run
    self.iclass.run()
  File "/usr/lib/python2.5/site-packages/gourmet/importers/xml_importer.py", line 62, in run
    self.parse = xml.sax.parse(self.fn, self.rh)
  File "/usr/lib/python2.5/xml/sax/__init__.py", line 33, in parse
    parser.parse(source)
  File "/usr/lib/python2.5/xml/sax/expatreader.py", line 107, in parse
    xmlreader.IncrementalParser.parse(self, source)
  File "/usr/lib/python2.5/xml/sax/xmlreader.py", line 123, in parse
    self.feed(buffer)
  File "/usr/lib/python2.5/xml/sax/expatreader.py", line 207, in feed
    self._parser.Parse(data, isFinal)
  File "/usr/lib/python2.5/xml/sax/expatreader.py", line 304, in end_element
    self._cont_handler.endElement(name)
  File "/usr/lib/python2.5/site-packages/gourmet/importers/gxml2_importer.py", line 50, in endElement
    self.commit_ing()
  File "/usr/lib/python2.5/site-packages/gourmet/importers/importer.py", line 282, in commit_ing
    self.added_ings.append(self.rd.add_ing(self.ing))
  File "/usr/lib/python2.5/site-packages/gourmet/backends/rdatabase.py", line 668, in add_ing
    return self.do_add_ing(dic)
  File "/usr/lib/python2.5/site-packages/gourmet/backends/sql_db.py", line 443, in do_add_ing
    self.do_add(self.iview,ingdict)
  File "/usr/lib/python2.5/site-packages/gourmet/backends/sql_db.py", line 410, in do_add
    self.execute(self.cursor,SQL,d.values())
  File "/usr/lib/python2.5/site-packages/gourmet/backends/sql_db.py", line 114, in execute
    cursor.execute(sql,params)
IntegrityError: PRIMARY KEY must be unique

anybody know how to fix this?

---

### Post by chrisod on 2008-12-15
Have you tried reverting back to the previous version of the application? Also,since this is a question very specific to an application that is not part of the standard Ubuntu distro, you might get better/quicker support from the author of the program. It looks like the problem is not related to Linux, but something about the update has broken the program. This is just a wild guess, but given the references to SQL in the errors, maybe there is a dB update patch that you need to apply prior to running the new version?

---

### Post by Mark_in_Hollywood on 2008-12-16
I found a "the?" solution. From the Sourceforge forum for Gourmet RM

RE: --> Gourmet and Intrepid
By: mumcs01 (mumcs01) - 2008-10-17 15:13
Interesting. I've had problems as well with the webpage import feature as well, though a little different. When I do an import I get an error following the import saying it was unsuccessful, however if I restart the application, the receipe is actually there.

      RE: --> Gourmet and Intrepid
      By: Alex Carlos (alexantao) - 2008-10-17 17:29
      I removed my ~/.gourmet directory and it is working now. Started importing and it is working now.  
       
      I backed up my previous recipes, but I'll not try to bring them back. 
       
      I don't know what happened, maybe some confusion with the version changes. Even purging the data... 
       
      But anyway, it is working now... thanks a lot...

---

