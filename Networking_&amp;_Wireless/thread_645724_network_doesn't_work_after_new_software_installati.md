---
title: "network doesn't work after new software installation. .xsession-errors generated."
date: 2007-12-20
forum: Networking &amp; Wireless
---

### Post by antalar on 2007-12-20
I have installed some new software (PAM libraries and mingw) and my work stopped to work. My device is still active, but i can't ping my gateway. 

I found in ~/ file named .xsession-errors and there can be some clues to the solution of this problem. can anybody help me to understand contents of this file?



Xsession: X session started for antalar at &#1063;&#1090;&#1074; &#1044;&#1077;&#1082; 20 19:33:20 MSK 2007
Setting IM through im-switch for locale=ru_RU.
Start IM through /etc/X11/xinit/xinput.d/all_ALL linked to /etc/X11/xinit/xinput.d/default.
xset:  bad font path element (#103), possible causes are:
    Directory does not exist or has wrong permissions
    Directory missing fonts.dir
    Incorrect font server address or syntax
startkde: Starting up...
startkde: kpersonalizer not found! Please install to properly configure your user.
kbuildsycoca running...
*** attempt to put segment in horiz list twice
kdesktop: WARNING: Pixmap not found for mimetype image/x-djvu
kdesktop: WARNING: Pixmap not found for mimetype image/x-djvu
kdesktop: WARNING: Pixmap not found for mimetype image/x-djvu
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  15
  Minor opcode:  0
  Resource id:  0x100004a
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x1a00059
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/firefox/plugins/libjavaplugin.so: undefined symbol: NP_GetValue
nspluginscan: WARNING: Plugin doesn't implement NP_GetValue
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/firefox/plugins/libjavaplugin.so: undefined symbol: NP_GetMIMEDescription
Ignored duplicate item: GNU TeXmacs Editor
Ignored duplicate item: KArm
Ignored duplicate item: KDE Groupware Wizard
Ignored duplicate item: KNotes
Ignored duplicate item: Kontact
Ignored duplicate item: kFlickr
Ignored duplicate item: KDE Groupware Wizard
Ignored duplicate item: Qalculate!
Ignored duplicate item: Strigi
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/mozilla/plugins/libjavaplugin.so: undefined symbol: NP_GetValue
nspluginscan: WARNING: Plugin doesn't implement NP_GetValue
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/mozilla/plugins/libjavaplugin.so: undefined symbol: NP_GetMIMEDescription
khelpcenter: WARNING: Main template file name is empty.
Could not find 'guidance-power-manager.py' executable.
kwin: X_CopyArea(0x10000f2): BadMatch (invalid parameter attributes)
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x140027c
kbuildsycoca running...
Reusing existing ksycoca
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1400281
QObject::connect: No such slot MakeWidget::slotDocumentOpened(const KURL&)
QObject::connect:  (sender name:   'unnamed')
QObject::connect:  (receiver name: 'make widget')
kdecore (KProcess): WARNING: _attachPty() 13
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x140029a
kdecore (KProcess): WARNING: _attachPty() 11
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x14002b8
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x80d7510 ): KAccel object already contains an action name "file_quit"
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x80d7510 ): KAccel object already contains an action name "file_quit"
WARNING: DCOPReply<>: cast to 'bool' error
DCOP aborting while waiting for answer from 'kded'
DCOPServer::DCOPReply for unknown connection.
QLayout "unnamed" added to IndexView "unnamed", which already has a layout
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x14002e9
kbuildsycoca running...
Reusing existing ksycoca
DCOP Cleaning up dead connections.
kdecore (KAction): WARNING: KAction::initPrivate(): trying to assign a shortcut (Alt+Ctrl+Shift+N) to an unnamed action.
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1400329
kdecore (KProcess): WARNING: _attachPty() 12
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1400368
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 4' gave syntax error
QObject::connect: No such signal KListBox::clicked(QListBoxItem*item)
QObject::connect:  (sender name:   'srcDistFileListBox')
QObject::connect:  (receiver name: 'dist_widget')
QObject::connect: No such slot GDBDebugger::GDBBreakpointWidget::slotAddBlankBreakpoint()
QObject::connect:  (sender name:   'gdbBreakpointWidget')
QObject::connect:  (receiver name: 'gdbBreakpointWidget')
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 4' gave syntax error
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 4' gave syntax error
QObject::connect: No such slot subversionPart::projectConfigWidget(KDialogBase*)
QObject::connect:  (sender name:   'unnamed')
QObject::connect:  (receiver name: 'Subversion')
QObject::connect: No such slot subversionPart::slotStopButtonClicked(KDevPlugin*)
QObject::connect:  (sender name:   'unnamed')
QObject::connect:  (receiver name: 'Subversion')
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x14006c3
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x14006f6
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1400701
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x140070c
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1400727
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x140073e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1400755
QObject::connect: Cannot connect (null)::dropEventPass(QDropEvent *) to SimpleMainWindow::slotDropEvent(QDropEvent *)
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x140077b
QObject::connect: Cannot connect (null)::dropEventPass(QDropEvent *) to SimpleMainWindow::slotDropEvent(QDropEvent *)
QObject::connect: Cannot connect (null)::dropEventPass(QDropEvent *) to SimpleMainWindow::slotDropEvent(QDropEvent *)
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x14007f3
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x14007fd
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1400814
QObject::connect: Cannot connect (null)::dropEventPass(QDropEvent *) to SimpleMainWindow::slotDropEvent(QDropEvent *)
QObject::connect: Cannot connect (null)::dropEventPass(QDropEvent *) to SimpleMainWindow::slotDropEvent(QDropEvent *)
QObject::connect: Cannot connect (null)::dropEventPass(QDropEvent *) to SimpleMainWindow::slotDropEvent(QDropEvent *)
QObject::connect: Cannot connect (null)::dropEventPass(QDropEvent *) to SimpleMainWindow::slotDropEvent(QDropEvent *)
QObject::connect: Cannot connect (null)::dropEventPass(QDropEvent *) to SimpleMainWindow::slotDropEvent(QDropEvent *)
QObject::connect: Cannot connect (null)::dropEventPass(QDropEvent *) to SimpleMainWindow::slotDropEvent(QDropEvent *)
QObject::connect: Cannot connect (null)::dropEventPass(QDropEvent *) to SimpleMainWindow::slotDropEvent(QDropEvent *)
QObject::connect: Cannot connect (null)::dropEventPass(QDropEvent *) to SimpleMainWindow::slotDropEvent(QDropEvent *)
QObject::connect: Cannot connect (null)::dropEventPass(QDropEvent *) to SimpleMainWindow::slotDropEvent(QDropEvent *)
QObject::connect: Cannot connect (null)::dropEventPass(QDropEvent *) to SimpleMainWindow::slotDropEvent(QDropEvent *)
QObject::connect: Cannot connect (null)::dropEventPass(QDropEvent *) to SimpleMainWindow::slotDropEvent(QDropEvent *)
QObject::connect: Cannot connect (null)::dropEventPass(QDropEvent *) to SimpleMainWindow::slotDropEvent(QDropEvent *)
QObject::connect: Cannot connect (null)::dropEventPass(QDropEvent *) to SimpleMainWindow::slotDropEvent(QDropEvent *)
QObject::connect: Cannot connect (null)::dropEventPass(QDropEvent *) to SimpleMainWindow::slotDropEvent(QDropEvent *)
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1400986
QObject::connect: Cannot connect (null)::dropEventPass(QDropEvent *) to SimpleMainWindow::slotDropEvent(QDropEvent *)
QObject::connect: Cannot connect (null)::dropEventPass(QDropEvent *) to SimpleMainWindow::slotDropEvent(QDropEvent *)
ASSERT: "part && parent" in /build/buildd/kdevelop-3.5.0/./parts/fileview/partwidget.cpp (41)
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 4' gave syntax error
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 4' gave syntax error
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 4' gave syntax error
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 4' gave syntax error
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 4' gave syntax error
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 4' gave syntax error
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 4' gave syntax error
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 4' gave syntax error
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 4' gave syntax error
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 4' gave syntax error
kio (KTrader): WARNING: Parsing ' and [X-KDevelop-Version] == 4' gave syntax error
QObject::connect: No such slot ProblemReporter::configWidget(KDialogBase*)
QObject::connect:  (sender name:   'unnamed')
QObject::connect:  (receiver name: 'problemReporterWidget')
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1400a19
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1400a23
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1400a60
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1400a6c
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1400a7b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1400a87
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1400a94
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1400aa1
QObject::connect: Parentheses expected, slot SettingsDialog::
QObject::connect:  (sender name:   'notify_dialog')
QObject::connect:  (receiver name: 'SettingsDialog')
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1400af9
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x2800e89
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x2800e89
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1400b7d
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1400bc1
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x28010d7
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x28010d7
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1400c04
passprompt
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1400c55


X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1400c90
kbuildsycoca running...

DCOP Cleaning up dead connections.

kdecore (KProcess): WARNING: _attachPty() 11

X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1400cd7
--get XML:
<?xml version='1.0' encoding='UTF-8' standalone='yes'?>
<!DOCTYPE network []>

<network>

  <dialinstalled>1</dialinstalled>
  <domain>8ka</domain>
  <gateway>194.85.80.1</gateway>
  <gatewaydev>eth0</gatewaydev>
  <hostmatch>0</hostmatch>
  <hostname>antalar</hostname>
  <smartdhcpcd>0</smartdhcpcd>
  <smbinstalled>1</smbinstalled>
  <smbuse>1</smbuse>

  <nameserver>194.85.83.73</nameserver>
  <nameserver>194.85.83.83</nameserver>

  <statichost>
    <ip>127.0.0.1</ip>
    <alias>localhost</alias>
  </statichost>
  <statichost>
    <ip>127.0.1.1</ip>
    <alias>antalar</alias>
  </statichost>

  <interface type='modem'>

    <dev>ppp0</dev>
    <enabled>0</enabled>
  </interface>

  <interface type='loopback'>

    <configuration>
      <address>127.0.0.1</address>
      <auto>1</auto>
      <bootproto>none</bootproto>
      <broadcast>127.255.255.255</broadcast>
      <file>lo</file>
      <netmask>255.0.0.0</netmask>
      <network>127.0.0.0</network>
    </configuration>
    <dev>lo</dev>
    
<enabled>1</enabled>
  </interface>

  <interface type='ethernet'>

    <configuration>
      <address>194.85.80.223</address>
      <auto>1</auto>
      <bootproto>none</bootproto>
      <broadcast>194.85.83.255</broadcast>
      <file>eth0</file>
      <gateway>194.85.80.1</gateway>
      <netmask>255.255.252.0</netmask>
      <network>194.85.80.0</network>
    </configuration>
    <dev>eth0</dev>
    <enabled>1</enabled>
    <hwaddr>00:02:B3:65:3D:25</hwaddr>
  </interface>

  <profiledb>
  </profiledb>

</network>

<!-- GST: end of request -->

XML -d list_ifaces: <?xml version='1.0' encoding='UTF-8' standalone='yes'?>
<!DOCTYPE network-ifaces []>

<network-ifaces>

  <interface>
    <addr>127.0.0.1</addr>
    <dev>lo</dev>
    <enabled>1</enabled>
    <mask>255.0.0.0</mask>
    <type>loopback</type>
  </interface>

  <interface>
    <addr>194.85.80.223</addr>
    <bcast>194.85.83.255</bcast>
    <dev>eth0</dev>
    <enabled>1</enabled>
    <hwaddr>00:02:B3:65:3D:25</hwaddr>
    <mask>255.255.252.0</mask>
    <type>ethernet</type>
  </interface>

</network-ifaces>

<!-- GST: end of request -->

X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1400d89
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1400dc4
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1400e28
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1400e61
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1400f14
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1400f40
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1400f4a
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1400f57
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1400f75
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1401057
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1401070
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x140108a
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x14010a5
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x14010c0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x14010ec
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x140114a
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1401155
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x140117d
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1401195
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x140119f
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x14011ae
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x14011cd
QObject::connect: No such signal ListPanel::contentsMoving(int,int)
QObject::connect:  (sender name:   'unnamed')
QObject::connect:  (receiver name: 'unnamed')
QObject::connect: No such signal ListPanel::contentsMoving(int,int)
QObject::connect:  (sender name:   'unnamed')
QObject::connect:  (receiver name: 'unnamed')
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1401211
kdecore (KProcess): WARNING: _attachPty() 13
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x140125a
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x140206c
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1402101
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1402210
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1402243
krusader: WARNING: KXMLGUIClient::setXMLFile: cannot find .rc file krviewer.rc
krusader: WARNING: KXMLGUIClient::setXMLFile: cannot find .rc file krviewer.rc
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x14022d1
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x1600aca
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x140231a
krusader: WARNING: KXMLGUIClient::setXMLFile: cannot find .rc file krviewer.rc
krusader: WARNING: KXMLGUIClient::setXMLFile: cannot find .rc file krviewer.rc
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x140236a
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x1600be0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x14023b3
krusader: WARNING: KXMLGUIClient::setXMLFile: cannot find .rc file krviewer.rc
krusader: WARNING: KXMLGUIClient::setXMLFile: cannot find .rc file krviewer.rc
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1402403
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1402f2e
ERROR: Communication problem with keep, it probably crashed.
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1402f4d
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1402fa6
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1403011
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x140306d
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x14030b6
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1403111
QApplication::postEvent: Unexpected null receiver
QApplication::postEvent: Unexpected null receiver
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1403143
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1403172
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1403191
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x140319b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1403810
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x14051b0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x14051cf
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x140520b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x14052b2
kbuildsycoca running...

DCOP Cleaning up dead connections.

X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x14056f4
kdecore (KProcess): WARNING: _attachPty() 11

--get XML:
<?xml version='1.0' encoding='UTF-8' standalone='yes'?>
<!DOCTYPE network []>

<network>

  <dialinstalled>1</dialinstalled>
  <domain>8ka</domain>
  <gateway>194.85.80.1</gateway>
  <gatewaydev>eth0</gatewaydev>
  <hostmatch>0</hostmatch>
  <hostname>antalar</hostname>
  <smartdhcpcd>0</smartdhcpcd>
  <smbinstalled>1</smbinstalled>
  <smbuse>1</smbuse>

  <nameserver>194.85.83.73</nameserver>
  <nameserver>194.85.83.83</nameserver>

  <statichost>
    <ip>127.0.0.1</ip>
    <alias>localhost</alias>
  </statichost>
  <statichost>
    <ip>127.0.1.1</ip>
    <alias>antalar</alias>
  </statichost>

  <interface type='modem'>

    <dev>ppp0</dev>
    <enabled>0</enabled>
  </interface>

  <interface type='loopback'>

    <configuration>
      <address>127.0.0.1</address>
      <auto>1</auto>
      <bootproto>none</bootproto>
      <broadcast>127.255.255.255</broadcast>
      <file>lo</file>
      <netmask>255.0.0.0</netmask>
      <network>127.0.0.0</network>
    </configuration>
    <dev>lo</dev>
    
<enabled>1</enabled>
  </interface>

  <interface type='ethernet'>

    <configuration>
      <address>194.85.80.223</address>
      <auto>1</auto>
      <bootproto>none</bootproto>
      <broadcast>194.85.83.255</broadcast>
      <file>eth0</file>
      <gateway>194.85.80.1</gateway>
      <netmask>255.255.252.0</netmask>
      <network>194.85.80.0</network>
    </configuration>
    <dev>eth0</dev>
    <enabled>1</enabled>
    <hwaddr>00:02:B3:65:3D:25</hwaddr>
  </interface>

  <profiledb>
  </profiledb>

</network>

<!-- GST: end of request -->

XML -d list_ifaces: <?xml version='1.0' encoding='UTF-8' standalone='yes'?>
<!DOCTYPE network-ifaces []>

<network-ifaces>

  <interface>
    <addr>127.0.0.1</addr>
    <dev>lo</dev>
    <enabled>1</enabled>
    <mask>255.0.0.0</mask>
    <type>loopback</type>
  </interface>

  <interface>
    <addr>194.85.80.223</addr>
    <bcast>194.85.83.255</bcast>
    <dev>eth0</dev>
    <enabled>1</enabled>
    <hwaddr>00:02:B3:65:3D:25</hwaddr>
    <mask>255.255.252.0</mask>
    <type>ethernet</type>
  </interface>

</network-ifaces>

<!-- GST: end of request -->

X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1405729
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x22002ab
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x22002ab
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x22002ab
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1405768
profile updated

--set XML:
<?xml version="1.0" ?>
<!DOCTYPE network []>
<network>
 <gateway>194.85.80.1</gateway>
 <gatewaydev>eth0</gatewaydev>
 <hostname>antalar</hostname>
 <domain>8ka</domain>
 <nameserver>194.85.83.73</nameserver>
 <nameserver>194.85.83.83</nameserver>
 <statichost>
  <ip>127.0.0.1</ip>
  <alias>localhost</alias>
 </statichost>
 <statichost>
  <ip>127.0.1.1</ip>
  <alias>antalar</alias>
 </statichost>
 <interface type="loopback" >
  <configuration>
   <address>127.0.0.1</address>
   <broadcast>127.255.255.255</broadcast>
   <netmask>255.0.0.0</netmask>
   <network>127.0.0.0</network>
   <auto>1</auto>
   <bootproto>none</bootproto>
   <file>lo</file>
  </configuration>
  <dev>lo</dev>
  <enabled>1</enabled>
  <hwaddr></hwaddr>
 </interface>
 <interface type="ethernet" >
  <configuration>
   <address>194.85.80.223</address>
   <gateway>194.85.80.1</gateway>
   <broadcast>194.85.83.255</broadcast>
   <netmask>255.255.252.0</netmask>
   <network>194.85.80.0</network>
   <auto>1</auto>
   <bootproto>none</b
ootproto>
   <file>eth0</file>
  </configuration>
  <dev>eth0</dev>
  <enabled>1</enabled>
  <hwaddr>00:02:B3:65:3D:25</hwaddr>
 </interface>
 <profiledb>
  <profile>
   <name>dorm</name>
   <gateway>194.85.80.1</gateway>
   <gatewaydev>eth0</gatewaydev>
   <hostname>antalar</hostname>
   <domain>8ka</domain>
   <nameserver>194.85.83.73</nameserver>
   <nameserver>194.85.83.83</nameserver>
   <statichost>
    <ip>127.0.0.1</ip>
    <alias>localhost</alias>
   </statichost>
   <statichost>
    <ip>127.0.1.1</ip>
    <alias>antalar</alias>
   </statichost>
   <interface type="loopback" >
    <configuration>
     <address>127.0.0.1</address>
     <broadcast>127.255.255.255</broadcast>
     <netmask>255.0.0.0</netmask>
     <network>127.0.0.0</network>
     <auto>1</auto>
     <bootproto>none</bootproto>
     <file>lo</file>
    </configuration>
    <dev>lo</dev>
    <enabled>1</enabled>
    <hwaddr></hwaddr>
   </interface>
   <interface type="ethernet" >
    <configuration>
     <address>194.85.80.223</address>

     <gateway>194.85.80.1</gateway>
     <broadcast>194.85.83.255</broadcast>
     <netmask>255.255.252.0</netmask>
     <network>194.85.80.0</network>
     <auto>1</auto>
     <bootproto>none</bootproto>
     <file>eth0</file>
    </configuration>
    <dev>eth0</dev>
    <enabled>1</enabled>
    <hwaddr>00:02:B3:65:3D:25</hwaddr>
   </interface>
  </profile>
 </profiledb>
</network>
<!-- GST: end of request -->

X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x14057bf
XML -d list_ifaces: <?xml version='1.0' encoding='UTF-8' standalone='yes'?>
<!DOCTYPE network-ifaces []>

<network-ifaces>

  <interface>
    <addr>127.0.0.1</addr>
    <dev>lo</dev>
    <enabled>1</enabled>
    <mask>255.0.0.0</mask>
    <type>loopback</type>
  </interface>

  <interface>
    <addr>194.85.80.223</addr>
    <bcast>194.85.83.255</bcast>
    <dev>eth0</dev>
    <enabled>1</enabled>
    <hwaddr>00:02:B3:65:3D:25</hwaddr>
    <mask>255.255.252.0</mask>
    <type>ethernet</type>
  </interface>

</network-ifaces>

<!-- GST: end of request -->

X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x14057f4
--set XML:
<?xml version="1.0" ?>
<!DOCTYPE network []>
<network>
 <gateway>194.85.80.1</gateway>
 <gatewaydev>eth0</gatewaydev>
 <hostname>antalar</hostname>
 <domain>8ka</domain>
 <nameserver>194.85.83.73</nameserver>
 <nameserver>194.85.83.83</nameserver>
 <statichost>
  <ip>127.0.0.1</ip>
  <alias>localhost</alias>
 </statichost>
 <statichost>
  <ip>127.0.1.1</ip>
  <alias>antalar</alias>
 </statichost>
 <interface type="loopback" >
  <configuration>
   <address>127.0.0.1</address>
   <broadcast>127.255.255.255</broadcast>
   <netmask>255.0.0.0</netmask>
   <network>127.0.0.0</network>
   <auto>1</auto>
   <bootproto>none</bootproto>
   <file>lo</file>
  </configuration>
  <dev>lo</dev>
  <enabled>1</enabled>
  <hwaddr></hwaddr>
 </interface>
 <interface type="ethernet" >
  <configuration>
   <address>194.85.80.223</address>
   <gateway>194.85.80.1</gateway>
   <broadcast>194.85.83.255</broadcast>
   <netmask>255.255.252.0</netmask>
   <network>194.85.80.0</network>
   <auto>1</auto>
   <bootproto>none</b
ootproto>
   <file>eth0</file>
  </configuration>
  <dev>eth0</dev>
  <enabled>1</enabled>
  <hwaddr>00:02:B3:65:3D:25</hwaddr>
 </interface>
 <profiledb>
  <profile>
   <name>dorm</name>
   <gateway>194.85.80.1</gateway>
   <gatewaydev>eth0</gatewaydev>
   <hostname>antalar</hostname>
   <domain>8ka</domain>
   <nameserver>194.85.83.73</nameserver>
   <nameserver>194.85.83.83</nameserver>
   <statichost>
    <ip>127.0.0.1</ip>
    <alias>localhost</alias>
   </statichost>
   <statichost>
    <ip>127.0.1.1</ip>
    <alias>antalar</alias>
   </statichost>
   <interface type="loopback" >
    <configuration>
     <address>127.0.0.1</address>
     <broadcast>127.255.255.255</broadcast>
     <netmask>255.0.0.0</netmask>
     <network>127.0.0.0</network>
     <auto>1</auto>
     <bootproto>none</bootproto>
     <file>lo</file>
    </configuration>
    <dev>lo</dev>
    <enabled>1</enabled>
    <hwaddr></hwaddr>
   </interface>
   <interface type="ethernet" >
    <configuration>
     <address>194.85.80.223</address>

     <gateway>194.85.80.1</gateway>
     <broadcast>194.85.83.255</broadcast>
     <netmask>255.255.252.0</netmask>
     <network>194.85.80.0</network>
     <auto>1</auto>
     <bootproto>none</bootproto>
     <file>eth0</file>
    </configuration>
    <dev>eth0</dev>
    <enabled>1</enabled>
    <hwaddr>00:02:B3:65:3D:25</hwaddr>
   </interface>
  </profile>
 </profiledb>
</network>
<!-- GST: end of request -->

X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x140582d
XML -d list_ifaces: <?xml version='1.0' encoding='UTF-8' standalone='yes'?>
<!DOCTYPE network-ifaces []>

<network-ifaces>

  <interface>
    <addr>127.0.0.1</addr>
    <dev>lo</dev>
    <enabled>1</enabled>
    <mask>255.0.0.0</mask>
    <type>loopback</type>
  </interface>

  <interface>
    <addr>194.85.80.223</addr>
    <bcast>194.85.83.255</bcast>
    <dev>eth0</dev>
    <enabled>1</enabled>
    <hwaddr>00:02:B3:65:3D:25</hwaddr>
    <mask>255.255.252.0</mask>
    <type>ethernet</type>
  </interface>

</network-ifaces>

<!-- GST: end of request -->

X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1405862
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x2200007
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1405893
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x14058b0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x14058c2
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x14058de
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x14058f3
kdecore (KProcess): WARNING: _attachPty() 10
kwin: X_CopyArea(0x100385d): BadMatch (invalid parameter attributes)
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1405945
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1405960
kwin: X_CopyArea(0x1003866): BadMatch (invalid parameter attributes)
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1405987
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x140599e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1405a5d
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1405a87
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1405ae7
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1405afe
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1405b49
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1405c11
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0xa00028
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1405c53
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1405c8e
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1405cdc
kio (KMimeType): WARNING: KServiceType::offers : servicetype trash not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype trash not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype system not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype system not found
ASSERT: "m_pendingMimetypeInfos.count() == 1" in /build/buildd/kdelibs-3.5.8/./kio/kio/kfilemetainfo.cpp (975)
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1405d52
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KLauncher): ERROR: SlavePool: No communication with slave.
GPL Ghostscript SVN PRE-RELEASE 8.61: Failed to interpret TT instructions for glyph index 25 of font DejaVuSans-Bold. Continue ignoring instructions of the font.
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1405d80
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1405da9
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1405db4
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1405dbf
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1405dca
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1405dd5
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1405de0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1405deb
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1405df6
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1405e01
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1405e19
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1405e26
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1405e37
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1405e52
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1405e6c
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1405e95
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1405eae
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1405ec7
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1405ee0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1405ef9
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1405f17
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1405f31
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  62
  Minor opcode:  0
  Resource id:  0x1405f40

---

### Post by jdackle on 2007-12-20
Hey!

I know nothing about PAM nor mingw.

And most of the output of that .xsession-errors don't really mean much to me.

However... It seems you have a ppp0 device (modem dial-out connection, also can include dsl) referenced somewhere. You have no eth0 reference (ethernet, usually local network but also common for both cable and dsl modems), so that probably means you're using a ppp0 interface to connect to the network. But you got this relating to ppp0:

> <interface type='modem'>

<dev>ppp0</dev>
<enabled>0</enabled>
</interface>

The "enabled" tag above is set to "0" and "0" = "false".
So the above quote says the interface to your modem (ppp0) is NOT enabled.

Can you check out your configuration for it?

---

### Post by antalar on 2007-12-20
I'm sorry, but I forget to tell some important information. :(

I use eth0 device to connect to internet and I doesn't use modem. It mentioned in these strings:

...
<interface type="ethernet" >
<configuration>
<address>194.85.80.223</address>
<gateway>194.85.80.1</gateway>
<broadcast>194.85.83.255</broadcast>
<netmask>255.255.252.0</netmask>
<network>194.85.80.0</network>
<auto>1</auto>
<bootproto>none</b
ootproto>
<file>eth0</file>
</configuration>
<dev>eth0</dev>
<enabled>1</enabled>
<hwaddr>00:02:B3:65:3D:25</hwaddr>
</interface>
...

As i understand there is some problem connected with this XML file.

---

### Post by jdackle on 2007-12-20
Right... I did a search for eth0, not ethernet... My bad... :(

I can't really tell for sure but I suppose what you quoted shows your ehternet IS properly *configured*, which is not to say by itself it's a hardware problem... Much more is usually done to actualy connect...

But I myself can't help you with this, I just don't have enough knowledge. Sorry... :(


But maybe someone else can help you.

Good luck! :)


P.S.: if that XML is from the .xsession-errors file, I don't really think it's a file you need to edit or something, rather some kind of error log...? But I'm not sure...

Anyways... .xsession relates to your X graphical interface, NOT your Internet connection. I suppose it can however run a few tests and specially try and setup some remote-desktop capabilities in case you've set it up that way...

For those in the know (not me!) to better help you, you should try and post more information on your connection...
- It uses ethernet, alright, we know that now...
- What hardware (modem, wireless card, router, whatever...) are you using?
- Are you using any special software (or scripts, settings, ..) to make the connection or was it automatically done by Ubuntu (with my crappy modem, I have to do some tweakings... lol)?

---

### Post by antalar on 2007-12-21
Sorry, I've badly described my situation. :(
Everything was working fine until yesterday, when I installed some new software and added new scripts, that work with hotplug usbware (is there such word in English? :). 

I use network card installed in my laptop hp 6720s. Our campus network designed so, that I must set all network parameters (IP, gateway, MAC) manually. I added new strings in /etc/network/interfaces for this. 

Now ifconfig tells me, that everything configurated write, but I cannot ping my gateway. But, trouble is in my computer, because other computers works fine with this cable.

You said, that there are some tests for network. What did you mean? :)

---

### Post by antalar on 2007-12-21
antalar@antalar:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:B3:65:3D:25
          inet addr:194.85.80.223  Bcast:194.85.83.255  Mask:255.255.252.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Base address:0x4020 Memory:e4600000-e4620000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 &#1044;&#1080;&#1072;&#1087;&#1072;&#1079;&#1086;&#1085;:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:589 errors:0 dropped:0 overruns:0 frame:0
          TX packets:589 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:53899 (52.6 KB)  TX bytes:53899 (52.6 KB)

antalar@antalar:~$ ping 194.85.80.1
PING 194.85.80.1 (194.85.80.1) 56(84) bytes of data.
From 194.85.80.223 icmp_seq=1 Destination Host Unreachable
From 194.85.80.223 icmp_seq=2 Destination Host Unreachable
From 194.85.80.223 icmp_seq=3 Destination Host Unreachable

--- 194.85.80.1 ping statistics ---
4 packets transmitted, 0 received, +3 errors, 100% packet loss, time 3009ms
, pipe 3
antalar@antalar:~$

---

### Post by antalar on 2007-12-21
Uuughh, thanks. I've found the cause of this problem.

It seems, that some new software somehow changed /boot/grub/menu.lst and flag "pci=noacpi" was lost. I wrote it again and everything works fine now. :)

---

