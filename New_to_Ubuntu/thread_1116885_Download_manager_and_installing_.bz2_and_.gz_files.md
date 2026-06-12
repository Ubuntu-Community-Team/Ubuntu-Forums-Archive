---
title: "Download manager and installing .bz2 and .gz files"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by Coolsaber57 on 2009-04-05
Hi,

Problem 1: I would like to find a program that has the same functionality as Flashget, which for me is:
-Multiple file downloads
-Ability to use a username/password for a specified site
-mass copying/pasting and/or clipboard monitoring (meaning that if I have a list of 10 links as text and I copy it, I would like to be able to paste it in or have it automatically pasted into the download manager. The ones I've tried so far have made me input the links one by one, which is not an option)

Problem 2: Ok, I get that .bz2 and .gz are sort of like zipped or archived files, and when I extract them, i follow the instructions to install them, namely:
./configure
make

However, I can't even get that far, as it says that the "C++ compiler cannot create executables.."

What am I doing wrong?

---

### Post by taurus on 2009-04-05
Have you installed the build-essential package before you try to build anything from source?

```
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by Coolsaber57 on 2009-04-05
> **taurus said:**
> Have you installed the build-essential package before you try to build anything from source?

```
sudo apt-get update
sudo apt-get install build-essential
```

lol..I didn't know I had to. installing now.

Thanks!

What about the DL manager? Does anyone know of one that works like Flashget?

---

### Post by Coolsaber57 on 2009-04-05
Ok, this is driving me nuts, when I get the step "su make install" it asks for a password.

I put in my password and it says "authentication failure"

Help?

---

### Post by taurus on 2009-04-05
```
**sudo** make install
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Coolsaber57 on 2009-04-05
> **taurus said:**
> ```
**sudo** make install
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Ok, I did that, but I don't think that the install was successful, as I can't find it in my programs list.

>                                      
chris@Skywalker13:~/Downloads/prozgui-2.0.2$ sudo make install   
Making install in libprozilla                                    
make[1]: Entering directory `/home/chris/Downloads/prozgui-2.0.2/libprozilla'
Making install in intl                                                       
make[2]: Entering directory `/home/chris/Downloads/prozgui-2.0.2/libprozilla/intl'
if test "libprozilla" = "gettext" \                                               
           && test '' = 'intl-compat.o'; then \                                   
          /bin/sh `case "./mkinstalldirs" in /*) echo "./mkinstalldirs" ;; *) echo ".././mkinstalldirs" ;; esac` /usr/local/lib /usr/local/include; \                                     
          /usr/bin/install -c -m 644 libintl.h /usr/local/include/libintl.h; \               
          /bin/sh ../libtool --mode=install \                                                
            /usr/bin/install -c -m 644 libintl.a /usr/local/lib/libintl.a; \                 
        else \                                                                               
          : ; \                                                                              
        fi                                                                                   
if test 'no' = yes; then \                                                                   
          /bin/sh `case "./mkinstalldirs" in /*) echo "./mkinstalldirs" ;; *) echo ".././mkinstalldirs" ;; esac` /usr/local/lib; \                                                        
          temp=/usr/local/lib/t-charset.alias; \                                             
          dest=/usr/local/lib/charset.alias; \                                               
          if test -f /usr/local/lib/charset.alias; then \                                    
            orig=/usr/local/lib/charset.alias; \                                             
            sed -f ref-add.sed $orig > $temp; \                                              
            /usr/bin/install -c -m 644 $temp $dest; \                                        
            rm -f $temp; \                                                                   
          else \                                                                             
            if test yes = no; then \                                                         
              orig=charset.alias; \                                                          
              sed -f ref-add.sed $orig > $temp; \                                            
              /usr/bin/install -c -m 644 $temp $dest; \                                      
              rm -f $temp; \                                                                 
            fi; \                                                                            
          fi; \                                                                              
          /bin/sh `case "./mkinstalldirs" in /*) echo "./mkinstalldirs" ;; *) echo ".././mkinstalldirs" ;; esac` /usr/local/share/locale; \                                               
          test -f /usr/local/share/locale/locale.alias \                                     
            && orig=/usr/local/share/locale/locale.alias \                                   
            || orig=./locale.alias; \                                                        
          temp=/usr/local/share/locale/t-locale.alias; \                                     
          dest=/usr/local/share/locale/locale.alias; \                                       
          sed -f ref-add.sed $orig > $temp; \                                                
          /usr/bin/install -c -m 644 $temp $dest; \                                          
          rm -f $temp; \                                                                     
        else \                                                                               
          : ; \                                                                              
        fi                                                                                   
if test "libprozilla" = "gettext"; then \                                                    
          /bin/sh `case "./mkinstalldirs" in /*) echo "./mkinstalldirs" ;; *) echo ".././mkinstalldirs" ;; esac` /usr/local/share/gettext/intl; \                                         
          /usr/bin/install -c -m 644 VERSION /usr/local/share/gettext/intl/VERSION; \        
          /usr/bin/install -c -m 644 ChangeLog.inst /usr/local/share/gettext/intl/ChangeLog; \                                                                                            
          dists="Makefile.in config.charset locale.alias ref-add.sin ref-del.sin gettext.h gettextP.h hash-string.h libgnuintl.h libgettext.h loadinfo.h bindtextdom.c dcgettext.c dgettext.c gettext.c finddomain.c loadmsgcat.c localealias.c textdomain.c l10nflist.c explodename.c dcigettext.c dcngettext.c dngettext.c ngettext.c plural.y localcharset.c intl-compat.c"; \   
          for file in $dists; do \                                                           
            /usr/bin/install -c -m 644 ./$file \                                             
                            /usr/local/share/gettext/intl/$file; \                           
          done; \                                                                            
          chmod a+x /usr/local/share/gettext/intl/config.charset; \                          
          dists="plural.c"; \                                                                
          for file in $dists; do \                                                           
            if test -f $file; then dir=.; else dir=.; fi; \                                  
            /usr/bin/install -c -m 644 $dir/$file \                                          
                            /usr/local/share/gettext/intl/$file; \                           
          done; \                                                                            
          dists="xopen-msg.sed linux-msg.sed po2tbl.sed.in cat-compat.c"; \                  
          for file in $dists; do \                                                           
            rm -f /usr/local/share/gettext/intl/$file; \                                     
          done; \                                                                            
        else \                                                                               
          : ; \                                                                              
        fi                                                                                   
make[2]: Leaving directory `/home/chris/Downloads/prozgui-2.0.2/libprozilla/intl'            
Making install in po                                                                         
make[2]: Entering directory `/home/chris/Downloads/prozgui-2.0.2/libprozilla/po'             
if test -r ".././mkinstalldirs"; then \                                                      
          .././mkinstalldirs /usr/local/share; \                                             
        else \                                                                               
          /bin/sh ../mkinstalldirs /usr/local/share; \                                       
        fi                                                                                   
installing pt_BR.gmo as /usr/local/share/locale/pt_BR/LC_MESSAGES/libprozilla.mo             
installing ro.gmo as /usr/local/share/locale/ro/LC_MESSAGES/libprozilla.mo                   
installing nl.gmo as /usr/local/share/locale/nl/LC_MESSAGES/libprozilla.mo                   
if test "libprozilla" = "gettext"; then \                                                    
          if test -r ".././mkinstalldirs"; then \                                            
            .././mkinstalldirs /usr/local/share/gettext/po; \                                
          else \                                                                             
            /bin/sh ../mkinstalldirs /usr/local/share/gettext/po; \                          
          fi; \                                                                              
          /usr/bin/install -c -m 644 ./Makefile.in.in \                                      
                          /usr/local/share/gettext/po/Makefile.in.in; \                      
        else \                                                                               
          : ; \                                                                              
        fi                                                                                   
make[2]: Leaving directory `/home/chris/Downloads/prozgui-2.0.2/libprozilla/po'              
Making install in docs                                                                       
make[2]: Entering directory `/home/chris/Downloads/prozgui-2.0.2/libprozilla/docs'           
make[3]: Entering directory `/home/chris/Downloads/prozgui-2.0.2/libprozilla/docs'           
make[3]: Nothing to be done for `install-exec-am'.                                           
make[3]: Nothing to be done for `install-data-am'.                                           
make[3]: Leaving directory `/home/chris/Downloads/prozgui-2.0.2/libprozilla/docs'            
make[2]: Leaving directory `/home/chris/Downloads/prozgui-2.0.2/libprozilla/docs'            
Making install in src                                                                        
make[2]: Entering directory `/home/chris/Downloads/prozgui-2.0.2/libprozilla/src'            
/bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I..   -DLOCALEDIR=\"/usr/local/share/locale\"    -Wall -O2 -D_REENTRANT -c debug.c                                         
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DLOCALEDIR=\"/usr/local/share/locale\" -Wall -O2 -D_REENTRANT -Wp,-MD,.deps/debug.pp -c debug.c  -fPIC -o .libs/debug.o
debug.c: In function 'proz_debug_delete_log':
debug.c:47: error: 'PATH_MAX' undeclared (first use in this function)
debug.c:47: error: (Each undeclared identifier is reported only once
debug.c:47: error: for each function it appears in.)
debug.c:47: warning: unused variable 'logfile_name'
debug.c: In function 'proz_debug':
debug.c:75: error: 'PATH_MAX' undeclared (first use in this function)
debug.c:75: warning: unused variable 'logfile_name'
make[2]: *** [debug.lo] Error 1
make[2]: Leaving directory `/home/chris/Downloads/prozgui-2.0.2/libprozilla/src'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/chris/Downloads/prozgui-2.0.2/libprozilla'
make: *** [install-recursive] Error 1


---

### Post by krzysz00 on 2009-04-05
Did you try searching synaptic for the name of the program?

---

### Post by Coolsaber57 on 2009-04-05
> **krzysz00 said:**
> Did you try searching synaptic for the name of the program?

I did, no dice :/

---

### Post by taurus on 2009-04-05
Did you see the last few lines of the output from "sudo make install"?

```

make[2]: Entering directory `/home/chris/Downloads/prozgui-2.0.2/libprozilla/src'
/bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -DLOCALEDIR=\"/usr/local/share/locale\" -Wall -O2 -D_REENTRANT -c debug.c
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DLOCALEDIR=\"/usr/local/share/locale\" -Wall -O2 -D_REENTRANT -Wp,-MD,.deps/debug.pp -c debug.c -fPIC -o .libs/debug.o
debug.c: In function 'proz_debug_delete_log':
debug.c:47: error: 'PATH_MAX' undeclared (first use in this function)
debug.c:47: error: (Each undeclared identifier is reported only once
debug.c:47: error: for each function it appears in.)
debug.c:47: warning: unused variable 'logfile_name'
debug.c: In function 'proz_debug':
debug.c:75: error: 'PATH_MAX' undeclared (first use in this function)
debug.c:75: warning: unused variable 'logfile_name'
**[COLOR="Red"]make[2]: *** [debug.lo] Error 1[/COLOR]**
make[2]: Leaving directory `/home/chris/Downloads/prozgui-2.0.2/libprozilla/src'
**[COLOR="Red"]make[1]: *** [install-recursive] Error 1[/COLOR]**
make[1]: Leaving directory `/home/chris/Downloads/prozgui-2.0.2/libprozilla'
**[COLOR="Red"]make: *** [install-recursive] Error 1[/COLOR]** 

```

---

### Post by Coolsaber57 on 2009-04-06
> **taurus said:**
> Did you see the last few lines of the output from "sudo make install"?

```

make[2]: Entering directory `/home/chris/Downloads/prozgui-2.0.2/libprozilla/src'
/bin/sh ../libtool --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I.. -DLOCALEDIR=\"/usr/local/share/locale\" -Wall -O2 -D_REENTRANT -c debug.c
gcc -DHAVE_CONFIG_H -I. -I. -I.. -DLOCALEDIR=\"/usr/local/share/locale\" -Wall -O2 -D_REENTRANT -Wp,-MD,.deps/debug.pp -c debug.c -fPIC -o .libs/debug.o
debug.c: In function 'proz_debug_delete_log':
debug.c:47: error: 'PATH_MAX' undeclared (first use in this function)
debug.c:47: error: (Each undeclared identifier is reported only once
debug.c:47: error: for each function it appears in.)
debug.c:47: warning: unused variable 'logfile_name'
debug.c: In function 'proz_debug':
debug.c:75: error: 'PATH_MAX' undeclared (first use in this function)
debug.c:75: warning: unused variable 'logfile_name'
**[COLOR="Red"]make[2]: *** [debug.lo] Error 1[/COLOR]**
make[2]: Leaving directory `/home/chris/Downloads/prozgui-2.0.2/libprozilla/src'
**[COLOR="Red"]make[1]: *** [install-recursive] Error 1[/COLOR]**
make[1]: Leaving directory `/home/chris/Downloads/prozgui-2.0.2/libprozilla'
**[COLOR="Red"]make: *** [install-recursive] Error 1[/COLOR]** 

```

I did see that, but have no idea what they mean.  What do they mean? I'm really not familiar with debugging software too much. I've only done it a few times and i didn't really have any success.  What's error 1 mean?

---

### Post by Coolsaber57 on 2009-04-06
bump, can anyone help?

---

### Post by Christmas on 2009-04-06
OK, I tried this on Jaunty (9.10), but it should work on previous Ubuntu releases too.

I couldn't compile prozgui-2.0.2 or 4beta3 (it may have something to do with incompatible FLTK libraries), but instead you can download the already built binary from [here](http://prozilla.genesys.ro/downloads/prozgui/static/) (the file is called *prozgui-2.0.4beta-static.tar.gz*). Just uncompress it and run it. You may have to install libfltk1.1:
```
sudo apt-get install libfltk1.1
```
After uncompressing it, run it as:
```
./prozgui
```

---

### Post by Coolsaber57 on 2009-04-06
> **Christmas said:**
> OK, I tried this on Jaunty (9.10), but it should work on previous Ubuntu releases too.

I couldn't compile prozgui-2.0.2 or 4beta3 (it may have something to do with incompatible FLTK libraries), but instead you can download the already built binary from [here](http://prozilla.genesys.ro/downloads/prozgui/static/) (the file is called *prozgui-2.0.4beta-static.tar.gz*). Just uncompress it and run it. You may have to install libfltk1.1:
```
sudo apt-get install libfltk1.1
```
After uncompressing it, run it as:
```
./prozgui
```

Thanks man! I'm gonna try this when I get home tonight.

---

### Post by Coolsaber57 on 2009-04-08
Ok, well, I got Prozgui to work, but it's not really what I'm looking for.

Can anyone recommend a program that:

-Monitors the clipboard and/or can import many links at the same time?
-Can use a username/password for specific sites?

Thanks!

---

