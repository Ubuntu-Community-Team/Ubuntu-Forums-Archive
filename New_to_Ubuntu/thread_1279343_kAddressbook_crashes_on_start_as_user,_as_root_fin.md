---
title: "kAddressbook crashes on start as user, as root fine"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by poekie on 2009-09-30
My kAddressbook, either started from Kontact or standalone, crashes on startup. However, if I start it as root, there's nothing wrong and it functions properly. Does anybody have any idea what's the problem?

Kubuntu 9.04, everything up to date from jaunty repos. Kernel 2.6.28-13-generic, KDE 4.2.4. kAddressbook 4.2.4-0ubuntu1~jaunty2

backtrace:
```
Application: Kontact (kontact), signal SIGSEGV

Thread 1 (Thread 0xb47b8700 (LWP 2537)):
[KCrash Handler]
#6  KIconLoader::loadIcon (this=0x836cc30, _name=@0x2f95990c, group=KIconLoader::Small, size=0, state=0, overlays=@0xbff79d04, path_store=0x0, canReturnNull=false)
    at /usr/include/qt4/QtCore/qstring.h:711
#7  0xb6c5d5ff in SmallIcon (name=@0x2f95990c, force_size=0, state=0, overlays=@0xbff79d04) at /build/buildd/kde4libs-4.2.4/kdeui/icons/kiconloader.cpp:1633
#8  0xb7160920 in KIMProxy::presenceIcon (this=0x9990f70, uid=@0xbff79d9c) at /build/buildd/kde4libs-4.2.4/interfaces/kimproxy/library/kimproxy.cpp:369
#9  0xac0e2c26 in ContactListViewItem::refresh (this=0x9aeb330) at /build/buildd/kdepim-4.2.4/kaddressbook/views/contactlistview.cpp:227
#10 0xac0e36fb in KAddressBookTableView::updatePresence (this=0x9a61e08, uid=@0x997e114) at /build/buildd/kdepim-4.2.4/kaddressbook/views/kaddressbooktableview.cpp:355
#11 0xac0e4952 in KAddressBookTableView::qt_metacall (this=0x9a61e08, _c=QMetaObject::InvokeMetaMethod, _id=4, _a=0xbff79eec)
    at /build/buildd/kdepim-4.2.4/obj-i486-linux-gnu/kaddressbook/views/kaddressbooktableview.moc:78
#12 0xb5bb1ca8 in QMetaObject::activate (sender=0x9990f70, from_signal_index=4, to_signal_index=4, argv=0xbff79eec) at kernel/qobject.cpp:3069
#13 0xb5bb2932 in QMetaObject::activate (sender=0x9990f70, m=0xb7167d60, local_signal_index=0, argv=0xbff79eec) at kernel/qobject.cpp:3143
#14 0xb715b593 in KIMProxy::sigContactPresenceChanged (this=0x9990f70, _t1=@0x997e114) at /build/buildd/kde4libs-4.2.4/obj-i486-linux-gnu/interfaces/kimproxy/library/kimproxy.moc:167
#15 0xb715e885 in KIMProxy::pollApp (this=0x9990f70, appId=@0x97f79ac) at /build/buildd/kde4libs-4.2.4/interfaces/kimproxy/library/kimproxy.cpp:600
#16 0xb715ef06 in KIMProxy::initialize (this=0x9990f70) at /build/buildd/kde4libs-4.2.4/interfaces/kimproxy/library/kimproxy.cpp:241
#17 0xb18255ab in KABCore::setContactSelected (this=0x983e0d0, uid=@0xbff7a468) at /build/buildd/kdepim-4.2.4/kaddressbook/kabcore.cpp:402
#18 0xb182c8e2 in KABCore::qt_metacall (this=0x983e0d0, _c=QMetaObject::InvokeMetaMethod, _id=0, _a=0xbff7a30c) at /build/buildd/kdepim-4.2.4/obj-i486-linux-gnu/kaddressbook/kabcore.moc:182
#19 0xb5bb1ca8 in QMetaObject::activate (sender=0x998e6b8, from_signal_index=27, to_signal_index=27, argv=0xbff7a30c) at kernel/qobject.cpp:3069
#20 0xb5bb2932 in QMetaObject::activate (sender=0x998e6b8, m=0xb1894640, local_signal_index=0, argv=0xbff7a30c) at kernel/qobject.cpp:3143
#21 0xb1851c43 in ViewManager::selected (this=0x998e6b8, _t1=@0xbff7a468) at /build/buildd/kdepim-4.2.4/obj-i486-linux-gnu/kaddressbook/viewmanager.moc:136
#22 0xb1857bee in ViewManager::qt_metacall (this=0x998e6b8, _c=QMetaObject::InvokeMetaMethod, _id=0, _a=0xbff7a41c) at /build/buildd/kdepim-4.2.4/obj-i486-linux-gnu/kaddressbook/viewmanager.moc:102
#23 0xb5bb1ca8 in QMetaObject::activate (sender=0x9a61e08, from_signal_index=28, to_signal_index=28, argv=0xbff7a41c) at kernel/qobject.cpp:3069
#24 0xb5bb2932 in QMetaObject::activate (sender=0x9a61e08, m=0xb18930a4, local_signal_index=1, argv=0xbff7a41c) at kernel/qobject.cpp:3143
#25 0xb182ea53 in KAddressBookView::selected (this=0x9a61e08, _t1=@0xbff7a468) at /build/buildd/kdepim-4.2.4/obj-i486-linux-gnu/kaddressbook/kaddressbookview.moc:125
#26 0xac0e3bd3 in KAddressBookTableView::addresseeSelected (this=0x9a61e08) at /build/buildd/kdepim-4.2.4/kaddressbook/views/kaddressbooktableview.cpp:318
#27 0xac0e4993 in KAddressBookTableView::qt_metacall (this=0x9a61e08, _c=QMetaObject::InvokeMetaMethod, _id=1, _a=0xbff7a518)
    at /build/buildd/kdepim-4.2.4/obj-i486-linux-gnu/kaddressbook/views/kaddressbooktableview.moc:75
#28 0xb5bb1ca8 in QMetaObject::activate (sender=0x9a6b348, from_signal_index=50, to_signal_index=50, argv=0x0) at kernel/qobject.cpp:3069
#29 0xb5bb2932 in QMetaObject::activate (sender=0x9a6b348, m=0xb7602748, local_signal_index=0, argv=0x0) at kernel/qobject.cpp:3143
#30 0xb757c3d7 in Q3ListView::selectionChanged (this=0x9a6b348) at .moc/release-shared/moc_q3listview.cpp:267
#31 0xb74013fe in Q3ListView::setSelected (this=0x9a6b348, item=0x9a83740, selected=true) at itemviews/q3listview.cpp:5193
#32 0xac0e325a in KAddressBookTableView::setFirstSelected (this=0x9a61e08, selected=12) at /build/buildd/kdepim-4.2.4/kaddressbook/views/kaddressbooktableview.cpp:300
#33 0xb182f5d1 in KAddressBookView::updateView (this=0x9a61e08) at /build/buildd/kdepim-4.2.4/kaddressbook/kaddressbookview.cpp:195
#34 0xb182fb1b in KAddressBookView::qt_metacall (this=0x9a61e08, _c=QMetaObject::InvokeMetaMethod, _id=15, _a=0xbff7a6e8)
    at /build/buildd/kdepim-4.2.4/obj-i486-linux-gnu/kaddressbook/kaddressbookview.moc:107
#35 0xac0e490a in KAddressBookTableView::qt_metacall (this=0x9a61e08, _c=QMetaObject::InvokeMetaMethod, _id=42, _a=0xbff7a6e8)
    at /build/buildd/kdepim-4.2.4/obj-i486-linux-gnu/kaddressbook/views/kaddressbooktableview.moc:69
#36 0xb5bb1ca8 in QMetaObject::activate (sender=0x98051e8, from_signal_index=4, to_signal_index=4, argv=0x0) at kernel/qobject.cpp:3069
#37 0xb5bb2932 in QMetaObject::activate (sender=0x98051e8, m=0xb189549c, local_signal_index=0, argv=0x0) at kernel/qobject.cpp:3143
#38 0xb1866fc7 in KAB::SearchManager::contactsUpdated (this=0x98051e8) at /build/buildd/kdepim-4.2.4/obj-i486-linux-gnu/kaddressbook/searchmanager.moc:82
#39 0xb1867a0a in KAB::SearchManager::search (this=0x98051e8, pattern=@0xbff7a968, fields=@0xbff7a824, type=KAB::SearchManager::Contains)
    at /build/buildd/kdepim-4.2.4/kaddressbook/searchmanager.cpp:261
#40 0xb1821e0b in KABCore::incrementalTextSearch (this=0x983e0d0, text=@0xbff7a968) at /build/buildd/kdepim-4.2.4/kaddressbook/kabcore.cpp:603
#41 0xb182c77e in KABCore::qt_metacall (this=0x983e0d0, _c=QMetaObject::InvokeMetaMethod, _id=18, _a=0xbff7a93c) at /build/buildd/kdepim-4.2.4/obj-i486-linux-gnu/kaddressbook/kabcore.moc:200
#42 0xb5bb1ca8 in QMetaObject::activate (sender=0x98bdb60, from_signal_index=27, to_signal_index=27, argv=0xbff7a93c) at kernel/qobject.cpp:3069
#43 0xb5bb2932 in QMetaObject::activate (sender=0x98bdb60, m=0xb1892c60, local_signal_index=0, argv=0xbff7a93c) at kernel/qobject.cpp:3143
#44 0xb181ac03 in IncSearchWidget::doSearch (this=0x98bdb60, _t1=@0xbff7a968) at /build/buildd/kdepim-4.2.4/obj-i486-linux-gnu/kaddressbook/incsearchwidget.moc:93
#45 0xb181aeae in IncSearchWidget::timeout (this=0x98bdb60) at /build/buildd/kdepim-4.2.4/kaddressbook/incsearchwidget.cpp:100
#46 0xb181af58 in IncSearchWidget::qt_metacall (this=0x98bdb60, _c=QMetaObject::InvokeMetaMethod, _id=5, _a=0xbff7aa18)
    at /build/buildd/kdepim-4.2.4/obj-i486-linux-gnu/kaddressbook/incsearchwidget.moc:81
#47 0xb5bb1ca8 in QMetaObject::activate (sender=0x97edc98, from_signal_index=4, to_signal_index=4, argv=0x0) at kernel/qobject.cpp:3069
#48 0xb5bb2932 in QMetaObject::activate (sender=0x97edc98, m=0xb5c8e904, local_signal_index=0, argv=0x0) at kernel/qobject.cpp:3143
#49 0xb5bed717 in QTimer::timeout (this=0x97edc98) at .moc/release-shared/moc_qtimer.cpp:128
#50 0xb5bb76fe in QTimer::timerEvent (this=0x97edc98, e=0xbff7ae9c) at kernel/qtimer.cpp:261
#51 0xb5bac15f in QObject::event (this=0x97edc98, e=0xbff7ae9c) at kernel/qobject.cpp:1082
#52 0xb606ae9c in QApplicationPrivate::notify_helper (this=0x8365f08, receiver=0x97edc98, e=0xbff7ae9c) at kernel/qapplication.cpp:4084
#53 0xb607319e in QApplication::notify (this=0xbff7b148, receiver=0x97edc98, e=0xbff7ae9c) at kernel/qapplication.cpp:3631
#54 0xb6c8ee0d in KApplication::notify (this=0xbff7b148, receiver=0x97edc98, event=0xbff7ae9c) at /build/buildd/kde4libs-4.2.4/kdeui/kernel/kapplication.cpp:307
#55 0xb5b9ba3b in QCoreApplication::notifyInternal (this=0xbff7b148, receiver=0x97edc98, event=0xbff7ae9c) at kernel/qcoreapplication.cpp:602
#56 0xb5bcad71 in QTimerInfoList::activateTimers (this=0x836863c) at ../../include/QtCore/../../src/corelib/kernel/qcoreapplication.h:213
#57 0xb5bc74e0 in timerSourceDispatch (source=0x8368608) at kernel/qeventdispatcher_glib.cpp:164
#58 0xb4c6eb88 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#59 0xb4c720eb in ?? () from /usr/lib/libglib-2.0.so.0
#60 0xb4c72268 in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
#61 0xb5bc7438 in QEventDispatcherGlib::processEvents (this=0x833a238, flags={i = -1074286568}) at kernel/qeventdispatcher_glib.cpp:323
#62 0xb610c365 in QGuiEventDispatcherGlib::processEvents (this=0x833a238, flags={i = -1074286520}) at kernel/qguieventdispatcher_glib.cpp:202
#63 0xb5b9a06a in QEventLoop::processEvents (this=0xbff7b0c0, flags={i = -1074286456}) at kernel/qeventloop.cpp:149
#64 0xb5b9a4aa in QEventLoop::exec (this=0xbff7b0c0, flags={i = -1074286392}) at kernel/qeventloop.cpp:200
#65 0xb5b9c959 in QCoreApplication::exec () at kernel/qcoreapplication.cpp:880
#66 0xb606ad17 in QApplication::exec () at kernel/qapplication.cpp:3553
#67 0x0804c072 in main (argc=1, argv=0xbff7b444) at /build/buildd/kdepim-4.2.4/kontact/src/main.cpp:218


```

---

### Post by pawhtiobo on 2009-09-30
Hi :)
 
This is just a wild guess...maybe you need to give permissions in the kAddressbook folder, so your user can read/write in to that... Have tried to launch kAddressbook from the command line with the sudo argument...?
 
see ya...

---

### Post by poekie on 2009-09-30
Well, the addressbook can be opened by text editors just fine, it's in my home directory and owned by my user. 
This problem arose when updating to jaunty and I haven't found a solution in two months, so any help is welcome.

---

