---
title: "Screenlets for Karmic Koala"
date: 2009-11-21
forum: New to Ubuntu
---

### Post by Captainflowers91 on 2009-11-21
I'm running Karmic Koala and I cant get screenlets to install regardless of what I try. Nothing seems to work. Ill post the results that I get when I  try

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  screenlets: Depends: python-wnck but it is not going to be installed or
                       python-gnome2-desktop but it is not going to be installed
              Recommends: python-feedparser but it is not going to be installed
              Recommends: python-gtkmozembed but it is not going to be installed or
                          python-gnome2-extras (< 2.19) but it is not going to be installed
              Recommends: iceweasel but it is not installable or
                          firefox
              Recommends: python-evolution but it is not going to be installed or
                          python-gnome2-desktop but it is not going to be installed
  sun-java6-jre: Depends: sun-java6-bin (= 6-15-1) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-15-1) but it is not installable
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


Updating does not help either. Please help!

---

### Post by Captainflowers91 on 2009-11-21
Also, when I try and install it through the Ubuntu Software Center, I get this 

E:I wasn't able to locate a file for the sun-java6-jre package. This might mean you need to manually fix this package. (due to missing arch):

---

### Post by booksnmore4you on 2009-12-26
Screenlets does not appear to have been developed for a while. In Karmic, I cannot get half of them to delete, and I get the following when running desklets

```
** (screenlets-manager.py:27662): WARNING **: Trying to register gtype 'WnckWindowState' as flags when in fact it is of type 'GEnum'

** (screenlets-manager.py:27662): WARNING **: Trying to register gtype 'WnckWindowActions' as flags when in fact it is of type 'GEnum'

** (screenlets-manager.py:27662): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as flags when in fact it is of type 'GEnum'
/usr/share/screenlets-manager/screenlets-manager.py:93: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips = gtk.Tooltips()
/usr/share/screenlets-manager/screenlets-manager.py:414: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but1, _('Launch/add a new instance of the selected Screenlet ...'))
/usr/share/screenlets-manager/screenlets-manager.py:415: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but2, _('Install a new Screenlet, SuperKaramba or Web Widget or Web Application  ...'))
/usr/share/screenlets-manager/screenlets-manager.py:416: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but3, _('Permanently uninstall/delete the currently selected Screenlet ...'))
/usr/share/screenlets-manager/screenlets-manager.py:417: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but4, _('Reset this Screenlet configuration (will only work if screenlet isnt running)'))
/usr/share/screenlets-manager/screenlets-manager.py:418: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but5, _('Install new theme for this screenlet'))
/usr/share/screenlets-manager/screenlets-manager.py:419: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but6, _('Restart all screenlets that have auto start at login'))
/usr/share/screenlets-manager/screenlets-manager.py:420: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but7, _('Close all Screenlets running'))
/usr/share/screenlets-manager/screenlets-manager.py:421: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but8, _('New Screenlets Options/Properties'))
/usr/share/screenlets-manager/screenlets-manager.py:422: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but9, _('Create a Desktop shortcut for this Screenlet'))
/usr/share/screenlets-manager/screenlets-manager.py:477: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but_about, _('Show info about this dialog ...'))
/usr/share/screenlets-manager/screenlets-manager.py:478: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but_download, _('Download more screenlets ...'))
/usr/share/screenlets-manager/screenlets-manager.py:479: DeprecationWarning: Use the new widget gtk.Tooltip
  self.tips.set_tip(but_close, _('Close this dialog ...'))
```gdesklets are so buggy nowadays as to be embarrassing.

---

