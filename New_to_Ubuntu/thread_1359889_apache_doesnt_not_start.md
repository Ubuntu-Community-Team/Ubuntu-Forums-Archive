---
title: "apache doesnt not start"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by sisqonrw on 2009-12-20
hi,

my apache doesnt not start.

it had worked. i wanted to use localhost to install some programms like joomla. i had use it for some weeks but now it doesnt work. i dont no why.

---

### Post by ikt on 2009-12-20
Need to find the apache log file,

checkout in

/var/log/apache2/

some of the log files and see if they mention any errors specific to apache starting.

---

### Post by sisqonrw on 2009-12-20
[http://pastebin.kubuntu-de.org/92](http://pastebin.kubuntu-de.org/92)

---

### Post by Joeb454 on 2009-12-20
```
[Sun Dec 20 14:40:15 2009] [error] Can't locate /usr/share/otrs/scripts/apache2-perl-startup.pl in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.0 /usr/local/share/perl/5.10.0 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl . /etc/apache2) at (eval 2) line 1.\n
```

That's the error you'll need to fix - it looks like there's a perl script missing from /usr/share/otrs/scripts/ which should be named apache2-perl-startup.pl

It looks like otrs is a plugin of some variety for apache, as it isn't on the system I have running apache

---

### Post by sisqonrw on 2009-12-20
what can i do? how can i install it?

---

### Post by ikt on 2009-12-21
> **sisqonrw said:**
> what can i do? how can i install it?

[http://forums.whirlpool.net.au/forum-replies-archive.cfm/1171794.html](http://forums.whirlpool.net.au/forum-replies-archive.cfm/1171794.html)

> Ok, I fixed it.

I installed OTRS2 via apt-get on Friday. It wasn't working very well so I remove it shortly after via apt-get.

Left behind was a config file in /etc/apache2/conf.d called otrs2. I deleted this file and everything is now working again.

---

### Post by sisqonrw on 2009-12-21
Hi,

i wanted to remove otrs2 but i get this error report:

```
 Ein Fehler ist beim Löschen der Datenbank aufgetreten:                      &#8593;
 &#9474;                                                                             &#9646;
 &#9474; psql: FATAL: Passwort-Authentifizierung für Benutzer »root« fehlgeschlagen  &#9618;
 &#9474; FATAL: Passwort-Authentifizierung für Benutzer »root« fehlgeschlagen        &#9618;
 &#9474;                                                                             &#9618;
 &#9474; Falls Sie zu diesem Zeitpunkt die Option »Wiederholen« wählen, werden alle  &#9618;
 &#9474; Konfigurationsfragen noch einmal gestellt und ein erneuter Versuch          &#9618;
 &#9474; vorgenommen, die Operation durchzuführen. Die Option »Wiederholen (Fragen   &#9618;
 &#9474; überspringen)« wird die Operation sofort versuchen und alle Fragen          &#9618;
 &#9474; überspringen. Wenn »Abbruch« gewählt wird, schlägt die Operation fehl und
```

what can i do? can i reset the password?

---

### Post by sisqonrw on 2009-12-21
i set a new passwort with:

mysqladmin -u root -p password "newpassword"now i get this:

```
sudo apt-get remove otrs2
Paketlisten werden gelesen... Fertig               
Abhängigkeitsbaum wird aufgebaut                   
Lese Status-Informationen ein... Fertig            
Paket otrs2 ist nicht installiert, wird also auch nicht entfernt
Die folgenden Pakete wurden automatisch installiert und werden nicht länger benötigt:                                                                               
  libconvert-binhex-perl libmime-tools-perl libio-stringy-perl                    
Verwenden Sie »apt-get autoremove«, um sie zu entfernen.                          
0 aktualisiert, 0 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.       
salsero@salsero-laptop:~$ sudo apt-get install otrs2                              
Paketlisten werden gelesen... Fertig                                              
Abhängigkeitsbaum wird aufgebaut                                                  
Lese Status-Informationen ein... Fertig                                           
Vorgeschlagene Pakete:                                                            
  otrs2-doc-en otrs2-doc-de                                                       
Die folgenden NEUEN Pakete werden installiert:                                    
  otrs2                                                                           
0 aktualisiert, 1 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.       
Es müssen noch 0B von 2.513kB an Archiven heruntergeladen werden.                 
Nach dieser Operation werden 16,1MB Plattenplatz zusätzlich benutzt.              
Vorkonfiguration der Pakete ...                                                   
/tmp/otrs2.config.265111: 50: /usr/share/otrs/bin/otrs.getConfig: not found       
/tmp/otrs2.config.265111: 50: /usr/share/otrs/bin/otrs.getConfig: not found       
/tmp/otrs2.config.265111: 50: /usr/share/otrs/bin/otrs.getConfig: not found       
Wähle vormals abgewähltes Paket otrs2.                                            
(Lese Datenbank ... 422849 Dateien und Verzeichnisse sind derzeit installiert.)   
Entpacke otrs2 (aus .../archives/otrs2_2.3.4-1_all.deb) ...                       
Warnung: Auf das angegebene Benutzerverzeichnis /usr/share/otrs kann nicht zugegriffen werden: No such file or directory                                            
Der Systembenutzer »otrs« existiert bereits. Abbruch.                             
Verarbeite Trigger für ureadahead ...                                             
Richte otrs2 ein (2.3.4-1) ...                                                    
ERROR: No such file or directory: /usr/share/otrs/Kernel/Config/Files/ZZZAAuto.pm 
ERROR: No such file or directory: /usr/share/otrs/Kernel/Config/Files/ZZZAuto.pm  
ERROR: No such file or directory: /usr/share/otrs/Kernel/Config/Files/ZZZAAuto.pm 
ERROR: No such file or directory: /usr/share/otrs/Kernel/Config/Files/ZZZAuto.pm  
ERROR: No such file or directory: /usr/share/otrs/Kernel/Config/Files/ZZZAAuto.pm 
ERROR: No such file or directory: /usr/share/otrs/Kernel/Config/Files/ZZZAuto.pm  
dbconfig-common: writing config to /etc/dbconfig-common/otrs2.conf                
Replacing config file /etc/otrs/database.pm with new version                      
Module perl already enabled                                                       
Module rewrite already enabled                                                    
 * Reloading web server config apache2                                            ERROR: No such file or directory: /usr/share/otrs/Kernel/Config/Files/ZZZAAuto.pm
ERROR: No such file or directory: /usr/share/otrs/Kernel/Config/Files/ZZZAuto.pm
DBI connect('dbname=otrs;host=localhost;port=5432;','otrs',...) failed: fe_sendauth: no password supplied at /usr/share/otrs/Kernel/System/DB.pm line 216
ERROR: OTRS-otrs.RebuildConfig.pl-10 Perl: 5.10.0 OS: linux Time: Mon Dec 21 18:13:35 2009

 Message: fe_sendauth: no password supplied

 Traceback (27089):
   Module: Kernel::System::DB::new (v1.95) Line: 190
   Module: /usr/share/otrs/bin/otrs.RebuildConfig.pl (v1.8) Line: 53

Got no DBObject! at /usr/share/otrs/Kernel/System/Config.pm line 84.
dpkg: Fehler beim Bearbeiten von otrs2 (--configure):
 Unterprozess installiertes post-installation-Skript gab den Fehlerwert 255 zurück
Fehler traten auf beim Bearbeiten von:
 otrs2
E: Sub-process /usr/bin/dpkg returned an error code (1)
salsero@salsero-laptop:~$
```

---

### Post by sisqonrw on 2009-12-24
i dont know why, but apache works:

sudo /etc/init.d/apache2 start
 * Starting web server apache2

---

### Post by sisqonrw on 2010-01-04
i dont know why, but i have to start apache2 and cups manually:

> sudo /etc/init.d/apache2 start
[sudo] password for salsero:
 * Starting web server apache2                                             [ OK ]
salsero@salsero-laptop:~$ sudo /etc/init.d/cups start
 * Starting Common Unix Printing System: cupsd                             [ OK ]

I do this and get this error report:

> sudo /etc/init.d/apache2 start
[sudo] password for salsero:
 * Starting web server apache2                                             [ OK ]
salsero@salsero-laptop:~$ sudo /etc/init.d/cups start
 * Starting Common Unix Printing System: cupsd                             [ OK ]

what is the problem here?

---

### Post by sisqonrw on 2010-01-05
i need professional help.

i see if otrs is not installed apache doesnt work if it is installed it works. see here:

> /etc/init.d/apache2 start
[sudo] password for salsero:                            
 * Starting web server apache2                                                                                                               [fail] 
salsero@salsero-laptop:~$ sudo apt-get install otrs2
Paketlisten werden gelesen... Fertig                
Abhängigkeitsbaum wird aufgebaut                    
Lese Status-Informationen ein... Fertig             
Die folgenden Pakete wurden automatisch installiert und werden nicht länger benötigt:
  libpurple0 libsilc-1.1-2 python-gtksourceview2 gedit-common libgtksourceview2.0-common libgtksourceview2.0-0 python-vte libvte9 apturl
  software-properties-gtk synaptic libvte-common                                                                                        
Verwenden Sie »apt-get autoremove«, um sie zu entfernen.                                                                                
Vorgeschlagene Pakete:                                                                                                                  
  otrs2-doc-en otrs2-doc-de                                                                                                             
Die folgenden NEUEN Pakete werden installiert:                                                                                          
  otrs2                                                                                                                                 
0 aktualisiert, 1 neu installiert, 0 zu entfernen und 0 nicht aktualisiert.                                                             
Es müssen 2.513kB an Archiven heruntergeladen werden.                                                                                   
Nach dieser Operation werden 16,1MB Plattenplatz zusätzlich benutzt.                                                                    
Hole:1 [http://de.archive.ubuntu.com](http://de.archive.ubuntu.com) karmic/universe otrs2 2.3.4-1 [2.513kB]                                                             
Es wurden 2.513kB in 2s geholt (1.249kB/s)                                                                                              
Vorkonfiguration der Pakete ...                                                                                                         
/tmp/otrs2.config.290481: 50: /usr/share/otrs/bin/otrs.getConfig: not found                                                             
/tmp/otrs2.config.290481: 50: /usr/share/otrs/bin/otrs.getConfig: not found                                                             
/tmp/otrs2.config.290481: 50: /usr/share/otrs/bin/otrs.getConfig: not found                                                             
Wähle vormals abgewähltes Paket otrs2.                                                                                                  
(Lese Datenbank ... 354894 Dateien und Verzeichnisse sind derzeit installiert.)                                                         
Entpacke otrs2 (aus .../archives/otrs2_2.3.4-1_all.deb) ...                                                                             
Warnung: Auf das angegebene Benutzerverzeichnis /usr/share/otrs kann nicht zugegriffen werden: No such file or directory                
Der Systembenutzer »otrs« existiert bereits. Abbruch.                                                                                   
Verarbeite Trigger für ureadahead ...                                                                                                   
Richte otrs2 ein (2.3.4-1) ...                                                                                                          
ERROR: No such file or directory: /usr/share/otrs/Kernel/Config/Files/ZZZAAuto.pm                                                       
ERROR: No such file or directory: /usr/share/otrs/Kernel/Config/Files/ZZZAuto.pm                                                        
ERROR: No such file or directory: /usr/share/otrs/Kernel/Config/Files/ZZZAAuto.pm                                                       
ERROR: No such file or directory: /usr/share/otrs/Kernel/Config/Files/ZZZAuto.pm                                                        
ERROR: No such file or directory: /usr/share/otrs/Kernel/Config/Files/ZZZAAuto.pm                                                       
ERROR: No such file or directory: /usr/share/otrs/Kernel/Config/Files/ZZZAuto.pm                                                        
dbconfig-common: writing config to /etc/dbconfig-common/otrs2.conf                                                                      
Replacing config file /etc/otrs/database.pm with new version                                                                            
Module perl already enabled                                                                                                             
Module rewrite already enabled                                                                                                          
 * Reloading web server config apache2                                                                                                              ERROR: No such file or directory: /usr/share/otrs/Kernel/Config/Files/ZZZAAuto.pm                                                                   
ERROR: No such file or directory: /usr/share/otrs/Kernel/Config/Files/ZZZAuto.pm
DBI connect('dbname=otrs;host=localhost;port=5432;','otrs',...) failed: fe_sendauth: no password supplied at /usr/share/otrs/Kernel/System/DB.pm line 216
ERROR: OTRS-otrs.RebuildConfig.pl-10 Perl: 5.10.0 OS: linux Time: Tue Jan  5 09:37:21 2010

 Message: fe_sendauth: no password supplied

 Traceback (30111):
   Module: Kernel::System::DB::new (v1.95) Line: 190
   Module: /usr/share/otrs/bin/otrs.RebuildConfig.pl (v1.8) Line: 53

Got no DBObject! at /usr/share/otrs/Kernel/System/Config.pm line 84.
dpkg: Fehler beim Bearbeiten von otrs2 (--configure):
 Unterprozess installiertes post-installation-Skript gab den Fehlerwert 255 zurück
Fehler traten auf beim Bearbeiten von:
 otrs2
E: Sub-process /usr/bin/dpkg returned an error code (1)
salsero@salsero-laptop:~$ sudo /etc/init.d/apache2 start
 * Starting web server apache2    

what can i do?

---

### Post by freackout on 2010-01-08
apache uses the /var/www
xampp & joomla is /opt/lampp/htdocs/joomla
or wherever you extracted the joomla to...
ie:- your apache is intsalled twice and the apache config file tells you where to go for it.
point it to the correct location. or create a link ie:-
sudo ln -s ~/public_html /opt/lampp/htdocs/$USER
if your index files you wish to use are for instance in the home public_html directory.
thus you would use if your name was tom
(in the browser) localhost/tom

---

### Post by sisqonrw on 2010-01-08
hi i dont use xampp & joomla.

i have a otrs, apache2 and cups problem and not xampp and joomla problem.

so what can i do to fix this problem.

thanks

---

