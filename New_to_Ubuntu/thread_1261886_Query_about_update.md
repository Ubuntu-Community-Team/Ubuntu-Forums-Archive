---
title: "Query about update"
date: 2009-09-09
forum: New to Ubuntu
---

### Post by Tapas Bose, India on 2009-09-09
Hallo everybody.
I have a query about system update. Using update manager I had installed many times the following updates :
1. firefox
2. firefox-3.5
3. frefox-3.5-branding
4. firefox-3.5-gnome-support
5. firefox-gnome-support
6. xulrunner-1.9.1
7. xulrunner-1.9.1-gnome-support.

While I am trying to see the description of the above mentioned updates, the update manager show me : "Failed to detect distribution". After that, I had installed these updates many times. But after one or two days the update manager again show me that these updates are available under the heading "Other updates". If I install these update the same problem again arise after some day. I want to know is there any problem ?
Waiting for reply. Thanks in advance.

---

### Post by Rob Maddison on 2009-09-09
Hmm - I haven't found Firefox 3.5 in my update mgr but have tried to dl direct from Mozilla's website (noob so thought dl and install was the same in Ubuntu as Windows, now know it's not).

Would also like advice on getting up to date with Mozilla's releases :-)

---

### Post by Tapas Bose, India on 2009-09-09
Thank you for reply.
What about for 
xulrunner-1.9.1
xulrunner-1.9.1-gnome-support ?

---

### Post by winotree on 2009-09-09
> **Rob Maddison said:**
> Hmm - I haven't found Firefox 3.5 in my update mgr but have tried to dl direct from Mozilla's website (noob so thought dl and install was the same in Ubuntu as Windows, now know it's not).

Would also like advice on getting up to date with Mozilla's releases :-)
I used this method [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox) just day before yesterday to upgrade my Firefox from 3.0.13 to 3.5.2 and *it works great* on my little device.  Hope to hear that it does the same for you!

---

### Post by winotree on 2009-09-09
> **Tapas Bose, India said:**
> Thank you for reply.
What about for 
xulrunner-1.9.1
xulrunner-1.9.1-gnome-support ?
There is a method -- sorry but I don't recall it but perhaps you'll find it by searching the forums now that you have this information -- that allows you to *lock* your current package so that it can't be updated by the Update Manager, thus stopping those annoying pop-ups (although you still retain the ability to update it manually).  This may not be what you're looking for and it may not help -- but at the moment it seems to be an option.  Let me know one way or the other, if you don't mind.  ;)

---

### Post by Rob Maddison on 2009-09-09
> **winotree said:**
> I used this method [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox) just day before yesterday to upgrade my Firefox from 3.0.13 to 3.5.2 and *it works great* on my little device.  Hope to hear that it does the same for you!

Thanks winotree. I followed the link then went to the next stage - 'installing... the right way...'

I can follow most of it although copy/paste using ctrl c/v doesn't do it in terminal, but what does this - 
**Setting up the ubuntu-mozilla-daily repository**

 You can add to your system a repository maintained by the mozilla developers.
 Add the following line at the bottom of /etc/apt/sources.list:


- mean? (Mainly the /etc/apt/...)


Is it a terminal command?

---

### Post by Rob Maddison on 2009-09-12
> **Rob Maddison said:**
> Thanks winotree. I followed the link then went to the next stage - 'installing... the right way...'

I can follow most of it although copy/paste using ctrl c/v doesn't do it in terminal, but what does this - 
**Setting up the ubuntu-mozilla-daily repository**

 You can add to your system a repository maintained by the mozilla developers.
 Add the following line at the bottom of /etc/apt/sources.list:


- mean? (Mainly the /etc/apt/...)


Is it a terminal command?

Right - I now know to right click and use the cut command and that's fine.

I've also followed the instructions in the  [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox) link nand it's fine for me too. Thanks for the help :-)

(Wont mark as solved as OP had other queries)

Rob

---

### Post by jmundale on 2009-09-17
I have had the same problem with the identical set of packages you mention.  The description tab in update manager states "failed to detect distribution" for each.  I am running ubuntu 9.04

---

