---
title: "How can I install the Toggle-Compositing plasmoid on Kubuntu 9.04?"
date: 2009-10-25
forum: New to Ubuntu
---

### Post by KIAaze on 2009-10-25
Hi,

I'm trying to install the Toggle-Compositing plasmoid: [http://www.kde-look.org/content/show.php?action=content&content=78299&PHPSESSID=cae](http://www.kde-look.org/content/show.php?action=content&content=78299&PHPSESSID=cae)

I followed the instruction in INSTALL and did:
```
mkdir build
cd build/
cmake ../
make
sudo make install

```

Everything worked without errors. make install output the following:
```
[  0%] Built target plasma_applet_toggle_compositing_automoc                                                                                                                                              
[100%] Built target plasma_applet_toggle_compositing                                                                                                                                                      
Install the project...                                                                                                                                                                                    
-- Install configuration: "RelWithDebInfo"                                                                                                                                                                
-- Installing: /usr/local/lib/kde4/plasma_applet_toggle_compositing.so                                                                                                                                    
-- Set runtime path of "/usr/local/lib/kde4/plasma_applet_toggle_compositing.so" to "/usr/local/lib"                                                                                                      
-- Installing: /usr/local/share/kde4/services/plasma-applet-toggle_compositing.desktop                                                                                                                    
-- Installing: /usr/local/share/apps/desktoptheme/default/widgets/onoff_switch.svg                   
```

But when I want to test it with
```
plasmoidviewer plasma_applet_toggle_compositing
```
I get "Could not find requested component: plasma_applet_toggle_compositing"

And on the command-line:
```
plasmoidviewer(13198) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"
plasmoidviewer(13198) KServiceFactory::findServiceByDesktopPath: "findServiceByDesktopPath:  not found"

```

How can I get it to work?

edit: Figured it out after playing around with different CMAKE_INSTALL_PREFIX values:

```
mkdir build
cd build/
cmake -DCMAKE_INSTALL_PREFIX=/usr ../
make
sudo make install

```
My first plasmoid installation. :)

---

