---
title: "skype wont install"
date: 2010-04-28
forum: New to Ubuntu
---

### Post by iamsolost on 2010-04-28
an error keeps popping up as i try to install skype.......error dependencies not satisfiable libgcc1.....what the heck is this and how do i get around it....
ubuntu version 9.1 or something like that. 32 bit and help would be awesome....pleassse. haha

---

### Post by ttshivers on 2010-04-28
There is another way to install Skype so all the dependencies for it are also installed.  To do this follow these steps:
 
[LIST=1]
[*]Open the Update manager
[*]Click on settings
[*]Click the tab:  other software
[*]click the button "add"
[*]Add the following text into that:  ```
deb http://download.skype.com/linux/repos/debian/ stable non-free

```
[*]click add source and close all windows
[*]open the Synaptics package manager
[*]do a search for Skype
[*]right click on the Skype result that comes up and select mark for install
[*]click the button "upgrade"
[*]it should install
[/LIST]

---

### Post by iamsolost on 2010-04-28
when i click on update manager....it says all updates are installed....and it doesnt give me anything as far as to click on....as far as the synaptic way...no luck either. i can see the option for update but it wont let me click on anything but mark for install....when it tries to install i get this....


skype:
  Depends: libgcc1 (>=1:4.3) but 1:4.2.4-1ubuntu4 is to be installed
 Depends: libqt4-dbus (>=4.4.3) but it is not installable
 Depends: libqt4-network (>=4.4.3) but it is not installable
 Depends: libqtcore4 (>=4.4.3) but it is not installable
 Depends: libqtgui4 (>=4.4.3) but it is not installable
  Depends: libstdc++6 (>=4.3) but 4.2.4-1ubuntu4 is to be installed

---

### Post by ttshivers on 2010-04-28
I really dont know how to help you.  Hopefully someone who knows how will find this thread.

---

### Post by iamsolost on 2010-04-28
ok great, thanks for the advice!

---

### Post by anewguy on 2010-04-29
> **iamsolost said:**
> an error keeps popping up as i try to install skype.......error dependencies not satisfiable libgcc1.....what the heck is this and how do i get around it....
ubuntu version 9.1 or something like that. 32 bit and help would be awesome....pleassse. haha  It looks like the Skype install is looking for libs that are at a newer release than in your Ubuntu.  Could you verify the following:

- what version of Ubuntu are you running?

- what version of Skype are you trying to download?

- if the first attempts where not through apt-get or via Synaptic Package Manager, please post what you were doing.  It may be neccessary to "reverse" what you were doing before we can get it to install.

Dave ;)

---

### Post by pastalavista on 2010-04-29
Try this then. Open System/Administration/Software Sources (same tool as update mnager settings), click the 'Other Software' tab, click 'Add' and paste in the line offered above:

deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

Then open Applications/Accessories/Terminal and paste in this line
```
sudo apt-get update && sudo apt-get install skype
```

The laubcher will appear in the Applications/Internet menu.

---

