---
title: "Automatically grab webpage content and send it via email to predefined address"
date: 2013-12-20
forum: Networking &amp; Wireless
---

### Post by nickpetrikusa on 2013-12-20
Hi,

I am not sure if that is the correct place to ask this question but I still hope to get some advice / directions to achieve the below.

I want to my system to grab the content of a webpage and send it to a predefined email address. This should run every hour.

Thanks a lot for your help. Regards Nick

---

### Post by tfrue on 2013-12-20
I would check out using wget, crontab, and mail. Assuming you are doing this through the command line. Here is an interesting article on wget:
[http://www.cyberciti.biz/tips/linux-wget-your-ultimate-command-line-downloader.html](http://www.cyberciti.biz/tips/linux-wget-your-ultimate-command-line-downloader.html)

Here are the manpages for each command:
[wget]("http://linux.die.net/man/1/wget")
[URL="http://ss64.com/bash/crontab.html"]crontab
[/URL][mail]("http://linux.die.net/man/1/mail")

Maybe set up wget to download files every so often or if there is a way to keep wget open then do that. If that doesn't work, set up crontab to start wget every hour and download the files, then another crontab entry to use 'mail' which would mail it to your email address. 

Good luck!

---

### Post by nickpetrikusa on 2013-12-20
Hi Chis,

Thanks for your reply. However I think that I'll go with Python.

I got this scrip to take a screenshot of a webpage and store it. Now I only need a python script to send the file to a predefined email address and add both scripts to CRON.

-------------------------------------- snip ---------------------------------------------
import sys
import time
from PyQt4.QtCore import *
from PyQt4.QtGui import *
from PyQt4.QtWebKit import *


class Screenshot(QWebView):
    def __init__(self):
        self.app = QApplication(sys.argv)
        QWebView.__init__(self)
        self._loaded = False
        self.loadFinished.connect(self._loadFinished)


    def capture(self, url, output_file):
        self.load(QUrl(url))
        self.wait_load()
        # set to webpage size
        frame = self.page().mainFrame()
        self.page().setViewportSize(frame.contentsSize())
        # render image
        image = QImage(self.page().viewportSize(), QImage.Format_ARGB32)
        painter = QPainter(image)
        frame.render(painter)
        painter.end()
        print 'saving', output_file
        image.save(output_file)


    def wait_load(self, delay=0):
        # process app events until page loaded
        while not self._loaded:
            self.app.processEvents()
            time.sleep(delay)
        self._loaded = False


    def _loadFinished(self, result):
        self._loaded = True


s = Screenshot()
s.capture('http://cnn.com/', 'cnn.png')
-------------------------------------- snip ---------------------------------------------

Regards Nick

---

### Post by tfrue on 2013-12-20
Sounds good! 

-Chris

---

