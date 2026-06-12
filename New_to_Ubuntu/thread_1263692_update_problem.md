---
title: "update problem"
date: 2009-09-11
forum: New to Ubuntu
---

### Post by Daniel1994 on 2009-09-11
Hey, I've been having a lot of trouble with my updates for a while now. It's updating, but I'm getting alot of errors also. 

I've posted the output here, it's in norwegian, so I'll just write a short translation:
Funnet=Found
Klarte ikke koble til= Could not connect
Hented=Fetched
Leser pakkelister=Reading package lists
Klarte ikke skaffe=Could not get
Klarte ikke å laste ned alle oversiktfilene. De ble ignorerte, eller gamle ble brukt isteden. = Could not download alle the overview files. They were ignored, or old ones were used instead.
Det kan hende du vil kjøre «apt-get update» for å rette på disse problemene= You migth wanna run "apt-get update" to fix these problems.(PS: This does not work)

Appreciate any help 

```

daniel@daniel-laptop:~$ sudo apt-get update
Feil http://wine.budgetdedicated.com jaunty Release.gpg
  Klarte ikke å koble til wine.budgetdedicated.com:80 (81.171.111.247). - connect (111 Connection refused)
Funnet http://no.archive.ubuntu.com jaunty Release.gpg                                           
Funnet http://no.archive.ubuntu.com jaunty/main Translation-nb                                                                        
Funnet http://deb.opera.com stable Release.gpg                                                                                        
Ign http://deb.opera.com stable/non-free Translation-nb                                                                                                  
Funnet http://deb.opera.com stable Release.gpg                                                                                                           
Ign http://deb.opera.com stable/non-free Translation-nb                                                                                                  
Funnet http://no.archive.ubuntu.com jaunty/restricted Translation-nb                                                                                     
Funnet http://no.archive.ubuntu.com jaunty/universe Translation-nb                                                                                       
Funnet http://no.archive.ubuntu.com jaunty/multiverse Translation-nb                                                                                     
Funnet http://no.archive.ubuntu.com jaunty-updates Release.gpg                                                                                           
Ign http://no.archive.ubuntu.com jaunty-updates/main Translation-nb                                                                                      
Ign http://no.archive.ubuntu.com jaunty-updates/restricted Translation-nb                                                                                
Funnet http://deb.opera.com stable Release                                                                                                               
Ign http://no.archive.ubuntu.com jaunty-updates/universe Translation-nb                                                                                  
Ign http://no.archive.ubuntu.com jaunty-updates/multiverse Translation-nb                                                                                
Funnet http://no.archive.ubuntu.com jaunty-security Release.gpg                                                                                          
Ign http://no.archive.ubuntu.com jaunty-security/main Translation-nb                                                                                     
Ign http://no.archive.ubuntu.com jaunty-security/restricted Translation-nb                                                                               
Funnet http://archive.canonical.com jaunty Release.gpg                                                                                                   
Ign http://archive.canonical.com jaunty/partner Translation-nb                                                                                           
Ign http://ppa.launchpad.net hardy Release.gpg                                                                                                           
Ign http://ppa.launchpad.net hardy/main Translation-nb                                                                                                   
Funnet http://packages.medibuntu.org hardy Release.gpg                                                                                                   
Ign http://packages.medibuntu.org hardy/free Translation-nb                                                                                              
Funnet http://deb.opera.com stable Release                                                                                                               
Feil http://wine.budgetdedicated.com jaunty/main Translation-nb                                                                                          
  Klarte ikke å koble til wine.budgetdedicated.com:80 (81.171.111.247). - connect (111 Connection refused)
Funnet http://ppa.launchpad.net jaunty Release.gpg                                                                                                          
Ign http://ppa.launchpad.net jaunty/main Translation-nb                                                                                                     
Funnet http://ppa.launchpad.net jaunty Release.gpg                                                                                                          
Ign http://ppa.launchpad.net jaunty/main Translation-nb                                                                                                     
Ign http://no.archive.ubuntu.com jaunty-security/universe Translation-nb                                                                                    
Ign http://no.archive.ubuntu.com jaunty-security/multiverse Translation-nb                                                                                  
Funnet http://no.archive.ubuntu.com jaunty Release                                                                                                          
Ign http://packages.medibuntu.org hardy/non-free Translation-nb                                                                                             
Ign http://deb.opera.com stable/non-free Packages                                                                                                           
Feil http://wine.budgetdedicated.com intrepid Release.gpg                                                                                                   
  Klarte ikke å koble til wine.budgetdedicated.com:80 (81.171.111.247). - connect (111 Connection refused)
Funnet http://archive.canonical.com jaunty Release                                                                                                          
Hent:1 http://ppa.launchpad.net hardy Release [27,6kB]                                            
Funnet http://packages.medibuntu.org hardy Release                                                  
Funnet http://no.archive.ubuntu.com jaunty-updates Release                                          
Funnet http://no.archive.ubuntu.com jaunty-security Release                      
Funnet http://deb.opera.com stable/non-free Packages                             
Ign http://deb.opera.com stable/non-free Packages             
Funnet http://ppa.launchpad.net jaunty Release                                   
Funnet http://ppa.launchpad.net jaunty Release                                   
Funnet http://deb.opera.com stable/non-free Packages                             
Funnet http://no.archive.ubuntu.com jaunty/main Packages                         
Funnet http://no.archive.ubuntu.com jaunty/restricted Packages                   
Ign http://ppa.launchpad.net hardy/main Packages            
Funnet http://archive.canonical.com jaunty/partner Packages                                         
Funnet http://no.archive.ubuntu.com jaunty/universe Packages                                        
Funnet http://no.archive.ubuntu.com jaunty/multiverse Packages                                      
Funnet http://packages.medibuntu.org hardy/free Packages                                            
Funnet http://ppa.launchpad.net hardy/main Packages                                                 
Funnet http://archive.canonical.com jaunty/partner Sources                       
Funnet http://no.archive.ubuntu.com jaunty-updates/main Packages               
Funnet http://no.archive.ubuntu.com jaunty-updates/restricted Packages
Funnet http://no.archive.ubuntu.com jaunty-updates/universe Packages
Funnet http://no.archive.ubuntu.com jaunty-updates/multiverse Packages
Funnet http://ppa.launchpad.net jaunty/main Packages        
Funnet http://ppa.launchpad.net jaunty/main Sources         
Funnet http://no.archive.ubuntu.com jaunty-security/main Packages
Funnet http://no.archive.ubuntu.com jaunty-security/restricted Packages
Funnet http://no.archive.ubuntu.com jaunty-security/universe Packages
Funnet http://no.archive.ubuntu.com jaunty-security/multiverse Packages
Funnet http://packages.medibuntu.org hardy/non-free Packages
Funnet http://packages.medibuntu.org hardy/free Sources
Funnet http://packages.medibuntu.org hardy/non-free Sources
Ign http://ppa.launchpad.net jaunty/main Packages
Funnet http://ppa.launchpad.net jaunty/main Packages
Hentet 1B på 0s (2B/s)
Leser pakkelister ... Ferdig
W: Klarte ikke å skaffe http://wine.budgetdedicated.com/apt/dists/jaunty/Release.gpg  Klarte ikke å koble til wine.budgetdedicated.com:80 (81.171.111.247). - connect (111 Connection refused)

W: Klarte ikke å skaffe http://wine.budgetdedicated.com/apt/dists/jaunty/main/i18n/Translation-nb.bz2  Klarte ikke å koble til wine.budgetdedicated.com:80 (81.171.111.247). - connect (111 Connection refused)

W: Klarte ikke å skaffe http://wine.budgetdedicated.com/apt/dists/intrepid/Release.gpg  Klarte ikke å koble til wine.budgetdedicated.com:80 (81.171.111.247). - connect (111 Connection refused)

W: Klarte ikke å laste ned alle oversiktfilene. De ble ignorerte, eller gamle ble brukt isteden. 
W: Det kan hende du vil kjøre «apt-get update» for å rette på disse problemene
daniel@daniel-laptop:~$ 

```

---

### Post by grotesk on 2009-09-11
wine.budgetdedicated.com has been down for a few days. That is a system run by a third party developer and not supported by Ubuntu.

You can disable that repository in System>Administration>Software Sources which should suppress the error message for now.

There's a forum post for the Wine project on the matter here:
[http://forum.winehq.org/viewtopic.php?t=5997](http://forum.winehq.org/viewtopic.php?t=5997)

---

### Post by Daniel1994 on 2009-09-11
thanks:popcorn:

---

