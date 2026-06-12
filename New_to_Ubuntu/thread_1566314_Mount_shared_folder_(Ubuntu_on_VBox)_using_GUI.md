---
title: "Mount shared folder (Ubuntu on VBox) using GUI"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by Zbigniew on 2010-09-02
Hi, 
using Ubuntu on VirtualBox (guest OS- Win7). 
I can find instructions to mount a drive or folder using the command line, but it is too complex for me. 
help.ubuntu.com/community/VirtualBox/SharedFolders

Can you suggest the way using graphical tools to complete this? All set up from VBox management- I just need Ubuntu to see it and mount.

---

### Post by bredman on 2010-09-02
Can you explain which command you need a GUI replacement for?

From the example on the link you provide, there are only 3 commands.

$ cd Desktop
$ sudo mkdir ubuntushared
$ sudo mount -t vboxsf -o uid=1000,gid=1000 shared ubuntushared/ 

For the first two commands, right-click a blank space on the Desktop and select "Create Folder"

For the third command, I don't know how to do it by GUI, but I'm sure somebody may be able to suggest a way.

---

