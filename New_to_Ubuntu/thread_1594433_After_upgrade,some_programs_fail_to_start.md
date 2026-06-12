---
title: "After upgrade,some programs fail to start"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by JackNocturne on 2010-10-12
Hi:),
Some programs applications work, some don't:(

Some of the programs which **don't** launch include Chromium-browser,software-center,ubuntu-tweak,update manager etc

When i launch them through terminal,this is what i get;

For example i want to launch Ubuntu Software-center
```
$ software-center
Traceback (most recent call last):
  File "/usr/bin/software-center", line 29, in <module>
    import gtk
  File "/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: /usr/lib/pymodules/python2.6/gtk-2.0/gtk/_gtk.so: undefined symbol: gtk_viewport_get_view_window

```Chromium-browser
```
$ chromium-browser
Gtk-Message: Failed to load module "canberra-gtk-module": libcanberra-gtk-module.so: cannot open shared object file: No such file or directory

(chromium-browser:5511): Gtk-WARNING **: Unable to locate theme engine in module_path: "industrial",

(chromium-browser:5511): Gtk-WARNING **: Unable to locate theme engine in module_path: "industrial",

(chromium-browser:5511): Gtk-WARNING **: Unable to locate theme engine in module_path: "industrial",

(chromium-browser:5511): Gtk-WARNING **: Unable to locate theme engine in module_path: "industrial",

(chromium-browser:5511): Gtk-WARNING **: Unable to locate theme engine in module_path: "industrial",
Gtk-Message: Failed to load module "gnomesegvhandler": libgnomesegvhandler.so: cannot open shared object file: No such file or directory
Attempting to load the system libmoon 
Segmentation fault (core dumped)

```I have tried removing them and re-installing, no dice.
I also made sure all dependencies where installed.

Though not-related, nautilus file browser crashes when **dragging** files.

Is anybody experiencing/experienced same problems or know what to do?
Any help is appreciated

---

### Post by Hippytaff on 2010-10-12
Found this...might help?
 
> 
this means that gtk does not know where your GUI (aka X-Server) is running, your best bet is to run the following command
 
export DISPLAY=:0
 
if this works, add that file to your ~/.bashrc file
 
echo "export DISPLAY=:0" >> ~/.bashrc


---

### Post by JackNocturne on 2010-10-12
Thanks for reply:)

No,im afraid things remain the same when i execute that command. I'm kinda stuck, firefox works though, its the one i'm using to browse the internet.

By the way i didn't do a fresh install , i upgraded through Update Manager(when it worked) if that helps.

---

### Post by AndyM3 on 2010-10-12
You got all that from PPAs, right?
On upgrading, all PPA entries from /etc/apt/sources.list.d/* are commented. You need to uncomment each entry from each file and change "lucid" to "maverick" (if it isn't changed already).

You can probably also run Update Manager > Settings... button > Other Software tab > re-enable every PPA, but I haven't tried it. ;)

**EDIT**: apparently I haven't fully read your first post, you don't have access to Update Manager or Software Center. Try running "sudo apt-get update && sudo apt-get dist-upgrade" from a terminal and see if it fixes anything.

---

### Post by sandyd on 2010-10-12
> **JackNocturne said:**
> Thanks for reply:)

No,im afraid things remain the same when i execute that command. I'm kinda stuck, firefox works though, its the one i'm using to browse the internet.

By the way i didn't do a fresh install , i upgraded through Update Manager(when it worked) if that helps.
if I remember correctly, 3dparty repos are disabled after an upgrade.
therefore you have to reenable them.
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
see if that helps first.

---

### Post by JackNocturne on 2010-10-12
Hello again,

I **uncommented** the ppa lists in /etc/apt/sources.list.d ,updated & upgraded.

If i do a apt-get dist-upgrade ,it replies with [B]0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
[/B]
The problem still remains, the programs(Ubuntu software-center etc) don't launch :(

As from my #1 post, do you think its a problem with Python modules? I tried re-installing Python , Python-gtk bindings etc  no success as of present.

---

### Post by davidmohammed on 2010-10-12
in your chrome trace it mentions an issue with your theme engine - "industrial".  Have you got a non default theme installed?

Maybe you have to reinstall the gtk2-engine again.

Suggest - open synaptic manager.  Search for gtk2-engine.  Right click the gtk2-engine.  Select "install" or "reinstall" from the pop-up menu option followed by the "apply" button on the toolbar.

---

### Post by JackNocturne on 2010-10-12
> **davidmohammed said:**
> in your chrome trace it mentions an issue with your theme engine - "industrial".  Have you got a non default theme installed?

Maybe you have to reinstall the gtk2-engine again.

Suggest - open synaptic manager.  Search for gtk2-engine.  Right click the gtk2-engine.  Select "install" or "reinstall" from the pop-up menu option followed by the "apply" button on the toolbar.


I have re-installed it last week but did it again just to be sure, still no dice. Whats bad is, it feels like its an isolated problem because nobody has really reported any problem of the sort.

---

### Post by davidmohammed on 2010-10-12
if you create a new administrator user account and login with that, do you have the same issue?

---

### Post by JackNocturne on 2010-10-12
Hi again,

I created new user with Administrator privileges , **Same** result as before. When i launch certain programs, they just stay in a state of "opening" and they crash(or get killed in this case because the process never starts)

---

### Post by davidmohammed on 2010-10-12
ok - have you installed any themes lately?

suggest search for "-theme" in synaptic manager.  Remove any themes installed except for those that canonical has supplied - they have a "*" in the second column.

Also search for "gtk engine".  Again, remove any engines other than those with "*" in the second column.

---

### Post by JackNocturne on 2010-10-13
Hello again,

I haven't installed any themes lately (maybe 2 months ago was last time).
I have tried to remove unofficial themes from Synaptic but still **no** success with the problem. What **type** of problem do you think this?

---

### Post by davidmohammed on 2010-10-13
Hi there,
  I was thinking that a recently installed theme introduced a gtk problem as per [this thread]("http://ubuntuforums.org/showthread.php?t=1589396") which has similar errors reported as yourself.

perhaps you should backup your /home partition, reinstall a clean installation of meerkat and then (via the live CD) copy back your /home partition OR just the important files you need.

---

### Post by JackNocturne on 2010-10-18
bump:)

---

### Post by beew on 2010-10-18
> **JackNocturne said:**
> I have re-installed it last week but did it again just to be sure, still no dice. Whats bad is, it feels like its an isolated problem because nobody has really reported any problem of the sort.

I experienced a similar problem but only for some obscure small applications. By and large most things work but I have bigger problems concerning graphic and wireless drivers.

I did an upgrade from a "test" installation just to find out how it works. I don't know if it is normal but it took hours and some settings might be messed up (resulting in softwares not starting and may be some other problems that haven't shown up yet) I decided that it is a lot easier and faster to do a fresh install (20 minutes max) and reinstall the apps (maybe an hour max but would be a lot less for my "test system" which is quite minimalist)

---

### Post by johankronberg on 2011-04-03
```
:~$ update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 29, in <module>
    import gtk
  File "/usr/lib/pymodules/python2.6/gtk-2.0/gtk/__init__.py", line 40, in <module>
    from gtk import _gtk
ImportError: cannot import name _gtk
```I got almost the same problem it seems.

Firefox and Synaptic and most other stuff run without problems but I can't start Update Manager, Computer Janitor or Ubuntu Software Center.

My problems started with another problem that seems like this one:
[http://ubuntuforums.org/showthread.php?t=1603149](http://ubuntuforums.org/showthread.php?t=1603149)

I think before that one I had some kind of file system failure. I think the computer in question is running 64-bit 10.10.

EDIT: In Synaptic I searched for python and sorted by installed state, selected all installed rows and marked for reinstallation.

---

