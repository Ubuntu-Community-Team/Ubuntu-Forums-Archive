---
title: "How to use Logitech Quickcam Deluxe?"
date: 2009-11-02
forum: New to Ubuntu
---

### Post by grastafaram on 2009-11-02
Hi, I have Ubuntu 9.04 on my Dell and it doesn't recognize my "Logitech quickcam deluxe for notebooks" webcam.  I really need to be able to use it with Skype, so if anyone could help me out that would be great.  Oh, I don't speak programmer so any help will have to be pretty clear, for the average guy kind of stuff.

Thanks

---

### Post by Locke_99GS on 2009-11-02
I don't know anything about configuring skype, but a simple way to find out if the system detected it and can use it (v4l2) would be to simply install *cheese* and see if you can get a camera image in there.

```
sudo apt-get install cheese
```

If it works, then somebody who knows more about configuring Skype will be able to help you. If it doesn't, I (or somebody) will help you to get it functioning with v4l2.

---

### Post by grastafaram on 2009-11-02
Thanks,  where should I type "sudo apt-get install cheese", I'm really new to this.

---

### Post by Locke_99GS on 2009-11-02
In the menu at the top left of the screen, do "Applications -> Accessories -> Terminal" to open a terminal. Remember where this is, as although many many things can be done with the GUI, it is often faster to perform and instruct others to do from the terminal. Much of you help in the forums here will direct you to the terminal.

Also, **NEVER** run the command "*sudo rm-rf /*" if instructed to do so. Never ever.

---

### Post by grastafaram on 2009-11-03
Thanks a lot for your help, I always wondered where to write those commands.  Well, this is what happened when I tried that, any ideas?

graham@graham-laptop:~$ sudo apt-get install cheese
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
graham@graham-laptop:~$ sudo dpkg --configure -a
graham@graham-laptop:~$ sudo apt-get install cheese
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  sun-java6-jre: Depends: sun-java6-bin (= 6-16-0ubuntu1.9.04) but it is not going to be installed or
                          ia32-sun-java6-bin (= 6-16-0ubuntu1.9.04) but it is not installable
                 Recommends: gsfonts-x11 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
graham@graham-laptop:~$ apt-get -f install
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by Locke_99GS on 2009-11-03
The system's instructions will tend to assume you are root. Prefix apt-get with *sudo* to run it as root.

```
sudo apt-get -f install
```

---

### Post by grastafaram on 2009-11-03
Ok, thanks, that worked and then it started installing packages.  blue screen came up that said "Configuring Sun -Java6- bin" which was a license agreement page, I scrolled to the bottom and tried to click on "ok", but it doesn't work.   Now I can't get rid of the screen and I can't accept the license agreement.  What can I do?

---

