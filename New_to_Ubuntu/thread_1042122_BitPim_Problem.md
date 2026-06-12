---
title: "BitPim Problem"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by jpoRS on 2009-01-17
Hey Folks,

I am trying to make some ringtones, but BitPim is giving me the following error:

```
BitPim version: 1.0.5-Debian
An unexpected exception has occurred.
Please see the help for details on what to do.

Traceback (most recent call last):
  File "/usr/share/bitpim/code/gui.py", line 248, in OnClose
    self.goforit()
  File "/usr/share/bitpim/code/gui.py", line 245, in goforit
    self.app.makemainwindow()
  File "/usr/share/bitpim/code/gui.py", line 548, in makemainwindow
    self.frame=MainWindow(None, -1, title, self.config)
  File "/usr/share/bitpim/code/gui.py", line 896, in __init__
    self.tree.CreatePhone("Phone", self.config, self.configpath, "bitpim.db")
  File "/usr/share/bitpim/code/phone_root.py", line 124, in CreatePhone
    phone.Initialise(self, self.mw, config, path, phone_id, database_name)
  File "/usr/share/bitpim/code/phone_root.py", line 331, in Initialise
    self.EnsureDatabase(self.path, self.path, database_name)
  File "/usr/share/bitpim/code/phone_root.py", line 427, in EnsureDatabase
    self.database=database.Database(newdbpath, vtabs)
  File "/usr/share/bitpim/code/database.py", line 344, in __init__
    idquote(vtable['modulename'])))
  File "apsw.c", line 3518, in resetcursor
IOError: IOError: disk I/O error

Variables by last 8 frames, innermost last

Frame goforit in /usr/share/bitpim/code/gui.py at line 245
           self =  <gui.MySplashScreen; proxy of C++ wxSplashScreen instance at _c038510200000000_p

Frame makemainwindow in /usr/share/bitpim/code/gui.py at line 548
           self =  <gui.MainApp; proxy of C++ wxPyApp instance at _40453b0100000000_p_wxPyApp>
           name =  None
          title =  'BitPim'

Frame __init__ in /usr/share/bitpim/code/gui.py at line 896
           help =  'Export Media Files to a Zip file'
            pos =  200
        expmenu =  <wx._core.Menu; proxy of C++ wxMenu instance at _e0147d0200000000_p_wxMenu>
             ib =  <wx._gdi.IconBundle; proxy of C++ wxIconBundle instance at _e038790200000000_p_w
             id =  -1
          title =  'BitPim'
           menu =  <wx._core.Menu; proxy of C++ wxMenu instance at _f0a07e0200000000_p_wxMenu>
           self =  <gui.MainWindow; proxy of C++ wxFrame instance at _c098740200000000_p_wxFrame>
          _desc =  'Execute'
          _help =  'Perform Auto Calendar Import'
         config =  <bp_config.Config instance at 0x1085368>
          _func =  None
        impmenu =  <wx._core.Menu; proxy of C++ wxMenu instance at _f0367b0200000000_p_wxMenu>
         parent =  None
           func =  <function OnFileExportMediaZip at 0x1f50a28>
              x =  185
           desc =  'Media to Zip File...'
             sz =  wx.Size(32, 32)
       _submenu =  <wx._core.Menu; proxy of C++ wxMenu instance at _b08c7b0200000000_p_wxMenu>
             sb =  <guiwidgets.MyStatusBar; proxy of C++ wxStatusBar instance at _700d530200000000_
            _id =  180
        menuBar =  <wx._core.MenuBar; proxy of C++ wxMenuBar instance at _e08d7a0200000000_p_wxMenu

Frame CreatePhone in /usr/share/bitpim/code/phone_root.py at line 124
           name =  'Phone'
  database_name =  'bitpim.db'
       phone_id =  <wx._controls.TreeItemId; proxy of C++ wxTreeItemId instance at _608500030000000
          phone =  <phone_root.Phone; proxy of C++ wxScrolledWindow instance at _3087e60200000000_p
           path =  '/home/owner/.bitpim-files'
         config =  <bp_config.Config instance at 0x1085368>
           self =  <phone_root.PhoneTree; proxy of C++ wxPyTreeCtrl instance at _70e0a20200000000_p

Frame Initialise in /usr/share/bitpim/code/phone_root.py at line 331
      blob_path =  'bitpim.db_blobs'
           tree =  <phone_root.PhoneTree; proxy of C++ wxPyTreeCtrl instance at _70e0a20200000000_p
  database_name =  'bitpim.db'
       phone_id =  <wx._controls.TreeItemId; proxy of C++ wxTreeItemId instance at _608500030000000
           self =  <phone_root.Phone; proxy of C++ wxScrolledWindow instance at _3087e60200000000_p
             mw =  <gui.MainWindow; proxy of C++ wxFrame instance at _c098740200000000_p_wxFrame>
           path =  '/home/owner/.bitpim-files'
         config =  <bp_config.Config instance at 0x1085368>
             id =  None

Frame EnsureDatabase in /usr/share/bitpim/code/phone_root.py at line 427
        newpath =  '/home/owner/.bitpim-files'
           self =  <phone_root.Phone; proxy of C++ wxScrolledWindow instance at _3087e60200000000_p
        oldpath =  '/home/owner/.bitpim-files'
          vtabs =  [{'args': ('/home/owner/.bitpim-files/ringer',), 'modulename': 'ringtonemodule',
      newdbpath =  '/home/owner/.bitpim-files/bitpim.db'
  database_file =  'bitpim.db'

Frame __init__ in /usr/share/bitpim/code/database.py at line 344
  virtualtables =  [{'args': ('/home/owner/.bitpim-files/ringer',), 'modulename': 'ringtonemodule',
         vtable =  Keys ['args', 'moduleclass', 'modulename', 'tablename']
                   {'args': ('/home/owner/.bitpim-files/ringer',), 'modulename': 'ringtonemodule', 
         icheck =  u'ok'
           self =  <database.Database instance at 0x2e49518>
       filename =  '/home/owner/.bitpim-files/bitpim.db'
            row =  (u'ok',)

Frame resetcursor in apsw.c at line 3518

```

This happened right when I opened BitPim for the first time, as the problem came with the download (which I got from the repositories).  Also When I try and run it from terminal I get the same error, and no output in terminal.

I am running 8.10 on a System76.

Thanks,
jim

---

