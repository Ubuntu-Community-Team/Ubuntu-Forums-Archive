---
title: "ISO a RELIABLE weather widget"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by Gotaro on 2009-02-01
Does anyone know of a good weather widget?  The "LCD Weather Station" widget that comes default does not get very close to my house..  I can get an RSS feed for the weather just fine, as there's a weather station less than half a mile from my house, but I would like something prettier! ;)  I tried to install [_yaWP_](http://www.kde-look.org/content/show.php/yaWP+(Yet+Another+Weather+Plasmoid)?content=94106), but couldn't figure out how..

---

### Post by OutOfReach on 2009-02-01
We are talking about KDE, right?

If so I like the Weather Forecast widget, I think it comes default. I am using Arch Linux so that may a difference...

---

### Post by LouisZepher on 2009-02-01
I use the weather applet in Gnome and a command-line weather program.  Both seem to be accurate for my area.

---

### Post by Gotaro on 2009-02-01
> **OutOfReach said:**
> We are talking about KDE, right?

If so I like the Weather Forecast widget, I think it comes default. I am using Arch Linux so that may a difference...
Yes, KDE.  I don't have that one on the list, and when I go to Install New Widgets->Download New Plasma Widgets, it isn't on that list, either, granted there are only about 5 available for me to download :(..

> **LouisZepher said:**
> I use the weather applet in Gnome and a command-line weather program.  Both seem to be accurate for my area.
What is the name of the Gnome applet, for future reference?

---

### Post by jerrynewt on 2009-02-01
Weather Report 2.25.2

---

### Post by txcrackers on 2009-02-02
Just because there's a weather station near you, it doesn't mean that **you** can get the data. Likely, given that you're in the US, it belongs to either a TV station or NOAA. Also, *all* weather-reporting applications/widgets are tied into the globally-accessible services, like NOAA, Weather.com, BBC, etc. And they only report from the "official" weather sites (NOAA, again) and those are responsible for covering a wide area.

I don't think you're going to get what you want, no matter what widget you use.

---

### Post by Gotaro on 2009-02-02
> **txcrackers said:**
> Just because there's a weather station near you, it doesn't mean that **you** can get the data. Likely, given that you're in the US, it belongs to either a TV station or NOAA. Also, *all* weather-reporting applications/widgets are tied into the globally-accessible services, like NOAA, Weather.com, BBC, etc. And they only report from the "official" weather sites (NOAA, again) and those are responsible for covering a wide area.

I don't think you're going to get what you want, no matter what widget you use.
When I used whatever the standard weather widget thing was for Windows Vista in its early days, I would type in my zip code and get a list of locations to choose from, one being the location right by my house.  On one weather widget I tried a few days ago, the same format was used, but I only had a couple choices for locations, the closest wasn't exactly right (reported cloudy when it was sunny, not sure about the accuracy of the temp).  In any case, all I'm asking for is a reliable one and instructions on how to install! :P  The standard one in KDE 4.2 is VERY limited in locations, and the closest on that one is way too far from me to use.

---

### Post by MistralWind on 2009-02-02
> **Gotaro said:**
> Does anyone know of a good weather widget?  The "LCD Weather Station" widget that comes default does not get very close to my house..  I can get an RSS feed for the weather just fine, as there's a weather station less than half a mile from my house, but I would like something prettier! ;)  I tried to install [_yaWP_](http://www.kde-look.org/content/show.php/yaWP+(Yet+Another+Weather+Plasmoid)?content=94106), but couldn't figure out how..
What went wrong with YAWP? I had some issues at first, too, but I got it to work when I followed the installation notes. (It's a great widget, BTW. I like it even more than Liquid Weather!)

---

### Post by Gotaro on 2009-02-02
> **MistralWind said:**
> What went wrong with YAWP? I had some issues at first, too, but I got it to work when I followed the installation notes. (It's a great widget, BTW. I like it even more than Liquid Weather!)
I don't really remember..  I've NEVER gotten cmake to work.  It either installs incompletely, or when I try to make something it fails.  I'm usually missing packages, etc.  So what would the instructions be to make yaWP, for someone with a fresh install of Kubuntu 8.10?  (That means no cmake, either.)

---

### Post by MistralWind on 2009-02-02
> **Gotaro said:**
> I don't really remember..  I've NEVER gotten cmake to work.  It either installs incompletely, or when I try to make something it fails.  I'm usually missing packages, etc.  So what would the instructions be to make yaWP, for someone with a fresh install of Kubuntu 8.10?  (That means no cmake, either.)
I just did this, as per the notes:
> tar -zxf yawp*
./install.sh
The automatic installer script worked fine for me, though YMMV. (My 8.10 was an upgrade.)

---

### Post by Gotaro on 2009-02-02
> **MistralWind said:**
> I just did this, as per the notes:

The automatic installer script worked fine for me, though YMMV. (My 8.10 was an upgrade.)
Wow!  I was going about things the hard way, huh?!  Well, it still gave the infamous errors:
```

gotaro@gotaro-linux:~/Downloads/yawp-0.1.65$ ./install.sh
KDE version: 4.2.00                                      
Using CMakeLists.kde42.txt                               
-- The C compiler identification is GNU                  
-- The CXX compiler identification is unknown            
-- Check for working C compiler: /usr/bin/gcc            
-- Check for working C compiler: /usr/bin/gcc -- works   
-- Detecting C compiler ABI info                         
-- Detecting C compiler ABI info - done                  
CMake Error: your CXX compiler: "CMAKE_CXX_COMPILER-NOTFOUND" was not found.   Please set CMAKE_CXX_COMPILER to a valid compiler path or name.                  
-- Looking for Q_WS_X11                                                         
-- Looking for Q_WS_X11 - found                                                 
-- Looking for Q_WS_WIN                                                         
-- Looking for Q_WS_WIN - not found.                                            
-- Looking for Q_WS_QWS                                                         
-- Looking for Q_WS_QWS - not found.                                            
-- Looking for Q_WS_MAC                                                         
-- Looking for Q_WS_MAC - not found.                                            
-- Found Qt-Version 4.4.3 (using /usr/bin/qmake)                                
-- Looking for XOpenDisplay in /usr/lib/libX11.so;/usr/lib/libXext.so;/usr/lib/libXft.so;/usr/lib/libXau.so;/usr/lib/libXdmcp.so                                
-- Looking for XOpenDisplay in /usr/lib/libX11.so;/usr/lib/libXext.so;/usr/lib/libXft.so;/usr/lib/libXau.so;/usr/lib/libXdmcp.so - found                        
-- Looking for gethostbyname                                                    
-- Looking for gethostbyname - found                                            
-- Looking for connect                                                          
-- Looking for connect - found                                                  
-- Looking for remove                                                           
-- Looking for remove - found                                                   
-- Looking for shmat                                                            
-- Looking for shmat - found                                                    
-- Looking for IceConnectionNumber in ICE                                       
-- Looking for IceConnectionNumber in ICE - found                               
-- Found X11: /usr/lib/libX11.so                                                
-- Looking for include files CMAKE_HAVE_PTHREAD_H                               
-- Looking for include files CMAKE_HAVE_PTHREAD_H - found                       
-- Looking for pthread_create in pthreads                                       
-- Looking for pthread_create in pthreads - not found                           
-- Looking for pthread_create in pthread
-- Looking for pthread_create in pthread - found
-- Found Threads: TRUE
-- Found Automoc4: /usr/bin/automoc4
-- Found Perl: /usr/bin/perl
-- Performing Test _OFFT_IS_64BIT
CMake Error at /usr/share/cmake-2.6/Modules/CMakeCXXInformation.cmake:17 (GET_FILENAME_COMPONENT):
  get_filename_component called with incorrect number of arguments
Call Stack (most recent call first):
  CMakeLists.txt:3 (PROJECT)


CMake Error: CMAKE_CXX_COMPILER not set, after EnableLanguage
CMake Error: Internal CMake error, TryCompile configure of cmake failed
-- Performing Test _OFFT_IS_64BIT - Failed
-- Phonon Version: 4.3.0
-- Found Phonon: /usr/lib/libphonon.so
-- Found Phonon Includes: /usr/include/KDE;/usr/include
-- Found KDE 4.2 include dir: /usr/include
-- Found KDE 4.2 library dir: /usr/lib
-- Found the KDE4 kconfig_compiler preprocessor: /usr/bin/kconfig_compiler
-- Found automoc4: /usr/bin/automoc4
-- Looking for dgettext
-- Looking for dgettext - found
-- Found Gettext: built in libc
CMake Error at po/CMakeLists.txt:6 (MESSAGE):
  Please install the msgfmt binary


-- Configuring incomplete, errors occurred!
/home/gotaro/Downloads/yawp-0.1.65/build
make: *** No rule to make target `clean'.  Stop.
make: *** No targets specified and no makefile found.  Stop.
Compilation failed, sorry :-(
```

---

