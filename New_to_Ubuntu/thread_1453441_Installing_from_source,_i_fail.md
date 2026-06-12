---
title: "Installing from source, i fail"
date: 2010-04-13
forum: New to Ubuntu
---

### Post by Falc7 on 2010-04-13
I am trying to install fancy tasks from kde-look.org.
I downloaded the source code
[http://kde-look.org/content/show.php/Fancy+Tasks?content=99737](http://kde-look.org/content/show.php/Fancy+Tasks?content=99737)

But i get stuck when following the instructions in the readme
```
jamie@jamie-kubuntu:~/Desktop/fancytasks-1.0.92/build$ sudo cmake ../ -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix`
CMake Error at /usr/share/cmake-2.8/Modules/FindKDE4.cmake:98 (MESSAGE):
  ERROR: cmake/modules/FindKDE4Internal.cmake not found in
  /home/jamie/.kde/share/apps;/usr/share/kde4/apps
Call Stack (most recent call first):
  CMakeLists.txt:1 (find_package)


CMake Warning (dev) in CMakeLists.txt:
  No cmake_minimum_required command is present.  A line of code such as

    cmake_minimum_required(VERSION 2.8)

  should be added at the top of the file.  The version specified may be lower
  if you wish to support older CMake versions for this project.  For more
  information run "cmake --help-policy CMP0000".
This warning is for project developers.  Use -Wno-dev to suppress it.

-- Configuring incomplete, errors occurred!

```

Ideally i would like to make a deb file from this, but if it straight installs thats is ok too

I also tried following this guide:
[http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html](http://www.ubuntugeek.com/how-to-install-source-files-in-ubuntu.html)
But still no luck

---

### Post by Sub101 on 2010-04-13
There is a deb file available on that page:

[http://www.mediafire.com/?sharekey=369e0576213df60175a4fc82078ae6c8e04e75f6e8ebb871](http://www.mediafire.com/?sharekey=369e0576213df60175a4fc82078ae6c8e04e75f6e8ebb871)

Or does that not work for you?

---

### Post by Falc7 on 2010-04-13
The deb there is for a much older version, and not designed for kde4.4 (which i am using)

---

### Post by kellemes on 2010-04-13
Install "kdelibs5-dev" and see if that works..

---

### Post by Falc7 on 2010-04-13
Got further than before, but i think something went wrong

```
jamie@jamie-kubuntu:~/Desktop/fancytasks-1.0.92$ cd /home/jamie/Desktop/fancytasks-1.0.92
jamie@jamie-kubuntu:~/Desktop/fancytasks-1.0.92$ cd /home/jamie/Desktop/fancytasks-1.0.92/build
jamie@jamie-kubuntu:~/Desktop/fancytasks-1.0.92/build$ sudo cmake ../ -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix`
-- Found Qt-Version 4.6.2 (using /usr/bin/qmake)
-- Found X11: /usr/lib/libX11.so
-- Phonon Version: 4.3.1
-- Found KDE 4.4 include dir: /usr/include
-- Found KDE 4.4 library dir: /usr/lib
-- Found the KDE4 kconfig_compiler preprocessor: /usr/bin/kconfig_compiler
-- Found automoc4: /usr/bin/automoc4
-- Configuring done
-- Generating done
-- Build files have been written to: /home/jamie/Desktop/fancytasks-1.0.92/build
jamie@jamie-kubuntu:~/Desktop/fancytasks-1.0.92/build$ sudo make
[  0%] Built target plasma_applet_fancytasks_automoc
[  2%] Building CXX object applet/CMakeFiles/plasma_applet_fancytasks.dir/plasma_applet_fancytasks_automoc.o
In file included from /home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksMenu.h:24,                                                                         
                 from /home/jamie/Desktop/fancytasks-1.0.92/build/applet/moc_FancyTasksMenu.cpp:10,
                 from /home/jamie/Desktop/fancytasks-1.0.92/build/applet/plasma_applet_fancytasks_automoc.cpp:4:
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksApplet.h:39:30: error: taskmanager/task.h: No such file or directory
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksApplet.h:40:34: error: taskmanager/taskitem.h: No such file or directory
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksApplet.h:41:37: error: taskmanager/taskactions.h: No such file or directory
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksApplet.h:42:37: error: taskmanager/taskmanager.h: No such file or directory
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksApplet.h:43:38: error: taskmanager/groupmanager.h: No such file or directory
In file included from /home/jamie/Desktop/fancytasks-1.0.92/build/applet/moc_FancyTasksTask.cpp:10,
                 from /home/jamie/Desktop/fancytasks-1.0.92/build/applet/plasma_applet_fancytasks_automoc.cpp:6:
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksTask.h:36:50: error: taskmanager/abstractgroupingstrategy.h: No such file or directory
In file included from /home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksMenu.h:24,
                 from /home/jamie/Desktop/fancytasks-1.0.92/build/applet/moc_FancyTasksMenu.cpp:10,
                 from /home/jamie/Desktop/fancytasks-1.0.92/build/applet/plasma_applet_fancytasks_automoc.cpp:4:
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksApplet.h:50: error: ‘TaskManager’ has not been declared
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksApplet.h:51: error: ‘TaskManager’ has not been declared
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksApplet.h:52: error: ‘TaskManager’ has not been declared
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksApplet.h:53: error: ‘TaskManager’ has not been declared
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksApplet.h:54: error: ‘TaskManager’ has not been declared
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksApplet.h:55: error: ‘TaskManager’ has not been declared
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksApplet.h:56: error: ‘TaskManager’ has not been declared
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksApplet.h:149: error: expected ‘;’ before ‘(’ token
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksApplet.h:151: error: ‘TaskManager’ has not been declared
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksApplet.h:151: error: ISO C++ forbids declaration of ‘GroupManager’ with no type
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksApplet.h:151: error: expected ‘;’ before ‘*’ token
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksApplet.h:176: error: ‘AbstractGroupableItem’ has not been declared
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksApplet.h:177: error: ‘AbstractGroupableItem’ has not been declared
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksApplet.h:178: error: ‘AbstractGroupableItem’ has not been declared
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksApplet.h:213: error: ISO C++ forbids declaration of ‘GroupManager’ with no type
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksApplet.h:213: error: expected ‘;’ before ‘*’ token
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksApplet.h:220: error: ‘AbstractGroupableItem’ was not declared in this scope
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksApplet.h:220: error: template argument 1 is invalid
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksApplet.h:221: error: ‘AbstractGroupableItem’ was not declared in this scope
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksApplet.h:221: error: template argument 1 is invalid
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksApplet.h:230: error: ‘TaskManager’ has not been declared
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksApplet.h:230: error: ISO C++ forbids declaration of ‘TaskGroupingStrategy’ with no type
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksApplet.h:230: error: expected ‘;’ before ‘m_groupingStrategy’
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksApplet.h:231: error: ‘TaskManager’ has not been declared
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksApplet.h:231: error: ISO C++ forbids declaration of ‘TaskSortingStrategy’ with no type
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksApplet.h:231: error: expected ‘;’ before ‘m_sortingStrategy’
In file included from /home/jamie/Desktop/fancytasks-1.0.92/build/applet/moc_FancyTasksTask.cpp:10,
                 from /home/jamie/Desktop/fancytasks-1.0.92/build/applet/plasma_applet_fancytasks_automoc.cpp:6:
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksTask.h:40: error: ‘TaskManager’ has not been declared
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksTask.h:41: error: ‘TaskManager’ has not been declared
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksTask.h:42: error: ‘TaskManager’ has not been declared
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksTask.h:43: error: ‘TaskManager’ has not been declared
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksTask.h:44: error: ‘TaskManager’ has not been declared
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksTask.h:45: error: ‘TaskManager’ has not been declared
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksTask.h:46: error: ‘TaskManager’ has not been declared
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksTask.h:64: error: ‘TaskManager’ has not been declared
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksTask.h:64: error: expected ‘)’ before ‘*’ token
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksTask.h:66: error: ‘TaskManager’ has not been declared
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksTask.h:66: error: expected ‘,’ or ‘...’ before ‘items’
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksTask.h:68: error: ISO C++ forbids declaration of ‘AbstractGroupableItem’ with no type
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksTask.h:68: error: expected ‘;’ before ‘*’ token
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksTask.h:69: error: ISO C++ forbids declaration of ‘TaskItem’ with no type
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksTask.h:69: error: expected ‘;’ before ‘*’ token
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksTask.h:70: error: ISO C++ forbids declaration of ‘TaskGroup’ with no type
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksTask.h:70: error: expected ‘;’ before ‘*’ token
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksTask.h:81: error: ‘TaskManager’ has not been declared
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksTask.h:81: error: expected ‘,’ or ‘...’ before ‘*’ token
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksTask.h:89: error: ‘::TaskManager’ has not been declared
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksTask.h:89: error: expected ‘,’ or ‘...’ before ‘changes’
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksTask.h:90: error: ‘AbstractGroupableItem’ has not been declared
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksTask.h:91: error: ‘AbstractGroupableItem’ has not been declared
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksTask.h:94: error: ‘TaskManager’ was not declared in this scope
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksTask.h:94: error: template argument 1 is invalid
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksTask.h:95: error: ‘TaskManager’ was not declared in this scope
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksTask.h:95: error: template argument 1 is invalid
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksTask.h:96: error: ‘TaskManager’ was not declared in this scope
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksTask.h:96: error: template argument 1 is invalid
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksTask.h:97: error: ‘TaskManager’ has not been declared
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksTask.h:97: error: ISO C++ forbids declaration of ‘GroupManager’ with no type
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksTask.h:97: error: expected ‘;’ before ‘*’ token
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksTask.h:103: error: ‘TaskManager’ has not been declared
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/../../applet/FancyTasksTask.h:103: error: expected ‘,’ or ‘...’ before ‘*’ token
In file included from /home/jamie/Desktop/fancytasks-1.0.92/build/applet/plasma_applet_fancytasks_automoc.cpp:6:
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/moc_FancyTasksTask.cpp: In member function ‘virtual int FancyTasks::Task::qt_metacall(QMetaObject::Call, int, void**)’:
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/moc_FancyTasksTask.cpp:99: error: expected type-specifier before ‘TaskManager’
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/moc_FancyTasksTask.cpp:99: error: expected ‘>’ before ‘TaskManager’
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/moc_FancyTasksTask.cpp:99: error: expected ‘(’ before ‘TaskManager’
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/moc_FancyTasksTask.cpp:99: error: ‘TaskManager’ has not been declared
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/moc_FancyTasksTask.cpp:99: error: expected primary-expression before ‘)’ token
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/moc_FancyTasksTask.cpp:102: error: expected type-specifier before ‘TaskManager’
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/moc_FancyTasksTask.cpp:102: error: expected ‘>’ before ‘TaskManager’
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/moc_FancyTasksTask.cpp:102: error: expected ‘(’ before ‘TaskManager’
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/moc_FancyTasksTask.cpp:102: error: ‘TaskManager’ has not been declared
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/moc_FancyTasksTask.cpp:102: error: expected primary-expression before ‘)’ token
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/moc_FancyTasksTask.cpp:110: error: expected type-specifier before ‘::’ token
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/moc_FancyTasksTask.cpp:110: error: expected ‘>’ before ‘::’ token
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/moc_FancyTasksTask.cpp:110: error: expected ‘(’ before ‘::’ token
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/moc_FancyTasksTask.cpp:110: error: ‘::TaskManager’ has not been declared
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/moc_FancyTasksTask.cpp:110: error: expected primary-expression before ‘)’ token
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/moc_FancyTasksTask.cpp:111: error: expected type-specifier before ‘AbstractGroupableItem’
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/moc_FancyTasksTask.cpp:111: error: expected ‘>’ before ‘AbstractGroupableItem’
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/moc_FancyTasksTask.cpp:111: error: expected ‘(’ before ‘AbstractGroupableItem’
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/moc_FancyTasksTask.cpp:111: error: ‘AbstractGroupableItem’ was not declared in this scope
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/moc_FancyTasksTask.cpp:111: error: expected primary-expression before ‘)’ token
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/moc_FancyTasksTask.cpp:112: error: expected type-specifier before ‘AbstractGroupableItem’
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/moc_FancyTasksTask.cpp:112: error: expected ‘>’ before ‘AbstractGroupableItem’
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/moc_FancyTasksTask.cpp:112: error: expected ‘(’ before ‘AbstractGroupableItem’
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/moc_FancyTasksTask.cpp:112: error: expected primary-expression before ‘)’ token
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/moc_FancyTasksTask.cpp: At global scope:
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/moc_FancyTasksTask.cpp:128: error: variable or field ‘publishGeometry’ declared void
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/moc_FancyTasksTask.cpp:128: error: ‘TaskManager’ has not been declared
/home/jamie/Desktop/fancytasks-1.0.92/build/applet/moc_FancyTasksTask.cpp:128: error: ‘_t1’ was not declared in this scope
make[2]: *** [applet/CMakeFiles/plasma_applet_fancytasks.dir/plasma_applet_fancytasks_automoc.o] Error 1
make[1]: *** [applet/CMakeFiles/plasma_applet_fancytasks.dir/all] Error 2
make: *** [all] Error 2
jamie@jamie-kubuntu:~/Desktop/fancytasks-1.0.92/build$ 

```

---

### Post by nerdy_kid on 2010-04-13
make sure that kdelibs5-dev and kdebase-workspace-dev are installed.

---

### Post by Falc7 on 2010-04-13
```
jamie@jamie-kubuntu:~/Desktop/fancytasks-1.0.92/build$ sudo cmake ../ -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix`
-- Found Qt-Version 4.6.2 (using /usr/bin/qmake)
-- Found X11: /usr/lib/libX11.so
-- Phonon Version: 4.3.1
-- Found KDE 4.4 include dir: /usr/include
-- Found KDE 4.4 library dir: /usr/lib
-- Found the KDE4 kconfig_compiler preprocessor: /usr/bin/kconfig_compiler
-- Found automoc4: /usr/bin/automoc4
-- Configuring done
-- Generating done
-- Build files have been written to: /home/jamie/Desktop/fancytasks-1.0.92/build
jamie@jamie-kubuntu:~/Desktop/fancytasks-1.0.92/build$ sudo make
[  0%] Built target plasma_applet_fancytasks_automoc
[  2%] Building CXX object applet/CMakeFiles/plasma_applet_fancytasks.dir/plasma_applet_fancytasks_automoc.o
[  5%] Building CXX object applet/CMakeFiles/plasma_applet_fancytasks.dir/FancyTasksApplet.o                                                                                       
[  8%] Building CXX object applet/CMakeFiles/plasma_applet_fancytasks.dir/FancyTasksIcon.o                                                                                         
[ 11%] Building CXX object applet/CMakeFiles/plasma_applet_fancytasks.dir/FancyTasksLight.o                                                                                        
[ 14%] Building CXX object applet/CMakeFiles/plasma_applet_fancytasks.dir/FancyTasksSeparator.o                                                                                    
[ 17%] Building CXX object applet/CMakeFiles/plasma_applet_fancytasks.dir/FancyTasksDropZone.o                                                                                     
[ 20%] Building CXX object applet/CMakeFiles/plasma_applet_fancytasks.dir/FancyTasksMenu.o                                                                                         
[ 23%] Building CXX object applet/CMakeFiles/plasma_applet_fancytasks.dir/FancyTasksTask.o                                                                                         
[ 26%] Building CXX object applet/CMakeFiles/plasma_applet_fancytasks.dir/FancyTasksLauncher.o                                                                                     
/home/jamie/Desktop/fancytasks-1.0.92/applet/FancyTasksLauncher.cpp:33:29: error: konq_operations.h: No such file or directory                                                     
/home/jamie/Desktop/fancytasks-1.0.92/applet/FancyTasksLauncher.cpp: In member function ‘void FancyTasks::Launcher::emptyTrash()’:
/home/jamie/Desktop/fancytasks-1.0.92/applet/FancyTasksLauncher.cpp:392: error: ‘KonqOperations’ has not been declared
make[2]: *** [applet/CMakeFiles/plasma_applet_fancytasks.dir/FancyTasksLauncher.o] Error 1
make[1]: *** [applet/CMakeFiles/plasma_applet_fancytasks.dir/all] Error 2
make: *** [all] Error 2
jamie@jamie-kubuntu:~/Desktop/fancytasks-1.0.92/build$ 

```

---

### Post by nerdy_kid on 2010-04-13
could always just install all the -dev packages...might not use that much space idk

---

### Post by mgranet on 2010-04-13
Try installing the kde-devel package. That seems to supply the required header file.

---

### Post by Falc7 on 2010-04-16
Yes! that did it thanks :)

---

