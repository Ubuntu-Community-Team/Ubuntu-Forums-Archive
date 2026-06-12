---
title: "Installation problems (Windows - no Disk problems)"
date: 2009-12-23
forum: New to Ubuntu
---

### Post by selloutboy on 2009-12-23
I get this message when I try install Wubi 9.10:

Exception Processing Message 0xc0000013 Parameters 0x75D692A0 0x00000004 0x75D629A0 0x75D692A0


Butt after clicking again after a couple of times, it disappears and the installers starts.

At around 3/4 of the way, I get an error message.


can someone point me to the proper way or at least link me if this was already answered before :)

I already have tried several times already so I wish I could get this solved soon :)

Thank you very much and looking forward to enjoying ubuntu :)

---

### Post by unmole on 2009-12-23
This is a Windows issue. See if this helps [http://wiki.answers.com/Q/How_do_I_remove_exception_processing_message_c0000013_parameters_75b6bf7c4](http://wiki.answers.com/Q/How_do_I_remove_exception_processing_message_c0000013_parameters_75b6bf7c4)

---

### Post by selloutboy on 2009-12-23
> **unmole said:**
> This is a Windows issue. See if this helps [http://wiki.answers.com/Q/How_do_I_remove_exception_processing_message_c0000013_parameters_75b6bf7c4](http://wiki.answers.com/Q/How_do_I_remove_exception_processing_message_c0000013_parameters_75b6bf7c4)


Thanks for the link :D Link doesn't seem to work though... 



Oh and I forgot to mention my specs

Dell Vostro 1200, Vista Business SP1, 1.0 GB RAM, Intel Core2 Duo CPU T7250 @ 2.00Ghz

---

### Post by unmole on 2009-12-23
> **selloutboy said:**
> Thanks for the link :D Link doesn't seem to work though... 



Oh and I forgot to mention my specs

Dell Vostro 1200, Vista Business SP1, 1.0 GB RAM, Intel Core2 Duo CPU T7250 @ 2.00Ghz

Link works for me ! Did you click on it or did you copy and paste ? I clicked with no issues.

---

### Post by selloutboy on 2009-12-23
Ok here's what I did:

I went into Device Manager and disabled my Generic Multi-Card Device (My Card Reader).

The no Disk problems did not appear anymore.

Ubuntu is currently installing. Will update when the entire OS works :)

Thanks Much :)

---

### Post by selloutboy on 2009-12-23
This message appears at around 3/4 the way:

An error occured:
Permission Denied

For more information, please see the log file:
c:\users\ag\appdata\local\temp\wubi-9.10ubuntu1-rev160.log


Here are the contents of that file...

> 
12-23 14:27 INFO   saplog: Verified a signature from ID:'46181433FBB75451'.
12-23 14:27 INFO   saplog: Checking block bindings..
12-23 14:27 INFO   saplog: Key verified successfully.
12-23 14:27 DEBUG  CommonBackend: metalink md5sums:
683777ef543a4b6a45813b7216770ee7  ubuntu-9.10-alternate-amd64.metalink
052059122005c3cafb6ac609a0fe10be  ubuntu-9.10-alternate-i386.metalink
60cd73f45c330846ffa97e4b7a2acd16  ubuntu-9.10-desktop-amd64.metalink
e2297eca9d2807b4341f5790e5603951  ubuntu-9.10-desktop-armel+dove.metalink
cdc858c794f06f7af01f6684d6ff92de  ubuntu-9.10-desktop-armel+imx51.metalink
d39fa28ac9b7793b0ebe1a247515f800  ubuntu-9.10-desktop-i386.metalink
def4596649912b7d93608f1c604472a0  ubuntu-9.10-server-amd64.metalink
526cabdf640f195935877222dbd607b6  ubuntu-9.10-server-i386.metalink

12-23 14:27 DEBUG  TaskList: ### Finished get_metalink
12-23 14:27 DEBUG  TaskList: New task download
12-23 14:27 DEBUG  TaskList: ### Running download...
12-23 14:27 DEBUG  btdownloader: downloading [http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.iso.torrent](http://releases.ubuntu.com/9.10/ubuntu-9.10-desktop-amd64.iso.torrent) > C:\ubuntu\install\ubuntu-9.10-desktop-amd64.iso
12-23 15:57 ERROR  TaskList: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\btdownloader.py", line 79, in download
  File "\lib\bittorrent\download.py", line 303, in download
  File "\lib\bittorrent\RawServer.py", line 256, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request


12-23 15:57 ERROR  TaskList: Non fatal error Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 229, in listen_forever
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Traceback (most recent call last):
  File "\lib\bittorrent\RawServer.py", line 221, in listen_forever
  File "\lib\bittorrent\Rerequester.py", line 96, in fail
  File "\lib\wubi\backends\common\btdownloader.py", line 70, in error_callback
DownloadError: Problem connecting to tracker - HTTP Error 400: Bad Request

 in task download
12-23 15:57 DEBUG  TaskList: ### Finished download
12-23 15:57 ERROR  TaskList: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-9.10-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-9.10-desktop-amd64.iso'
12-23 15:57 DEBUG  TaskList: # Cancelling tasklist
12-23 15:57 DEBUG  TaskList: # Finished tasklist
12-23 15:57 ERROR  root: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-9.10-desktop-amd64.iso'
Traceback (most recent call last):
  File "\lib\wubi\application.py", line 56, in run
  File "\lib\wubi\application.py", line 130, in select_task
  File "\lib\wubi\application.py", line 156, in run_installer
  File "\lib\wubi\backends\common\tasklist.py", line 197, in __call__
  File "\lib\wubi\backends\common\backend.py", line 492, in get_iso
  File "\lib\wubi\backends\common\backend.py", line 348, in download_iso
OSError: [Errno 13] Permission denied: u'C:\\ubuntu\\install\\ubuntu-9.10-desktop-amd64.iso'


still not working for me :(

But will still try to make it work :D

---

### Post by selloutboy on 2009-12-23
still wasn't able to get wubi to work.

Tried 1 more time and the same error occurred. 


Currently DL'ing a torrent of ubuntu 9.10 desktop amd64

Hopefully wubi would work from there.

---

### Post by selloutboy on 2009-12-23
Finally got ubuntu running!!! :D

DL'ed ubuntu ISO through torrent and placed it in the same folder as wubi, worked well.

Currently writing this in Ubuntu :D 

Now I just have to know how to migrate my bookmarks from my Firefox in Vista.

---

