---
title: "problem regarding &quot;sudo apt-get update&quot; and installing gnome desktop"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by praveen97uma on 2009-03-09
I had recently installed Ubuntu server 8.1.0(LAMP Server)
When i executed the command sudo apt-get update, it returned an error stating

" W: Failed to fetch [http://in.archive.ubuntu.com/ubuntu/disks/intrepid-updates/universe/i18n/Translation-en_IN.bz2](http://in.archive.ubuntu.com/ubuntu/disks/intrepid-updates/universe/i18n/Translation-en_IN.bz2) Could not resolve 'in.archive.ubuntu.com'
....
..... 
W: Some index files failed to download, they have been ignored, or old ones used instead."

I used the command "sudo apt-get install ubuntu-desktop" and it returned something that reads as
" Reading package lists.....Done
Building dependency tree
Reading state information....Done
E: Could not find package ubuntu-desktop" 

when i executed "sudo aptitude", there were two options
1. Obsolete and Locally Created Packages (334)
2. Virtual Packages (136)

and there were two lines written at the lower half of the screen for "Obsolete and Locally Created Packages" that read as
" These packages are currently installed on your system, but they are not available from any apt source. They may be obsolete and removed from the archive....."


I think the system is unable to connect to the network..The network settings were assigned by DHCP during the install..
I don't know what the problem is. I am not able to install the GUI , update  the system etc..The error reported is that it couldnot find the package..
Please Help

---

### Post by 3rdalbum on 2009-03-09
Your diagnosis is correct: The system is not connecting to the Internet, and it can't find the package in its package list because its package list currently consists of only the software it shipped with.

Unfortunately I know nothing about how to use DHCP manually (on the command-line) to get your computer connected; you might need to search for a HOWTO or hang on and see if someone can give you some directions.

---

### Post by mister_pink on 2009-03-09
Quick steps to take in trying to diagnose network issues!

1. What do you get if you type "ping www.google.com" - press ctrl+C to stop it.
2. If that fails, can you do "ping 209.85.229.147" (thats the IP for a google server)
3. If that succeeds, then its a DNS problem.
4. Post the contents of your network configuration: "less /etc/network/interfaces"
5. Post the output of "ifconfig -a"
6. Try restarting networking and see if you get any errors: "sudo /etc/init.d/networking restart"

---

