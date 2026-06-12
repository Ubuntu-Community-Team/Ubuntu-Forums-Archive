---
title: "Upgraded to Ubuntu 8.10 from 8.04 cannot login"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by thedeluge on 2009-01-07
Upgraded to ubunto 8.10 from 8.04,but cannot log in when i boot.I get a white screen and everything freezes, even ctrl+alt+backspace doesn't work..removed compiz after  reading some posts, but same problem afterwards.Any advice would be helpful!
Thanks

---

### Post by tuxxy on 2009-01-07
When you hit the white screen have you tried pressing CTRL + ALT + F2 to bring up a terminal login, here we could run commands from to fix the issue.

---

### Post by thedeluge on 2009-01-07
Hi tuxxy,
CTRL + ALT + F2 doesnt work either. I am restarting manually and going to the recovery mode to try out things...
cheers

---

### Post by stchman on 2009-01-07
> **thedeluge said:**
> Upgraded to ubunto 8.10 from 8.04,but cannot log in when i boot.I get a white screen and everything freezes, even ctrl+alt+backspace doesn't work..removed compiz after  reading some posts, but same problem afterwards.Any advice would be helpful!
Thanks

Did you do a clean install or go the upgrade route?  If upgrade I recommend you do the clean install route as it is actually faster.

---

### Post by abn91c on 2009-01-07
after removing compiz did you do: [COLOR="Blue"]metacity --replace[/COLOR]

---

### Post by thedeluge on 2009-01-07
I upgraded it( a rush of blood to the head,the previous version  was working very well:)).

---

### Post by abn91c on 2009-01-07
> **thedeluge said:**
> I upgraded it( a rush of blood to the head,the previous version  was working very well:)).
Not sure what you mean, but that the command to revert ubuntu back to the default windows manager.

---

### Post by thedeluge on 2009-01-07
> **abn91c said:**
> after removing compiz did you do: [COLOR="Blue"]metacity --replace[/COLOR]
just tried and it says:

 window manager error:unable to open x display

---

### Post by abn91c on 2009-01-07
> **thedeluge said:**
> just tried and it says:

 window manager error:unable to open x display
you may have to do sudo apt-get install metacity
look at this thread also: [http://ubuntuforums.org/showthread.php?t=1033256&highlight=metacity](http://ubuntuforums.org/showthread.php?t=1033256&highlight=metacity)

---

### Post by wirewrapped on 2009-01-07
Happened to me to. Its the magnify plugin in Compiz. You want to disable, but you can't login! So!

"1. In the login screen, select Options > Select Session...
2. Choose "Failsafe Terminal" and press "Change Session"
3. Write your username and password, and click the info window away

Then:

Method A (if you use the GConf backend for compiz, which is the default):
--------
4A. At the terminal, type
    gedit .gconf/apps/compiz/general/allscreens/options/%gconf.xml
    and press enter
5A. Delete these three lines:
      <li type="string">
        <stringvalue>mag</stringvalue>
      </li>
6A. Click on save
7A. Select File > Quit, type "exit" in the terminal and press enter. Then login as usual.

Method B (if you use the GConf backend for compiz, which is the default):
--------
4B. At the terminal, type
     gconf-editor
     and press enter
5B. Navigate to apps/compiz/general/allscreens/options on the left pane
6B. On the right pane, double-click on "active_plugins"
7B. Select "mag" in the list, click "Remove" and press OK
8B. Exit gconf-editor using the File > Quit option, type "exit" in the terminal and press enter. Then login as usual.

Method C (if you have ccsm installed, which it is not by default)
--------
4C. At the terminal type
    ccsm
5C. Deactivate the Magnifier plugin.
6C. Exit ccsm at the "Close" button, type "exit" in the terminal and press enter. Then login as usual."

All credit to pablomme on this forum for ubuntu bugs on the launchpad: [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/276311](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/276311)

I did not notice this when I upgraded from hardy. So I reinstalled Intrepid only to find out I could have used this simple method! Use method C is you installed CMSS through synaptic.

I really hope this helps so you can get straight into awesome ubuntu.:wink:

[No credit to me, but [https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/276311]](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/276311])

---

