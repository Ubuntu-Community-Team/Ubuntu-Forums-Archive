---
title: "Dockbarx is not previewing windows."
date: 2010-12-14
forum: New to Ubuntu
---

### Post by karthick87 on 2010-12-14
I have installed dockborx,but windows prieview is not working there..Can anybody help me??

---

### Post by M7S on 2010-12-15
The simple solutions first:

1) You need to run compiz
2) Open dockbarx preference and check "show preference" in window list tab and nswer yes in the dialogs if you get any.
3) If it still doesn't work open compiz settings manager (install it if you don't have it) and activate kde compability plugin and in kde compability plugin acitvate "Support plasma tumbnails"

---

### Post by karthick87 on 2010-12-15
What you have told is already done..But windows preview is not working..Do you want me to check any other settings??

---

### Post by M7S on 2010-12-15
What version of compiz are you using?

Do you get any errors when you run dockbarx in window? dockbarx_factory.py run-in-window

---

### Post by karthick87 on 2010-12-16
Version: 1:0.8.6-0ubuntu9

```
karthick@karthick-VirtualBox:~$ dockbarx_factory.py

** (dockbarx_factory.py:1640): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (dockbarx_factory.py:1640): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (dockbarx_factory.py:1640): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'

```

---

### Post by M7S on 2010-12-16
Nothing that helps there. Which version of dockbarx do you use (according to the about dialog of dockbarx)?

---

### Post by karthick87 on 2010-12-16
[IMG]http://imgur.com/Mg0gH.png[/IMG]

---

### Post by M7S on 2010-12-17
You are running in awn... I really need to add that version number to terminal output so that people don't have to add DockbarX to the panel just to be able to report back what version of dockbarx they really are using. 

Could you add DockbarX to a gnome-panel, right click the handle and choose about so that it's clear what version of Dockbarx you are using. Also could you take a screenshot of previews not showing so I know in what way they are missing?

---

### Post by karthick87 on 2010-12-17
See the attachment pls..

---

### Post by M7S on 2010-12-17
That's a minimized window, you're not supposed to have previews for them (well, compiz 0.9 are supposed to bring it). 

But I guess you don't have previews anyway, right? I'm guess this since your screenshot suggests that you don't have compiz running after all. The window list should be slightly transparent otherwise.

Does this help?  
alt+F2 --> "compiz --replace && killall gnome-panel"

---

### Post by karthick87 on 2010-12-17
No that didn't help..I am ready to remove all the pacakages and re-install again..Can you say me step by step instructions???

---

### Post by M7S on 2010-12-17
Is compiz running? Does other compiz effects work in ubuntu?

If no, try run that "compiz --replace" command in a terminal and see what errors you get.

---

### Post by karthick87 on 2010-12-17
```
karthick@Ubuntu-desktop:~$ compiz --replace
WARNING: Application calling GLX 1.3 function "glXCreatePixmap" when GLX 1.3 is not supported!  This is an application bug!
Starting gtk-window-decorator
WARNING: Application calling GLX 1.3 function "glXDestroyPixmap" when GLX 1.3 is not supported!  This is an application bug!

```

---

### Post by M7S on 2010-12-17
Do you come back to command line after that or do compiz continue running?

---

### Post by karthick87 on 2010-12-17
No it continues to run.I din get back to  the command line..

---

### Post by karthick87 on 2010-12-18
> **M7S said:**
> Do you come back to command line after that or do compiz continue running?


What should i do now???Any idea??

---

### Post by M7S on 2010-12-18
Can you confirm whether or not compiz is working? Can you use any compiz effects at all in ubuntu? DockbarX is at least behaving as if there are no compositing window manager running (compiz or metacity with compositing).

If compiz isn't running for you, search for a forum thread about problems running compiz or start a new one. There are surely people here with more experience in compiz troubleshooting than me.

---

### Post by karthick87 on 2010-12-18
How to see whether compiz is running or not???When i type **compiz --replace** in terminal dockbarx can prieview windows..After that it's not showing the prieviews..

---

### Post by M7S on 2010-12-18
It works when you write compiz --replace in terminal?

Alt+F2  and write compiz --replace there then, and it should stay until you restart.

To make it stick after restarts: go to system->preference->startup programs and choose "add" (translated from swedish so the real name can differ some) . Name: Compiz, Command: compiz --replace

---

### Post by karthick87 on 2010-12-18
My system hangs when i type **compiz --replace** in terminal..

---

### Post by karthick87 on 2010-12-18
I am sure compiz is running,

```
karthick@Ubuntu-desktop:~$ ps -ef | grep compiz
karthick  2672     1  0 00:58 ?        00:00:00 /bin/sh -c /usr/bin/compiz-decorator
karthick  3489     1  0 01:03 ?        00:00:25 compiz --replace
karthick  5121  5103  0 02:07 pts/0    00:00:00 grep --color=auto compiz
```

```
karthick@Ubuntu-desktop:~$ compiz --version
compiz 0.8.4

```

---

### Post by M7S on 2010-12-18
OK, defenitely time to open a new thread (or finding an old one) about compiz not working.

---

### Post by M7S on 2010-12-18
Sorry, posted my post at the same time as you posted yours so it's not a response to your last post. That the computer hangs on compiz --replace sounds a bit wierd, though.

One last test to know if compiz runs correctly... Does compiz scale windows work (should be super+w in ubuntu by default if I remember correctly)?

---

### Post by karthick87 on 2010-12-18
Yes it works..

---

### Post by karthick87 on 2010-12-19
Do you want me to try anyother things??

---

### Post by karthick87 on 2010-12-20
Bump for a move..

---

### Post by M7S on 2010-12-20
Sorry for not answering lately much to do.

I'm a bit unsure of what you have working and what not at this moment. You still don't have any previews, right, but compiz is working as it should?

---

### Post by karthick87 on 2010-12-20
Yes compiz is running perfectly..

---

### Post by M7S on 2010-12-20
Ok, can you take a new screenshot of a preview window, and make sure it's not of a minimized window this time.

---

### Post by karthick87 on 2010-12-20
[IMG]http://imgur.com/3YbAi.png[/IMG]

---

### Post by M7S on 2010-12-20
That is still a minimized window. Do you get previews for non-minimized windows?

---

### Post by karthick87 on 2010-12-20
See this,
[IMG]http://imgur.com/g4jUQ.png[/IMG]

---

### Post by M7S on 2010-12-21
I don't really know what to do next. I guess the problem is on compiz side, since the code in for previews dockbarx are very simple, compiz does most of the work for those previews, dockbarx just tells compiz what window to preview and at what coordinates that preview should be put. But that's just a wild guess I may just as well have some irritating hard to catch bug somewhere in the dockbarx code.

---

### Post by karthick87 on 2010-12-21
Anyway to get it work??

---

### Post by moonbeam on 2010-12-21
It might be worthwhile running 

xprop -root | grep KDE

from a terminal you should get output of 

KDE_WINDOW_PREVIEW(_KDE_WINDOW_PREVIEW) = 0x0

If not then that's a good indication that the KDE compatibility module isn't active/working.

---

### Post by karthick87 on 2010-12-21
I din get any output..What should i do now??

---

### Post by moonbeam on 2010-12-21
Then I'd agree with M7S... it's a compiz issue.  As was mentioned at the beginning of the thread make sure "KDE Compatibility" is active in CCSM.  If it is checked and you're still getting that result then you probably should seek support in a compiz support forum.

---

### Post by karthick87 on 2010-12-21
But i have enabled KDE compatibility in CCSM.

---

### Post by moonbeam on 2010-12-21
Well the result from that console command indicates that the compiz KDE compatibility module is _not_ working.  It is a compiz issue not a dockbarx issue.

---

### Post by karthick87 on 2010-12-21
Disabled KDE compatibility and re-enabled it again..Now it's working..Thanks a lot M7S and moonbeam :)

[IMG]http://imgur.com/q7nXn.png[/IMG]

---

### Post by karthick87 on 2010-12-21
Is it possible to view previews for minimized windows??

---

### Post by moonbeam on 2010-12-21
> **karthick87 said:**
> Is it possible to view previews for minimized windows??

It can be done with Kwin but not with compiz.

I believe that it is being worked on in compiz - don't know how much progress has been made on that though.  The problem with minimized previews is that it tends to break some apps.

---

### Post by karthick87 on 2010-12-21
Another problem is i cant add Dockbarx Applet to my panel in ubuntu 10.10..

[IMG]http://imgur.com/DuOTG.png[/IMG]

---

### Post by karthick87 on 2010-12-21
I ran,
```
killall gnome-panel
```
but i cant add..

---

### Post by M7S on 2010-12-21
Do you mean that dockbarx works after you run killall gnome-panel but not directly after you add dockbarx to the panel?

---

### Post by karthick87 on 2010-12-21
When i try to add dockbarx applet to my panel,i get that pop up..

---

### Post by M7S on 2010-12-21
And killall gnome-panel gives the same?

---

### Post by karthick87 on 2010-12-21
Yes it gives the same..

---

### Post by M7S on 2010-12-21
Ok, what error messages do you get when you run

```
dockbarx_factory.py run-in-window
```

---

### Post by karthick87 on 2010-12-21
```
karthick@karthick-VirtualBox:~$ dockbarx_factory.py run-in-window

** (dockbarx_factory.py:1934): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (dockbarx_factory.py:1934): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (dockbarx_factory.py:1934): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
Traceback (most recent call last):
  File "/usr/bin/dockbarx_factory.py", line 26, in <module>
    import dockbarx.dockbar
  File "/usr/lib/pymodules/python2.6/dockbarx/dockbar.py", line 29, in <module>
    import dbus
  File "/usr/lib/pymodules/python2.6/dbus/__init__.py", line 100, in <module>
    from dbus._dbus import Bus, SystemBus, SessionBus, StarterBus
  File "/usr/lib/pymodules/python2.6/dbus/_dbus.py", line 46, in <module>
    from dbus.bus import BusConnection
  File "/usr/lib/pymodules/python2.6/dbus/bus.py", line 46, in <module>
    from dbus.connection import Connection
  File "/usr/lib/pymodules/python2.6/dbus/connection.py", line 42, in <module>
    from dbus.proxies import ProxyObject
  File "/usr/lib/pymodules/python2.6/dbus/proxies.py", line 35, in <module>
    from dbus._expat_introspect_parser import process_introspection_data
  File "/usr/lib/pymodules/python2.6/dbus/_expat_introspect_parser.py", line 26, in <module>
    from xml.parsers.expat import ExpatError, ParserCreate
ImportError: No module named parsers.expat
```

---

### Post by M7S on 2010-12-21
Some googling on that error gives that you probably need to re-install python. The problem is not in DockbarX.

---

### Post by karthick87 on 2010-12-21
Reinstalled python using the following command,but still it is same...
```
sudo apt-get install --reinstall python
```

---

### Post by M7S on 2010-12-21
You could try install libexpat1 (that one is installed on my computer) if you don't have it and lib64expat1 if you run a 64 bit system. This is just wild guesses again.

---

### Post by karthick87 on 2010-12-21
It is already installed,```

karthick@linuxbox:~$ sudo apt-get install libexpat1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libexpat1 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

```

---

### Post by M7S on 2010-12-22
You could try to (re)install python-lxml and python-libxml2. I'm beginning run out of ideas here.

---

### Post by karthick87 on 2010-12-22
Tried that..No change..

---

