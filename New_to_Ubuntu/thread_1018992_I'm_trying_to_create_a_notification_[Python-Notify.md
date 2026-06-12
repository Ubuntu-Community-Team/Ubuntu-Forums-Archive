---
title: "I'm trying to create a notification [Python-Notify SAC (SteepandCheap)]"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by jerrycrabb on 2008-12-22
Hello all,

Slowly but surely I'm learning to love ubuntu. 

I'm attempting to create a desktop notifier for steepandcheap.com (If you're unfamiliar with this website, and like outdoors gear, then you owe it to yourself to check it out.)

Anyway I found some instructions in another forum online. The creator used the following code with python-notifier:
```


#!/usr/bin/python

"""

SAC RSS Notification Tool v0.2
(c) 2008 Michael Seiler and Eric Larson


"""

import urllib
import Image, cStringIO
from xml.dom import minidom
from pynotify import *
import gtk, gobject
import subprocess

#Global Constants
TIMEOUT = EXPIRES_DEFAULT                   #Time in milliseconds for the popup to stick around
                                            #Use EXPIRES_DEFAULT for the default or EXPIRE_NEVER for forever
WEBSITE = 'http://www.steepandcheap.com'    #SAC Website
CHECK_DELAY = 15                            #Time in seconds between website checks
BROWSER = '/usr/lib/firefox-3.0/firefox.sh' #No symlinks!
FEEDADDRESS = 'http://feeds.feedburner.com/SteepandCheap' # SAC RSS Feed
ICONURL = 'http://images.steepandcheap.com/images/icon/steepcheap.ico' # SAC statusbar icon URL
SHOW_NOTIFICATION_ICON = True               # Show SAC icon in notification area?
RECHECK_ON_CLICK = False                    # Check the SAC deal every time the notifier is activated by clicking the icon?

def url2pixbuf(imgurl):
    img_feed = None
    
    try:
        img_feed = urllib.urlopen(imgurl).read()
    except:
        img_feed = None
    if img_feed:
        im = Image.open(cStringIO.StringIO(img_feed)).convert("RGB")
        return gtk.gdk.pixbuf_new_from_data(im.tostring(),gtk.gdk.COLORSPACE_RGB,False,8,im.size[0],im.size[1],3*im.size[0])
    else:
        return None

class MyNotify(object):
    """

    MyNotify

        Create and maintain the notification window and corresponding action methods

        USAGE:  n = MyNotify()
                n.notify(title, message)

    """

    def notify(self, title, message, imgPixbuf):
        """Show notification with a buy button and image"""
        
        self.notification.update(title, message)
        
        if imgPixbuf:
            self.notification.set_icon_from_pixbuf(imgPixbuf)
            
        self.notification.show()
        self.isvisible = True

    def icon_clicked(icon,event,self):
        if self.isvisible:
            self.notification.close()
        else:
            if RECHECK_ON_CLICK and not self.checkingnow:
                self.site_poll_timeout()
            self.notification.show()
            self.isvisible = True

    def show_menu(self, icon, button, time):
        self.menu.popup(None, None, gtk.status_icon_position_menu, button, time, icon)

    def quit_clicked(self, menuItem):
        if self.isvisible:
            self.notification.close()
        gtk.main_quit()

    def open_site(self, n, action):
        """Called if the user clicks the buy button"""

        subprocess.Popen([BROWSER, WEBSITE])

    def destroy(self, n, action=None):
        """Called whenever the window disappears"""

        self.isvisible = False
    
    def __init__(self):

        init('sacrss.py')

        self.notification = Notification("Product", "Pricing", gtk.STOCK_DIALOG_WARNING)
    
        self.notification.set_urgency(URGENCY_LOW)
        self.notification.set_timeout(TIMEOUT)
  
        self.notification.connect('closed', self.destroy)

        self.notification.add_action('buy', 'Buy this item', self.open_site)    #User clicks button


class SAC_notifier(MyNotify):
    """

    SAC_notifier

        Handle timing, notification, and gtk interaction

        USAGE:  s = SAC_notifier()
                s.main()

        Creates a timeout that downloads information from SAC every CHECK_DELAY seconds,
        then pops up a notification using pynotify if it finds a different product.


    """

    def read_data(self):
        """Read data from the SAC website, then parse it"""
        self.checkingnow = True
        self.new_product = ""
        self.description = ""
        self.imgLocation = ""
        self.priceCurrent = ""
        self.priceRegular = ""
        self.imgPixbuf = None

        try:
            self.file_feed = urllib.urlopen(FEEDADDRESS).read()
        except:
            #No interweb connection? SAC down?
            self.file_feed = None

        if self.file_feed:
            self.file_xml = minidom.parseString(self.file_feed)
            self.item_node = self.file_xml.getElementsByTagName("item")
        

            for childNode in self.item_node[0].childNodes:
                if childNode.nodeType == childNode.ELEMENT_NODE:
                    if childNode.tagName == 'title':
                        self.new_product = childNode.firstChild.data
                    if childNode.tagName == 'sac:listDescription':
                        self.description = childNode.firstChild.data
                    if childNode.tagName == 'sac:priceCurrent':
                        self.priceCurrent = childNode.firstChild.data
                    if childNode.tagName == 'sac:priceRegular':
                        self.priceRegular = childNode.firstChild.data
                    if childNode.tagName == 'sac:tinyImage':
                        self.imgLocation = childNode.firstChild.data

            self.imgPixbuf = url2pixbuf(self.imgLocation)

        self.checkingnow = False

    def site_poll_timeout(self):
        """Timeout called every CHECK_DELAY secs, which calls read_data, then notify if the item changed"""

        self.read_data()

        if self.file_feed:
            if self.new_product != self.old_product and not self.new_product in self.seen_products:
                if self.new_product:
                    percOff = '%d' % round(100.0*(float(self.priceRegular) - float(self.priceCurrent))/float(self.priceRegular))
                    descriptionString = "\n<b>Price: $" + self.priceCurrent + " (" + percOff + "% off!)</b>\nRegularly: $" + self.priceRegular + "\n\n" + self.description
                    self.notify(self.new_product, descriptionString, self.imgPixbuf)
                    self.seen_products.append(self.new_product)
                    self.old_product = self.new_product

        return True

    def main(self):
        """Create the timeout object and let the program sit in gtk.main()"""

        self.site_poller = gobject.timeout_add(self.seconds_to_check, self.site_poll_timeout)

        if SHOW_NOTIFICATION_ICON:
            self.icon = gtk.StatusIcon()
            iconBuf = url2pixbuf(ICONURL)
            if iconBuf:
                self.icon.set_from_pixbuf(iconBuf)
            else:
                self.icon.set_from_stock(gtk.STOCK_DIALOG_ERROR)
            self.menu = gtk.Menu()
            quit = gtk.MenuItem("Quit")
            quit.connect("activate", self.quit_clicked)
            quit.show()
            self.menu.append(quit)
            self.icon.connect("activate", self.icon_clicked, self)
            self.icon.connect("popup-menu", self.show_menu)
    
        gtk.main()

    def __init__(self):

        MyNotify.__init__(self)

        self.old_product = ""
        self.new_product = ""
        self.priceCurrent = ""
        self.priceRegular = ""
        self.imgPixbuf = None
        self.isvisible = False

        self.seen_products = list()

        self.seconds_to_check = CHECK_DELAY * 1000
        
        self.checkingnow = False

        self.site_poll_timeout()


if __name__ == '__main__':

    s = SAC_notifier()
    s.main()

```

According to the instructions I found I'm simply supposed to "run the command" and viola.... I have my desktop notifier.

I have had no such luck.

I have saved the sac.py file but when typing "sudo ./sac.py" into the terminal I only get

"command not found"

I have also tried:
sudo /sac.py
sudo /home/user/sac.py (this is where the file is)
sudo ./home/user/sac.py
sudo run ./sac.py
sudo run /sac.py
sudo run /home/user/sac.py
sudo run ./home/user/sac.py


Does anybody have any suggestions?


Thank you for your time

-Jerry

---

### Post by chrisod on 2008-12-22
You might have better luck with this over in the programming forum. This really isn't absolute beginner material :)

---

### Post by jerrycrabb on 2008-12-22
I dunno,

I pretty terrified of being made fun of in any other forum....

---

### Post by mc4man on 2008-12-22
Overall I don't know how it'll work but to start remove this (last 2 lines written

> </code>

the code is saved into a file "sac.py".

Then try again with either ./sac.py or python ./sac.py

edit 
plus in terminal go before using
 ```
chmod +x sac.py
```
or maybe chmod u+x (not sure

---

### Post by jerrycrabb on 2008-12-22
Thanks,

The last two lines of code were actually a mistake I made when posting my question here. I have fixed that in the post.

I will try the recommended prefix in the terminal and report back.

---

### Post by mc4man on 2008-12-22
I don't know python but another obvious mistake in script is line 23

> BROWSER = '/usr/lib/firefox-3.0/firefox.sh' #No symlinks!

should be (at least here, ck. in your install


```
BROWSER = '/usr/lib/firefox-3.0.4/firefox.sh'
```

don't know how this is supposed to work, just tried, see a little green icon in upper taskbar, clicking on pulls up notification box, does connect to site on  clicking 'buy now'. 
Seems to only have shown 2 different items over 5 min. period (sandals now ...?

---

### Post by jerrycrabb on 2008-12-22
Thank you Mac4Man

python ./sac.py    Ran the command I was looking for!

One thing left, when the notifier comes up, clicking on the buy this item button should launch the website in my browser.

I think the browser launch command in the code is incorrect.

what should I replace it with in order to launch my browser, ie, where can I find the command that will launch firefox?

thanks,

Jerry

---

### Post by 76tdffixie on 2009-10-07
[FONT=Times New Roman][SIZE=3]I don't know if any of you guys have been following the golden deal days or one dollar deal days on steepandcheap but if you have you probably have missed out on a few deals because you were too slow to purchase the item.  I would love to create a script that could alert me when ever there was an item up for 1 dollar on any of the backcounty.com sites (steepandcheap.com, chainlove.com, brociety.com, tramdock.com, bonktown.com, and whiskeymilitia.com).  It would be sweet if it could automatically purchase the item as well, but that may be too difficult.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3] [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]The problem is I know nothing about scripting and by the time I could learn the one dollar deal days will probably be over.  If one of you guys could create something like this maybe we could all benefit.[/SIZE][/FONT]

---

