---
title: "How to cancel 409 pending updates?"
date: 2010-04-26
forum: New to Ubuntu
---

### Post by resander on 2010-04-26
I wanted a package and added its repository details by Software Sources on the main menu.  When I clicked OK/Apply a prompt popped up asking if I wanted to update all (don't remember the exact words). I thought this prompt related to the new repository I was adding. I exited and then clicked the 'Update' icon on the top taskbar. The Update Manager displayed there were 510 pending updates. I unchecked 409 of these and tolerated (didn't want any actually) the rest. I thought that would be the end of the matter, but the Update icon was still showing on the top taskbar. On reentry to the Update Manager I was told there were 409 pending updates. I don't want any of them and I don't want to sit and uncheck them each every time. 

How can I stop them?

---

### Post by tom.swartz07 on 2010-04-26
> **resander said:**
> I wanted a package and added its repository details by Software Sources on the main menu.  When I clicked OK/Apply a prompt popped up asking if I wanted to update all (don't remember the exact words). I thought this prompt related to the new repository I was adding. I exited and then clicked the 'Update' icon on the top taskbar. The Update Manager displayed there were 510 pending updates. I unchecked 409 of these and tolerated (didn't want any actually) the rest. I thought that would be the end of the matter, but the Update icon was still showing on the top taskbar. On reentry to the Update Manager I was told there were 409 pending updates. I don't want any of them and I don't want to sit and uncheck them each every time. 

How can I stop them?


Honestly, the only way to stop them is to actually download them and install them.

Its really unsafe to leave that many updates unchecked on your system. Many of them are security patches and fixes that will prevent your computer from borking out completely. 


If I were you, I would just put up with it for today, and let the updates run overnight when youre not using it.

---

### Post by resander on 2010-04-26
I always respond to and immediately install updates that are notified via the icon on the top taskbar, especially so for the security updates, typically every morning. These unwelcome updates arrived when I responded to the prompt in Software Sources. The update icon did not show immediately before this. 

They seem to be updates of applications, tools or language support, none appeared system critical. For example: 

 anacron         - cronlike program that does not go by time
 apache2-utils   - utility programs for webservers
 aspell          - GNU Aspell spell checker
 avahiutils      - avahi browsing, publishing utilities
 bluez           - Bluetooth tools
 bogofilter      - a fast Bayesian spam filter
 cvs             - concurrent version system
 docbase         - utilities to manage online documention
 fluid sound font - Fluid MIDI sound font  113MB!!!!
 fortunemod       - provides fortune cookies on demand 
 ...
 Python imaging library and a lot of other Python language support
 loads of PERL support stuff
 font updates
 ...
 yasm            - modular assembler with multi-syntax support


Most of the 409 updates are for products I have never heard of and I don't need any of them. The extra space needed would be 500MB and I have only 4GB left on the hard disk, so I really want to stop this. Can it be done from the command line in some way, for example by removing or editing the pending updates list?

P.S.
I am Ubuntu 8.10.

---

### Post by Elfy on 2010-04-26
Running sudo apt-get autoclean would remove the old packages leaving the newer ones.

What was the Software Sources prompt - was it a new version is available - eg an upgrade from 8.10 to 9.04? 

Though you don't say what repository you added? That might throw some light on the subject.

---

### Post by tom.swartz07 on 2010-04-26
> **resander said:**
> I always respond to and immediately install updates that are notified via the icon on the top taskbar, especially so for the security updates, typically every morning. These unwelcome updates arrived when I responded to the prompt in Software Sources. The update icon did not show immediately before this. 

They seem to be updates of applications, tools or language support, none appeared system critical. For example: 

 anacron         - cronlike program that does not go by time
 apache2-utils   - utility programs for webservers
 aspell          - GNU Aspell spell checker
 avahiutils      - avahi browsing, publishing utilities
 bluez           - Bluetooth tools
 bogofilter      - a fast Bayesian spam filter
 cvs             - concurrent version system
 docbase         - utilities to manage online documention
 fluid sound font - Fluid MIDI sound font  113MB!!!!
 fortunemod       - provides fortune cookies on demand 
 ...
 Python imaging library and a lot of other Python language support
 loads of PERL support stuff
 font updates
 ...
 yasm            - modular assembler with multi-syntax support


Most of the 409 updates are for products I have never heard of and I don't need any of them. The extra space needed would be 500MB and I have only 4GB left on the hard disk, so I really want to stop this. Can it be done from the command line in some way, for example by removing or editing the pending updates list?

P.S.
I am Ubuntu 8.10.

You could inspect where the specific updates are coming from through Synaptic..

For example, you click on the Origin filter and mark the upgrades. From there you could sort each list by repository to see where each of the packages are coming from. If they are coming from Ibex/Main Ibex/Multiverse, etc (in your specific case) then you need to apply them. If they are from the specific repo that you just added, then you could safely unmark the upgrades and select "lock version" to prevent it from pestering you in the future. As you could see in my screenshot, I have some that are applied from the Lucid/Main repo, as they are security updates.

I attached screen caps to help you along.

---

### Post by resander on 2010-04-27
I needed one and only one program, gprbuild, to be able to use GNAT Ada and C++ mixed mode programming.  An Ada forum said this is available at Libre adacore.com or in the Debian testing. 
It was not available at Libre only in Debian testing. I selected a repository at  deb [http://ftp.de.debian.org/debian](http://ftp.de.debian.org/debian) squeeze main and added it in via the Sources on the Admin menu. I don't do this very often and did not notice and think of the significance of 'Sqeeze'. That was a mistake and now I seem to have a mixed 8.10 and more recent version (10.04?).

I cannot login from the login dialog. The cursor/caret sits there blinking, but it does not accept any keyboard input. I can log in on the command line after Alt+F1. All the important files and directories are intact, but anyting with a GUI like gedit, brasero produces error message: 

  GTK-warning: ** cannot open Display.

How can I recover the GUI and restore Ubuntu 8.10?

---

### Post by QLee on 2010-04-27
> **resander said:**
> I needed one and only one program, gprbuild, to be able to use GNAT Ada and C++ mixed mode programming.  An Ada forum said this is available at Libre adacore.com or in the Debian testing. 
It was not available at Libre only in Debian testing. I selected a repository at  deb [http://ftp.de.debian.org/debian](http://ftp.de.debian.org/debian) squeeze main and added it in via the Sources on the Admin menu. I don't do this very often and did not notice and think of the significance of 'Sqeeze'. That was a mistake and now I seem to have a mixed 8.10 and more recent version (10.04?).

I cannot login from the login dialog. The cursor/caret sits there blinking, but it does not accept any keyboard input. I can log in on the command line after Alt+F1. All the important files and directories are intact, but anyting with a GUI like gedit, brasero produces error message: 

  GTK-warning: ** cannot open Display.

How can I recover the GUI and restore Ubuntu 8.10?

Well, the correct way to have done what you tried would have been to "pin"(apt pinning) the individual package(s) you need before you tried to download from the added repository. ...and, certainly not an upgrade with an upstream repository in your list.

Of course, you would have had to make sure that using the squeeze version was going to work beforehand. I think I would have tried the Lucid repository, if I was trying what you wanted to do.

Unfortunately, you now have a mixed system of Ubuntu and Squeeze (which is Debian, testing, not Ubuntu and it's likely a real mess. Trying to downgrade even between Debian versions has never been recommended, although, sometimes it is possible for an experienced and knowledgeable GNU/Linux user to manage getting things back as they were but it would probably take a long time with no guarantee to work.

Your best bet is to restore from your backup.


Edit: I see I didn't answer the question you first posted with because you had already "upgraded" when I read this.

If you were still at that point, you would have been able to remove the Squeeze repository from your list and then apt-get update (or check on update manager) to have only the packages files for 8.04, that would have eliminated the "409" you were concerned about.

---

