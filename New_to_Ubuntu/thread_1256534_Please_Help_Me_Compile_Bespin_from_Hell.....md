---
title: "Please Help Me Compile Bespin from Hell...."
date: 2009-09-02
forum: New to Ubuntu
---

### Post by kamitsukai on 2009-09-02
I'm trying to compile bespin with argb but it's impossible:(:confused:

Here's the errors I get from command:

```
carl@carl-laptop ~/cloudcity/build $ cd ~/
carl@carl-laptop ~ $ cd cloudcity
carl@carl-laptop ~/cloudcity $ ./configure


==================== Bespin interactive configuration ====================

    Seems you have cmake.
    In addition to the style, you can have a KWin decoration,
    a mac-like menu plasmoid and config plugins IFF you have KDE....

--> Do you want to compile with KDE support? [Y/n]

-- Found Qt-Version 4.5.0 (using /usr/bin/qmake-qt4)
-- Found X11: /usr/lib/libX11.so                    
-- Phonon Version: 4.3.0                            
-- Found KDE 4.2 include dir: /usr/include          
-- Found KDE 4.2 library dir: /usr/lib              
-- Found the KDE4 kconfig_compiler preprocessor: /usr/bin/kconfig_compiler
-- Found automoc4: /usr/bin/automoc4                                      
-- Found X11: /usr/lib/libX11.so                                          
-- INFO: XRender was found - kwin deco & FX via GPU available!            
-- Configuring done                                                       
-- Generating done                                                        
-- Build files have been written to: /home/carl/cloudcity/build           

Configuration succeeded...

--> Do you want to run a cmake GUI to adjust the configuration? [y/N]


========================= Configuration done ============================

   Ok, now just "cd build", "make" and "sudo make install"...


carl@carl-laptop ~/cloudcity $ make
make: *** No targets specified and no makefile found. Stop.
carl@carl-laptop ~/cloudcity $ cd build
carl@carl-laptop ~/cloudcity/build $ make
[ 62%] Built target bespin               
[ 75%] Built target bespin               
[ 75%] Built target kstyle_bespin_config_automoc
[ 80%] Built target kstyle_bespin_config        
[ 80%] Built target kwin3_bespin_automoc        
[ 81%] Building CXX object kwin/CMakeFiles/kwin3_bespin.dir/kwin3_bespin_automoc.o
In file included from /home/carl/cloudcity/build/kwin/moc_client.cpp:10,                                                                       
                 from /home/carl/cloudcity/build/kwin/kwin3_bespin_automoc.cpp:4:                                                              
/home/carl/cloudcity/build/kwin/../../kwin/client.h:31:25: error: kdecoration.h: No such file or directory                                     
In file included from /home/carl/cloudcity/build/kwin/../../kwin/client.h:32,                                                                  
                 from /home/carl/cloudcity/build/kwin/moc_client.cpp:10,                                                                       
                 from /home/carl/cloudcity/build/kwin/kwin3_bespin_automoc.cpp:4:                                                              
/home/carl/cloudcity/build/kwin/../../kwin/factory.h:32:32: error: kdecorationfactory.h: No such file or directory                             
In file included from /home/carl/cloudcity/build/kwin/../../kwin/client.h:32,                                                                  
                 from /home/carl/cloudcity/build/kwin/moc_client.cpp:10,                                                                       
                 from /home/carl/cloudcity/build/kwin/kwin3_bespin_automoc.cpp:4:                                                              
/home/carl/cloudcity/build/kwin/../../kwin/factory.h:53: error: expected class-name before ‘{’ token                                           
/home/carl/cloudcity/build/kwin/../../kwin/factory.h:57: error: ISO C++ forbids declaration of ‘KDecoration’ with no type                      
/home/carl/cloudcity/build/kwin/../../kwin/factory.h:57: error: expected ‘;’ before ‘*’ token                                                  
/home/carl/cloudcity/build/kwin/../../kwin/factory.h:59: error: ‘Ability’ has not been declared                                                
/home/carl/cloudcity/build/kwin/../../kwin/factory.h:63: error: ‘BorderSize’ was not declared in this scope                                    
/home/carl/cloudcity/build/kwin/../../kwin/factory.h:63: error: template argument 1 is invalid                                                 
/home/carl/cloudcity/build/kwin/../../kwin/factory.h: In member function ‘int Bespin::Factory::borderSizes() const’:                           
/home/carl/cloudcity/build/kwin/../../kwin/factory.h:65: error: ‘BorderSize’ was not declared in this scope                                    
/home/carl/cloudcity/build/kwin/../../kwin/factory.h:65: error: template argument 1 is invalid                                                 
/home/carl/cloudcity/build/kwin/../../kwin/factory.h:65: error: ‘BorderTiny’ was not declared in this scope                                    
/home/carl/cloudcity/build/kwin/../../kwin/factory.h:65: error: ‘BorderNormal’ was not declared in this scope                                  
/home/carl/cloudcity/build/kwin/../../kwin/factory.h:66: error: ‘BorderLarge’ was not declared in this scope                                   
/home/carl/cloudcity/build/kwin/../../kwin/factory.h:66: error: ‘BorderVeryLarge’ was not declared in this scope                               
/home/carl/cloudcity/build/kwin/../../kwin/factory.h:66: error: ‘BorderHuge’ was not declared in this scope                                    
/home/carl/cloudcity/build/kwin/../../kwin/factory.h:66: error: ‘BorderVeryHuge’ was not declared in this scope                                
/home/carl/cloudcity/build/kwin/../../kwin/factory.h:67: error: ‘BorderOversized’ was not declared in this scope                               
In file included from /home/carl/cloudcity/build/kwin/moc_client.cpp:10,                                                                       
                 from /home/carl/cloudcity/build/kwin/kwin3_bespin_automoc.cpp:4:                                                              
/home/carl/cloudcity/build/kwin/../../kwin/client.h: At global scope:                                                                          
/home/carl/cloudcity/build/kwin/../../kwin/client.h:53: error: expected class-name before ‘{’ token                                            
/home/carl/cloudcity/build/kwin/../../kwin/client.h:56: error: expected `)' before ‘*’ token                                                   
/home/carl/cloudcity/build/kwin/../../kwin/client.h:71: error: ‘KDecorationDefines’ has not been declared                                      
/home/carl/cloudcity/build/kwin/../../kwin/client.h:71: error: ISO C++ forbids declaration of ‘Position’ with no type                          
/home/carl/cloudcity/build/kwin/../../kwin/client.h:71: error: expected ‘;’ before ‘mousePosition’                                             
/home/carl/cloudcity/build/kwin/../../kwin/client.h:97: error: ‘ColorType’ has not been declared                                               
/home/carl/cloudcity/build/kwin/../../kwin/client.h:53: warning: ‘class Bespin::Client’ has virtual functions and accessible non-virtual destructor                                                                                                                                           
/home/carl/cloudcity/build/kwin/../../kwin/client.h: In member function ‘Bespin::Gradients::Type Bespin::Client::gradient()’:                  
/home/carl/cloudcity/build/kwin/../../kwin/client.h:66: error: ‘isActive’ was not declared in this scope                                       
In file included from /home/carl/cloudcity/build/kwin/kwin3_bespin_automoc.cpp:4:                                                              
/home/carl/cloudcity/build/kwin/moc_client.cpp: At global scope:                                                                               
/home/carl/cloudcity/build/kwin/moc_client.cpp:52: error: ‘KDecoration’ has not been declared                                                  
/home/carl/cloudcity/build/kwin/moc_client.cpp: In member function ‘virtual void* Bespin::Client::qt_metacast(const char*)’:                   
/home/carl/cloudcity/build/kwin/moc_client.cpp:66: error: ‘KDecoration’ has not been declared                                                  
/home/carl/cloudcity/build/kwin/moc_client.cpp: In member function ‘virtual int Bespin::Client::qt_metacall(QMetaObject::Call, int, void**)’:  
/home/carl/cloudcity/build/kwin/moc_client.cpp:71: error: ‘KDecoration’ has not been declared                                                  
/home/carl/cloudcity/build/kwin/moc_client.cpp: In member function ‘void Bespin::Client::maximizeChanged(bool)’:                               
/home/carl/cloudcity/build/kwin/moc_client.cpp:93: error: no matching function for call to ‘QMetaObject::activate(Bespin::Client* const, const QMetaObject*, int, void* [2])’                                                                                                                 
/usr/include/qt4/QtCore/qobjectdefs.h:333: note: candidates are: static void QMetaObject::activate(QObject*, int, void**)                      
/usr/include/qt4/QtCore/qobjectdefs.h:334: note:                 static void QMetaObject::activate(QObject*, int, int, void**)                 
/usr/include/qt4/QtCore/qobjectdefs.h:335: note:                 static void QMetaObject::activate(QObject*, const QMetaObject*, int, void**)  
/usr/include/qt4/QtCore/qobjectdefs.h:336: note:                 static void QMetaObject::activate(QObject*, const QMetaObject*, int, int, void**)
/home/carl/cloudcity/build/kwin/moc_client.cpp: In member function ‘void Bespin::Client::stickyChanged(bool)’:
/home/carl/cloudcity/build/kwin/moc_client.cpp:100: error: no matching function for call to ‘QMetaObject::activate(Bespin::Client* const, const QMetaObject*, int, void* [2])’
/usr/include/qt4/QtCore/qobjectdefs.h:333: note: candidates are: static void QMetaObject::activate(QObject*, int, void**)
/usr/include/qt4/QtCore/qobjectdefs.h:334: note:                 static void QMetaObject::activate(QObject*, int, int, void**)
/usr/include/qt4/QtCore/qobjectdefs.h:335: note:                 static void QMetaObject::activate(QObject*, const QMetaObject*, int, void**)
/usr/include/qt4/QtCore/qobjectdefs.h:336: note:                 static void QMetaObject::activate(QObject*, const QMetaObject*, int, int, void**)
/home/carl/cloudcity/build/kwin/moc_client.cpp: In member function ‘void Bespin::Client::shadeChanged(bool)’:
/home/carl/cloudcity/build/kwin/moc_client.cpp:107: error: no matching function for call to ‘QMetaObject::activate(Bespin::Client* const, const QMetaObject*, int, void* [2])’
/usr/include/qt4/QtCore/qobjectdefs.h:333: note: candidates are: static void QMetaObject::activate(QObject*, int, void**)
/usr/include/qt4/QtCore/qobjectdefs.h:334: note:                 static void QMetaObject::activate(QObject*, int, int, void**)
/usr/include/qt4/QtCore/qobjectdefs.h:335: note:                 static void QMetaObject::activate(QObject*, const QMetaObject*, int, void**)
/usr/include/qt4/QtCore/qobjectdefs.h:336: note:                 static void QMetaObject::activate(QObject*, const QMetaObject*, int, int, void**)
make[2]: *** [kwin/CMakeFiles/kwin3_bespin.dir/kwin3_bespin_automoc.o] Error 1
make[1]: *** [kwin/CMakeFiles/kwin3_bespin.dir/all] Error 2
make: *** [all] Error 2

```

Please Help!

---

### Post by NoaHall on 2009-09-02
Are you sure if it failed? These things can say one thing, and mean another. Try opening it. (bespin in terminal probably.)

---

### Post by kamitsukai on 2009-09-02
> **NoaHall said:**
> Are you sure if it failed? These things can say one thing, and mean another. Try opening it. (bespin in terminal probably.)

I haven't installed it only built...should I install if it says there were errors?

---

### Post by NoaHall on 2009-09-02
Yes, just carry on - it doesn't do harm.

run "sudo make install" next

---

### Post by kamitsukai on 2009-09-02
> **NoaHall said:**
> Yes, just carry on - it doesn't do harm.

run "sudo make install" next


```
carl@carl-laptop ~/cloudcity/build $ sudo make install
[ 62%] Built target bespin                            
[ 75%] Built target bespin                            
Generating moc_bconfig.cpp                            
Generating moc_config.cpp                                                                                                                      
[ 75%] Built target kstyle_bespin_config_automoc                                                                                               
Scanning dependencies of target kstyle_bespin_config                                                                                           
[ 76%] Building CXX object config/CMakeFiles/kstyle_bespin_config.dir/kstyle_bespin_config_automoc.o                                           
Linking CXX shared module ../lib/kstyle_bespin_config.so                                                                                       
[ 80%] Built target kstyle_bespin_config                                                                                                       
[ 80%] Built target kwin3_bespin_automoc                                                                                                       
[ 81%] Building CXX object kwin/CMakeFiles/kwin3_bespin.dir/kwin3_bespin_automoc.o                                                             
In file included from /home/carl/cloudcity/build/kwin/moc_client.cpp:10,                                                                       
                 from /home/carl/cloudcity/build/kwin/kwin3_bespin_automoc.cpp:4:                                                              
/home/carl/cloudcity/build/kwin/../../kwin/client.h:31:25: error: kdecoration.h: No such file or directory                                     
In file included from /home/carl/cloudcity/build/kwin/../../kwin/client.h:32,                                                                  
                 from /home/carl/cloudcity/build/kwin/moc_client.cpp:10,                                                                       
                 from /home/carl/cloudcity/build/kwin/kwin3_bespin_automoc.cpp:4:                                                              
/home/carl/cloudcity/build/kwin/../../kwin/factory.h:32:32: error: kdecorationfactory.h: No such file or directory                             
In file included from /home/carl/cloudcity/build/kwin/../../kwin/client.h:32,                                                                  
                 from /home/carl/cloudcity/build/kwin/moc_client.cpp:10,                                                                       
                 from /home/carl/cloudcity/build/kwin/kwin3_bespin_automoc.cpp:4:                                                              
/home/carl/cloudcity/build/kwin/../../kwin/factory.h:53: error: expected class-name before ‘{’ token                                           
/home/carl/cloudcity/build/kwin/../../kwin/factory.h:57: error: ISO C++ forbids declaration of ‘KDecoration’ with no type                      
/home/carl/cloudcity/build/kwin/../../kwin/factory.h:57: error: expected ‘;’ before ‘*’ token                                                  
/home/carl/cloudcity/build/kwin/../../kwin/factory.h:59: error: ‘Ability’ has not been declared                                                
/home/carl/cloudcity/build/kwin/../../kwin/factory.h:63: error: ‘BorderSize’ was not declared in this scope                                    
/home/carl/cloudcity/build/kwin/../../kwin/factory.h:63: error: template argument 1 is invalid                                                 
/home/carl/cloudcity/build/kwin/../../kwin/factory.h: In member function ‘int Bespin::Factory::borderSizes() const’:                           
/home/carl/cloudcity/build/kwin/../../kwin/factory.h:65: error: ‘BorderSize’ was not declared in this scope                                    
/home/carl/cloudcity/build/kwin/../../kwin/factory.h:65: error: template argument 1 is invalid                                                 
/home/carl/cloudcity/build/kwin/../../kwin/factory.h:65: error: ‘BorderTiny’ was not declared in this scope                                    
/home/carl/cloudcity/build/kwin/../../kwin/factory.h:65: error: ‘BorderNormal’ was not declared in this scope                                  
/home/carl/cloudcity/build/kwin/../../kwin/factory.h:66: error: ‘BorderLarge’ was not declared in this scope                                   
/home/carl/cloudcity/build/kwin/../../kwin/factory.h:66: error: ‘BorderVeryLarge’ was not declared in this scope                               
/home/carl/cloudcity/build/kwin/../../kwin/factory.h:66: error: ‘BorderHuge’ was not declared in this scope                                    
/home/carl/cloudcity/build/kwin/../../kwin/factory.h:66: error: ‘BorderVeryHuge’ was not declared in this scope                                
/home/carl/cloudcity/build/kwin/../../kwin/factory.h:67: error: ‘BorderOversized’ was not declared in this scope                               
In file included from /home/carl/cloudcity/build/kwin/moc_client.cpp:10,                                                                       
                 from /home/carl/cloudcity/build/kwin/kwin3_bespin_automoc.cpp:4:                                                              
/home/carl/cloudcity/build/kwin/../../kwin/client.h: At global scope:                                                                          
/home/carl/cloudcity/build/kwin/../../kwin/client.h:53: error: expected class-name before ‘{’ token                                            
/home/carl/cloudcity/build/kwin/../../kwin/client.h:56: error: expected `)' before ‘*’ token                                                   
/home/carl/cloudcity/build/kwin/../../kwin/client.h:71: error: ‘KDecorationDefines’ has not been declared                                      
/home/carl/cloudcity/build/kwin/../../kwin/client.h:71: error: ISO C++ forbids declaration of ‘Position’ with no type                          
/home/carl/cloudcity/build/kwin/../../kwin/client.h:71: error: expected ‘;’ before ‘mousePosition’                                             
/home/carl/cloudcity/build/kwin/../../kwin/client.h:97: error: ‘ColorType’ has not been declared                                               
/home/carl/cloudcity/build/kwin/../../kwin/client.h:53: warning: ‘class Bespin::Client’ has virtual functions and accessible non-virtual destructor                                                                                                                                           
/home/carl/cloudcity/build/kwin/../../kwin/client.h: In member function ‘Bespin::Gradients::Type Bespin::Client::gradient()’:                  
/home/carl/cloudcity/build/kwin/../../kwin/client.h:66: error: ‘isActive’ was not declared in this scope                                       
In file included from /home/carl/cloudcity/build/kwin/kwin3_bespin_automoc.cpp:4:                                                              
/home/carl/cloudcity/build/kwin/moc_client.cpp: At global scope:                                                                               
/home/carl/cloudcity/build/kwin/moc_client.cpp:52: error: ‘KDecoration’ has not been declared                                                  
/home/carl/cloudcity/build/kwin/moc_client.cpp: In member function ‘virtual void* Bespin::Client::qt_metacast(const char*)’:                   
/home/carl/cloudcity/build/kwin/moc_client.cpp:66: error: ‘KDecoration’ has not been declared                                                  
/home/carl/cloudcity/build/kwin/moc_client.cpp: In member function ‘virtual int Bespin::Client::qt_metacall(QMetaObject::Call, int, void**)’:  
/home/carl/cloudcity/build/kwin/moc_client.cpp:71: error: ‘KDecoration’ has not been declared                                                  
/home/carl/cloudcity/build/kwin/moc_client.cpp: In member function ‘void Bespin::Client::maximizeChanged(bool)’:                               
/home/carl/cloudcity/build/kwin/moc_client.cpp:93: error: no matching function for call to ‘QMetaObject::activate(Bespin::Client* const, const QMetaObject*, int, void* [2])’                                                                                                                 
/usr/include/qt4/QtCore/qobjectdefs.h:333: note: candidates are: static void QMetaObject::activate(QObject*, int, void**)                      
/usr/include/qt4/QtCore/qobjectdefs.h:334: note:                 static void QMetaObject::activate(QObject*, int, int, void**)                 
/usr/include/qt4/QtCore/qobjectdefs.h:335: note:                 static void QMetaObject::activate(QObject*, const QMetaObject*, int, void**)  
/usr/include/qt4/QtCore/qobjectdefs.h:336: note:                 static void QMetaObject::activate(QObject*, const QMetaObject*, int, int, void**)
/home/carl/cloudcity/build/kwin/moc_client.cpp: In member function ‘void Bespin::Client::stickyChanged(bool)’:
/home/carl/cloudcity/build/kwin/moc_client.cpp:100: error: no matching function for call to ‘QMetaObject::activate(Bespin::Client* const, const QMetaObject*, int, void* [2])’
/usr/include/qt4/QtCore/qobjectdefs.h:333: note: candidates are: static void QMetaObject::activate(QObject*, int, void**)
/usr/include/qt4/QtCore/qobjectdefs.h:334: note:                 static void QMetaObject::activate(QObject*, int, int, void**)
/usr/include/qt4/QtCore/qobjectdefs.h:335: note:                 static void QMetaObject::activate(QObject*, const QMetaObject*, int, void**)
/usr/include/qt4/QtCore/qobjectdefs.h:336: note:                 static void QMetaObject::activate(QObject*, const QMetaObject*, int, int, void**)
/home/carl/cloudcity/build/kwin/moc_client.cpp: In member function ‘void Bespin::Client::shadeChanged(bool)’:
/home/carl/cloudcity/build/kwin/moc_client.cpp:107: error: no matching function for call to ‘QMetaObject::activate(Bespin::Client* const, const QMetaObject*, int, void* [2])’
/usr/include/qt4/QtCore/qobjectdefs.h:333: note: candidates are: static void QMetaObject::activate(QObject*, int, void**)
/usr/include/qt4/QtCore/qobjectdefs.h:334: note:                 static void QMetaObject::activate(QObject*, int, int, void**)
/usr/include/qt4/QtCore/qobjectdefs.h:335: note:                 static void QMetaObject::activate(QObject*, const QMetaObject*, int, void**)
/usr/include/qt4/QtCore/qobjectdefs.h:336: note:                 static void QMetaObject::activate(QObject*, const QMetaObject*, int, int, void**)
make[2]: *** [kwin/CMakeFiles/kwin3_bespin.dir/kwin3_bespin_automoc.o] Error 1
make[1]: *** [kwin/CMakeFiles/kwin3_bespin.dir/all] Error 2
make: *** [all] Error 2

```

Nope not working....

---

### Post by Bachstelze on 2009-09-02
> **NoaHall said:**
> Are you sure if it failed?

It failed.

@kamitsukai: you need kdebase-workspace-dev.

---

### Post by NoaHall on 2009-09-02
Oops, sorry, didn't see the code - damn browsers.

---

### Post by kamitsukai on 2009-09-02
Thank you both ever so much! all built and installed:D

---

