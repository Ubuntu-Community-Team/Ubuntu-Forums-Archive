---
title: "trouble installing icecat"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by akfred on 2009-05-04
I know this problem has probably been raised more than a few times.  I downloaded Icecat 3.0.9 and undid the tar ball.  Tried to run install but am having no luck.  Did a sudo get update the a sudo upgrade and install but just get errors.

sudo apt-get upgrade
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
$ sudo apt-get install  libxt-dev
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
There is not an executable file for named icecat or anyother exe file.  I did a ./configure but could not get an exe file or much in the way of anything.

I have a little experience with ubuntu but not much.  Using 9.0.4.

Thanks

---

### Post by Master_Odin on 2009-05-04
The errors you're getting are indicating you have another process handling upgrading/installing/etc open such as running Synaptic Package Manager. Close it and try again.

---

### Post by akfred on 2009-05-05
Tried to install again but with no luck.  Here's what the directory has in it.

accessible       config        gfx          nsprpub         sun-java
aclocal.m4       config.cache  intl         parser          testing
allmakefiles.sh  config.log    ipc          plugin          toolkit
a.out            configure     jpeg         probes          tools
browser          configure.in  js           profile         uriloader
build            content       layout       rdf             view
calendar         db            LEGAL        README          webshell
camino.mk        dbm           LICENSE      README.ICECAT   widget
caps             docshell      mail         README.txt      xpcom
ChangeLog        dom           Makefile.in  remove.nonfree  xpfe
chrome           editor        memory       security        xpinstall
client.mk        embedding     modules      storage         xulrunner
confdefs.h       extensions    netwerk      suite

I can not find any file that is an exe or will allow me to install icecat.  I have tried to make, configure, just about all I can think of "ok all I can think of".  Nothing else is running.

AkFred

---

### Post by neu2buntu on 2009-05-05
use```
 cd
``` command to goto the directory and run code ```
./run-icecat.sh
```

---

### Post by neu2buntu on 2009-05-05
update.....  this is only running icecat from inside the folder....  it does not actually install it....ooops,... i will take another look at the files to see if i can see how to install

---

### Post by neu2buntu on 2009-05-05
reading up on an older version it seems it can be installed statically to the /opt directory, this should just be a case of moving the folder here...   follow this [SIZE=3][COLOR=Red][link]("http://www.linuxconfig.org/GNU_IceCat#Installation") [COLOR=Black][SIZE=1]here and cahnge the name of the folder in the commands to the name of youre ie icecat-3.0.9-g1-i386.....[/SIZE][/COLOR][/COLOR][/SIZE]

---

### Post by akfred on 2009-05-05
Tried the run command but no such luck.  Tried in the icecat and my directory but the file is not found.  I downloaded it as a tar ball but it must not be complete.  I may need to try downloading it again. 

AkFred

---

### Post by akfred on 2009-05-05
Tried the link and did what is said but no luck.
Here's what the terminal output is..

greg@greg-laptop:~$ apt-get install lzma
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
greg@greg-laptop:~$ cd icecat
greg@greg-laptop:~/icecat$ icecat &
[1] 3932
greg@greg-laptop:~/icecat$ bash: icecat: command not found
ls
accessible         config          gfx            nsprpub           sun-java
aclocal.m4         config.cache    intl           parser            testing
allmakefiles.sh    config.log      ipc            plugin            toolkit
a.out              configure       jpeg           probes            tools
browser            configure.in    js             profile           uriloader
build              content         layout         rdf               view
calendar           db              LEGAL          README            webshell
camino.mk          dbm             LICENSE        README.ICECAT     widget
caps               docshell        mail           README.txt        xpcom
ChangeLog          dom             Makefile.in    remove.nonfree    xpfe
chrome             editor          memory         security          xpinstall
client.mk          embedding       modules        storage           xulrunner
confdefs.h         extensions      netwerk        suite
[1]+  Exit 127                icecat
greg@greg-laptop:~/icecat$ 

The icecat that you see is not really there.  I still get the same output of can not open but there is nothing else running, I did a cold restart and went right into terminal so nothing else was running.

AkFred

---

### Post by neu2buntu on 2009-05-06
i should have specified the commands to run i will do it for you now ( you already have the folder extracted,so if it is not in your home folder move it now)  
```
sudo mv icecat-3.0.9-g1-i386 /opt/icecat
``` this copies icecat to the /opt dir (make sure this is the exact name of icecat)
```
sudo apt-get install gnash
``` (this is needed to view flash)
```
sudo ln -s /usr/lib/gnash/* /opt/icecat/plugins
``` (symbolic link to gnash)
that should now be icecat installed , so now to run we need to run this in terminal (you can also make a panel or desktop launcher for this command)
```
/opt/icecat/icecat &
```   thats it ,really easy!!!

update... to get flash working i had to link icecats plugin folder with firefox flashplayer (worked this out myself) there probably is another way of doing it (1) i know of is to install gnash-0.8.5 from source.. obviously you will need firefox setup to play flash already...  do this code then restart icecat and we should be good to go ```
sudo ln -s /usr/lib/firefox/plugins/flashplugin-alternative.so /opt/icecat/plugins
```

---

