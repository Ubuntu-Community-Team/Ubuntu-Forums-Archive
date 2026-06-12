---
title: "no videos (BBC, Youtube) on Opera 9.64"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by al.adab on 2009-08-11
hello,

I decided to switch to Opera 9.64 from Firefox 3.0 (on Ubuntu 9.04). 

The problem is that I can't play any BBC or Youtube video on Opera. I've noticed a couple of recent posts on the subject, but I don't seem to see that a solution was found/given. 

The plug-in path in Opera at the moment is "/usr/lib/opera/plugins:/usr/lib/mozilla/plugins". After installing Ubuntu, I followed [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) to update the multimedia software, and in fact everything worked after that, including any kind of media played on Firefox. 

Can anyone tell me what the matter might be? Thanks.

---

### Post by al.adab on 2009-08-11
thought it might help if I show a screenshot of the plugins detected by Opera...

---

### Post by Aweyer2 on 2009-08-11
It sounds to me like you need to install the necessary flash player add ons for that particular web browser. Firefox already has that capability, but opera may not.

---

### Post by al.adab on 2009-08-12
you mean I should do this? But then they seem to be already there! Or do I need some other version of the flash plugin?

[I]~$ sudo apt-get install flashplugin-nonfree
[sudo] password for daniele: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.[/I]

---

### Post by al.adab on 2009-08-12
is it a possibility that Opera hasn't detected the flash plugins? I only see a "shockwave flash" in the list...if this is the reason, any idea of how I can get Opera detect them?

---

### Post by al.adab on 2009-08-12
Right...solution found. Just follow the directions at

[http://ubuntuforums.org/showthread.php?t=1228708](http://ubuntuforums.org/showthread.php?t=1228708) 

-except that I couldn't find "Opera non-static" at Synaptics, that's why I moved to

[http://www.qc4blog.com/?p=842](http://www.qc4blog.com/?p=842)

Have to open Opera in Terminal now (just need to remember how to put it back in Main Menu) but it works fine, videos and everything! :)

---

### Post by al.adab on 2009-08-12
to be able to launch Opera from the main menu: 

[http://ubuntuforums.org/showthread.php?t=225390](http://ubuntuforums.org/showthread.php?t=225390) 

(jump to the paragraph: "D. If you have an application which has an icon in the Ubuntu Applications menu, but only opens from the command line").

---

