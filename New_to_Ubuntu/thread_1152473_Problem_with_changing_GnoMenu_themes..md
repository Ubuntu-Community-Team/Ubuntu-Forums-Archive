---
title: "Problem with changing GnoMenu themes."
date: 2009-05-07
forum: New to Ubuntu
---

### Post by WinterMadness on 2009-05-07
Okay, so when I select the theme I want, naturally I click okay afterwards. Nothing happens. I decided to run the gnomenu settings in the terminal so I can get some feed back as to whats going on. heres what it says

keep in mind, that i definitely used sudo, so when it says permission denied I dont know why.

```

joe@joe-mint /usr/lib/gnomenu $ sudo GnoMenu-Settings.py
[sudo] password for joe: 
sudo: GnoMenu-Settings.py: command not found
joe@joe-mint /usr/lib/gnomenu $ ./GnoMenu-Settings.py
None
./GnoMenu-Settings.py:410: GtkWarning: Error parsing gtk-icon-sizes string:
	'panel-menu=24,24
panel=20,20
gtk-button=18,18
gtk-large-toolbar=24,24'
  wTree = gtk.glade.XML(Images.GladeSettingsFile)
Kore
Newstyles
ubuntustudio-circle
Classic
Recoverable Error: Widget not found: LA
Recoverable Error: Widget not found: DI
Recoverable Error: Widget not found: AD
Recoverable Error: Widget not found: LALBL1
Recoverable Error: Widget not found: LAThmHasLBL
Recoverable Error: Widget not found: LALblAddLang
Recoverable Error: Widget not found: DIDesc
Recoverable Error: Widget not found: THInclOpts
Recoverable Error: Widget not found: ADSpin1
Recoverable Error: Widget not found: ADSpin2
Recoverable Error: Widget not found: ADSpin3
Recoverable Error: Widget not found: ADWinKey
Recoverable Error: Widget not found: LAImg1
Recoverable Error: Widget not found: LALangBox
Recoverable Error: Widget not found: THInclOpts
Warning: Name location identifier not recognised from: <Name Id="0" Loc="DesktopIntegrationTable_Cat" Text="Focus Steal Prevention"/>
Warning: Name location identifier not recognised from: <Name Id="1" Loc="DesktopIntegrationTable_Cat" Text="Panel Shadow"/>
Warning: Name location identifier not recognised from: <Name Id="2" Loc="DesktopIntegrationTable_Cat" Text="Panel Transparency"/>
Warning: Name location identifier not recognised from: <Name Id="3" Loc="DesktopIntegrationTable_Cat" Text="Menu Transparency"/>
Warning: Name location identifier not recognised from: <Name Id="Enabled" Loc="DesktopIntegrationTable" Text="Enabled"/>
Warning: Name location identifier not recognised from: <Name Id="Disabled" Loc="DesktopIntegrationTable" Text="Disabled"/>
Warning: Name location identifier not recognised from: <Name Id="0" Loc="DesktopIntegrationTable_Col" Text="Setting"/>
Warning: Name location identifier not recognised from: <Name Id="1" Loc="DesktopIntegrationTable_Col" Text="Value"/>
Warning: Name location identifier not recognised from: <Name Id="2" Loc="DesktopIntegrationTable_Col" Text="Enabled"/>
Traceback (most recent call last):
  File "./GnoMenu-Settings.py", line 394, in OK_Pressed
    SaveSettings()
  File "./GnoMenu-Settings.py", line 389, in SaveSettings
    file_object = open(Images.HomeDirectory+"/.GnoMenuSettings.xml","w") 
IOError: [Errno 13] Permission denied: '/home/joe/.GnoMenuSettings.xml'
Traceback (most recent call last):
  File "./GnoMenu-Settings.py", line 394, in OK_Pressed
    SaveSettings()
  File "./GnoMenu-Settings.py", line 389, in SaveSettings
    file_object = open(Images.HomeDirectory+"/.GnoMenuSettings.xml","w") 
IOError: [Errno 13] Permission denied: '/home/joe/.GnoMenuSettings.xml'
Traceback (most recent call last):
  File "./GnoMenu-Settings.py", line 394, in OK_Pressed
    SaveSettings()
  File "./GnoMenu-Settings.py", line 389, in SaveSettings
    file_object = open(Images.HomeDirectory+"/.GnoMenuSettings.xml","w") 
IOError: [Errno 13] Permission denied: '/home/joe/.GnoMenuSettings.xml'
Traceback (most recent call last):
  File "./GnoMenu-Settings.py", line 394, in OK_Pressed
    SaveSettings()
  File "./GnoMenu-Settings.py", line 389, in SaveSettings
    file_object = open(Images.HomeDirectory+"/.GnoMenuSettings.xml","w") 
IOError: [Errno 13] Permission denied: '/home/joe/.GnoMenuSettings.xml'
^CTraceback (most recent call last):
  File "./GnoMenu-Settings.py", line 533, in <module>
    gtk.main()
KeyboardInterrupt

```

---

### Post by WinterMadness on 2009-05-08
bump

---

