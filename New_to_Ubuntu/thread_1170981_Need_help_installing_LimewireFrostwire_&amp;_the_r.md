---
title: "Need help installing Limewire/Frostwire &amp; the right Java, nothing works!"
date: 2009-05-26
forum: New to Ubuntu
---

### Post by banwich11 on 2009-05-26
I recently switched to Kubuntu from Ubuntu, and am having some difficulties getting java installed so I can download Limewire or Frostwire.  Anyone know of a step-by-step or can offer some help?  I downloaded Limewire already, and it's installed but after opening it, it shows in the tray for about 10-20 seconds and then disappears without the program starting.  I read another post somewhere about how that is because I don't have Java set up, but I don't know which version to get and there are so many!  I've run a couple commands in terminal but it keeps asking if I am the root... and I'm the administrator and sole user on this computer.  I've tried saying "Yes" and "Y" and it says it doesn't understand the command "Yes" and when I type "Y" it shows lines of:
y
y
y
y
y
y
y
y
y

Anyone else figure this out?:confused:

---

### Post by abn91c on 2009-05-26
sudo apt-get install kubuntu-restricted-extras
when it gets to the sun/java EULA screen, hi the TAB key to highlight OK then press enter to continue

---

### Post by SunnyRabbiera on 2009-05-26
firstly ignore the java website, it wont help here.
secondly, use synaptic package manager located under system > administration > synaptic package manager.
Use that to install java 5 and 6 by searching for java.
Here is a good tutorial for using synaptic:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by banwich11 on 2009-05-26
abn91c.. I tried that and I got the following... Not so sure what to make of it.  I tried "apt-get -f install" as it suggested but that brought me back to the "are you root?"... "yes" or "y" 

jjb@laptop:~$ sudo apt-get install kubuntu-restricted-extras
[sudo] password for jjb:                                           
Reading package lists... Done                                           
Building dependency tree                                                
Reading state information... Done                                       
You might want to run `apt-get -f install' to correct these:            
The following packages have unmet dependencies:                         
  limewire-basic: Depends: sun-java6-jre but it is not going to be installed or
                           icedtea-java7-jre but it is not installable or      
                           sun-java6-jdk but it is not going to be installed or
                           icedtea-java7-jdk but it is not installable         
                  Recommends: libgnome2-0 (>= 2.14.1) but it is not going to be installed                                                                       
                  Recommends: libstdc++5 (>= 1:3.3.4-1) but it is not going to be installed                                                                     
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution). 
jjb@laptop:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
jjb@laptop:~$

---

### Post by Sef on 2009-05-26
> sudo apt-get install kubuntu-restricted-extras
when it gets to the sun/java EULA screen, hi the TAB key to highlight OK then press enter to continue

That is an incorrect command.   Kubuntu uses kdesu instead of sudo.


>  secondly, use synaptic package manager located under system > administration > synaptic package manager.

That is also incorrect.  Kubuntu uses adept instead of synaptic.


banwich11:

Go into adept and download java from there.

---

### Post by abn91c on 2009-05-27
> **banwich11 said:**
> abn91c.. I tried that and I got the following... Not so sure what to make of it.  I tried "apt-get -f install" as it suggested but that brought me back to the "are you root?"... "yes" or "y" 

jjb@laptop:~$ sudo apt-get install kubuntu-restricted-extras
[sudo] password for jjb:                                           
Reading package lists... Done                                           
Building dependency tree                                                
Reading state information... Done                                       
You might want to run `apt-get -f install' to correct these:            
The following packages have unmet dependencies:                         
  limewire-basic: Depends: sun-java6-jre but it is not going to be installed or
                           icedtea-java7-jre but it is not installable or      
                           sun-java6-jdk but it is not going to be installed or
                           icedtea-java7-jdk but it is not installable         
                  Recommends: libgnome2-0 (>= 2.14.1) but it is not going to be installed                                                                       
                  Recommends: libstdc++5 (>= 1:3.3.4-1) but it is not going to be installed                                                                     
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution). 
jjb@laptop:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
jjb@laptop:~$
you must use **sudo** in front of the command to be "root"
**sudo apt-get install -f**
as for the last error make sure adept or synaptic is not running before you use the terminal commands. you can install the restricted extras from Adept Manager also.

---

### Post by noveron714 on 2010-04-13
how do you download limewire for Kubuntu 9.10

---

### Post by Cityscape on 2010-04-13
> **noveron714 said:**
> how do you download limewire for Kubuntu 9.10

Download the .deb package from their website.

---

### Post by deancasino on 2010-04-13
Seriously, look at using torrents, Limewire/Frostwire are old news.

---

### Post by unmole on 2010-04-13
Try gtk-gnutella, from the package manager. You can access Limewire/Frostwire using it.

---

