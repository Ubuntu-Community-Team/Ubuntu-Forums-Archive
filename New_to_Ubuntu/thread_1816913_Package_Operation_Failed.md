---
title: "Package Operation Failed"
date: 2011-08-02
forum: New to Ubuntu
---

### Post by KleioWatson on 2011-08-02
Hello, I recently switched from Windows to Ubuntu 11.04. I am having a problem downloading programs, but I wasn't at first. Every time I try to download (or remove failed downloads once they have failed) it says:
"Package Operation Failed"
I would really appreciate some help.

These are the details from when I was trying to remove something:


installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 174483 files and directories currently installed.) 
Removing amarok ... 
Processing triggers for man-db ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache... 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Processing triggers for python-support ... 
Setting up libnunit2.4-cil (2.4.7+dfsg-6) ... 
* Installing 6 assemblies from libnunit2.4-cil into Mono 
 
** (/usr/lib/mono/2.0/gacutil.exe:23774): WARNING **: The class System.Collections.Generic.Dictionary`2 could not be loaded, used in mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089 
 
Unhandled Exception: System.TypeLoadException: Could not load type 'Mono.Tools.Driver' from assembly 'gacutil, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null'. 
E: installing Assembly /usr/lib/cli/nunit.core-2.4/nunit.core.dll failed 
E: Installation of libnunit2.4-cil with /usr/share/cli-common/runtimes.d/mono failed 
dpkg: error processing libnunit2.4-cil (--configure): 
 subprocess installed post-installation script returned error exit status 9 
dpkg: dependency problems prevent configuration of libnunit-cil-dev: 
 libnunit-cil-dev depends on libnunit2.4-cil (= 2.4.7+dfsg-6); however: 
  Package libnunit2.4-cil is not configured yet. 
dpkg: error processing libnunit-cil-dev (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libmono-cil-dev: 
 libmono-cil-dev depends on libnunit-cil-dev (>= 2.4); however: 
  Package libnunit-cil-dev is not configured yet. 
dpkg: error processing libmono-cil-dev (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of mono-devel: 
 mono-devel depends on libmono-cil-dev (= 2.6.7-5ubuntu3); however: 
  Package libmono-cil-dev is not configured yet. 
dpkg: error processing mono-devel (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
Errors were encountered while processing: 
 libnunit2.4-cil 
 libnunit-cil-dev 
 libmono-cil-dev 
 mono-devel 
Setting up libnunit2.4-cil (2.4.7+dfsg-6) ... 
* Installing 6 assemblies from libnunit2.4-cil into Mono 
 
** (/usr/lib/mono/2.0/gacutil.exe:23798): WARNING **: The class System.Collections.Generic.Dictionary`2 could not be loaded, used in mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089 
 
Unhandled Exception: System.TypeLoadException: Could not load type 'Mono.Tools.Driver' from assembly 'gacutil, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null'. 
E: installing Assembly /usr/lib/cli/nunit.core-2.4/nunit.core.dll failed 
E: Installation of libnunit2.4-cil with /usr/share/cli-common/runtimes.d/mono failed 
dpkg: error processing libnunit2.4-cil (--configure): 
 subprocess installed post-installation script returned error exit status 9 
dpkg: dependency problems prevent configuration of libnunit-cil-dev: 
 libnunit-cil-dev depends on libnunit2.4-cil (= 2.4.7+dfsg-6); however: 
  Package libnunit2.4-cil is not configured yet. 
dpkg: error processing libnunit-cil-dev (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libmono-cil-dev: 
 libmono-cil-dev depends on libnunit-cil-dev (>= 2.4); however: 
  Package libnunit-cil-dev is not configured yet. 
dpkg: error processing libmono-cil-dev (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of mono-devel: 
 mono-devel depends on libmono-cil-dev (= 2.6.7-5ubuntu3); however: 
  Package libmono-cil-dev is not configured yet. 
dpkg: error processing mono-devel (--configure): 
 dependency problems - leaving unconfigured

Thank you!

-Kleio

---

### Post by lkjoel on 2011-08-02
Try:
```
sudo aptitude -f install

```

---

### Post by KleioWatson on 2011-08-02
It says:

sudo: aptitude: command not found

---

### Post by bodhi.zazen on 2011-08-02
Where did you get the broken package from ? If from the Ubuntu repositories you should file a bug report on launchapd.

In terms of fixing the problem, try

```
sudo apt-get install -f
```

That will almost certainly fail.

In that case try:

```
sudo dpkg --remove --force-all libnunit2.4-cil
```

If that fails, see this blog

[http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/](http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/)

and report back any problems you have following those instructions.

---

### Post by lkjoel on 2011-08-02
Try this:
```
sudo apt-get install aptitude
aptitude -f install

```

---

### Post by KleioWatson on 2011-08-02
> **lkjoel said:**
> Try this:
```
sudo apt-get install aptitude
aptitude -f install

```

Alright, I did that and this is what it said:

The program 'aptitude' can be found in the following packages:
 * aptitude
 * aptitude-gtk
Try: sudo apt-get install <selected package>

What is the difference between the two and which one do I want to do?

---

### Post by lisati on 2011-08-02
@lkjoell:  recent versions of Ubuntu don't have aptitude installed by default. I've been caught out by this myself a couple of times.

---

### Post by KleioWatson on 2011-08-02
Ah, what does that mean? I am a bit confused.

---

### Post by KleioWatson on 2011-08-02
None of those seem to be working, and I am sure it is probably annoying that I have no idea what is going on, but I really appreciate your help. This is what it says when I try the first step on the blog:

rm: cannot remove `flashplugin-nonfree.*': No such file or directory

---

### Post by bodhi.zazen on 2011-08-02
> **KleioWatson said:**
> None of those seem to be working, and I am sure it is probably annoying that I have no idea what is going on, but I really appreciate your help. This is what it says when I try the first step on the blog:

rm: cannot remove `flashplugin-nonfree.*': No such file or directory

You have to use the correct package name. In my blog I was having a problem with flash. In your case your are having a problem with libnunit2.4-cil

---

### Post by KleioWatson on 2011-08-02
That make sense. It still says:
rm: cannot remove `libnunit2.4-cil': No such file or directory

---

### Post by lkjoel on 2011-08-02
```
sudo apt-get install aptitude

```
That will install aptitude.
Then:
```
sudo aptitude -f install

```
Aptitude has smarter package fixing than apt-get

---

### Post by KleioWatson on 2011-08-02
When I try installing aptitude this is what it says:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 aptitude : Depends: libboost-iostreams1.42.0 (>= 1.42.0-1) but it is not going to be installed
            Depends: libcwidget3 but it is not going to be installed
 libnunit-cil-dev : Depends: libnunit2.4-cil (= 2.4.7+dfsg-6) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

And so I tried the 'apt-get -f install' with no packages and it says this:

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by lkjoel on 2011-08-02
> **KleioWatson said:**
> When I try installing aptitude this is what it says:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 aptitude : Depends: libboost-iostreams1.42.0 (>= 1.42.0-1) but it is not going to be installed
            Depends: libcwidget3 but it is not going to be installed
 libnunit-cil-dev : Depends: libnunit2.4-cil (= 2.4.7+dfsg-6) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

And so I tried the 'apt-get -f install' with no packages and it says this:

E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
Try:
```
sudo apt-get -f install

```
You need sudo to use apt-get and aptitude.

---

### Post by directhex on 2011-08-02
> **KleioWatson said:**
> Hello, I recently switched from Windows to Ubuntu 11.04. I am having a problem downloading programs, but I wasn't at first. Every time I try to download (or remove failed downloads once they have failed) it says:
"Package Operation Failed"
I would really appreciate some help.

These are the details from when I was trying to remove something:


installArchives() failed: (Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 174483 files and directories currently installed.) 
Removing amarok ... 
Processing triggers for man-db ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache... 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Processing triggers for python-support ... 
Setting up libnunit2.4-cil (2.4.7+dfsg-6) ... 
* Installing 6 assemblies from libnunit2.4-cil into Mono 
 
** (/usr/lib/mono/2.0/gacutil.exe:23774): WARNING **: The class System.Collections.Generic.Dictionary`2 could not be loaded, used in mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089 
 
Unhandled Exception: System.TypeLoadException: Could not load type 'Mono.Tools.Driver' from assembly 'gacutil, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null'. 
E: installing Assembly /usr/lib/cli/nunit.core-2.4/nunit.core.dll failed 
E: Installation of libnunit2.4-cil with /usr/share/cli-common/runtimes.d/mono failed 
dpkg: error processing libnunit2.4-cil (--configure): 
 subprocess installed post-installation script returned error exit status 9 
dpkg: dependency problems prevent configuration of libnunit-cil-dev: 
 libnunit-cil-dev depends on libnunit2.4-cil (= 2.4.7+dfsg-6); however: 
  Package libnunit2.4-cil is not configured yet. 
dpkg: error processing libnunit-cil-dev (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libmono-cil-dev: 
 libmono-cil-dev depends on libnunit-cil-dev (>= 2.4); however: 
  Package libnunit-cil-dev is not configured yet. 
dpkg: error processing libmono-cil-dev (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of mono-devel: 
 mono-devel depends on libmono-cil-dev (= 2.6.7-5ubuntu3); however: 
  Package libmono-cil-dev is not configured yet. 
dpkg: error processing mono-devel (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
Errors were encountered while processing: 
 libnunit2.4-cil 
 libnunit-cil-dev 
 libmono-cil-dev 
 mono-devel 
Setting up libnunit2.4-cil (2.4.7+dfsg-6) ... 
* Installing 6 assemblies from libnunit2.4-cil into Mono 
 
** (/usr/lib/mono/2.0/gacutil.exe:23798): WARNING **: The class System.Collections.Generic.Dictionary`2 could not be loaded, used in mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089 
 
Unhandled Exception: System.TypeLoadException: Could not load type 'Mono.Tools.Driver' from assembly 'gacutil, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null'. 
E: installing Assembly /usr/lib/cli/nunit.core-2.4/nunit.core.dll failed 
E: Installation of libnunit2.4-cil with /usr/share/cli-common/runtimes.d/mono failed 
dpkg: error processing libnunit2.4-cil (--configure): 
 subprocess installed post-installation script returned error exit status 9 
dpkg: dependency problems prevent configuration of libnunit-cil-dev: 
 libnunit-cil-dev depends on libnunit2.4-cil (= 2.4.7+dfsg-6); however: 
  Package libnunit2.4-cil is not configured yet. 
dpkg: error processing libnunit-cil-dev (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of libmono-cil-dev: 
 libmono-cil-dev depends on libnunit-cil-dev (>= 2.4); however: 
  Package libnunit-cil-dev is not configured yet. 
dpkg: error processing libmono-cil-dev (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of mono-devel: 
 mono-devel depends on libmono-cil-dev (= 2.6.7-5ubuntu3); however: 
  Package libmono-cil-dev is not configured yet. 
dpkg: error processing mono-devel (--configure): 
 dependency problems - leaving unconfigured

Thank you!

-Kleio

It looks to me like you've managed to fry your Mono install.

The first issue is getting dpkg back on its feet - erase /var/lib/dpkg/info/libnunit2.4-cil.postinst, and run "apt-get f install" - this ought to get you into a state where dpkg is happy

Next, install [debsums](apt:debsums), and run "debsums -s" - this should tell you which package you've managed to fry, and you can reinstall that package.

Finally, reinstall libnunit2.4-cil, since it wasn't properly installed due to the missing postinst script.

---

### Post by KleioWatson on 2011-08-02
> **directhex said:**
> It looks to me like you've managed to fry your Mono install.

The first issue is getting dpkg back on its feet - erase /var/lib/dpkg/info/libnunit2.4-cil.postinst, and run "apt-get f install" - this ought to get you into a state where dpkg is happy

Next, install [debsums]("apt:debsums"), and run "debsums -s" - this should tell you which package you've managed to fry, and you can reinstall that package.

Finally, reinstall libnunit2.4-cil, since it wasn't properly installed due to the missing postinst script.


When I try and erase it says "no such file or directory". :(

---

### Post by bodhi.zazen on 2011-08-02
You have to manually delete the packages.

You will need to find the package name, lol

```
cd /var/lib/dpkg/info
ls | grep libnunit2.4
```

You need to stop panicking and look.

My blog listed "sudo rm flashplugin-nonfree.*"

1. You need to change "flashplugin-nonfree" to "libnunit2.4"

2. Your forgot the ".*"

3. If it says file not found, you need to use ls to list the contents of the directory and find the file to delete.

4. Or use tab completion

```
sudo rm libnunit2.4<tab>
```

---

### Post by KleioWatson on 2011-08-02
> **bodhi.zazen said:**
> You have to manually delete the packages.

You will need to find the package name, lol

```
cd /var/lib/dpkg/info
ls | grep libnunit2.4
```You need to stop panicking and look.

My blog listed "sudo rm flashplugin-nonfree.*"

1. You need to change "flashplugin-nonfree" to "libnunit2.4"

2. Your forgot the ".*"

3. If it says file not found, you need to use ls to list the contents of the directory and find the file to delete.

4. Or use tab completion

```
sudo rm libnunit2.4<tab>
```


Alright, I did the ls code and it listed these:

libnunit2.4-cil.clilibs
libnunit2.4-cil.list
libnunit2.4-cil.md5sums
libnunit2.4-cil.postinst
libnunit2.4-cil.prerm

and I tried deleting them with the information on the blog, but it says there is no package installed that matches the file name. 


I am not panicking, just frustrated. I, unfortunately, don't understand any of this and am trying to make sense of what I am typing into the terminal, but quite honestly am lost. So even when I look, I am not seeing. I am sure I'm doing something wrong, but I don't know what it is. So, if you would be so kind, could you possibly go through it again but with a little more detail?

Also, when I try tab completion (which I don't understand at all) it says:
bash: syntax error near unexpected token `newline'

---

### Post by EkuquoL on 2011-08-02
You are missing a mono program.  I believe mono is a code language(?)
devel is short, for developer < < Code language

You can also attempt to instal a RPM archiver and look for a RPM package for the program you are attempting to install. 

You can look for that dependency in apt-get
# apt-get mono-devel

---

### Post by bodhi.zazen on 2011-08-02
> **KleioWatson said:**
> Alright, I did the ls code and it listed these:

libnunit2.4-cil.clilibs
libnunit2.4-cil.list
libnunit2.4-cil.md5sums
libnunit2.4-cil.postinst
libnunit2.4-cil.prerm

```
sudo rm libnunit2.4-cil.*
```

You use the tab key, start typing a file name or path, hit the tab key

libnunit2.<tab>

<tab> signifies the tab key.

At any rate, the next step is to 

```
sudo dpkg --remove --force-remove-reinstreq libnunit2.4-cil
```

Then apt-get update , should be working.

Post any error message you get.

You may need to remove additional packages, what were you originally installing ?

---

### Post by KleioWatson on 2011-08-02
This is the error message I received:

(Reading database ... 174404 files and directories currently installed.)
Removing libnunit2.4-cil ...
Removing libnunit2.4-cil from Mono

** (/usr/lib/mono/2.0/gacutil.exe:25575): WARNING **: The class System.Collections.Generic.Dictionary`2 could not be loaded, used in mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089

Unhandled Exception: System.TypeLoadException: Could not load type 'Mono.Tools.Driver' from assembly 'gacutil, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null'.
W: removing assembly: nunit.core, Version=2.4.7.0, Culture=neutral, PublicKeyToken=96d09a1eb7f44a77 failed!

---

### Post by bodhi.zazen on 2011-08-02
What happens when you run sudo apt-get update ?

You may need to remove additional packages (mono)

---

### Post by KleioWatson on 2011-08-03
This is what is says:

Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease
Ign [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty InRelease                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates InRelease             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease              
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg [72 B]              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release.gpg                             
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg [198 B]  
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg                   
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release [27.2 kB]    
Hit [http://archive.canonical.com](http://archive.canonical.com) natty Release                                 
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release.gpg [198 B]           
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release                                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty Release                                 
Hit [http://archive.canonical.com](http://archive.canonical.com) natty/partner i386 Packages                   
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates Release [27.2 kB]             
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Sources                               
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner TranslationIndex                
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Sources [63.5 kB]         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main i386 Packages                          
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main TranslationIndex                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Sources                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Sources                        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Sources                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main i386 Packages                      
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted i386 Packages                
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe i386 Packages                  
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse i386 Packages                
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main TranslationIndex                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted TranslationIndex             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe TranslationIndex               
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Sources [98.1 kB]        
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Sources [14 B]      
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Sources [9,829 B]     
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Sources [658 B]    
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main i386 Packages [165 kB]   
Get:12 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Sources [14 B]    
Get:13 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Sources [22.1 kB]   
Get:14 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Sources [1,893 B] 
Get:15 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main i386 Packages [286 kB]  
Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted i386 Packages [14 B]
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe i386 Packages [31.9 kB]
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse i386 Packages [2,074 B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main TranslationIndex            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted TranslationIndex      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe TranslationIndex        
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en_US               
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en_US                      
Ign [http://archive.canonical.com](http://archive.canonical.com) natty/partner Translation-en                  
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) natty/main Translation-en                         
Get:19 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted i386 Packages [14 B]
Get:20 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe i386 Packages [80.2 kB]
Get:21 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse i386 Packages [4,267 B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main TranslationIndex          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted TranslationIndex
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe TranslationIndex
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en_US   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/main Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/multiverse Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/restricted Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) natty-security/universe Translation-en
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/main Translation-en                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/multiverse Translation-en               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en_US            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/restricted Translation-en               
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en_US              
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty/universe Translation-en                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en_US          
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/main Translation-en             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/multiverse Translation-en       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en_US    
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/restricted Translation-en       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en_US      
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) natty-updates/universe Translation-en         
Fetched 821 kB in 6s (121 kB/s)                                                
Reading package lists... Done

---

### Post by bodhi.zazen on 2011-08-03
That looks good, apt-get seems to be working.

Mono may well be broken.

run ```
sudo apt-get -s -f
```

Again, post any error messages

---

### Post by KleioWatson on 2011-08-03
It just says this:

apt 0.8.13.2ubuntu4.1 for i386 compiled on Jul  7 2011 18:30:45
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]

apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.

Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   autoremove - Remove automatically all unused packages
   purge - Remove packages and config files
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies
   markauto - Mark the given packages as automatically installed
   unmarkauto - Mark the given packages as manually installed
   changelog - Download and display the changelog for the given package
   download - Download the binary package into the current directory

Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to correct a system with broken dependencies in place
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.

I don't know what I am supposed to do with that. But it helps a lot with trying to understand things.

---

### Post by bodhi.zazen on 2011-08-03
sorry, ```
sudo apt-get install -s -f
```

---

### Post by KleioWatson on 2011-08-03
It says this:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.38-8 linux-headers-2.6.38-8-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Conf libnunit2.4-cil (2.4.7+dfsg-6 Ubuntu:11.04/natty [all])
Conf libnunit-cil-dev (2.4.7+dfsg-6 Ubuntu:11.04/natty [all])
Conf libmono-cil-dev (2.6.7-5ubuntu3 Ubuntu:11.04/natty [all])
Conf mono-devel (2.6.7-5ubuntu3 Ubuntu:11.04/natty [all])

Should I just do what is says with the 'apt-get autoremove'?

---

### Post by bodhi.zazen on 2011-08-03
no, try removing those 4 packages

> Conf libnunit2.4-cil (2.4.7+dfsg-6 Ubuntu:11.04/natty [all])
Conf libnunit-cil-dev (2.4.7+dfsg-6 Ubuntu:11.04/natty [all])
Conf libmono-cil-dev (2.6.7-5ubuntu3 Ubuntu:11.04/natty [all])
Conf mono-devel (2.6.7-5ubuntu3 Ubuntu:11.04/natty [all])

sudo apt-get -s purge libnunit2.4-cil libnunit-cil-dev libmono-cil-dev mono-devel[/code]

The -s is simulate, post any error messages.

You may need to remove them one at a time

sudo dpkg --remove --force-remove-reinstreq libnunit2.4-cil
sudo dpkg --remove --force-remove-reinstreq libnunit-cil-dev
sudo dpkg --remove --force-remove-reinstreq libmono-cil-dev
sudo dpkg --remove --force-remove-reinstreq mono-devel

---

### Post by KleioWatson on 2011-08-03
It didn't work at first so I tried doing them one by one. This is what it says for each one:

sudo dpkg --remove --force-remove-reinstreq libnunit2.4-cil:

(Reading database ... 174404 files and directories currently installed.)
Removing libnunit2.4-cil ...
Removing libnunit2.4-cil from Mono

** (/usr/lib/mono/2.0/gacutil.exe:26613): WARNING **: The class System.Collections.Generic.Dictionary`2 could not be loaded, used in mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089

Unhandled Exception: System.TypeLoadException: Could not load type 'Mono.Tools.Driver' from assembly 'gacutil, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null'.
W: removing assembly: nunit.core, Version=2.4.7.0, Culture=neutral, PublicKeyToken=96d09a1eb7f44a77 failed!


sudo dpkg --remove --force-remove-reinstreq libnunit-cil-dev:

(Reading database ... 174404 files and directories currently installed.)
Removing libnunit2.4-cil ...
Removing libnunit2.4-cil from Mono

** (/usr/lib/mono/2.0/gacutil.exe:26613): WARNING **: The class System.Collections.Generic.Dictionary`2 could not be loaded, used in mscorlib, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089

Unhandled Exception: System.TypeLoadException: Could not load type 'Mono.Tools.Driver' from assembly 'gacutil, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null'.
W: removing assembly: nunit.core, Version=2.4.7.0, Culture=neutral, PublicKeyToken=96d09a1eb7f44a77 failed!
kleiowatson@kleiowatson-LT21:~$ sudo dpkg --remove --force-remove-reinstreq libnunit-cil-dev
(Reading database ... 174388 files and directories currently installed.)
Removing libnunit-cil-dev ...

And the same for the third one. Then  sudo dpkg --remove --force-remove-reinstreq mono-devel:

(Reading database ... 174388 files and directories currently installed.)
Removing libnunit-cil-dev ...
kleiowatson@kleiowatson-LT21:~$ sudo dpkg --remove --force-remove-reinstreq libmono-cil-dev
(Reading database ... 174384 files and directories currently installed.)
Removing libmono-cil-dev ...
kleiowatson@kleiowatson-LT21:~$ sudo dpkg --remove --force-remove-reinstreq mono-devel
(Reading database ... 174371 files and directories currently installed.)
Removing mono-devel ...
Processing triggers for man-db ...

And then the message for all of them (just in case...):

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.38-8 linux-headers-2.6.38-8-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  libmono-cil-dev* libnunit-cil-dev* libnunit2.4-cil* mono-devel*
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
4 not fully installed or removed.
Purg mono-devel [2.6.7-5ubuntu3]
Purg libmono-cil-dev [2.6.7-5ubuntu3]
Purg libnunit-cil-dev [2.4.7+dfsg-6]
Purg libnunit2.4-cil [2.4.7+dfsg-6]

---

### Post by bodhi.zazen on 2011-08-03
Run the command you ran last, the one that shows all 4 packages being removed, the command that gave this output

> Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
linux-headers-2.6.38-8 linux-headers-2.6.38-8-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
libmono-cil-dev* libnunit-cil-dev* libnunit2.4-cil* mono-devel*
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
4 not fully installed or removed.
Purg mono-devel [2.6.7-5ubuntu3]
Purg libmono-cil-dev [2.6.7-5ubuntu3]
Purg libnunit-cil-dev [2.4.7+dfsg-6]
Purg libnunit2.4-cil [2.4.7+dfsg-6] 

After running those command, and removing those 4 packages, I think you should be good to go =P

---

### Post by KleioWatson on 2011-08-03
Ah brilliant! My download worked :D þakka þér fyrir! Thank you so much!

-Kleio

---

