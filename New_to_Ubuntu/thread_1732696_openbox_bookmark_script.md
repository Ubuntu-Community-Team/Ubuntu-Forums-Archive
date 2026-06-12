---
title: "openbox bookmark script"
date: 2011-04-18
forum: New to Ubuntu
---

### Post by dzon65 on 2011-04-18
I'm looking for a script that allows me to open my Firefox bookmarks list from within my openbox menu  AND allows me to launch a bookmark from there.
I've got a script that shows me the bookmarks, but so far I can't launch an item. Any ideas?

---

### Post by Minx'ish on 2011-04-18
Hm. 

Does the code for the link (your bookmark(s) menu entry in your menu) in your menu's configuration file say anything similar to (for instance, if the bookmarked site is *ubuntuforums.org*):

[CENTER]firefox [http://ubuntuforums.org](http://ubuntuforums.org)[/CENTER]

---

### Post by dzon65 on 2011-04-19
I just randomly picked some that are available from the openbox pipe wiki. Here's the py I'm using to get into the bookmarks menu:

#!/usr/bin/env python
import sqlite3
from xml.sax.saxutils import quoteattr

import shutil
import tempfile

browser = 'firefox'
ffsqlite= '/home/john/.mozilla/firefox/mhvwa9ef.default/places.sqlite'

def print_label(title,url):
    print '<item label=%s>' % (quoteattr(title.encode('utf-8')))
    print '<action name="Execute">'
    print '<command>%s %s</command>'  % (browser,quoteattr(url.encode('utf-8')))
    print '</action>'
    print '</item>'


def build_tree(conn):
    c = conn.cursor()
    c.execute('select id,parent,title from moz_bookmarks where type = 2 and parent=2;')
    for id,parent,title in c:
        rbuild_tree(id,title, conn)
    c.execute('select b.title,p.title,p.url from moz_bookmarks b, moz_places p where b.fk = p.id and b.type=1 and parent=2;')
    for btitle, ptitle, url in c:
                if url == None or url.startswith("place"):
                    continue
                if btitle != None:
                    print_label(btitle,url)
                else:
                    print_label(btitle,url)


def rbuild_tree(id, title, conn):
        print '<menu id="%s" label=%s>' % (id, quoteattr(title.encode('utf-8')))
        c2 = conn.cursor()
        c2.execute('select id,title,type from moz_bookmarks b where parent=? and type=2;',(id,))
        for sid,stitle,type in c2:
            rbuild_tree(sid,stitle,conn)
        c2.execute('select b.title,p.title,p.url from moz_bookmarks b, moz_places p where b.fk = p.id and b.type=1 and parent=?;',(id,))
        for btitle, ptitle, url in c2:
            if url == None or url.startswith("place"):
                continue
            if btitle != None:
                print_label(btitle,url)
            else:
                print_label(btitle,url)
        print "</menu>"

def main():

    tf = tempfile.NamedTemporaryFile('r', suffix='.sqlite')

    shutil.copyfile(ffsqlite, tf.name)
    conn = sqlite3.connect(tf.name)

    print '<openbox_pipe_menu>'
    build_tree(conn)
    print '</openbox_pipe_menu>'

    conn.close()
    tf.close()

if __name__ == '__main__':
    main()



I tried some obm-moz commands but I only managed to get into the firefox menu.

, I came across a script that works with opera, so should be possible to have 'em launched.

---

