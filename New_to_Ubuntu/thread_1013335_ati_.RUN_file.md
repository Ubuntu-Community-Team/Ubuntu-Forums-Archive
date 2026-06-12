---
title: "ati .RUN file"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by bostock73 on 2008-12-16
my file is this -

ati-driver-installer-8-12-x86.x86_64.run

thats my graphics driver.
Its placed on my desktop. 

how do i install it?

---

### Post by taurus on 2008-12-16
Applications -> Accessories -> Terminal
```
cd ~/Desktop
chmod 755 ati-driver-installer-8-12-x86.x86_64.run
sudo ./ati-driver-installer-8-12-x86.x86_64.run
```

---

### Post by bostock73 on 2008-12-16
taurus... I'm very new to ubuntu and that command AMAZED ME!
ive been looking all day for this to work!

so could you explain what each command bit did? how does it work?

---

### Post by taurus on 2008-12-16
Since you saved ati-driver-installer-8-12-x86.x86_64.run to your desktop, the first command is to change directory from your $HOME to Desktop (not desktop since Unix/Linux is case sensitive.  In other words, desktop is not the same as Desktop.).  The ~/ means $HOME.  So if your login name is bostock, ~/Desktop is the same as /home/bostock/Desktop.

The second command changes the permissions to executable so you can run it.

The third is to install the driver with root privilege since you need to write to the system.  Whenever you need to write or modify something outside of your $HOME, you need root privilege since you don't have permissions to modify anything except your own $HOME.  So, be real careful when you use the sudo command because you could trash your machine if you're not careful with it.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by bostock73 on 2008-12-16
ok well it all installed fine.
in my restriced drivers bit i saw my wireless card there so i enabled it.

i restarted but ubuntu doesnt boot up, and on my xp partition my wireless card now doesnt work! it says its already in use!

whats going on?

---

### Post by XGC75 on 2008-12-29
Hey all thanks for dropping in...

Just got my new IceQ Radeon 4850 and driver from the AMD (ati) website. Got the same exact file, in fact. Lucky me I stumbled on this thread and had my console ready, but I got a different result:

```
op@A-1-0:~$ cd Desktop/
op@A-1-0:~/Desktop$ ls
**ati-driver-installer-8-12-x86.x86_64.run**  menu.lst~
GoogleEarthLinux.bin                      MI passphrase.txt
iwx                                       untitled folder
menu.lst                                  week at a glance.png
op@A-1-0:~/Desktop$ chmod 775 ati-driver-installer-8-12-x86.x86_64.run
op@A-1-0:~/Desktop$ sudo ./ati-driver-installer-8-12-x86-.x86_64.run
[sudo] password for op: 
sudo: ./ati-driver-installer-8-12-x86-.x86_64.run: command not found
op@A-1-0:~/Desktop$ 
```

... I didn't spell it wrong, did I??

---

### Post by markbuntu on 2008-12-29
You have a typo in the command.

---

### Post by garrydog on 2009-01-06
Hi
I to am in the same position as Bostock73 ,I put the command posted by Taurus into the terminal box ,and up came the ATI install screen .But i can't hit the next button as the pannel is so big ,I have tryed hitting the tab and enter ,space bar ,back space but all failed .What can be done now?.
Thanks.

---

