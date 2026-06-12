---
title: "MIRO stopped working"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by Langstracht on 2010-07-02
Yesterday I noticed that Update Manager offered up some Totem and Rhythm Box updates - all of which I accepted.

And now I find MIRO is totally inoperative.

Anyone know what's going on and how I can fix it?

Thanks.

---

### Post by okplayer02 on 2010-07-05
can you please start Miro from the command line and copy and paste the messages you get in the terminal window. otherwise it will be hard to help you with out any specifics like error message.

---

### Post by Langstracht on 2010-07-06
Certainly.  And thank you SO MUCH for taking the time to get back to me.

Here's the listing:

miro
failed 1
Traceback (most recent call last):
  File "/usr/bin/miro.real", line 268, in <module>
    startapp()
  File "/usr/bin/miro.real", line 225, in startapp
    startup(props_to_set)
  File "/usr/bin/miro.real", line 163, in startup
    application = load_frontend(globals(), locals(), att)
  File "/usr/bin/miro.real", line 139, in load_frontend
    _temp = __import__(frontend, globals_, locals_, ['application'], -1)
  File "/var/lib/python-support/python2.5/miro/plat/frontends/widgets/application.py", line 47, in <module>
    from miro.frontends.widgets.application import Application
  File "/var/lib/python-support/python2.5/miro/frontends/widgets/application.py", line 57, in <module>
    from miro.frontends.widgets import dialogs
  File "/var/lib/python-support/python2.5/miro/frontends/widgets/dialogs.py", line 42, in <module>
    from miro.frontends.widgets import style
  File "/var/lib/python-support/python2.5/miro/frontends/widgets/style.py", line 40, in <module>
    from miro.frontends.widgets import imagepool
  File "/var/lib/python-support/python2.5/miro/frontends/widgets/imagepool.py", line 42, in <module>
    from miro.plat.frontends.widgets import widgetset
  File "/var/lib/python-support/python2.5/miro/plat/frontends/widgets/widgetset.py", line 29, in <module>
    import gtkmozembed
SystemError: dynamic module not initialized properly


I REALLY appreciate your help.

---

### Post by okplayer02 on 2010-07-06
hmm was it working before and did you make any updates prior to it making these errors now. I suggest you also look in the bugzilla for anyone else having the same issue with miro.

---

### Post by Langstracht on 2010-07-06
No, as I (thought I) said there were (automatic) updates to Totem and to RhythmBox which were followed by MIRO ceasing to work.

And yes I have been using it (MIRO) forever.  Even Democracy player when it was so known.

---

### Post by okplayer02 on 2010-07-08
well i suggest you 

completely remove miro then try to reinstall i mean also the configuration files also 


```
sudo aptitude purge miro
```


then just do the same command also replace purge with install

---

### Post by akapi on 2010-07-09
> **okplayer02 said:**
> well i suggest you 

completely remove miro then try to reinstall i mean also the configuration files also 


```
sudo aptitude purge miro
```


then just do the same command also replace purge with install

Thanks for the advice, however it didn't help for me (I have the same problem as Langstracht). I'm still using Ubuntu 8.04 Do you think it has anything to do with not having upgraded?

---

### Post by Langstracht on 2010-07-11
Nor me.

---

### Post by brodi6 on 2010-07-20
I have the same problem as these guys.  After doing an auto update to I can't remember what, miro will not start and I have exactly the same errors as Langstracht.  I have tried uninstalling and re-installing Miro. No dice. I am also using 8.04. Any help would be appreciated.

---

### Post by Langstracht on 2010-07-20
Well I don't know about you but it sure is hard for me to believe that we are the only THREE people experiencing this problem.

Maybe MIRO is a whole lot less popular than I had thought ...

---

### Post by brodi6 on 2010-07-20
I think this problem is too new.  I searched the forums (not just ubuntuforums.org) for an answer to this question 3 weeks ago when it started happening for me, and found didley squat on the subect.  Maybe after more people have run the most recent updates, they will start posting here.

---

### Post by brodi6 on 2010-07-22
Ok, so  I fixed my Miro...sort of.  I bit the bullet and upgraded to 10.04 Lucid, then installed Miro 3.0.x, and it works...really well!  My feeds were still intact, and the upgrade to 10.04 could not have been more painless.  I thought jumping from 8.04 to 10.04 would be this huge process, with command line crap out the yin-yang.  I never touched the terminal once:D!

I highly recommend upgrading your release guys.

---

### Post by killer7061 on 2010-07-22
hey can anyone help me i downloaded  miro and have been useing it for monthes now and then my computer shut down not properly due to a storm and ever since miro wont open instead it says this in a little pop up (An unknown error prevented Miro from startup.  Please file a bug report at [http://www.getmiro.com/bug.html](http://www.getmiro.com/bug.html).) ive uninstalled and reinstalled miro twice to try to get it to work and ive even reinstalled the newer version in hopes it would work  but still nothing can anyone help me please.

---

### Post by Infinite Indefinite on 2010-10-20
Following the advice at the following launchpad page solved my problem:

[https://bugs.launchpad.net/ubuntu/+source/miro/+bug/566445]()

I opened Synaptic Package Manager and installed xulrunner-1.9.2 and xulrunner-1.9.2-gnome-support as it suggested, and that proved sufficient - miro works as normal again.

---

