---
title: "How can I install Vuze"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by Kedster on 2009-04-30
i went to install it they way it says to in the folder
```
ketterer@ketterer-laptop:~/Desktop/vuze$ ./azureus
Starting Azureus...
Java exec not found in PATH, starting auto-search...
ls: cannot access /usr/java/latest: No such file or directory
ls: cannot access /usr/java: No such file or directory
ls: cannot access /usr/lib/jvm/latest: No such file or directory
ls: cannot access /usr/lib/jvm: No such file or directory
Re-checking with GCJ (Sun Java recommended)..
Java exec not found in PATH, starting auto-search...
ls: cannot access /usr/java/latest /usr/java /usr/lib/jvm/latest /usr/lib/jvm: No such file or directory
OOPS, unable to locate java exec in  /usr/java/latest /usr/java /usr/lib/jvm/latest /usr/lib/jvm/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://java.sun.com
```
 
So how can i fix that, im pretty sure I have the latest Java installed (JRE 1.6 or 9). iv had vuze on here before i did a clean install to jaunty but Installed it from a deb

---

### Post by taurus on 2009-04-30
What's the output of this command from a terminal?

```
java -version
```

---

### Post by Duskao on 2009-04-30
use "add/remove" and search for java. Then install java. Do the same for azureus or vuze (they're the same just vuze is newer)

---

### Post by Kedster on 2009-04-30
Ok sorry i was mistaken i suppose i do not have java installed, i thought i had,

Is the Vuze/ azarus in add/remove the new one or is it the version that was black and buggy

---

### Post by Duskao on 2009-04-30
Not too sure if it is buggy or not in the add/remove, I haven't used asureus/vuze in a long time, for torrents I prefer the smaller lighter programs that work better. I'm completely happy with transmission but deluge is supposed to be good as well, I just found it a bit bloated. Guess it depends what your looking for.

---

### Post by Kedster on 2009-04-30
thanks guys, 
and i think the one thats in ad/remove is like 3 and the newest one is 4 and thay just added a btter ui and better searching

---

### Post by Duskao on 2009-04-30
Actually I just installed and you are completely correct, however, there is an automatic update that pops up and I have 4.2.0.2 now after upgrading :). Hope that helps man.

---

### Post by Kedster on 2009-04-30
so i installed java and then went to install from the one i downloaded manually 
and it worked and then wanted to have an update and then restarted and now is stuck on the splash screen
```
ketterer@ketterer-laptop:~/Desktop/vuze$ ./azureus
Starting Azureus...
Suitable java version found [java = 1.6.0_0]
Configuring environment...
Java exec found in PATH. Verifying...
GRE/XULRunner automatically found
Loading Azureus:
java -Xmx128m -cp "./Azureus2.jar:./swt.jar" -Djava.library.path="/home/ketterer/Desktop/vuze" -Dazureus.install.path="/home/ketterer/Desktop/vuze" -Dazureus.script="./azureus" -Dazureus.script.version=2 org.gudy.azureus2.ui.swt.Main 
file:/home/ketterer/Desktop/vuze/Azureus2.jar ; file:/home/ketterer/Desktop/vuze/swt.jar ; file:/home/ketterer/Desktop/vuze/
changeLocale: *Default Language* != English (Canada). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (Canada)' (en_CA), using 'English (default)'
Locale Initializing took 66ms
55226:    Core: 237ms for activity between 'Loading Plugin: azupdater' and 'Loading Plugin: azemp'
55277:    Core: 51ms for activity between 'Loading Plugin: azupnpav' and 'Loading Plugin: azrating'
55302:    Core: 25ms for activity between 'Loading Plugin: azrating' and 'Loading Plugin: azupdater'
55408:    Core: 106ms for activity between 'Loading Plugin: azplugins' and 'Loading Plugin: azupnpav'
55458:    Core: 50ms for activity between 'Initializing Global Torrent Manager' and 'Loading Plugin: Torrent Removal Rules'
55483:    Core: 25ms for activity between 'Loading Plugin: Share Hoster' and 'Loading Plugin: Plugin Update Checker'
55537:    Core: 28ms for activity between 'Loading Plugin: Plugin Update Checker' and 'Loading Plugin: UPnP'
55562:    Core: 25ms for activity between 'Loading Plugin: UPnP' and 'Loading Plugin: DHT'
55638:    Core: 51ms for activity between 'Loading Plugin: DHT Tracker' and 'Loading Plugin: Magnet URI Handler'
55682:    Core: 44ms for activity between 'Loading Plugin: Magnet URI Handler' and 'Loading Plugin: Core Update Checker'
55707:    Core: 25ms for activity between 'Loading Plugin: External Seed' and 'Loading Plugin: Local Tracker'
55732:    Core: 25ms for activity between 'Loading Plugin: Local Tracker' and 'Loading Plugin: Network Status'
56033:    Core: 301ms for activity between 'Loading Plugin: Buddy' and 'Initializing Plugin: Azureus Update Support'
56058:    Core: 25ms for activity between 'Initializing Plugin: Rating' and 'Initializing Plugin: Tracker Static Pages'
   Core: 155ms for Initializing Plugin: Tracker Static Pages
56239:    Core: 181ms for activity between 'Initializing Plugin: Tracker Static Pages' and 'Initializing Plugin: Start/Stop Rules'
56284:    Core: 45ms for activity between 'Initializing Plugin: Download Remove Rules' and 'Initializing Plugin: Share Hoster'
56337:    Core: 53ms for activity between 'Initializing Plugin: PluginUpdate' and 'Initializing Plugin: Universal Plug and Play (UPnP)'
56367:    Core: 30ms for activity between 'Initializing Plugin: Universal Plug and Play (UPnP)' and 'Initializing Plugin: Distributed DB'
56396:    Core: 29ms for activity between 'Initializing Plugin: Distributed DB' and 'Initializing Plugin: Distributed Tracker'
56444:    Core: 48ms for activity between 'Initializing Plugin: Distributed Tracker' and 'Initializing Plugin: Magnet URI Handler'
56469:    Core: 25ms for activity between 'Initializing Plugin: Magnet URI Handler' and 'Initializing Plugin: CoreUpdater'
56494:    Core: 25ms for activity between 'Initializing Plugin: CoreUpdater' and 'Initializing Plugin: CorePatcher'
56519:    Core: 25ms for activity between 'Initializing Plugin: External Seed' and 'Initializing Plugin: LAN Peer Finder'
Core Initializing took 1757ms
UIFunctions/ImageLoad took 22ms
new shell took 31ms
new shell setup took 131ms
skinlisteners init took 2ms
skin init took 339ms
MainMenu init took 215ms
createWindow init took 0ms
skin layout took 26ms
pre skin widgets init took 51ms
hooks init took 43ms
WARNING: already added UIUpdatable com.aelitis.azureus.ui.swt.views.skin.sidebar.SideBar@cb07ef
skin widgets (1/2) init took 242ms
skin widgets init took 192ms
pre SWTInstance init took 2ms
Init Core Columns took 150ms
SWTInstance init took 205ms
shell.layout took 188ms
---------READY AT 1241142911490
shell.open took 387ms
processStartupDMS took 7ms
vuzeactivities init took 2ms

(SWT:27603): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width 250 and height -1

(SWT:27603): Gtk-CRITICAL **: gtk_container_foreach: assertion `GTK_IS_CONTAINER (container)' failed
^[[A^[[A^[[BDEBUG::Thu Apr 30 20:55:39 CDT 2009  SWTUpdate: ignoring zip entry 'about.html'
DEBUG::Thu Apr 30 20:55:39 CDT 2009  SWTUpdate: ignoring zip entry 'about_files/about_cairo.html'
DEBUG::Thu Apr 30 20:55:39 CDT 2009  SWTUpdate: ignoring zip entry 'about_files/IJG_README'
DEBUG::Thu Apr 30 20:55:39 CDT 2009  SWTUpdate: ignoring zip entry 'about_files/lgpl-v21.txt'
DEBUG::Thu Apr 30 20:55:39 CDT 2009  SWTUpdate: ignoring zip entry 'about_files/mpl-v11.txt'
DEBUG::Thu Apr 30 20:55:39 CDT 2009  SWTUpdate: ignoring zip entry 'about_files/pixman-licenses.txt'
56680:    Core: 60113ms for activity between 'Initializing Plugin: Friends' and 'Unloading Torrents'
Exit from Azureus complete
Applying (possible) patches before restarting..
Restarting Azureus..
Starting Azureus...
Suitable java version found [java = 1.6.0_0]
Configuring environment...
Java exec found in PATH. Verifying...
GRE/XULRunner automatically found
Loading Azureus:
java -Xmx128m -cp "./Azureus2.jar:./swt.jar" -Djava.library.path="/home/ketterer/Desktop/vuze" -Dazureus.install.path="/home/ketterer/Desktop/vuze" -Dazureus.script="./azureus" -Dazureus.script.version=2 org.gudy.azureus2.ui.swt.Main 
file:/home/ketterer/Desktop/vuze/Azureus2.jar ; file:/home/ketterer/Desktop/vuze/swt.jar ; file:/home/ketterer/Desktop/vuze/
changeLocale: *Default Language* != English (Canada). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (Canada)' (en_CA), using 'English (default)'
Locale Initializing took 101ms
06428:    Core: 125ms for activity between 'Loading Plugin: azupdater' and 'Loading Plugin: azemp'
06453:    Core: 25ms for activity between 'Loading Plugin: azupnpav' and 'Loading Plugin: azrating'
06529:    Core: 76ms for activity between 'Loading Plugin: azrating' and 'Loading Plugin: azupdater'
06694:    Core: 165ms for activity between 'Loading Plugin: azplugins' and 'Loading Plugin: azupnpav'
06769:    Core: 75ms for activity between 'Loading Plugin: Torrent Removal Rules' and 'Loading Plugin: Share Hoster'
06794:    Core: 25ms for activity between 'Loading Plugin: Plugin Update Checker' and 'Loading Plugin: UPnP'
06820:    Core: 26ms for activity between 'Loading Plugin: UPnP' and 'Loading Plugin: DHT'
06870:    Core: 25ms for activity between 'Loading Plugin: DHT' and 'Loading Plugin: DHT Tracker'
06895:    Core: 25ms for activity between 'Loading Plugin: DHT Tracker' and 'Loading Plugin: Magnet URI Handler'
06972:    Core: 52ms for activity between 'Loading Plugin: Core Patch Checker' and 'Loading Plugin: Platform Checker'
07022:    Core: 50ms for activity between 'Loading Plugin: Local Tracker' and 'Loading Plugin: Network Status'
07180:    Core: 158ms for activity between 'Loading Plugin: Buddy' and 'Initializing Global Torrent Manager'
07556:    Core: 376ms for activity between 'Initializing Global Torrent Manager' and 'Initializing Plugin: Azureus Update Support'
07584:    Core: 28ms for activity between 'Initializing Plugin: UPnP Media Server' and 'Initializing Plugin: Rating'
   Core: 131ms for Initializing Plugin: Tracker Static Pages
07715:    Core: 131ms for activity between 'Initializing Plugin: Tracker Static Pages' and 'Initializing Plugin: Start/Stop Rules'
07742:    Core: 27ms for activity between 'Initializing Plugin: Start/Stop Rules' and 'Initializing Plugin: Download Remove Rules'
07792:    Core: 25ms for activity between 'Initializing Plugin: Download Remove Rules' and 'Initializing Plugin: Share Hoster'
07843:    Core: 51ms for activity between 'Initializing Plugin: PluginUpdate' and 'Initializing Plugin: Universal Plug and Play (UPnP)'
07894:    Core: 51ms for activity between 'Initializing Plugin: Universal Plug and Play (UPnP)' and 'Initializing Plugin: Distributed DB'
07894:    Core: 51ms for activity between 'Initializing Plugin: Universal Plug and Play (UPnP)' and 'Initializing Plugin: Distributed Tracker'
07945:    Core: 51ms for activity between 'Initializing Plugin: Magnet URI Handler' and 'Initializing Plugin: CoreUpdater'
Core Initializing took 1872ms


```

---

### Post by Duskao on 2009-04-30
did you download the tar.bz2 from vuze.com?
If so then follow these
[http://ubuntuforums.org/archive/index.php/t-1024583.html](http://ubuntuforums.org/archive/index.php/t-1024583.html)

BTW, vuze is really good in linux!!!! I'm amazed!!!! It is fully functional and it works really well!!!!! It bit the big one in windows, was so slow and such a nasty memory hog, and with the memory leaks in windows it sucked. But without any leaks and a lower memory usage it works well.

---

