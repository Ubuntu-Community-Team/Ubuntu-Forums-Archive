---
title: "chm2pdf not working"
date: 2009-11-17
forum: New to Ubuntu
---

### Post by Sup3r3g0 on 2009-11-17
Here's the command I used.

```
$ chm2pdf --book '/home/username/Desktop/GA39.chm' '/home/username/Desktop/GA40.pdf'
```

And here's what I get. 

```
Traceback (most recent call last):
  File "/usr/bin/chm2pdf", line 1108, in <module>
    main(sys.argv)
  File "/usr/bin/chm2pdf", line 1102, in main
    convert_to_pdf(cfile, filename, outputfilename, options)
  File "/usr/bin/chm2pdf", line 387, in convert_to_pdf
    correct_file(re.sub('\\\\ ', ' ', page_filename), htmlout_filename, html_list, objective_urls, options)
  File "/usr/bin/chm2pdf", line 142, in correct_file
    image_catcher.feed(page)
  File "/usr/lib/python2.6/sgmllib.py", line 104, in feed
    self.goahead(0)
  File "/usr/lib/python2.6/sgmllib.py", line 174, in goahead
    k = self.parse_declaration(i)
  File "/usr/lib/python2.6/markupbase.py", line 98, in parse_declaration
    decltype, j = self._scan_name(j, i)
  File "/usr/lib/python2.6/markupbase.py", line 388, in _scan_name
    % rawdata[declstartpos:declstartpos+20])
  File "/usr/lib/python2.6/sgmllib.py", line 111, in error
    raise SGMLParseError(message)
sgmllib.SGMLParseError: expected name token at '<!\x87#\xad<2\xad\n.A\x18\xa5`)Mh;\x0cU'
```

How do I convert the chm to a pdf?

---

