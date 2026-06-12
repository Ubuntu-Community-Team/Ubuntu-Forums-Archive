---
title: "Help with Weatherbug install"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by ebeckhusen on 2009-04-19
I just installed Weatherbug from the .deb file on weatherbug.com.  I try to start it and it doesn't come up. I ran the command in terminal and got:

```
Exception in thread "Thread-1" java.lang.NoClassDefFoundError: nu.xom.Builder
   at java.lang.Class.initializeClass(libgcj.so.90)
   at com.aws.java.tempest.service.impl.SettingServiceImpl.startUp(SettingServiceImpl.java:124)
   at com.aws.java.tempest.Tempest$LoadThread.run(Tempest.java:208)
Caused by: java.lang.ClassNotFoundException: org.apache.xerces.parsers.SAXParser not found in gnu.gcj.runtime.SystemClassLoader{urls=[file:/usr/share/java/weatherbug.jar], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null}}
   at java.net.URLClassLoader.findClass(libgcj.so.90)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.90)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at java.lang.VMClassLoader.defineClass(libgcj.so.90)
   at java.lang.ClassLoader.defineClass(libgcj.so.90)
   at java.security.SecureClassLoader.defineClass(libgcj.so.90)
   at java.net.URLClassLoader.findClass(libgcj.so.90)
   at gnu.gcj.runtime.SystemClassLoader.findClass(libgcj.so.90)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at java.lang.ClassLoader.loadClass(libgcj.so.90)
   at java.lang.Class.forName(libgcj.so.90)
   at java.lang.Class.initializeClass(libgcj.so.90)
   ...2 more

```

Anyone know what this means and how I can fix it?  I searched and there were a couple of threads, but no solution attempts, only people recommending other weather programs/applets.  Tried some of the others that were suggested but none are as accurate for me as Weatherbug.

Any help would be greatly appreciated.

---

### Post by llamabr on 2009-04-19
Where did you get that .deb?  And why didn't you install it from the repositories?

---

### Post by ebeckhusen on 2009-04-19
> **llamabr said:**
> Where did you get that .deb?  And why didn't you install it from the repositories?

I got the .deb from Weatherbug.com.  I didn't install from the repos because I didn't see it there.

---

### Post by llamabr on 2009-04-19
From: [http://www.ubuntugeek.com/installing-weatherbug-for-linux.html/comment-page-1](http://www.ubuntugeek.com/installing-weatherbug-for-linux.html/comment-page-1)

Goto System, Administration, Software Sources. Immediately, look for:

“Software restricted by copyright or legal issues (multiverse)”

Make sure that has a check in the box, hit “Close”, then when prompted, Reload.

After doing this, install the application from it’s Deb package, look on your desktop for the shortcut. Understand that it will NOT autostart at each boot without you choosing to make it do so from your Sessions area.

If you are still having issues, just post back here. I suspect that you are not running with all of your repositories enabled and this is a new install of Ubuntu.

---

### Post by starcannon on 2009-04-19
A weather agent comes default installed in Ubuntu, perhaps try that one first to see if it meets your needs? 


[LIST=1]
[*]R-click on the top or bottom panel.
[*]Click on "+Add to Panel" from the contextual menu.
[*]In the search field type "Weather Report" without quotes.
[*]Select the "Weather Report" item.
[*]Click "Add" near bottom right corner of the window.
[*]R-click on the applet, it may show up as "--" on first run.
[*]Choose Preferences
[*]Enable "Radar Map"
[*]Select the "Location Tab"
[*]Set it to a location suitable for your needs.
[/LIST]
Enjoy

---

### Post by ebeckhusen on 2009-04-19
> **llamabr said:**
> From: [http://www.ubuntugeek.com/installing-weatherbug-for-linux.html/comment-page-1](http://www.ubuntugeek.com/installing-weatherbug-for-linux.html/comment-page-1)

Goto System, Administration, Software Sources. Immediately, look for:

“Software restricted by copyright or legal issues (multiverse)”

Make sure that has a check in the box, hit “Close”, then when prompted, Reload.

After doing this, install the application from it’s Deb package, look on your desktop for the shortcut. Understand that it will NOT autostart at each boot without you choosing to make it do so from your Sessions area.

If you are still having issues, just post back here. I suspect that you are not running with all of your repositories enabled and this is a new install of Ubuntu.

The repository was already enabled.  I disabled then enabled again, reloaded, reinstalled the deb package, and I'm still in the same situation as before: will not launch from the icon, gives the error I reported above when I launch from terminal.

---

### Post by halitech on 2009-04-19
do you have java installed? almost looks like java errors either not installed or not the right version.

---

### Post by ebeckhusen on 2009-04-19
> **halitech said:**
> do you have java installed? almost looks like java errors either not installed or not the right version.

Yes I have Java installed, at least I believe so as I installed the restricted-extras and it works in my browser.  If I recall from my other installs, I had trouble getting any other java plugin to work with Firefox.

[edit] I thought that Java was installed, but apparently not.  In the process of installing Java 6, if I have further problems I'll write again.

---

### Post by ebeckhusen on 2009-04-19
> **starcannon said:**
> A weather agent comes default installed in Ubuntu, perhaps try that one first to see if it meets your needs? 


[LIST=1]
[*]R-click on the top or bottom panel.
[*]Click on "+Add to Panel" from the contextual menu.
[*]In the search field type "Weather Report" without quotes.
[*]Select the "Weather Report" item.
[*]Click "Add" near bottom right corner of the window.
[*]R-click on the applet, it may show up as "--" on first run.
[*]Choose Preferences
[*]Enable "Radar Map"
[*]Select the "Location Tab"
[*]Set it to a location suitable for your needs.
[/LIST]
Enjoy

Thanks, but I tried that one already.  It's about 10 or so degrees off (we have something like 4 different weather zones here, which is why it's so hard to find a weather gadget that works).

---

### Post by ebeckhusen on 2009-04-19
Well, Java didn't help either.  I tried both Java 5 and Java 6 and still get the same message.  At this point I'm thinking that I'll just have to use one of the other alternatives that isn't too horribly off the mark.  Thanks for your help.

---

### Post by starcannon on 2009-04-19
Doh, just realized I posted the same thing as [llamabr]("http://ubuntuforums.org/member.php?u=404864") posted ealier, sorry about that.

I looked around at some other tutes, and they all look the same.

---

### Post by ebeckhusen on 2009-04-19
> **starcannon said:**
> Heres a nice guide on weatherbug in Ubuntu:
[http://www.ubuntugeek.com/installing-weatherbug-for-linux.html](http://www.ubuntugeek.com/installing-weatherbug-for-linux.html)

Hope its useful.

GL

Thanks for that, but someone else posted it earlier

---

### Post by TideMan on 2009-04-19
> **starcannon said:**
> A weather agent comes default installed in Ubuntu, perhaps try that one first to see if it meets your needs? 


[LIST=1]
[*]R-click on the top or bottom panel.
[*]Click on "+Add to Panel" from the contextual menu.
[*]In the search field type "Weather Report" without quotes.
[*]Select the "Weather Report" item.
[*]Click "Add" near bottom right corner of the window.
[*]R-click on the applet, it may show up as "--" on first run.
[*]Choose Preferences
[*]Enable "Radar Map"
[*]Select the "Location Tab"
[*]Set it to a location suitable for your needs.
[/LIST]
Enjoy

These instructions worked beautifully for me, thank you starcannon.

---

### Post by ebeckhusen on 2009-04-19
If anyone really needs Weatherbug, I found out that you can also get it with Google Gadgets.  Search the web for the install instructions, though I have to warn you it doesn't come packaged, you need to install from source.

---

### Post by odindio on 2009-09-28
yes we want to use the real weatherbug not the stupid wether widget or some other crap - give an answer or don't -not a detour to something that we don't want.

---

