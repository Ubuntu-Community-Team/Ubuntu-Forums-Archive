---
title: "KAlarm bugs?"
date: 2011-01-24
forum: New to Ubuntu
---

### Post by itsols on 2011-01-24
Hi, I've just installed KAlarm. After installation, I could not find a shortcut in the menu. So I tried running it via terminal and this is what I got:

> <unknown program name>(3390)/ main: initialising

(<unknown>:3390): IBUS-WARNING **: Connect to unix:abstract=/tmp/dbus-vd51Ck3ALe,guid=0ddffd4f1598818a5a0ce50b00000024 failed: Failed to connect to socket /tmp/dbus-vd51Ck3ALe: Connection refused.
Connecting to deprecated signal QDBusConnectionInterface::serviceOwnerChanged(QString,QString,QString)

(<unknown>:3401): IBUS-WARNING **: Connect to unix:abstract=/tmp/dbus-vd51Ck3ALe,guid=0ddffd4f1598818a5a0ce50b00000024 failed: Failed to connect to socket /tmp/dbus-vd51Ck3ALe: Connection refused.
QMetaObject::invokeMethod: No such method KUniqueApplication::loadCommandLineOptionsForNewInstance()
kbuildsycoca4 running...
kbuildsycoca4(3403) KBuildMimeTypeFactory::createEntry: Missing <comment> field in "application/x-note.xml" 
kbuildsycoca4(3403) KConfigGroup::readXdgListEntry: List entry MimeType in "/usr/share/applications/monodevelop.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kbuildsycoca4(3403) KConfigGroup::readXdgListEntry: List entry Categories in "/usr/share/applications/supertux.desktop" is not compliant with XDG standard (missing trailing semicolon). 
kalarm(3390)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
<unknown program name>(3419)/ main: Unknown resource type:  "alarms" 
QMetaObject::invokeMethod: No such method KAlarmApp::loadCommandLineOptionsForNewInstance()

(<unknown>:3421): IBUS-WARNING **: Connect to unix:abstract=/tmp/dbus-vd51Ck3ALe,guid=0ddffd4f1598818a5a0ce50b00000024 failed: Failed to connect to socket /tmp/dbus-vd51Ck3ALe: Connection refused.
QMetaObject::invokeMethod: No such method KUniqueApplication::loadCommandLineOptionsForNewInstance()
QSystemTrayIcon::setVisible: No Icon set
QDBusConnection: name 'org.kde.kglobalaccel' had owner '' but we thought it was ':1.125'
kalarm(3390) KGlobalAccelPrivate::_k_serviceOwnerChanged: detected kglobalaccel restarting, re-registering all shortcut keys
khalid@khalid-laptop:~$ 
(<unknown>:3424): IBUS-WARNING **: Connect to unix:abstract=/tmp/dbus-vd51Ck3ALe,guid=0ddffd4f1598818a5a0ce50b00000024 failed: Failed to connect to socket /tmp/dbus-vd51Ck3ALe: Connection refused.
QMetaObject::invokeMethod: No such method KUniqueApplication::loadCommandLineOptionsForNewInstance()
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x460294c
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x4602742
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x46028e4
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x46028e4
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 18 (X_ChangeProperty)
  Resource id:  0x46028e4
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x460294c
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x460294c
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 18 (X_ChangeProperty)
  Resource id:  0x460294c
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x46038b6
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x4603a0f
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)
  Resource id:  0x4603852
^C


Somehow, the program runs. And I even tested an alert. It works.

So my questions are:

1. Is this an error that I should just ignore?
2. When run from terminal, I can't use the same terminal window for any other task. Isn't there a way around this to have it start up automatically?
3. Is KAlarm better or the Gnome Alarm program?
4. Do the errors mean that certain features will not work?

Thanks to everyone for their thoughts!

---

### Post by LewRockwellFAN on 2011-01-25
> **itsols said:**
> 
2. When run from terminal, I can't use the same terminal window for any other task. Isn't there a way around this to have it start up automatically?


If you mean you just don't want a terminal describing the inner doings of that program cluttering up your desktop, try a launcher. Just put the command you used to start the program in the terminal in the launcher. That doesn't always work but it usually does. If you mean automatically as in start every time your computer does, yes you can do that also. I don't recall how but if that is what you want to do use the search feature for the forum. I'm sure I've read about that somewhere, probably here.

---

### Post by itsols on 2011-01-25
Yeah, I guess I'll have to just use a launcher... But my worry is those other messages... Anyway, thank you for your time.

---

### Post by swords65 on 2011-02-04
Depending upon the version of Kalarm you have installed you can configure the autostart feature from within Kalarm itself. If it is an older version you can add it to your startup applications under System > Preferences > Startup Applications. Kalarm has gotten really crappy in the last few versions. I am having the same problem with all the internal errors and I can't build a newer version. None of them will compile. So, I'm stuck with 2.4.8 from the repositories.

---

### Post by itsols on 2011-02-04
Surprise! I don't see any more errors and I also see KAlarm in the menu!

I did nothing. Thank you all for your support.

---

