---
title: "Amarok problems"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by mazmaris on 2011-03-04
after using ubuntu for a few weeks i tried installing amarok
it doesnt play songs it skips to the next one without playing it
i tried to run it from terminal to see what is the problem
can somebody help me figure this out
[PHP]mazmaris@mazmaris-desktop:~$ amarok
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `gtk-enable-event-sounds' of type `gboolean' from rc file value "((GString*) 0x9666b30)" of type `gboolean'
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `gtk-enable-input-feedback-sounds' of type `gboolean' from rc file value "((GString*) 0x9666ad0)" of type `gboolean'
Gtk-Message: (for origin information, set GTK_DEBUG): failed to retrieve property `gtk-button-images' of type `gboolean' from rc file value "((GString*) 0x9666b00)" of type `gboolean'
Object::connect: No such signal Podcasts::SqlPodcastProvider::playlistAdded( Playlists::PlaylistPtr )
Object::connect: No such signal Podcasts::SqlPodcastProvider::playlistRemoved( Playlists::PlaylistPtr )
Object::connect: No such signal Playlists::SqlUserPlaylistProvider::playlistAdded( Playlists::PlaylistPtr )
Object::connect: No such signal Playlists::SqlUserPlaylistProvider::playlistRemoved( Playlists::PlaylistPtr )
kmimetype filetype guessing failed for /home/mazmaris/.wine/drive_c/windows/system32/winoldap.mod 
amarok(4128)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
amarok(4128)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
amarok(4128)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
amarok(4128)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
Calling appendChild() on a null node does nothing.
amarok(4128)/kdecore (KConfigSkeleton) KCoreConfigSkeleton::writeConfig:
Object::connect: No such signal QSortFilterProxyModel::renameIndex( QModelIndex )
Object::connect: No such signal QSortFilterProxyModel::renameIndex( QModelIndex )
Object::connect: No such signal QSortFilterProxyModel::renameIndex( QModelIndex )
Object::connect: No such signal QSortFilterProxyModel::renameIndex( QModelIndex )
amarok(4128)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "Amarok Script Console"
amarok(4128)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "LyricWiki"
amarok(4128)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "Cool Streams"
amarok(4128)/kdecore (KPluginInfo) KPluginInfo::kcmServices: found  0  offers for  "Librivox.org"
QMetaObject::invokeMethod: No such method App::loadCommandLineOptionsForNewInstance()
amarok:  ********************************************************************************************** 
amarok:  ** AMAROK WAS STARTED IN NORMAL MODE. IF YOU WANT TO SEE DEBUGGING INFORMATION, PLEASE USE: ** 
amarok:  ** amarok --debug                                                                           ** 
amarok:  ********************************************************************************************** 
mazmaris@mazmaris-desktop:~$ QVariantMap DBusMenuExporterDBus::GetProperties(int, const QStringList&): Condition failed: action 
mazmaris@mazmaris-desktop:~$ params.c:OpenConfFile() - Unable to open configuration file "/home/mazmaris/.smb/smb.conf":
	No such file or directory
params.c:OpenConfFile() - Unable to open configuration file "/home/mazmaris/.smb/smb.conf.append":
	No such file or directory
QVariantMap DBusMenuExporterDBus::GetProperties(int, const QStringList&): Condition failed: action 
QVariantMap DBusMenuExporterDBus::GetProperties(int, const QStringList&): Condition failed: action 
QVariantMap DBusMenuExporterDBus::GetProperties(int, const QStringList&): Condition failed: action 
QVariantMap DBusMenuExporterDBus::GetProperties(int, const QStringList&): Condition failed: action 
QVariantMap DBusMenuExporterDBus::GetProperties(int, const QStringList&): Condition failed: action 
QVariantMap DBusMenuExporterDBus::GetProperties(int, const QStringList&): Condition failed: action 
xine_open for gapless playback failed!
QVariantMap DBusMenuExporterDBus::GetProperties(int, const QStringList&): Condition failed: action 
[/PHP]

---

### Post by Dutch70 on 2011-03-04
Have you moved your songs around? as in from one folder to another after you loaded them into Amarok. If so, you'll have to reload them.

Other than that, you may want to try Exaile.

---

### Post by mazmaris on 2011-03-04
nope all my music is in the music folder
exaile works flawlessly

---

### Post by Dutch70 on 2011-03-04
Glad to hear it & welcome to UF.

---

