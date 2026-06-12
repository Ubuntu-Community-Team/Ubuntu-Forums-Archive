---
title: "Firefox stopped starting"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by igor1102828 on 2010-02-09
Ubuntu 8.10 64bit
[COLOR="Red"]Without visible reasons old version of Firefox 3.0 (installed from Ubuntu repositories) which worked perfectly yesterday evening today
in the morning does not want to start.[/COLOR]
Skype, Chrome, etc. are working properly, so problem is not connected with internet connection.
I have many valuable bookmarks in Firefox, I need them and would like to get back Firefox. 
**Attempts:**
1. tried to start it via terminal. Does not start and gives no any comments.
2. Reinstalled firefox and firefox-3.0  via Synaptic. ------- the same result, does not start
3. Removed it via Synaptic. 
4- Have downloaded the Firefox 3.6 for Linux from firefox's website.
```
5. sudo mv firefox /opt/.
6. cd /opt
7. sudo chown -R myusername firefox
8. cd firefox
9. sudo chmod +x firefox
10. firefox 
```
The response in the terminal is:
"The program 'firefox' is currently not installed.  You can install it by typing:
sudo apt-get install firefox-3.0
bash: firefox: command not found"

 while the command 
 ```
/opt/firefox/firefox
```

produces the following response in popup windows:
window 1:

```
ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0:ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1:()
2:()
3:()
4:epsGetAttr([object Object],hidden)
5:()
6:([object Object],0,[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object],[object Object])
7:SRCH_SVC_getSorted(false)
8:SRCH_SVC_getVisible([object Object])
9:getVisibleEngines([object Object])
10:rebuildPopup()
11:rebuildPopupServices()
12:init()
13:([object XULElement],180)
```

window2:

```
ASSERT: *** Search: _installLocation: engine has no file!
Stack Trace: 
0:ENSURE_WARN(false,_installLocation: engine has no file!,2147500037)
1:()
2:()
3:()
4:epsGetAttr([object Object],hidden)
5:()
6:()
7:currentEngine()
8:get_currentEngine()
9:updateDisplay()
10:init()
11:([object XULElement],123)
```

As i told, I don't want to use the option in Synaptic "uninstall completely" because I need my bookmarks from the past. 

The other attempt to install from repository
```
deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
```
Does not work:
"*W: Failed to fetch [http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/main/binary-amd64/Packages.gz](http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt/dists/all/main/binary-amd64/Packages.gz)  404 Not Found* "


Could not start also as
```
/opt/firefox/firefox -ProfileManager 
```
Got the same above-pasted pop-up windows 

Any suggestions?

---

### Post by subodh.rohilla on 2010-02-09
If you just want your bookmarks , then export them using Bookmarks>Organize Bookmarks > Import&BACKUP . then import them in firefox 3.6.

I know it is not the solution of your problem but at last you can do this

---

### Post by warfacegod on 2010-02-09
The troubleshooting guide here may help:

[http://ubuntuforums.org/showthread.php?t=1193567]("http://ubuntuforums.org/showthread.php?t=1193567")

---

### Post by lovinglinux on 2010-02-09
> **igor1102828 said:**
> As i told, I don't want to use the option in Synaptic "uninstall completely" because I need my bookmarks from the past. 

Uninstalling Firefox won't delete your bookmarks. They are stored in ~/.mozilla/firefox/<profilename>/places.sqlite and are not affected by Firefox system files.

Backup the ~/.mozilla/firefox if you are too worried, then just go to Synaptic and mark firefox and firefox-3.0 for re-installation, then apply.

If after that you can't start it, then create a new profile. To do that run this:

```
firefox -P
```

It will force Firefox to start with the profile manager, from where you can create a new profile. If the clean profile works, which is most likely, then your profile has a problem, which could be a corruption or some extension bug. You can try to figure out what is going on or simply copy the important files from the old profile to the new one. Here a some of them:

places.sqlite = bookmarks and history
key3.db + signons.sqlite = passwords
prefs.js = user preferences
localstore.rdf = toolbars customization
mimeTypes.rdf = how to open things like .avi, mailto and so on

Don't copy the entire profile, otherwise you will end up with the same issue.

If you want to figure out, try this:

```
firefox -safe-mode
```

If it starts, then you probably have a rogue extension. I would bet on Cooliris.

---

### Post by igor1102828 on 2010-02-09
> **warfacegod said:**
> The troubleshooting guide here may help:

[http://ubuntuforums.org/showthread.php?t=1193567]("http://ubuntuforums.org/showthread.php?t=1193567")


> **lovinglinux said:**
> Uninstalling Firefox won't delete your bookmarks. They are stored in ~/.mozilla/firefox/<profilename>/places.sqlite and are not affected by Firefox system files.

Backup the ~/.mozilla/firefox if you are too worried, then just go to Synaptic and mark firefox and firefox-3.0 for re-installation, then apply.

If after that you can't start it, then create a new profile. To do that run this:

```
firefox -P
```

It will force Firefox to start with the profile manager, from where you can create a new profile. If the clean profile works, which is most likely, then your profile has a problem, which could be a corruption or some extension bug. You can try to figure out what is going on or simply copy the important files from the old profile to the new one. Here a some of them:

places.sqlite = bookmarks and history
key3.db + signons.sqlite = passwords
prefs.js = user preferences
localstore.rdf = toolbars customization
mimeTypes.rdf = how to open things like .avi, mailto and so on

Don't copy the entire profile, otherwise you will end up with the same issue.

If you want to figure out, try this:

```
firefox -safe-mode
```

If it starts, then you probably have a rogue extension. I would bet on Cooliris.
 Thanks a lot, guys, both the link to Firefox troubleshooting and **lovinglinux** notes are very helpful. First step is done!

1. I had to backup old profile
```
mv .mozilla .mozillaOLD
```
2. after that the command 
```
sudo /opt/firefox/firefox 
```
has started at last the firefox and new profile has been created, but with a lot of complaints on impossibility to load some plugins...
3. After that I've written link to */opt/firefox/firefox *
via Main-menu editor (System--> Preferences-->Main menu) 
and now Firefox can be started from menu. It would be nice if you make also hint on [COLOR="DarkRed"]how to replace wrong icon in menu to the Firefox's one: icons in Firefox are *.png, whereas menu wants *.svg[/COLOR].

---

### Post by igor1102828 on 2010-02-09
Forgot to say, that, of course, I've changed ownship
 ```
sudo chown -R myusername:myusername .mozilla
```.

---

### Post by warfacegod on 2010-02-09
Are you sure that Firefox hasn't started stopping instead?

---

### Post by lovinglinux on 2010-02-09
> **warfacegod said:**
> Are you sure that Firefox hasn't started stopping instead?

That is a possibility. I have been dealing with this problem myself lately, since the upgrade to Firefox 3.6. What happens is that firefox-bin process doesn't shut down and you can't start Firefox while it is running. Nevertheless, the OP would probably receive a warning about Firefox being running already.

---

### Post by warfacegod on 2010-02-09
I was being utterly sarcastic when I said that.

Now that you mention it, I'm getting the same issue as you described, in 9.10 UNR with 3.5.7 not 3.6. Started last night and it's been 2? days since an update. I don't really care, it's in my experiment partition. Just thought that it was worth mentioning because of the version difference.

---

