---
title: "Automatically Starting programs?"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by DeviantGuy on 2011-02-02
Hello, I now have been using Ubuntu for about a month now, does anyone here know the Startup folder? Yes that folder that automatically starts programs. Does Ubuntu has a startup folder? I would love to have Empathy start up automatically. I just was curious... Thats all

---

### Post by jdmcclung on 2011-02-02
I'm not sure it's location in the gnome menu, but it you can find the Gnome Control Center. Click Startup applications. Click add then fill in the information.

---

### Post by NightwishFan on 2011-02-02
System -> Preferences -> Startup Applications

---

### Post by synicalx on 2011-02-02
> **jdmcclung said:**
> I'm not sure it's location in the gnome menu, but it you can find the Gnome Control Center. Click Startup applications. Click add then fill in the information.

System -> Preferences -> Startup Applications

;)

EDIT: Beaten =P

Also forgot to mention that some programs (not Empathy though) can be configured from within the program itself to start automatically. Good example of this is Cairo or Screenlets

---

### Post by sisco311 on 2011-02-02
Go to System -> Preferences -> Startup Applications and add a new one. In the command field type: ```
empathy --start-hidden
```.

Hmmm, the *startup directory* question is a little bit more complicated. Most desktop environments follow the freedesktop specs:
[http://standards.freedesktop.org/autostart-spec/autostart-spec-latest.html](http://standards.freedesktop.org/autostart-spec/autostart-spec-latest.html)

---

### Post by towheedm on 2011-02-02
The programs that starts when you log in are located under System > Preferences > Startup Applications.

To add empathy do the following:

1.  Open Startup Applications
2.  Click on Add in the Startup Applications Preferences dialog
3.  In the name box of the Add Startup Program, enter a name you would like to show in the Preferences dialog.  In this case enter 'Empathy'.
4.  In the Command box, enter empathy.
5.  Enter any comments.
6.  Click Add

Empathy should now be listed in the Preferences dialog and should start automatically the next time you log in.

---

### Post by HandeH on 2011-02-03
I have succeeded to run scripts and start applications by [gnome-schedule]("apt://gnome-schedule") or by putting into gnome-session-properties a quoted command (or commands separated by ;, i.e. semicolon) starting with bash -c, like this way: 
```
bash -c "rm -rf ~/.macromedia/Flash_Player/#SharedObjects/*"
``` as suggested [here]("http://ubuntuforums.org/showpost.php?p=10120454&postcount=4"). 


There is also another fresh [thread]("http://http://ubuntuforums.org/showthread.php?t=1676162") on this issue. And some bug reports: [460746]("https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/460746"), [518740]("https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/518740"). Consider to mark those affecting you also.

---

