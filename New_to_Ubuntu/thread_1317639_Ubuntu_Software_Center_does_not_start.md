---
title: "Ubuntu Software Center does not start"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by morphthecat on 2009-11-06
This is my first try with linux. I downloaded Ubuntu 9.10 last week and it works well with the hardware except that the parallel printer port is not recognised. The other more pressing problem is that the Ubuntu software center does not start. When I try to start it I see "Starting Ubuntu Softw.." in the bottom panel for about 10 seconds then that disappears and thats it. What's the secret?

---

### Post by unamanic on 2009-11-06
I don't know about why the software center isn't working for you (it works form me), but you can try to use synaptic instead.

System->Administration->Synaptic Package Manager

It provides a more advanced (but still fairly simple) interface.  Once you use it for a while you'll prefer it.

---

### Post by RochJer on 2009-11-07
Did you try to reboot ubuntu then try again and see if Ubuntu Software Center opens up again? Try logging off then log on, restart or shut down and see if it forces Ubuntu to open the Software Center.

---

### Post by morphthecat on 2009-11-07
No. I have started ubuntu many times but it's always the same. No software centre.

---

### Post by SavannahTux on 2009-11-13
I had the same issue but have now been able to resolve it.

First of all, you need to get more info on why it is not starting. Therefore, open a Terminal and type

software-center

If everything works properly, this should launch the Software Centre on the GUI, but probably it will produce a stream of errors in the Terminal window which you can post here for better support.

I my own case I found that the language settings were not correct. I was using English (Nigeria), which obviously triggers a bug. I changed the settings to English (United Kingdom) under System -> Language Support and then rebooted. After that it started ok

If you are using an unusual language, change the settings as I propose here, reboot and see what happens.

---

### Post by Cowboybebop79 on 2009-11-27
I have Had a similar problem when I first installed 9.10 the software centre was working fine then randomly it just stopped working so as advised I ran it from the terminal and this is the Trace back I get.

```

Traceback (most recent call last):
  File "/usr/bin/software-center", line 80, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path)
  File "/usr/share/software-center/softwarecenter/app.py", line 140, in __init__
    self.icons, datadir)
  File "/usr/share/software-center/softwarecenter/view/availablepane.py", line 70, in __init__
    self._build_ui()
  File "/usr/share/software-center/softwarecenter/view/availablepane.py", line 75, in _build_ui
    self.icons)
  File "/usr/share/software-center/softwarecenter/view/catview.py", line 73, in __init__
    self.categories = self.parse_applications_menu(desktopdir)
  File "/usr/share/software-center/softwarecenter/view/catview.py", line 131, in parse_applications_menu
    tree = ET.parse(datadir+"/desktop/applications.menu")
  File "/usr/lib/python2.6/xml/etree/ElementTree.py", line 862, in parse
    tree.parse(source, parser)
  File "/usr/lib/python2.6/xml/etree/ElementTree.py", line 579, in parse
    source = open(source, "rb")
IOError: [Errno 2] No such file or directory: '/usr/share/app-install/desktop/applications.menu'
```
 
I know that you can use synaptic package manager for adding software so it's not a problem for me. But I know why it has been included as I have used Linux Mint before which has a similar system and the reason it is there is to make it as easy as possible to get hold of new software without having to figure out which is the main package of a particular piece of software you would like to add.

If anyone finds a solution thank you in advance

ps. I have already updated the language which had no effect.

---

### Post by SeanHodges on 2009-11-27
> **Cowboybebop79 said:**
> I have Had a similar problem when I first installed 9.10 the software centre was working fine then randomly it just stopped working so as advised I ran it from the terminal and this is the Trace back I get.

```

Traceback (most recent call last):
  File "/usr/bin/software-center", line 80, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path)
  File "/usr/share/software-center/softwarecenter/app.py", line 140, in __init__
    self.icons, datadir)
  File "/usr/share/software-center/softwarecenter/view/availablepane.py", line 70, in __init__
    self._build_ui()
  File "/usr/share/software-center/softwarecenter/view/availablepane.py", line 75, in _build_ui
    self.icons)
  File "/usr/share/software-center/softwarecenter/view/catview.py", line 73, in __init__
    self.categories = self.parse_applications_menu(desktopdir)
  File "/usr/share/software-center/softwarecenter/view/catview.py", line 131, in parse_applications_menu
    tree = ET.parse(datadir+"/desktop/applications.menu")
  File "/usr/lib/python2.6/xml/etree/ElementTree.py", line 862, in parse
    tree.parse(source, parser)
  File "/usr/lib/python2.6/xml/etree/ElementTree.py", line 579, in parse
    source = open(source, "rb")
IOError: [Errno 2] No such file or directory: '/usr/share/app-install/desktop/applications.menu'
```
 
I know that you can use synaptic package manager for adding software so it's not a problem for me. But I know why it has been included as I have used Linux Mint before which has a similar system and the reason it is there is to make it as easy as possible to get hold of new software without having to figure out which is the main package of a particular piece of software you would like to add.

If anyone finds a solution thank you in advance

ps. I have already updated the language which had no effect.

Try installing the [app-install-data]("apt:/app-install-data") package...

---

### Post by Cowboybebop79 on 2009-11-27
Thanks for the reply Sean I used synaptic to reinstall "app-install-data" and the software centre is now up and running again. I still don't know why it stopped working in the first place but, I have been playing around with drivers to get everything on my laptop working. So its not a surprise that something may have got bent out of shape during all that. :oops:

Anyway thanks again and I will keep an eye out for anyone with the same problem especially new users because they won't know about synaptic or terminal for that matter.

---

### Post by ecatodarcus on 2010-07-18
Hello there. i have the same problem. I use Ubuntu 10.4. Ubuntu Software Center worked allright but suddenly it couldn't start. It starts booting but then stops. I opened terminal and wrote 
[HTML]software-center[/HTML]
and this had this result
[HTML]Traceback (most recent call last):
  File "/usr/bin/software-center", line 80, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path)
  File "/usr/share/software-center/softwarecenter/app.py", line 201, in __init__
    self.view_switcher = ViewSwitcher(datadir, self.db, self.icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 57, in __init__
    store = ViewSwitcherList(datadir, db, icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 204, in __init__
    self._update_channel_list()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 274, in _update_channel_list
    self.channels = self._get_channels()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 352, in _get_channels
    channels.append(partner_channel)
UnboundLocalError: local variable 'partner_channel' referenced before assignment[/HTML]

i re installed app-install-data but the problem continues to exist. 

Thank you in advance

p.s sorry for my english:p

---

### Post by jalampi360 on 2010-07-18
I'm having the same problem too. Here is my terminal info:

dogbert0360@dogbert0360-desktop:~$ sudo -i
[sudo] password for dogbert0360: 
root@dogbert0360-desktop:~# software-center
Traceback (most recent call last):
  File "/usr/bin/software-center", line 80, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path)
  File "/usr/share/software-center/softwarecenter/app.py", line 201, in __init__
    self.view_switcher = ViewSwitcher(datadir, self.db, self.icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 57, in __init__
    store = ViewSwitcherList(datadir, db, icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 204, in __init__
    self._update_channel_list()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 274, in _update_channel_list
    self.channels = self._get_channels()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 352, in _get_channels
    channels.append(partner_channel)
UnboundLocalError: local variable 'partner_channel' referenced before assignment
root@dogbert0360-desktop:~# 

Can anyone tell me what the problem is and how to fix this? Your response is always appreciated.

---

### Post by anakbaroe on 2010-07-18
hi mates,
i'm using ubuntu 10.04 lucid lynx and i just found out that i have same problems with ubuntu software center.

here is my command line response.
perhaps anyone can help me

myhasianku@myhasianku-laptop:~$ sudo software-center
[sudo] password for myhasianku: 
Traceback (most recent call last):
  File "/usr/bin/software-center", line 80, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path)
  File "/usr/share/software-center/softwarecenter/app.py", line 201, in __init__
    self.view_switcher = ViewSwitcher(datadir, self.db, self.icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 57, in __init__
    store = ViewSwitcherList(datadir, db, icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 204, in __init__
    self._update_channel_list()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 274, in _update_channel_list
    self.channels = self._get_channels()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 352, in _get_channels
    channels.append(partner_channel)
UnboundLocalError: local variable 'partner_channel' referenced before assignment

thanks a lot 

\m/

---

### Post by Lucifer The Dark on 2010-07-19
I'm using 10.04 as well, updated to v2.0.6 of software-center this morning & this is what I get...

rob@rob-desktop:~$ software-center
Traceback (most recent call last):
  File "/usr/bin/software-center", line 80, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path)
  File "/usr/share/software-center/softwarecenter/app.py", line 201, in __init__
    self.view_switcher = ViewSwitcher(datadir, self.db, self.icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 57, in __init__
    store = ViewSwitcherList(datadir, db, icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 204, in __init__
    self._update_channel_list()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 274, in _update_channel_list
    self.channels = self._get_channels()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 352, in _get_channels
    channels.append(partner_channel)
UnboundLocalError: local variable 'partner_channel' referenced before assignment


The same thing happened a couple of days ago & a full reinstall fixed it then but hasn't worked this time, any help fixing it would be appreciated.

---

### Post by burdebc on 2010-07-19
I had the same problem with Ubuntu 10.04 and the  local variable 'partner_channel' referenced before assignment error.  I got it working again by going into synaptic package manager and marking software-center for complete removal and then installed it again.

---

### Post by Frogs Hair on 2010-07-19
I helped with a Wubi install last night and had the same issue , so I installed the latest ppa and that solved the problem ? Not good for someone trying Ubuntu to be without a software center.

---

### Post by deadlockedgamer on 2010-07-19
I have the local variable 'partner_channel' referenced before assignment error. but completely removing software center and reinstalling did not fix. Of course I added back the Ubuntu desktop package it had installed with it as it was claimed it is important especially in upgrades. I also had to re remove totem pitv f-spot and gnome games. I am not sure but I don't think I had this problem till after updating with lucid proposed updates!

---

### Post by 3Dragz on 2010-07-19
Same problem. Looks like a coding error. Look at the last line in the traceback.

Traceback (most recent call last):
  File "/usr/bin/software-center", line 80, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path)
  File "/usr/share/software-center/softwarecenter/app.py", line 201, in __init__
    self.view_switcher = ViewSwitcher(datadir, self.db, self.icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 57, in __init__
    store = ViewSwitcherList(datadir, db, icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 204, in __init__
    self._update_channel_list()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 274, in _update_channel_list
    self.channels = self._get_channels()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 352, in _get_channels
    channels.append(partner_channel)
UnboundLocalError: local variable 'partner_channel' referenced before assignment

---

### Post by -TJ on 2010-07-19
Hello. I think I have a similar problem that you all are having. I try to open Ubuntu Software Center but it doesn't start. When I try to start it using the terminal, I get some error. Here it is:

```
tj@ubuntu:~$ sudo software-center
[sudo] password for tj: 
Traceback (most recent call last):
  File "/usr/bin/software-center", line 80, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path)
  File "/usr/share/software-center/softwarecenter/app.py", line 201, in __init__
    self.view_switcher = ViewSwitcher(datadir, self.db, self.icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 57, in __init__
    store = ViewSwitcherList(datadir, db, icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 204, in __init__
    self._update_channel_list()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 274, in _update_channel_list
    self.channels = self._get_channels()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 352, in _get_channels
    channels.append(partner_channel)
UnboundLocalError: local variable 'partner_channel' referenced before assignment

```

---

### Post by deadlockedgamer on 2010-07-20
I could do it later but not atm can someone report this bug on launchpad and put a link here so everyone can click effected too.

---

### Post by anakbaroe on 2010-07-25
hi mates,
this morning i tried to do sudo apt-get update and i found that there is some replacement package for software-center, and after installation is complete software-center is working properly.

thanks

---

### Post by ProntoAnthony on 2010-10-18
This morning I found myself with the same problem. I'm running Ubuntu 10.04.1 lucid lynx.

Read the above thread and went to Synaptic Package Manager, where I removed software-center and then reinstalled it. Still it wouldn't come up. Rebooted, in terminal, I issued the software-center command. The output was:

```

anthony@anthony-desktop:~$ sudo software-center
[sudo] password for anthony: 
WARNING:root:No styling hints for Raleigh were found... using Human hints.
WARNING:root:No styling hints for Raleigh were found... using Human hints.
WARNING:root:No styling hints for Raleigh were found... using Human hints.
WARNING:root:No styling hints for Raleigh were found... using Human hints.
WARNING:root:No styling hints for Raleigh were found... using Human hints.
WARNING:root:No styling hints for Raleigh were found... using Human hints.
WARNING:root:No styling hints for Raleigh were found... using Human hints.
WARNING:root:No styling hints for Raleigh were found... using Human hints.
WARNING:root:No styling hints for Raleigh were found... using Human hints.
/usr/share/software-center/softwarecenter/apt/aptcache.py:40: GtkWarning: gtk_container_add: assertion `GTK_IS_CONTAINER (container)' failed
  gtk.main_iteration()
ERROR:dbus.proxies:Introspect error on :1.51:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 1 matched rules; type="method_call", sender=":1.49" (uid=0 pid=2138 comm="/usr/bin/python) interface="org.freedesktop.DBus.Introspectable" member="Introspect" error name="(unset)" requested_reply=0 destination=":1.51" (uid=0 pid=2176 comm="/usr/bin/python))

```
But then the software-center came up!

Great...I thought. It still won't come up from the menu, though. And I'm curious as to those errors I'm getting in Terminal.

Thanks for any help you can give me.
-----
dug around some more through old posts. Found this:
> **bertilow said:**
> In that discussion someone wrote that choosing a specific GTK theme for GTK applications (not just using a KDE style) fixes the problem. I can confirm that. Problem solved for me.

System Settings -> Look & Feel -> Appearance -> GTK Styles and Fonts -> GTK Styles -> Use another Style -> (Pick one)

(Maybe you need to have parts of Gnome installed.)
I picked a new font. Now the software center comes up.

Yet I am still getting those same errors in Terminal. I going to reboot and see about the effect.
(later) Still am experiencing the same problem.

---

### Post by Jetro on 2010-10-25
I can't open Ubuntu Software Center either. I get the following error message:
[quote=Terminal]sudo software-center 
Traceback (most recent call last):
  File "/usr/bin/software-center", line 78, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 42, in <module>
    from view.viewswitcher import ViewSwitcher, ViewSwitcherList
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 34, in <module>
    from softwarecenter.backend.channel import SoftwareChannel
  File "/usr/share/software-center/softwarecenter/backend/channel.py", line 22, in <module>
    from softwarecenter.distro import get_distro
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 88, in <module>
    distro_instance=_get_distro()
  File "/usr/share/software-center/softwarecenter/distro/__init__.py", line 77, in _get_distro
    module =  __import__(distro_id, globals(), locals(), [], -1)
ImportError: No module named LinuxMint[/quote]
I installed a lot of tools in order to add a MintMenu button, so I thought this might be the problem. I went in Synaptic, uninstalled everything with "Mint" in it, but yet the problem persists, and I get the exact same error message.

---

### Post by KhensuRA on 2010-10-25
I am running into the same problem as well. This what I get when i try to run an update from the terminal


```
virgl@PachecosPuter:~$ sudo software-center
[sudo] password for virgl: 
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/apt/aptcache.py", line 105, in open
    self._cache = apt.Cache(GtkMainIterationProgress())
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 88, in __init__
    self.open(progress)
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 130, in open
    self._list.read_main_list()
SystemError: E:Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
2010-10-25 10:22:52,510 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/view/widgets/mkit_themes.py', 675, 'retrieve')'
2010-10-25 10:22:52,509 - root - WARNING - No styling hints for infinity were found... using Human hints.
Traceback (most recent call last):
  File "/usr/bin/software-center", line 90, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path, options, args)
  File "/usr/share/software-center/softwarecenter/app.py", line 316, in __init__
    self.view_switcher = ViewSwitcher(self.view_manager, datadir, self.db, self.cache, self.icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 59, in __init__
    store = ViewSwitcherList(view_manager, datadir, db, cache, icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 321, in __init__
    self._update_channel_list()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 399, in _update_channel_list
    self._update_channel_list_installed_view()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 452, in _update_channel_list_installed_view
    if (pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/apt/aptcache.py", line 128, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'
virgl@PachecosPuter:~$ 
```

---

### Post by Jetro on 2010-10-27
Bump...

---

### Post by cobra90 on 2010-10-31
i have the same problem, reinstalling didn't work apt-get upgrade didn't as well. here's the problem

ilias@ubuntu:~$ software-center
Traceback (most recent call last):
  File "/usr/bin/software-center", line 80, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path)
  File "/usr/share/software-center/softwarecenter/app.py", line 221, in __init__
    self.config = get_config()
  File "/usr/share/software-center/softwarecenter/backend/config.py", line 43, in get_config
    _software_center_config = SoftwareCenterConfig(SOFTWARE_CENTER_CONFIG_FILE)
  File "/usr/share/software-center/softwarecenter/backend/config.py", line 30, in __init__
    self.read(self.configfile)
  File "/usr/lib/python2.6/ConfigParser.py", line 286, in read
    self._read(fp, filename)
  File "/usr/lib/python2.6/ConfigParser.py", line 482, in _read
    raise MissingSectionHeaderError(fpname, lineno, line)
ConfigParser.MissingSectionHeaderError: File contains no section headers.
file: /home/ilias/.config/softwarecenter/softwarecenter.cfg, line: 1
'(dp0\n'

your answers would be appreciated. god bless you all linux users

---

### Post by arpho on 2010-12-28
HiI have the same problem with software center;
this is what I get from terminal
> 
Traceback (most recent call last):
  File "/usr/bin/software-center", line 88, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 48, in <module>
    from view.installedpane import InstalledPane
  File "/usr/share/software-center/softwarecenter/view/installedpane.py", line 33, in <module>
    from softwarepane import SoftwarePane, wait_for_apt_cache_ready
  File "/usr/share/software-center/softwarecenter/view/softwarepane.py", line 50, in <module>
    from  appdetailsview_gtk import AppDetailsViewGtk as AppDetailsView
  File "/usr/share/software-center/softwarecenter/view/appdetailsview_gtk.py", line 45, in <module>
    from appdetailsview import AppDetailsViewBase
  File "/usr/share/software-center/softwarecenter/view/appdetailsview.py", line 30, in <module>
    from purchasedialog import PurchaseDialog
  File "/usr/share/software-center/softwarecenter/view/purchasedialog.py", line 23, in <module>
    import simplejson
  File "/usr/local/lib/python2.6/dist-packages/simplejson-1.7.3-py2.5-win32.egg/simplejson/__init__.py", line 96, in <module>
    from encoder import JSONEncoder
  File "/usr/local/lib/python2.6/dist-packages/simplejson-1.7.3-py2.5-win32.egg/simplejson/encoder.py", line 6, in <module>
    from simplejson import _speedups
  File "/usr/local/lib/python2.6/dist-packages/simplejson-1.7.3-py2.5-win32.egg/simplejson/_speedups.py", line 7, in <module>
    __bootstrap__()
  File "/usr/local/lib/python2.6/dist-packages/simplejson-1.7.3-py2.5-win32.egg/simplejson/_speedups.py", line 5, in __bootstrap__
    del __bootstrap__, __loader__
NameError: global name '__loader__' is not defined


when I started to have problem with software-center, even other applications started to show the same behavior as software-center, now my ubuntuone and Labyrinth do not work any more; someone can help me? thanks in advance

---

### Post by Ethank on 2011-03-06
I know this thread is ancient, but I have had a similar problem for a bit.

I eventually figured out that it was the icon theme that I was using that was causing Software Center to not start. 
If any of you still have problems, try changing your icon theme.

Alternatively, you can right click on the desktop and click on **Create Launcher**. Then change the type to **Application In Terminal**. In the Name box, type whatever you want. Then in the box that says command, type "sudo software-center". Save the launcher and it should work. (:

---

### Post by tinnudile on 2011-03-10
thanks Ethank , I had this problem , once I reverted to old icon theme it was solved (^_^)

---

### Post by stonexjr on 2011-04-05
Hi I have the same problem, here is the error msg i got  from the terminal:

Traceback (most recent call last):
  File "/usr/bin/software-center", line 90, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path, options, args)
  File "/usr/share/software-center/softwarecenter/app.py", line 220, in __init__
    self.navhistory_forward_action)
  File "/usr/share/software-center/softwarecenter/view/availablepane.py", line 77, in __init__
    SoftwarePane.__init__(self, cache, history, db, distro, icons, datadir)
  File "/usr/share/software-center/softwarecenter/view/softwarepane.py", line 201, in __init__
    self.datadir)
  File "/usr/share/software-center/softwarecenter/view/appdetailsview_gtk.py", line 1063, in __init__
    self._overlay = gtk.gdk.pixbuf_new_from_file(INSTALLED_ICON)
[COLOR=Red]glib.GError: Failed to load image '/usr/share/software-center/icons/software-center-installed.png': Fatal error in PNG image file: Decompression error[/COLOR]

The software-center failed to work after  I installed KDevelop4 in software-center.
Is it the PNG lib that cause the problem, I guess.
Both my laptop and lab machine have got the same problem.
Any one could help?

---

### Post by stonexjr on 2011-04-05
I finally figured out how to cope with this problem shortly after I posted the above message.
The solution is go to /usr/share/software-center/icon, and open the three icon file with your image editor.
Export them as jpg file. remove the old png file and change the .jpg file extention into .png.

> **stonexjr said:**
> Hi I have the same problem, here is the error msg i got  from the terminal:

Traceback (most recent call last):
  File "/usr/bin/software-center", line 90, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path, options, args)
  File "/usr/share/software-center/softwarecenter/app.py", line 220, in __init__
    self.navhistory_forward_action)
  File "/usr/share/software-center/softwarecenter/view/availablepane.py", line 77, in __init__
    SoftwarePane.__init__(self, cache, history, db, distro, icons, datadir)
  File "/usr/share/software-center/softwarecenter/view/softwarepane.py", line 201, in __init__
    self.datadir)
  File "/usr/share/software-center/softwarecenter/view/appdetailsview_gtk.py", line 1063, in __init__
    self._overlay = gtk.gdk.pixbuf_new_from_file(INSTALLED_ICON)
[COLOR=Red]glib.GError: Failed to load image '/usr/share/software-center/icons/software-center-installed.png': Fatal error in PNG image file: Decompression error[/COLOR]

The software-center failed to work after  I installed KDevelop4 in software-center.
Is it the PNG lib that cause the problem, I guess.
Both my laptop and lab machine have got the same problem.
Any one could help?

---

### Post by nonkreon on 2011-04-09
```
File "/usr/bin/software-center", line 90, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path, options, args)
  File "/usr/share/software-center/softwarecenter/app.py", line 312, in __init__
    self.view_switcher = ViewSwitcher(self.view_manager, datadir, self.db, self.cache, self.icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 59, in __init__
    store = ViewSwitcherList(view_manager, datadir, db, cache, icons)
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 321, in __init__
    self._update_channel_list()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 399, in _update_channel_list
    self._update_channel_list_installed_view()
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 444, in _update_channel_list_installed_view
    matches = enquire.get_mset(0, len(self.db))
xapian.DatabaseCorruptError: Unexpected end of posting list for `XOLUbuntu'

```
I tried reinstalling app-install-data and sudo software-center. still got nowhere. can you guys help me figure out. thanks :)

---

### Post by nonkreon on 2011-04-10
okay guys I got it figured out with the help of Patrick Goleck. just terminal 
```
sudo update-apt-xapian-index
```
this may help the future generations. cheers. 
BTW don't dare shutting down the computer while software-center is open. i think that's what caused me the problem. ;)

---

### Post by nonkreon on 2011-05-12
After about a month another problem, I couldn't solve this one by googling it too;

```
Traceback (most recent call last):
  File "/usr/bin/software-center", line 90, in <module>
    app = SoftwareCenterApp(datadir, xapian_base_path, options, args)
  File "/usr/share/software-center/softwarecenter/app.py", line 145, in __init__
    self.history = get_apt_history()
  File "/usr/share/software-center/softwarecenter/apt/apthistory.py", line 178, in get_apt_history
    apt_history = AptHistory()
  File "/usr/share/software-center/softwarecenter/apt/apthistory.py", line 83, in __init__
    self.rescan()
  File "/usr/share/software-center/softwarecenter/apt/apthistory.py", line 98, in rescan
    self._scan(history_gz_file)
  File "/usr/share/software-center/softwarecenter/apt/apthistory.py", line 110, in _scan
    for stanza in deb822.Deb822.iter_paragraphs(f):
  File "/usr/lib/pymodules/python2.6/debian/deb822.py", line 287, in iter_paragraphs
    x = cls(iterable, fields, encoding=encoding)
  File "/usr/lib/pymodules/python2.6/debian/deb822.py", line 255, in __init__
    self._internal_parser(sequence, fields)
  File "/usr/lib/pymodules/python2.6/debian/deb822.py", line 308, in _internal_parser
    for line in self.gpg_stripped_paragraph(sequence):
  File "/usr/lib/pymodules/python2.6/debian/deb822.py", line 551, in gpg_stripped_paragraph
    return cls.split_gpg_and_payload(sequence)[1]
  File "/usr/lib/pymodules/python2.6/debian/deb822.py", line 503, in split_gpg_and_payload
    for line in sequence:
  File "/usr/lib/python2.6/gzip.py", line 438, in next
    line = self.readline()
  File "/usr/lib/python2.6/gzip.py", line 393, in readline
    c = self.read(readsize)
  File "/usr/lib/python2.6/gzip.py", line 219, in read
    self._read(readsize)
  File "/usr/lib/python2.6/gzip.py", line 255, in _read
    self._read_gzip_header()
  File "/usr/lib/python2.6/gzip.py", line 156, in _read_gzip_header
    raise IOError, 'Not a gzipped file'
IOError: Not a gzipped file

```

---

### Post by rpk94 on 2011-09-28
Well this is the problem i'm facing
```

roopak@ubuntu:~$ software-center
Error processing line 1 of /usr/lib/python2.7/dist-packages/python-support.pth:

  Traceback (most recent call last):
    File "/usr/lib/python2.7/site.py", line 161, in addpackage
      if not dircase in known_paths and os.path.exists(dir):
    File "/usr/lib/python2.7/genericpath.py", line 18, in exists
      os.stat(path)
  TypeError: must be encoded string without NULL bytes, not str

Remainder of file ignored
Traceback (most recent call last):
  File "/usr/bin/software-center", line 34, in <module>
    import gtk
  File "/usr/lib/pymodules/python2.7/gtk-2.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: No module named cairo

```
And yea, my computer did shut down while software centre was running

---

### Post by rpk94 on 2011-09-28
And synaptic gives me this.
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

---

