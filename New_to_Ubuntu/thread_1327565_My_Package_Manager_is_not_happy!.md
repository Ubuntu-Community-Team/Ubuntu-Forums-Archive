---
title: "My Package Manager is not happy!"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by chertsey on 2009-11-15
I'm getting an error message connected with my Package Manager.  
 

 “Error:Opening the cache (E=Encountered a section with no Package: header, E: Problem with MergeList /var/lib/apt/lists/
 gb.archive.ubuntu.com_dists_jaunty_universe_binary-i386_Packages, E the lists or status file could not be parsed or opened.)”
 This usually means that your installed packages have unmet dependencies
 

 After doing a search here I found this thread which seems exactly the problem I'm getting:
 

 [http://ubuntuforums.org/showthread.php?t=1203189](http://ubuntuforums.org/showthread.php?t=1203189) 
 

 I've followed the suggestions posted there and unfortunately it's just the same.  
 

 After changing the software source I had this:
 sudo apt-get update && sudo apt-get install -f
 

 sudo apt-get update && sudo apt-get install -f 
 [sudo] password for bill:  
 Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release.gpg 
 Ign [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Translation-en_GB 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty Release.gpg  
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty/main Translation-en_GB 
 Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty Release 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty/restricted Translation-en_GB 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty/universe Translation-en_GB 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty/multiverse Translation-en_GB 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-updates Release.gpg 
 Ign [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-updates/main Translation-en_GB 
 Ign [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-updates/restricted Translation-en_GB 
 Ign [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-updates/universe Translation-en_GB 
 Ign [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-updates/multiverse Translation-en_GB 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-security Release.gpg 
 Ign [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-security/main Translation-en_GB 
 Hit [http://archive.canonical.com](http://archive.canonical.com) jaunty/partner Packages 
 Ign [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-security/restricted Translation-en_GB 
 Ign [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-security/universe Translation-en_GB 
 Ign [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-security/multiverse Translation-en_GB 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-backports Release.gpg 
 Ign [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-backports/main Translation-en_GB 
 Ign [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-backports/restricted Translation-en_GB 
 Ign [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-backports/universe Translation-en_GB 
 Ign [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-backports/multiverse Translation-en_GB 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-proposed Release.gpg 
 Ign [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-proposed/restricted Translation-en_GB 
 Ign [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-proposed/main Translation-en_GB 
 Ign [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-proposed/multiverse Translation-en_GB 
 Ign [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-proposed/universe Translation-en_GB 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty Release 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-updates Release 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-security Release 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-backports Release 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-proposed Release 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty/main Packages 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty/restricted Packages 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty/main Sources 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty/restricted Sources 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty/universe Packages 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty/universe Sources 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty/multiverse Packages 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty/multiverse Sources 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-updates/main Packages 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-updates/restricted Packages 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-updates/main Sources 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-updates/restricted Sources 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-updates/universe Packages 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-updates/universe Sources 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-updates/multiverse Packages 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-updates/multiverse Sources 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-security/main Packages 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-security/restricted Packages 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-security/main Sources 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-security/restricted Sources 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-security/universe Packages 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-security/universe Sources 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-security/multiverse Packages 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-security/multiverse Sources 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-backports/main Packages 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-backports/restricted Packages 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-backports/universe Packages 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-backports/multiverse Packages 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-proposed/restricted Packages 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-proposed/main Packages 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-proposed/multiverse Packages 
 Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) jaunty-proposed/universe Packages 
 Reading package lists... Error! 
 E: Encountered a section with no Package: header 
 E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_jaunty_partner_binary-i386_Packages 
 E: The package lists or status file could not be parsed or opened. 
 

 

 Can anyone offer any help please as I'm out of my depth with this problem.
 

 Thanks

---

### Post by utnubuuser on 2009-11-15
Have you tried commenting out sources to try to trace which one is giving you issues? (seeing as you've got pretty much all of them enabled)

---

### Post by chertsey on 2009-11-15
Sorry, I'm clueless about these things "commenting  out sources" could you explain for me please?

---

