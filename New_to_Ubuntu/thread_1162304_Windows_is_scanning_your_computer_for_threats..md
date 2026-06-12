---
title: "Windows is scanning your computer for threats."
date: 2009-05-17
forum: New to Ubuntu
---

### Post by jw1405 on 2009-05-17
I have firefox set to open windows from previous session, and this website has firefox locked up. "http://atomscan4.info/22/?uid=141" 

So now I close one pop up and another one pops up, I close that one and the first one comes back. 

pop up#1:Windows is scanning your system for threats. The scanning is provided by our official partner Internet Antivirus Pro.
Please refrain from closing the window until the scanning is finished.
We highly recommend you to install the full version of Internet Antivirus Pro scanner to monitor your PC for threats and on-time security system updates.


pop up#2:Please note that Spyware is highly malicious for your PC information privacy.

If you want to install the full version, please click "Ok", wait for the page to load, start the installation process and follow the instructions.

If you want to wait for scanning results to appear, please click "Cancel".

After Internet Antivirus Pro is installed, you can close the scanning window and remove Spyware from your computer.


Nothing else in firefox is working, cannot change to different tab, or exit, nothing.....

     Please Help, What can I do?

---

### Post by mike555 on 2009-05-17
That is an old trick to install junk on Windows , if your using Ubuntu you probably don't need to worry , try starting Firefox in safe mode and see if that helps if it does clear your history and try starting it again ...

---

### Post by jimmy the saint on 2009-05-17
try going to ~/.mozilla/firefox/{yourprofile} and look for a file that is named something similar to sesionstore.js.  It may be in a subdirectory (I am just using google to gather some basic info).  If you use tabmixplus for your sessions it will be in a subdirectory called sessionbackups.

Try deleting the relevant file.  If that doesn't work, a more final solution would be ```
sudo apt-get purge firefox
``` which will delete firefox and its config files.  I would backup my bookmarks and plugins first before going that route to save time after reinstalling.

Edit:mikes suggestion seems easier, but if it doesn't work, deleting the session files should.

---

### Post by khelben1979 on 2009-05-17
Take a look at [this page]("http://www.cnet.com/windows/spyware-removers/?tag=ltcol;nav") from download.com if you're using Windows. Spy Hunter from [Enigma Software]("http://www.enigmasoftware.com/") is one of my own favourites, although it's sadly not enough.

What operating system are you using?

---

### Post by Dr. Nick on 2009-05-17
If your in gnome this should work. In an empty part of the panel right click, hit add to panel, the add "Force Quit" then when you launch FF and it freezes click the force quit button then click in the firefox window. Then when you restart FF it should ask if you want to start a new session or restore the old, Start a new session then go to tools, clear private data.

---

