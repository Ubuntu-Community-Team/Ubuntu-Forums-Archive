---
title: "what plug ins do I need?"
date: 2009-10-04
forum: New to Ubuntu
---

### Post by hduguay on 2009-10-04
Hey there
I am relatively new to Linux. I am trying to watch video feeds of cbc.ca but I am missing the plug in required to view these news feeds. I was wondering if anyone could help me with this. I tried to load a couple plug ins but none of them seem to do the trick. Any assistance with this would be greatly appreciated.

---

### Post by inobe on 2009-10-04
hi

in synaptic search for **ubuntu-restricted-extras**

that will install various things like java, codecs, flash player, fonts......


if you just want flash search for **flashplugin-nonfree** and **flashpligin-installer**

---

### Post by ikisham on 2009-10-04
Do you have Flash player installed? If not then
```
sudo apt-get install flashplugin-nonfree
```

Also you can install all the Gstreamer plugins: go to Applications > Software Center > Sound & Video and search for them.

---

### Post by Mylorharbour on 2009-10-04
Hi hduguay, welcome aboard.

In the Multimedia forum you'll find a sticky... [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

You should find the answer there.

Cheers

---

### Post by hduguay on 2009-10-04
I tried installing gstreamer,ubuntu restricted areas and am still unable to view newsfeeds from this particular website. I tried everything suggested, and still no change.

---

### Post by the.phantom on 2009-10-04
they changed something on their site ! i have watched their video's until about 2 weeks ago and no  they won't play!
i would go here
[http://www.cbc.ca/news/](http://www.cbc.ca/news/)

and click "latest video"

if you want to check your flash, go to [http://news.bbc.co.uk/](http://news.bbc.co.uk/) 
;-D

---

### Post by hduguay on 2009-10-05
I tried the link for [https://news.bbc.co.uk](https://news.bbc.co.uk). It seems to work fine and then tried CBC latest vides and still no go.

---

### Post by the.phantom on 2009-10-05
you can work the news page but not the video !
now if you click the stories you can view quicktime
think they moved all the video to a separate system ( with lots of ads)
so think they change the way the links and pages work and suspect it is for windows folks now ;-(

i have a few sites that dont work with linux and some tell me i need to use the latest WMP for it to work and sent a e-mail and got a reply saying most have windows so use a windows computer

---

### Post by spillin_dylan on 2009-10-05
Same results here, I have the flashplayer-nonfree installed in FF3, but still a no-go.  It looks as if it loads fine, but the 'buffer bar' never moves, and the time shows 0:00/0:00.  I know that other sites seem to work fine for me, (YouTube, etc...) so it must be the CBC's fault.  

Kind of ironic, really, because last winter they did a story regarding Ubuntu, which was what got me using it in the first place!

---

### Post by tareko on 2009-10-22
I have the same issue as well. Some other searches I've done have talked about needing Java installed, though even with the java 1.6 plugin, I still have the same problem.

Firefox via wine works fine, however, and displays video normally.

I think there are two parts to this: The first is trying to figure out what exactly causes things to work - if we can submit a patch to CBC, that much the better. Possibly it has something to do with this error message:

Error: [http://www.cbc.ca/includes/flashscripts/swfaddress/2.4/swfaddress.js:](http://www.cbc.ca/includes/flashscripts/swfaddress/2.4/swfaddress.js:) TypeError: Attempt to use a non-function object or a value as a function.

The second part is that we should email CBC and tell them we're not happy that they don't make our public broadcasts available to linux users. The contact info:

[http://www.cbc.ca/contact/](http://www.cbc.ca/contact/)

Be polite but firm.

tarek : )

---

