---
title: "Destroying private data."
date: 2009-03-11
forum: New to Ubuntu
---

### Post by waxyfresh on 2009-03-11
I have decided to deleted my pidgin logs,how can i,make sure they cant be recovered?

---

### Post by waxyfresh on 2009-03-11
Bump? ive found a program called scrub but i gt errors when i install it:
Sorry for bumping so soon but time is of the essence here.
> david@IceWeasel:~/Desktop/scrub-2.1$ dir                                                                                                           
AUTHORS    ChangeLog  configure     COPYING     htdocs   Makefile.am  META  README      src                                                        
bootstrap  config     configure.ac  DISCLAIMER  INSTALL  Makefile.in  NEWS  scrub.spec  test                                                       
david@IceWeasel:~/Desktop/scrub-2.1$ ./config                                                                                                      
bash: ./config: is a directory                                                                                                                     
david@IceWeasel:~/Desktop/scrub-2.1$ ./configure                                                                                                   
checking build system type... i686-pc-linux-gnu                                                                                                    
checking host system type... i686-pc-linux-gnu                                                                                                     
checking target system type... i686-pc-linux-gnu                                                                                                   
checking for a BSD-compatible install... /usr/bin/install -c                                                                                       
checking whether build environment is sane... yes                                                                                                  
checking for gawk... gawk                                                                                                                          
checking whether make sets $(MAKE)... yes                                                                                                          
checking whether to enable maintainer-specific portions of Makefiles... no                                                                         
checking for gcc... gcc                                                                                                                            
checking for C compiler default output file name... a.out                                                                                          
checking whether the C compiler works... yes                                                                                                       
checking whether we are cross compiling... no                                                                                                      
checking for suffix of executables...                                                                                                              
checking for suffix of object files... o                                                                                                           
checking whether we are using the GNU C compiler... yes                                                                                            
checking whether gcc accepts -g... yes                                                                                                                          
checking for gcc option to accept ANSI C... none needed                                                                                                         
checking for style of include used by make... GNU                                                                                                               
checking dependency style of gcc... gcc3                                                                                                                        
checking how to run the C preprocessor... gcc -E                                                                                                                
checking for egrep... grep -E                                                                                                                                   
checking for ANSI C header files... yes                                                                                                                         
checking for sys/types.h... yes                                                                                                                                 
checking for sys/stat.h... yes                                                                                                                                  
checking for stdlib.h... yes                                                                                                                                    
checking for string.h... yes                                                                                                                                    
checking for memory.h... yes                                                                                                                                    
checking for strings.h... yes                                                                                                                                   
checking for inttypes.h... yes                                                                                                                                  
checking for stdint.h... yes                                                                                                                                    
checking for unistd.h... yes                                                                                                                                    
checking getopt.h usability... yes                                                                                                                              
checking getopt.h presence... yes                                                                                                                               
checking for getopt.h... yes                                                                                                                                    
checking whether byte ordering is bigendian... no                                                                                                               
checking for an ANSI C-conforming const... yes                                                                                                                  
checking for getopt_long... yes                                                                                                                                 
checking for special C compiler options needed for large files... no                                                                                            
checking for _FILE_OFFSET_BITS value needed for large files... 64                                                                                               
checking for _LARGE_FILES value needed for large files... no                                                                                                    
configure: creating ./config.status                                                                                                                             
config.status: creating Makefile                                                                                                                                
config.status: creating src/Makefile                                                                                                                            
config.status: creating test/Makefile                                                                                                                           
config.status: creating config/config.h                                                                                                                         
config.status: executing depfiles commands                                                                                                                      
david@IceWeasel:~/Desktop/scrub-2.1$ scru                                                                                                                       
bash: scru: command not found                                                                                                                                   
david@IceWeasel:~/Desktop/scrub-2.1$ scrub                                                                                                                      
bash: scrub: command not found                                                                                                                                  
david@IceWeasel:~/Desktop/scrub-2.1$ make                                                                                                                       
Making all in src                                                                                                                                               
make[1]: Entering directory `/home/david/Desktop/scrub-2.1/src'                                                                                                 
if gcc -DHAVE_CONFIG_H -I. -I/home/david/Desktop/scrub-2.1/src -I../config     -g -O2 -MT aes.o -MD -MP -MF ".deps/aes.Tpo" -c -o aes.o aes.c; \                
        then mv -f ".deps/aes.Tpo" ".deps/aes.Po"; else rm -f ".deps/aes.Tpo"; exit 1; fi                                                                       
if gcc -DHAVE_CONFIG_H -I. -I/home/david/Desktop/scrub-2.1/src -I../config     -g -O2 -MT filldentry.o -MD -MP -MF ".deps/filldentry.Tpo" -c -o filldentry.o filldentry.c; \                                                                                                                                                    
        then mv -f ".deps/filldentry.Tpo" ".deps/filldentry.Po"; else rm -f ".deps/filldentry.Tpo"; exit 1; fi                                                  
if gcc -DHAVE_CONFIG_H -I. -I/home/david/Desktop/scrub-2.1/src -I../config     -g -O2 -MT fillfile.o -MD -MP -MF ".deps/fillfile.Tpo" -c -o fillfile.o fillfile.c; \                                                                                                                                                            
        then mv -f ".deps/fillfile.Tpo" ".deps/fillfile.Po"; else rm -f ".deps/fillfile.Tpo"; exit 1; fi                                                        
if gcc -DHAVE_CONFIG_H -I. -I/home/david/Desktop/scrub-2.1/src -I../config     -g -O2 -MT genrand.o -MD -MP -MF ".deps/genrand.Tpo" -c -o genrand.o genrand.c; \
        then mv -f ".deps/genrand.Tpo" ".deps/genrand.Po"; else rm -f ".deps/genrand.Tpo"; exit 1; fi                                                           
if gcc -DHAVE_CONFIG_H -I. -I/home/david/Desktop/scrub-2.1/src -I../config     -g -O2 -MT getsize.o -MD -MP -MF ".deps/getsize.Tpo" -c -o getsize.o getsize.c; \
        then mv -f ".deps/getsize.Tpo" ".deps/getsize.Po"; else rm -f ".deps/getsize.Tpo"; exit 1; fi                                                           
if gcc -DHAVE_CONFIG_H -I. -I/home/david/Desktop/scrub-2.1/src -I../config     -g -O2 -MT pattern.o -MD -MP -MF ".deps/pattern.Tpo" -c -o pattern.o pattern.c; \
        then mv -f ".deps/pattern.Tpo" ".deps/pattern.Po"; else rm -f ".deps/pattern.Tpo"; exit 1; fi                                                           
if gcc -DHAVE_CONFIG_H -I. -I/home/david/Desktop/scrub-2.1/src -I../config     -g -O2 -MT progress.o -MD -MP -MF ".deps/progress.Tpo" -c -o progress.o progress.c; \                                                                                                                                                            
        then mv -f ".deps/progress.Tpo" ".deps/progress.Po"; else rm -f ".deps/progress.Tpo"; exit 1; fi                                                        
if gcc -DHAVE_CONFIG_H -I. -I/home/david/Desktop/scrub-2.1/src -I../config     -g -O2 -MT scrub.o -MD -MP -MF ".deps/scrub.Tpo" -c -o scrub.o scrub.c; \        
        then mv -f ".deps/scrub.Tpo" ".deps/scrub.Po"; else rm -f ".deps/scrub.Tpo"; exit 1; fi                                                                 
if gcc -DHAVE_CONFIG_H -I. -I/home/david/Desktop/scrub-2.1/src -I../config     -g -O2 -MT sig.o -MD -MP -MF ".deps/sig.Tpo" -c -o sig.o sig.c; \                
        then mv -f ".deps/sig.Tpo" ".deps/sig.Po"; else rm -f ".deps/sig.Tpo"; exit 1; fi                                                                       
if gcc -DHAVE_CONFIG_H -I. -I/home/david/Desktop/scrub-2.1/src -I../config     -g -O2 -MT util.o -MD -MP -MF ".deps/util.Tpo" -c -o util.o util.c; \            
        then mv -f ".deps/util.Tpo" ".deps/util.Po"; else rm -f ".deps/util.Tpo"; exit 1; fi                                                                    
gcc  -g -O2   -o scrub  aes.o filldentry.o fillfile.o genrand.o getsize.o pattern.o progress.o scrub.o sig.o util.o                                             
make[1]: Leaving directory `/home/david/Desktop/scrub-2.1/src'                                                                                                  
Making all in test                                                                                                                                              
make[1]: Entering directory `/home/david/Desktop/scrub-2.1/test'                                                                                                
make[1]: Nothing to be done for `all'.                                                                                                                          
make[1]: Leaving directory `/home/david/Desktop/scrub-2.1/test'                                                                                                 
make[1]: Entering directory `/home/david/Desktop/scrub-2.1'                                                                                                     
make[1]: Nothing to be done for `all-am'.                                                                                                                       
make[1]: Leaving directory `/home/david/Desktop/scrub-2.1'                                                                                                      
david@IceWeasel:~/Desktop/scrub-2.1$ scrub                                                                                                                      
bash: scrub: command not found                                                                                                                                  
david@IceWeasel:~/Desktop/scrub-2.1$ make install                                                                                                               
Making install in src                                                                                                                                           
make[1]: Entering directory `/home/david/Desktop/scrub-2.1/src'                                                                                                 
make[2]: Entering directory `/home/david/Desktop/scrub-2.1/src'                                                                                                 
test -z "/usr/local/bin" || mkdir -p -- "/usr/local/bin"                                                                                                        
  /usr/bin/install -c 'scrub' '/usr/local/bin/scrub'                                                                                                            
/usr/bin/install: cannot create regular file `/usr/local/bin/scrub': Permission denied                                                                          
make[2]: *** [install-binPROGRAMS] Error 1
make[2]: Leaving directory `/home/david/Desktop/scrub-2.1/src'
make[1]: *** [install-am] Error 2
make[1]: Leaving directory `/home/david/Desktop/scrub-2.1/src'
make: *** [install-recursive] Error 1


---

### Post by stanz on 2009-03-11
bypass the trash...anything more secure--I think goes into wiping software.

best I can offer...    ;)

Would you please include more info on that software... a link to their website,
would be a start. Which one you downloaded and tried to install too.

have you searched thru synaptic package manager?
googled thru these forums--to see what others are using (that installed on Ubuntu)?

Thanks

---

### Post by waxyfresh on 2009-03-11
[http://www.cyberciti.biz/tips/linux-unix-make-retrieving-data-more-difficult.html](http://www.cyberciti.biz/tips/linux-unix-make-retrieving-data-more-difficult.html) 

I could not find anything in synaptic. this is the one i downloaded fromthat site: [http://downloads.sourceforge.net/diskscrub/scrub-2.1.tar.bz2?use_mirror=voxel](http://downloads.sourceforge.net/diskscrub/scrub-2.1.tar.bz2?use_mirror=voxel)

---

### Post by Paqman on 2009-03-11
Try the command shred:
```

shred -u -n3 /path/to/file

```

This will overwrite the file three times then remove it. That's secure enough to defeat even heroic data-recovery efforts.

---

### Post by mkvnmtr on 2009-03-11
I believe the package shread and the package wipe are in the repositories. I thing shread is included in a regular Ubuntu install.

---

### Post by waxyfresh on 2009-03-11
how would i use shread to delete an entie folder,just shread /foldername/?

---

### Post by stanz on 2009-03-11
> **mkvnmtr said:**
> I believe the package shread and the package wipe are in the repositories. I thing shread is included in a regular Ubuntu install.
I found wipe--and it has 'man' pages: "man wipe"
couldn't find shread :)

read well waxy!!

---

### Post by Paqman on 2009-03-12
> **waxyfresh said:**
> how would i use shread to delete an entie folder,just shread /foldername/?

```

shred -n3 -u /path/to/folder/*

```

That will shred everything inside the folder, then just delete the empty folder. To get the right path to the file you can hit TAB to autocomplete the folder names, btw.

Shred is installed by default IIRC, if not it's part of the package secure-delete.

---

### Post by aeiah on 2009-03-12
scrub didnt install because it didnt have the right permissions. for make install you need to run as root

```
sudo make install
```

---

### Post by Helios1276 on 2009-03-12
what about srm? 

[http://en.wikipedia.org/wiki/Srm_%E2%80%93_Secure_Remove](http://en.wikipedia.org/wiki/Srm_%E2%80%93_Secure_Remove)

---

### Post by Paqman on 2009-03-12
Seriously, shred is already installed.

You absolutely do not need to overwrite your data dozens of times like some of these utilities will. One of the nice things about shred is that you can set the number of writes to a sensible number (like 3, or 1) and save yourself a load of time. A lot of these tools will spend ages doing pointless writes. It's no more secure to do 35 writes than 3, wastes time, and increases wear on your drive.

---

### Post by HermanAB on 2009-03-12
The problem is that with a journaled file system like ext3, there is no guarantee that the overwrites actually do what you want.  The data may still be readable in a journal no matter how many times you overwrite the files.  There may also be copies in the swap partition.

This is why the only secure way to erase a disk is to encrypt it and when you want to erase it, forget the key.

Cheers,

Herman

---

### Post by redseventyseven on 2009-03-12
> **stanz said:**
> I found wipe--and it has 'man' pages: "man wipe"
couldn't find shread :)

read well waxy!!

You probably couldn't find *shred* because it hasn't got an "a" in it. :)

---

### Post by sdowney717 on 2009-03-12
> 
This is why the only secure way to erase a disk is to encrypt it and when you want to erase it, forget the key.

What about encrypting a directory.
How would you encrypt your home directory?
would this slow down the system?

---

### Post by hyper_ch on 2009-03-12
encryption is only noticeable if you read/write large chunks of data at the same time. During "normal" operations you won't really notice anything.

As for only encrypting a directory - this also depends again because of the journaled file system. If you're worried, just go for full disk encryption then you are (sort of) worry-free.

---

### Post by LowSky on 2009-03-12
> **waxyfresh said:**
> I have decided to deleted my pidgin logs,how can i,make sure they cant be recovered?

I like how everyone is suggesting  this way over that, but no one has asked why.. I like to know why!
But also, what if the person you were talking to also kept logs, what about the system server you used to hold the conversation? You cant erase those...unless you have access, not to mention if the log contains your IP address then they know where you are... got to love BIG Brother!

Are you afraid some agency is going to grab your computer to use it for evidence?

Just wanted to instill some extra fear..

---

### Post by waxyfresh on 2009-03-12
> **HermanAB said:**
> The problem is that with a journaled file system like ext3, there is no guarantee that the overwrites actually do what you want.  The data may still be readable in a journal no matter how many times you overwrite the files.  There may also be copies in the swap partition.

This is why the only secure way to erase a disk is to encrypt it and when you want to erase it, forget the key.

Cheers,

Herman

So theres no way short of formating,reinstalling and setting up encryption? theres alot of data id rather not loose an backing up would take a few hundred dvds,this seems like alot of work to simply remove pidgin logs. I do not know what kind of technology is availible to those who might want access to my hard drive,but at the very least my local DEA is definitely interested,the feds may also be interested but this is *hopefully* just healthy paranoia.

Where does pidgin store its logs? i cant seem to find it in my home folder,isnt that where Gaim stored theres?

---

### Post by waxyfresh on 2009-03-13
bump^

---

### Post by stanz on 2009-03-13
> Instant messages will only be logged if the "Log all instant messages" preference is enabled.
Tools->Preferences--> [COLOR=DarkRed]*make your changes...*[/COLOR]

;)

---

### Post by stanz on 2009-03-13
> **redseventyseven said:**
> You probably couldn't find *shred* because it hasn't got an "a" in it. :)
Ha ~ !       :guitar:

---

### Post by Andrew.Z on 2009-06-09
> **waxyfresh said:**
> I have decided to deleted my pidgin logs,how can i,make sure they cant be recovered?

[BleachBit 0.5.2](http://bleachbit.sourceforge.net[/url) has an option to shred any file from a convenient GUI.  Earlier I wanted to add Pidgin cleaning as a checkbox, but I couldn't find the files until today (they are listed under the old name gaim).  I'll add Pidgin and GAIM cleaning in a release soon--probably 0.5.2.

> **HermanAB said:**
> The problem is that with a journaled file system like ext3, there is no guarantee that the overwrites actually do what you want.  The data may still be readable in a journal no matter how many times you overwrite the files.  There may also be copies in the swap partition.

The [shred man page](http://unixhelp.ed.ac.uk/CGI/man-cgi?shred+1) is not quite so gloomy.  [Shredding is generally effective](http://bleachbit.blogspot.com/2009/06/validating-secure-erase.html) on Ubuntu's default file system.  For cases where the journal writes data in a new place, I heard bcwipe erases that data, and you can get a similar effect with

```

dd if=/dev/zero of=/home/myusername/bigfile bs=1M count=10000
rm /home/myusername/bigfile

```

---

