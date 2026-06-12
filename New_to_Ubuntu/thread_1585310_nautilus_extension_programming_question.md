---
title: "nautilus extension programming question"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by carrarin on 2010-09-30
Hello everyone, I wrote this nautilus extension ... 

```
# Based off OPEN_TERMINAL example by Martin Enlund
import os
import urllib

import nautilus
import gconf

COLORCODE_EXE = 'colorcode.py'
COLORCODE_DIR = '/usr/share/pyshared/colorcode/'

class ColorcodeExtension(nautilus.MenuProvider):
    def __init__(self):
        pass
        
    def runColorcode(self, file):
        filename = urllib.unquote(file.get_uri()[7:])

        os.chdir(COLORCODE_DIR)
        os.system('./' + COLORCODE_EXE )
        
    def menu_activate_cb(self, menu, file):
        self.runColorcode(file)
       
    def get_file_items(self, window, files):
        if len(files) != 1:
            return
        
        file = files[0]
        if not file.is_directory() or file.get_uri_scheme() != 'file':
            return
        
        item = nautilus.MenuItem('NautilusPython::colorcode_file_item',
                                 'Colorcode folder' ,
                                 'Colorcode folder %s' % file.get_name())
        item.connect('activate', self.menu_activate_cb, file)
        return item,

```

This code works! I know that. But, the code makes nautilus bog down and consequently makes my application run ten times slower. 

Why is this?

THanks
carrarin

---

