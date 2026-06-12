---
title: "applications bar has dissapeared"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by M0GEJ on 2009-01-12
last time I logged in the applications bar had dissapeared. I managed to get into the terminal (alt-f2)and tried the following commands-

xfce-setting-show = settings manager appears, but it will not let me select 'panel'

xfce-session = command not found

xfce4-session = **Message: another SSH agent is running at: tmp/ssh-NVXVyf5810/agent.5810

xfce-panel = command not recognised

xfce4-panel = applications tab reappears, but when I close down  the terminal it goes missing again

any ideas for a fix?

---

### Post by minsf on 2009-01-12
i had the same problem this morning. i booted from the live cd, and while running gparted the application bar dissappeard. i solved it by alt+ctrl+f1 to get a shell session outside gnome. then i restarted gnome with 
```
sudo /etc/init.d/gdm restart
``` and peace on earth...
the problem is that is seems like you are using xubuntu (xfce). so instead of gdm (=Gnome Desktop Manager), there should be some other executable in your /etc/init.d directory that corresponds to xcfe. try to locate it, and then restart is by ```
sudo /etc/init.d/some_xcfe_desktop_manager_name restart
```

---

### Post by M0GEJ on 2009-01-12
how would I go about locating that file?

---

### Post by M0GEJ on 2009-01-12
Ok- so when I try "cd /etc/init.d" , hit enter and then type "ls" I get a longish list. I don't really know what I should be looking for here (if anything), but tried the only two items on the list beginning with x - (x11-common and xserver-xorg-input-wacom), but this obviously doesn't work.

where should I look now???

---

### Post by minsf on 2009-01-12
I got a couple of ideas:

1. go to the command line interface with alt+ctrl+f1 (NOT with alt+f2). maybe you'll need to log in with username and password at that point. after that, enter: ```
xfce-panel
``` and then enter ```
exit
``` to go back to the GUI. did this help?

2. if not, try again alt+ctrl+f1, log in, and in the command line interface that you get, try to enter:```
sudo startx
``` and if you dont get the gui automatically, try to enter "exit" again.

3. if this still doesnt help, go to the command line interface again with ALT+CTRL+F1 and after you "cd" again to the /etc/init.d directory, try to look for something that starts with "start". let's say that you find something interesting like "startxfce4", then try to enter ```
sudo /etc/init.d/startxfce4 restart
```

4. if all this doesn't work and no xfce expert join our thread, then try to post the output of "ls /stc/init.d" and we can look for that file together :)

---

### Post by M0GEJ on 2009-01-13
It all seems to be working now.

Cheers

---

### Post by minsf on 2009-01-13
glad to hear all is working now. just out of curiousity, how did you make it work? by the way, do you have startxfce4 in the directory /etc/init.d?
also, we should probably mark this thread as solved (it's in the "thread tools" above")
have fun :)

---

