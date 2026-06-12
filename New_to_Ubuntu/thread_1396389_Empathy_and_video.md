---
title: "Empathy and video"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by Inodoro Pereyra on 2010-02-02
Ok, I have ubuntu 9.10 on an acer aspire 5000. I tried to use Empathy to connect to a windows live user and the chat works ok, but the video doesn't. The little camera icon I'm supposed to click on doesn't show, and the Video chat in the menu is greyed out. What am I doing wrong?
Thanks in advance.:)

---

### Post by NightwishFan on 2010-02-02
The Windows Live webcam support is disabled in Karmics Empathy. You can get it from a PPA or try another MSN program such as Amsn or Emesene.

---

### Post by Inodoro Pereyra on 2010-02-02
Thank you. I downloaded amsn, but it tells me my password is wrong. I know it's not wrong...
Do I have to set something up?

---

### Post by Sef on 2010-02-02
Have you tried typing in your password a few times and checked that cap locks is not enabled?

---

### Post by cbert78 on 2010-02-03
I'm having the same problem getting webcam to work. I've tried aMSN and the webcam option is there, but as soon as the MSN user accepts my invitation to webcam, the video goes blank and cannot connect. I know the cam is working, I can see myself. However, as soon as I try to let someone else see me (or try to see them), the picture goes blank.

---

### Post by Inodoro Pereyra on 2010-02-03
Sef: thanks for the reply. I did. Several times in fact. I even rebooted the computer, to see if that solved the problem. Nothing worked.

---

### Post by nhasian on 2010-02-03
to get video conferencing working for the MSN protocol in Empathy, simply copy and paste the following lines into a terminal:

```
sudo add-apt-repository ppa:telepathy/ppa
```

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by Inodoro Pereyra on 2010-02-03
nhasian: I tried it. Doesn't work...:(

---

### Post by nhasian on 2010-02-03
if you can be more descriptive we can assist you better.  what didnt work? adding the repository?  video conferencing? copy/pasting?

> **Inodoro Pereyra said:**
> nhasian: I tried it. Doesn't work...:(

---

### Post by Inodoro Pereyra on 2010-02-03
Sorry.
I tried doing what you said.
I opened the terminal, copy/paste each line as you suggested. It loaded a lot of stuff, but the video still doesn't work. I rebooted the computer, and nothing happened.

---

### Post by nhasian on 2010-02-03
... when you say nothing happened do you mean you are still running the old version of empathy?  or did you install the newer one successfully?  Please copy/paste here the output of this terminal command:

```
apt-cache policy empathy telepathy-butterfly python-papyon
```

this will tell me if you have the latest empathy installed along with the dependencies required to do video conferencing with the MSN protocol.

for example when i run that command i get:

```

empathy:
  Installed: 2.29.5.1-1~ppa9.10+2
  Candidate: 2.29.5.1-1~ppa9.10+2
  Version table:
 *** 2.29.5.1-1~ppa9.10+2 0
        500 http://ppa.launchpad.net karmic/main Packages
        100 /var/lib/dpkg/status
     2.28.1.1-0ubuntu1 0
        500 http://archive.ubuntu.com karmic-updates/main Packages
     2.28.1-1ubuntu1 0
        500 http://archive.ubuntu.com karmic/main Packages
telepathy-butterfly:
  Installed: 0.5.4-1~ppa9.10+1
  Candidate: 0.5.4-1~ppa9.10+1
  Version table:
 *** 0.5.4-1~ppa9.10+1 0
        500 http://ppa.launchpad.net karmic/main Packages
        100 /var/lib/dpkg/status
     0.5.2-0ubuntu1 0
        500 http://archive.ubuntu.com karmic/main Packages
python-papyon:
  Installed: 0.4.3-1ubuntu1
  Candidate: 0.4.3-1ubuntu1
  Version table:
 *** 0.4.3-1ubuntu1 0
        500 http://archive.ubuntu.com karmic/main Packages
        100 /var/lib/dpkg/status
     0.4.3-1~ppa9.10+1 0
        500 http://ppa.launchpad.net karmic/main Packages
```

---

### Post by Inodoro Pereyra on 2010-02-04
Ok, this is what I get:

empathy:
  Installed: 2.29.5.1-1~ppa9.10+2
  Candidate: 2.29.5.1-1~ppa9.10+2
  Version table:
 *** 2.29.5.1-1~ppa9.10+2 0
        500 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
        100 /var/lib/dpkg/status
     2.28.1.1-0ubuntu1 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
     2.28.1-1ubuntu1 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
telepathy-butterfly:
  Installed: 0.5.4-1~ppa9.10+1
  Candidate: 0.5.4-1~ppa9.10+1
  Version table:
 *** 0.5.4-1~ppa9.10+1 0
        500 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages
        100 /var/lib/dpkg/status
     0.5.2-0ubuntu1 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
python-papyon:
  Installed: 0.4.3-1ubuntu1
  Candidate: 0.4.3-1ubuntu1
  Version table:
 *** 0.4.3-1ubuntu1 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
        100 /var/lib/dpkg/status
     0.4.3-1~ppa9.10+1 0
        500 [http://ppa.launchpad.net](http://ppa.launchpad.net) karmic/main Packages

I want to thank you so much for everything. You're going out of your way to help me. I really appreciate it.

---

### Post by nhasian on 2010-02-04
great it looks like you got the most recent empathy up and running.  In Empathy go to View and then click show protocols.  in case you have multiple protocols for the same contact, we want to make sure you are using the msn one.  you should see two small icons next to your contact a mic and a webcam assuming they have a mic and camera hooked up.  click on the mic to start audio conferencing, click on the webcam to start video conferencing.

---

### Post by hnrkg on 2010-03-21
I have the same problem (running karmic). The weired thing is that I managed to get it to work by installing libtelepathy-farsight0 and python-farsight packages.

Later I upgraded empathy through telepathy PPA, because the universe version (?) is buggy when it comes to grouping contacts. After this upgrade I haven't been able to make audio or video calls. I've (hopefully) removed all relevant packages and reinstalled empathy from the official ubuntu repo. It doesn't seem to matter where I install from, I just can't get it to work anymore.

I can, however, initiate calls through "Chat" -> "New conversation..." and the A/V window pops up, but it just says "connecting..." and nothing happens after that. When I looked in the telepathy-butterfly debug I found this:

```
dispatcher_connection_new_requested_channel: Channel request failed: org.freedesktop.DBus.Python.AttributeError: Traceback (most recent call last):
  File "/usr/lib/pymodules/python2.6/dbus/service.py", line 702, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.6/dist-packages/telepathy/server/conn.py", line 517, in CreateChannel
    returnedProps = channel.get_props()
  File "/usr/lib/python2.6/dist-packages/telepathy/server/channel.py", line 108, in get_props
    self._prop_getters[iface][prop]()
  File "/usr/lib/python2.6/dist-packages/butterfly/channel/media.py", line 63, in <lambda>
    'InitiatorHandle': lambda: dbus.UInt32(self._initiator.id),
AttributeError: 'NoneType' object has no attribute 'id'
```

It would be nice to get Empathy to work.

---

### Post by hnrkg on 2010-03-21
I just found this, updated the 18 March:

[http://telepathy.freedesktop.org/wiki/Protocols%20Support](http://telepathy.freedesktop.org/wiki/Protocols%20Support)

It's a serverside issue, apparently.

---

### Post by krige on 2010-03-26
I have the same problem (on lucid). Audio and video calls works fine with all protocols except for MSN: the "Audio Call" and "Video Call" items in the Contact menu are grayed out.

> **nhasian said:**
> 
```
sudo add-apt-repository ppa:telepathy/ppa
sudo apt-get update && sudo apt-get dist-upgrade
```

I tried this but still video doesn't work with MSN.

This is what I get from running "apt-cache policy empathy telepathy-butterfly python-papyon":

```
empathy:
  Installed: 2.29.93-1+ppa10.4+1
  Candidate: 2.29.93-1+ppa10.4+1
  Version table:
 *** 2.29.93-1+ppa10.4+1 0
        500 http://ppa.launchpad.net/telepathy/ppa/ubuntu/ lucid/main Packages
        100 /var/lib/dpkg/status
     2.29.93-0ubuntu2 0
        500 http://it.archive.ubuntu.com/ubuntu/ lucid/main Packages
telepathy-butterfly:
  Installed: 0.5.6-1
  Candidate: 0.5.6-1
  Version table:
 *** 0.5.6-1 0
        500 http://it.archive.ubuntu.com/ubuntu/ lucid/main Packages
        100 /var/lib/dpkg/status
python-papyon:
  Installed: 0.4.5-1ubuntu3
  Candidate: 0.4.5-1ubuntu3
  Version table:
 *** 0.4.5-1ubuntu3 0
        500 http://it.archive.ubuntu.com/ubuntu/ lucid/main Packages
        100 /var/lib/dpkg/status
```

---

