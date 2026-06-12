---
title: "miro 2.0"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by DarinB on 2009-02-11
I got an email for miro 2.0
i tried to install it but i can't get it to work..therefore i removed it.
what is it and what does it do? i thought it was like hulu.
also when i installed it instead of the sunburst icon coming up the red down arrow did like it does for security updates... did i just cause a problem on my machine?????

---

### Post by cariboo on 2009-02-11
How did you install miro?

> Miro (previously known as Democracy Player) is a platform for Internet
television and video.
It allows you to download and watch videos from RSS feeds (including
podcasts, video blogs, and BitTorrent feeds).

Jim

---

### Post by DarinB on 2009-02-11
i added the link from the web site to synaptic and then installed it via synaptic.
[http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu)

---

### Post by jmszr on 2009-02-11
DarinB,
        I downloaded Miro 2.0 from here: [http://www.getmiro.com/](http://www.getmiro.com/) , installed the repository in Synaptic, reloaded and installed from Synaptic. Works.

---

### Post by RomeReactor on 2009-02-11
> **DarinB said:**
> i added the link from the web site to synaptic and then installed it via synaptic.
[http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu)

Hi. The correct repository entry would be:
```
**deb** http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu **intrepid/**
```
You forgot to add **deb** at the beginning of the line, and your version of Ubuntu (**intrepid**) at the end.

---

### Post by DarinB on 2009-02-11
i got it to work, i have no idea how. it certainly doesn't say deb before the ftp site in the repos
i got the program up it was in the sound and video menu but un checked. 
thanks for all the help.

---

### Post by mlwalla on 2009-02-13
I recently installed miro 2.0.1 in an acer aspire one running ubuntu netbook remix using the same method.  Here's what I get:


me@me:~$ miro

*************** INITIALIZE MOZEMBED
location: /usr/lib/xulrunner-1.9.0.5/libxpcom.so 
before 3
INFO     Starting up Miro
INFO     Version:    2.0.1
INFO     Revision:   [https://svn.participatoryculture.org/svn/dtv/tags/Miro-2.0.1/tv/resources](https://svn.participatoryculture.org/svn/dtv/tags/Miro-2.0.1/tv/resources) - 9185
INFO     Builder:    pbuilder@mercury
INFO     Build Time: 1234395336.79
INFO     Loading preferences...
INFO     Showing startup dialog...

(miro.real:6235): libglade-WARNING **: could not find glade file '/usr/share/miro/resources/miro.glade'
Traceback (most recent call last):
  File "/usr/bin/miro.real", line 112, in <module>
    startapp()
  File "/usr/bin/miro.real", line 86, in startapp
    app.main()
  File "/var/lib/python-support/python2.5/miro/app.py", line 106, in main
    Controller().Run()
  File "/var/lib/python-support/python2.5/miro/frontend_implementation/Application.py", line 60, in Run
    self.onStartup()
  File "/var/lib/python-support/python2.5/miro/app.py", line 679, in onStartup
    delegate.performStartupTasks(self.finishStartup)
  File "/var/lib/python-support/python2.5/miro/frontend_implementation/UIBackendDelegate.py", line 395, in performStartupTasks
    startup.performStartupTasks(terminationCallback)
  File "/var/lib/python-support/python2.5/miro/frontend_implementation/startup.py", line 75, in performStartupTasks
    widgetTree = MainFrame.WidgetTree(resources.path('miro.glade'), 'dialog-startup', 'miro')
RuntimeError: could not create GladeXML object





any help?

---

