---
title: "Unable to load from jnlp file"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by NutmegCT on 2010-05-17
Good morning.

Ubuntu 10.04, updated as of yesterday, latest FF as browser.  Click link to any jnlp file, default response is open OpenJDK Java 6 Policy Tool.

jnlp file downloads to desktop, but nothing more happens.

I tried the suggestion in:

[http://ubuntuforums.org/showthread.php?t=1381721](http://ubuntuforums.org/showthread.php?t=1381721)

But when I enter "sudo update-alternatives --config java" in terminal I get:

"There is only one alternative in link group java: /usr/lib/jvm/java-6-openjdk/jre/bin/java.  Nothing to configure."

Could someone suggest how I can get a jnlp file to load?  The jnlp procedure to launch an app works on my WinXP machine, but not on my Ubuntu machine.

Thanks.
Tom

---

### Post by cviorel on 2010-05-17
I had the same problem. Running the following commands solved it:

```

sudo apt-get -q -y --force-yes remove sun-java*
sudo apt-get -q -y --force-yes remove openjdk*
sudo apt-get -q -y --force-yes autoremove
sudo apt-get -q -y --force-yes install sun-java6-jre sun-java6-plugin sun-java6-jdk sun-java6-fonts
sudo update-java-alternatives -s java-6-sun

```
Of course, you may skip the sun-java6-jdk package.

---

### Post by NutmegCT on 2010-05-17
Thank you for your suggestions!  Here's what happened when I ran those terminal commands:

ethan@ethan-laptop:~$ sudo apt-get -q -y --force-yes remove sun-java*
Reading package lists...
Building dependency tree...
Reading state information...
Note, selecting sun-javadb-common for regex 'sun-java*'
Note, selecting sun-java6-plugin for regex 'sun-java*'
Note, selecting sun-java5-jre for regex 'sun-java*'
Note, selecting sun-javadb-doc for regex 'sun-java*'
Note, selecting sun-java6-fonts for regex 'sun-java*'
Note, selecting sun-java6-bin for regex 'sun-java*'
Note, selecting ia32-sun-java6-plugin for regex 'sun-java*'
Note, selecting sun-java6-doc for regex 'sun-java*'
Note, selecting ia32-sun-java6-bin for regex 'sun-java*'
Note, selecting sun-java6-jdk for regex 'sun-java*'
Note, selecting sun-javadb-demo for regex 'sun-java*'
Note, selecting sun-java6-jre for regex 'sun-java*'
Note, selecting sun-javadb-core for regex 'sun-java*'
Note, selecting sun-javadb-javadoc for regex 'sun-java*'
Note, selecting sun-javadb-client for regex 'sun-java*'
E: Couldn't find package sun-java*
ethan@ethan-laptop:~$ sudo apt-get -q -y --force-yes remove openjdk*
Reading package lists...
Building dependency tree...
Reading state information...
Note, selecting openjdk-6-demo for regex 'openjdk*'
Note, selecting openjdk-6-dbg for regex 'openjdk*'
Note, selecting openjdk-6-doc for regex 'openjdk*'
Note, selecting openjdk-6-jre-headless for regex 'openjdk*'
Note, selecting openjdk-6-jdk for regex 'openjdk*'
Note, selecting openjdk-6-jre-shark for regex 'openjdk*'
Note, selecting openjdk-6-jre-zero instead of openjdk-6-jre-shark
Note, selecting openjdk-6-jre for regex 'openjdk*'
Note, selecting openjdk-6-jre-lib for regex 'openjdk*'
Note, selecting openjdk-6-jre-zero for regex 'openjdk*'
Note, selecting openjdk-6-source for regex 'openjdk*'
E: Couldn't find package openjdk*
ethan@ethan-laptop:~$ sudo apt-get -q -y --force-yes autoremove
Reading package lists...
Building dependency tree...
Reading state information...
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ethan@ethan-laptop:~$ sudo apt-get -q -y --force-yes install sun-java6-jre sun-java6-plugin sun-java6-jdk sun-java6-fonts
Reading package lists...
Building dependency tree...
Reading state information...
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate
ethan@ethan-laptop:~$ sudo update-java-alternatives -s java-6-sun
sudo: update-java-alternatives: command not found
ethan@ethan-laptop:~$ 

(Doesn't look very good!) (Problem with jnlp remains.)

Thanks.
Tom

---

### Post by cviorel on 2010-05-18
Have you enabled the Medibuntu repos?
If not, run this command first:
```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update

```
Then you can install sun-java.

> **NutmegCT said:**
> Thank you for your suggestions!  Here's what happened when I ran those terminal commands:

ethan@ethan-laptop:~$ sudo apt-get -q -y --force-yes remove sun-java*
Reading package lists...
Building dependency tree...
Reading state information...
Note, selecting sun-javadb-common for regex 'sun-java*'
Note, selecting sun-java6-plugin for regex 'sun-java*'
Note, selecting sun-java5-jre for regex 'sun-java*'
Note, selecting sun-javadb-doc for regex 'sun-java*'
Note, selecting sun-java6-fonts for regex 'sun-java*'
Note, selecting sun-java6-bin for regex 'sun-java*'
Note, selecting ia32-sun-java6-plugin for regex 'sun-java*'
Note, selecting sun-java6-doc for regex 'sun-java*'
Note, selecting ia32-sun-java6-bin for regex 'sun-java*'
Note, selecting sun-java6-jdk for regex 'sun-java*'
Note, selecting sun-javadb-demo for regex 'sun-java*'
Note, selecting sun-java6-jre for regex 'sun-java*'
Note, selecting sun-javadb-core for regex 'sun-java*'
Note, selecting sun-javadb-javadoc for regex 'sun-java*'
Note, selecting sun-javadb-client for regex 'sun-java*'
E: Couldn't find package sun-java*
ethan@ethan-laptop:~$ sudo apt-get -q -y --force-yes remove openjdk*
Reading package lists...
Building dependency tree...
Reading state information...
Note, selecting openjdk-6-demo for regex 'openjdk*'
Note, selecting openjdk-6-dbg for regex 'openjdk*'
Note, selecting openjdk-6-doc for regex 'openjdk*'
Note, selecting openjdk-6-jre-headless for regex 'openjdk*'
Note, selecting openjdk-6-jdk for regex 'openjdk*'
Note, selecting openjdk-6-jre-shark for regex 'openjdk*'
Note, selecting openjdk-6-jre-zero instead of openjdk-6-jre-shark
Note, selecting openjdk-6-jre for regex 'openjdk*'
Note, selecting openjdk-6-jre-lib for regex 'openjdk*'
Note, selecting openjdk-6-jre-zero for regex 'openjdk*'
Note, selecting openjdk-6-source for regex 'openjdk*'
E: Couldn't find package openjdk*
ethan@ethan-laptop:~$ sudo apt-get -q -y --force-yes autoremove
Reading package lists...
Building dependency tree...
Reading state information...
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ethan@ethan-laptop:~$ sudo apt-get -q -y --force-yes install sun-java6-jre sun-java6-plugin sun-java6-jdk sun-java6-fonts
Reading package lists...
Building dependency tree...
Reading state information...
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate
ethan@ethan-laptop:~$ sudo update-java-alternatives -s java-6-sun
sudo: update-java-alternatives: command not found
ethan@ethan-laptop:~$ 

(Doesn't look very good!) (Problem with jnlp remains.)

Thanks.
Tom

---

### Post by NutmegCT on 2010-05-18
Thank you again!  I ran that long Medibuntu command, then the Install command.  Here's the result:

ethan@ethan-laptop:~$ sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list; sudo apt-get -q update; sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring; sudo apt-get -q update
[sudo] password for ethan: 
--2010-05-18 07:45:23--  [http://www.medibuntu.org/sources.list.d/lucid.list](http://www.medibuntu.org/sources.list.d/lucid.list)
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 268 [text/plain]
Saving to: `/etc/apt/sources.list.d/medibuntu.list'

100%[======================================>] 268         --.-K/s   in 0s      

2010-05-18 07:45:24 (12.4 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [268/268]

Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg [197B]
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Translation-en_US
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release [6,854B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages [3,253B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages [8,873B]
Fetched 19.2kB in 1s (10.7kB/s)
Reading package lists...
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
Reading package lists...
Building dependency tree...
Reading state information...
The following NEW packages will be installed:
  medibuntu-keyring
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,448B of archives.
After this operation, 49.2kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  medibuntu-keyring
Authentication warning overridden.
Get:1 [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free medibuntu-keyring 2008.04.20 [3,448B]
Fetched 3,448B in 1s (3,090B/s)
Selecting previously deselected package medibuntu-keyring.
(Reading database ... 157991 files and directories currently installed.)
Unpacking medibuntu-keyring (from .../medibuntu-keyring_2008.04.20_all.deb) ...
Setting up medibuntu-keyring (2008.04.20) ...
OK

Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_US
Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release.gpg [197B]
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/free Translation-en_US
Ign [http://packages.medibuntu.org/](http://packages.medibuntu.org/) lucid/non-free Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid Release
Get:2 [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid Release [6,854B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) lucid/non-free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) lucid-updates/multiverse Sources
Fetched 198B in 1s (124B/s)
Reading package lists...
ethan@ethan-laptop:~$ sudo apt-get -q -y --force-yes install sun-java6-jre sun-java6-plugin sun-java6-jdk sun-java6-fonts
Reading package lists...
Building dependency tree...
Reading state information...
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate
ethan@ethan-laptop:~$ 

Really sorry to trouble you with all this.  When I saw "Medibuntu repos" I had no clue what that meant.  Thought it was a new-age band!

It seems the Medibuntu command(s) ran successfully, but the Install failed.

Anyway, thanks again for helping.  Any suggestions will be greatly appreciated.

Tom

---

### Post by cviorel on 2010-05-18
Can you post the result of the following command:
```
sudo aptitude search sun-java
```

---

### Post by NutmegCT on 2010-05-18
Here you go:

ethan@ethan-laptop:~$ sudo aptitude search sun-java
[sudo] password for ethan: 
c   sun-java6-bin                   - Sun Java(TM) Runtime Environment (JRE) 6 (
c   sun-java6-jre                   - Sun Java(TM) Runtime Environment (JRE) 6 (
p   sun-javadb-client               - Java DB client                            
p   sun-javadb-common               - Java DB common files                      
p   sun-javadb-core                 - Java DB core                              
p   sun-javadb-demo                 - Java DB demo                              
p   sun-javadb-doc                  - Java DB documentation                     
p   sun-javadb-javadoc              - Java DB javadoc                           
ethan@ethan-laptop:~$

---

### Post by cviorel on 2010-05-18
Ok. All you need is to install those packages:
```
sudo aptitude install sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin
```

---

### Post by NutmegCT on 2010-05-18
Thanks again for your assistance.  I just ran the code (see below).  Does this mean it's all done?  My untrained eye sees all those "no candidate version found", so I don't know if this was successful.

Thanks.
Tom

* * * * *

ethan@ethan-laptop:~$ sudo aptitude install sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin
[sudo] password for ethan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
No candidate version found for sun-java6-bin
No candidate version found for sun-java6-fonts
No candidate version found for sun-java6-jre
No candidate version found for sun-java6-plugin
No candidate version found for sun-java6-bin
No candidate version found for sun-java6-fonts
No candidate version found for sun-java6-jre
No candidate version found for sun-java6-plugin
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

ethan@ethan-laptop:~$

---

### Post by NutmegCT on 2010-05-18
I rebooted, then tried the jnlp link I'd been trying.  Same result.  I get the jnlp file with the Ubuntu Firefox message "open with:  OpenJDK Java 6 Web Start (default)"

I click OK, and hear some disk activity.  But then nothing.  Same as always.

Should the jnlp file be opened with some other app?

Here's the jnlp file if that's helpful in diagnosing/solving the problem:

* * * * *

<?xml version="1.0" encoding="utf-8"?>
<!-- JNLP File for EPC Application Prototype -->
<jnlp spec="1.0+" codebase="http://epc-prod.startekinfo.com/EPC-net/servlets">
<information>
<title>EPC net</title>
<vendor>Snap-on Business Solutions</vendor>
<homepage href="http://java.sun.com/products/javawebstart/needdownload.html"/>
<description>EPC net</description>
<description kind="short">EPC net Application</description>
<icon href="images/icon.gif"/>
</information>
<security>
<all-permissions/>
</security>
<resources>
<j2se version="1.5+" href="http://java.sun.com/products/autodl/j2se"/>
<jar href="epc.jar" version="1.23.3.0"/>
<extension name="EWA net Client Tools Package" href="http://epc-prod.startekinfo.com/EWA-net/jnlp/client_res/client_tools_1.11.174.68.jnlp"/>
</resources>
<application-desc main-class="com.proquest.epc.view.impl.MBEPCApplication">
<argument>http://epc-prod.startekinfo.com/EWA-net/ewa-net;jsessionid=0000PuhhbPIXnQd9nfBLb8TMxYd:144tanrc3?appid=150&userid=*****&sessionid=GKtTcRoCH1c7NNqa_-sRM3G&license=start</argument>
<argument>userid=*****</argument>
<argument>LookAndFeel=Automatic</argument>
</application-desc>
</jnlp>

* * * * *

Thanks.
Tom

---

### Post by cviorel on 2010-05-18
My bad, you are using Lucid... You may want to try this:
```
sudo add-apt-repository "deb http://archive.canonical.com/ lucid partner"
```
and then
```
sudo aptitude install sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin
```

---

### Post by NutmegCT on 2010-05-18
OK - here's the result.  Doesn't look like the first command did anything, but at least there were no errors.  After posting this I'll reboot and try the jnlp file again.

Thanks!

* * * * *

ethan@ethan-laptop:~$ sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"
[sudo] password for ethan: 
ethan@ethan-laptop:~$ sudo aptitude install sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
No candidate version found for sun-java6-bin
No candidate version found for sun-java6-fonts
No candidate version found for sun-java6-jre
No candidate version found for sun-java6-plugin
No candidate version found for sun-java6-bin
No candidate version found for sun-java6-fonts
No candidate version found for sun-java6-jre
No candidate version found for sun-java6-plugin
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

ethan@ethan-laptop:~$

---

### Post by cviorel on 2010-05-18
After you add the 'partner' repository, you need to update the package list:
```
sudo aptitude update
```
Then install java:
```
sudo aptitude install sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin
```.

---

### Post by NutmegCT on 2010-05-18
Aha!  now we're getting somewhere.  I ran the update then the install.  Looks like all went well.

I clicked the jnlp file AND IT STARTED TO OPEN THE REQUESTED APPLICATION!

Here's the error I got:

Error:  Unexpected Exception:  java.lang.reflect.InvocationTargetException

followed by:

<?xml version="1.0" encoding="utf-8"?>
<!-- JNLP File for EPC Application Prototype -->
<jnlp spec="1.0+" codebase="http://epc-prod.startekinfo.com/EPC-net/servlets">
<information>
<title>EPC net</title>
<vendor>Snap-on Business Solutions</vendor>
<homepage href="http://java.sun.com/products/javawebstart/needdownload.html"/>
<description>EPC net</description>
<description kind="short">EPC net Application</description>
<icon href="images/icon.gif"/>
</information>
<security>
<all-permissions/>
</security>
<resources>
<j2se version="1.5+" href="http://java.sun.com/products/autodl/j2se"/>
<jar href="epc.jar" version="1.23.3.0"/>
<extension name="EWA net Client Tools Package" href="http://epc-prod.startekinfo.com/EWA-net/jnlp/client_res/client_tools_1.11.174.68.jnlp"/>
</resources>
<application-desc main-class="com.proquest.epc.view.impl.MBEPCApplication">
<argument>http://epc-prod.startekinfo.com/EWA-net/ewa-net;jsessionid=0000H2TR4RjOUEaMJO0FMKNZ5TK:144tanpro?appid=150&userid=epc08591&sessionid=efk4j59C6YzvVRkVn8iF1Gz&license=start</argument>
<argument>userid=epc08591</argument>
<argument>LookAndFeel=Automatic</argument>
</application-desc>
</jnlp>
 
followed by:

java.lang.reflect.InvocationTargetException
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:597)
    at com.sun.javaws.Launcher.executeApplication(Launcher.java:1749)
    at com.sun.javaws.Launcher.executeMainClass(Launcher.java:1695)
    at com.sun.javaws.Launcher.doLaunchApp(Launcher.java:1477)
    at com.sun.javaws.Launcher.run(Launcher.java:129)
    at java.lang.Thread.run(Thread.java:619)
Caused by: java.lang.NoClassDefFoundError: Could not initialize class com.hp.tis.ewo.common.win32.TerminalServer
    at com.hp.tis.ewo.common.communication.CommChannel.<init>(CommChannel.java:372)
    at com.hp.tis.ewo.ewanapi.api.ExternalCallInterface.isRunning(ExternalCallInterface.java:340)
    at com.proquest.epc.view.impl.MBEPCApplication.wisNetCheck(MBEPCApplication.java:768)
    at com.proquest.epc.view.impl.MBEPCApplication.main(MBEPCApplication.java:420)
    ... 9 more

This is farther than I've got before, so I think we're making progress.  Any suggestions on what's going wrong now, and how to fix it?

Thanks again!
Tom

---

### Post by cviorel on 2010-05-18
This is how it should look when you open the jnpl file in Firefox.
That means that you have java plugin installed and working.
Beyond this point you need to investigate that specific error message.

---

### Post by NutmegCT on 2010-05-18
Yes - that's exactly what the "open" dialog box shows now.  So that's working properly.

Do you have a suggestion on where I look to understand all the Java language errors?

Thanks.
Tom

---

### Post by cviorel on 2010-05-18
As a starting point: [http://forums.sun.com/forum.jspa?forumID=38&start=0]("http://forums.sun.com/forum.jspa?forumID=38&start=0").
Next: google :)

---

