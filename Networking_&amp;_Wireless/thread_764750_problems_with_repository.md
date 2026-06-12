---
title: "problems with repository"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by faytaliti on 2008-04-24
I am able to connect to the repository install packages and update only after I ping the corresponding repository index server. Can anyone solve this problem........ :confused:

I use this simple code to do so

```
#!/bin/bash
ping -a -c 2 in.archive.ubuntu.com | zenity --progress --auto-close --auto-kill --title="Archive" --text="Pinging..."
ping -a -c 2 security.ubuntu.com | zenity --progress --auto-close --auto-kill --title="Security" --text="Pinging..."
```

---

### Post by Sicundercover on 2008-04-24
Im haveing this exact same problem, nothing is connectin not even synaptic. I get several repository fails when trying to use update manager and if I try to do a sudo apt-get install then I get a message saying

```
Do you want to continue [Y/n]? y
0% [Connecting to us.archive.ubuntu.com (91.189.92.3)]
0% [Connecting to us.archive.ubuntu.com (91.189.88.46)]

```
It just sits there forever until i hit enter then it tries another ip and sits.

---

### Post by faytaliti on 2008-05-21
the problem is probably ipV6.... here's how to disable it..........

->go to the gnome terminal and type 

          ```
sudo gedit /etc/modprobe.d/aliases
```->Give your password in the terminal if prompted to do so.
->If everything is right then you should see a text editor.
->There, in the text editor you should see the line " alias net-pf-10 ipv6 ".
->Modify it to " alias net-pf-10 off ".
->Then immediately reboot.
->Once you do so and log back into your user go to the gnome terminal once again
->There type.....

          ```
lsmod | grep v6
```->If this returns nothing then you are done.:popcorn:

---

