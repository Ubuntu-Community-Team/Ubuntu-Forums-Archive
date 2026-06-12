---
title: "Google Earth exec: 19: ./googleearth-bin: not found"
date: 2010-12-23
forum: New to Ubuntu
---

### Post by Rabhak on 2010-12-23
I thought I've successfully installed google earth but after installation i got this message appeared in the terminal "exec: 19: ./googleearth-bin: not found"

This is my second attempt in installing google earth. . and now i got two (2) google earth icons in my application which i really couldn't get rid of.. 

Now I'm planning to uninstall it but still it remains in my application>internet>and 2 google earth icons..

Thanx!

---

### Post by mikewhatever on 2010-12-23
You can remove any menu icon by right clicking the menu and selecting 'Edit Menus'.

---

### Post by Rabhak on 2010-12-23
> **mikewhatever said:**
> You can remove any menu icon by right clicking the menu and selecting 'Edit Menus'.

There's no such thing as edit menu.
all i could see is this:
Add this launcher to panel
Add this launcher to desktop
Entire Menu > Add this as drawer to panel
              Add this as menu to panel

---

### Post by Rabhak on 2010-12-23
Ok guys,
I just wanted to install google earth.
But a lot of problems are occurring.

The google earth icons are useless (not working).

My plan is, I wanted to uninstall it completely and install it again. The problem is, I ain't got any idea how to do it.

---

### Post by beew on 2010-12-23
> **Rabhak said:**
> There's no such thing as edit menu.
all i could see is this:
Add this launcher to panel
Add this launcher to desktop
Entire Menu > Add this as drawer to panel
              Add this as menu to panel

Go yo System > Preference > Main Menu. Choose "Internet" on the left panel. Then you will see on the right panel all the launcher icons that appear in Applications > Internet. You see two googleearth because there are two entries for it here. Just delete one.

This is the easy part of your question. :)

---

### Post by mikewhatever on 2010-12-23
> **Rabhak said:**
> There's no such thing as edit menu.
all i could see is this:
Add this launcher to panel
Add this launcher to desktop
Entire Menu > Add this as drawer to panel
              Add this as menu to panel

Well, how about System->Administration->Main Menu?
As for installing, uninstalling and what not, check out the guide.
[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)

---

### Post by Rabhak on 2010-12-24
> **mikewhatever said:**
> Well, how about System->Administration->Main Menu?
As for installing, uninstalling and what not, check out the guide.
[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)


It's System>Preferences>Main Menu. 
Thanks Mike! You're really a genius.

Now I just have to uninstall it completely and install it as properly as possible. Mind if you share some help Mike?

---

### Post by Rabhak on 2010-12-24
> **beew said:**
> Go yo System > Preference > Main Menu. Choose "Internet" on the left panel. Then you will see on the right panel all the launcher icons that appear in Applications > Internet. You see two googleearth because there are two entries for it here. Just delete one.

This is the easy part of your question. :)

Hey beew. you're right! now i deleted two of them!

---

### Post by Rabhak on 2010-12-24
Thank God i can use google earth now!!

I've installed it by following these steps:
System > Administration > Synaptic Package Manager
I searched google earth and checked it. 

Last thing is hit apply!

Yow! yow!

---

### Post by mikewhatever on 2010-12-24
From what I remember, google-earth installed itself into /opt if the installer was run with admin privileges, or into the home folder if not.
... the link I posted has an 'Uninstall' section.;)

---

### Post by beew on 2010-12-24
If you install from Synaptic it is probably version 5.2, it will crash at launch with signal 11 or something like that. The fix is to disable startup tip (uncheck or check the box really quickly before ge crashes, don't remember which one) If you do that it won't crash on start up, but it will crash if you are not careful and click the wrong box while surfing. Since it is too much trouble I have pinned my version to 5.1.X and shall wait for the next version.

---

### Post by Rabhak on 2010-12-24
> **beew said:**
> If you install from Synaptic it is probably version 5.2, it will crash at launch with signal 11 or something like that. The fix is to disable startup tip (uncheck or check the box really quickly before ge crashes, don't remember which one) If you do that it won't crash on start up, but it will crash if you are not careful and click the wrong box while surfing. Since it is too much trouble I have pinned my version to 5.1.X and shall wait for the next version.


Thnaks for the tip brother!
I'm workin on it!
Peace!

---

### Post by Schugy on 2010-12-27
You can install [google earth 6]("http://dl.google.com/earth/client/current/GoogleEarthLinux.bin") with the official loki-installer.
To run googleearth you need some lsb-packages (one installs qt4-gui).
I don't know which ones aren't needed.

lsb-base        4.0-0ubuntu8
lsb-core        4.0-0ubuntu8
lsb-desktop     4.0-0ubuntu8
lsb-graphics    4.0-0ubuntu8
lsb-invalid-mta 4.0-0ubuntu8
lsb-languages   4.0-0ubuntu8
lsb-multimedia  4.0-0ubuntu8
lsb-printing    4.0-0ubuntu8
lsb-qt4 4.0-0ubuntu8
lsb-release     4.0-0ubuntu8
lsb-security    4.0-0ubuntu8

---

### Post by Trandre on 2010-12-27
I have the same problem and followed the instructions. 

But now the icon never comes up in my main menu. So I went to /opt and tried to start it, but it said that the application was not set to trusted. 

So I entered as attached in the terminal. This opened Google earth but gave my a warning as stated in the attached terminal view. 

Q1: What is the warning about
Q2: How can go in to properties and change to trusted with adm rights?
Q3: Will the change to trusted solve my main menu shortcut problem?
   
[HTML]famfem@ubuntu:~$ cd /opt
famfem@ubuntu:/opt$ dir
google
famfem@ubuntu:/opt$ google
google: command not found
famfem@ubuntu:/opt$ sudo google
[sudo] password for famfem: 
sudo: google: command not found
famfem@ubuntu:/opt$ sudo googleearth
/usr/bin/googleearth: line 4: warning: setlocale: LC_NUMERIC: cannot change locale (en_US.UTF-8): No such file or directory
[/HTML]

---

### Post by Trandre on 2010-12-28
Bump

---

### Post by Trandre on 2011-01-07
last try, Bump

---

### Post by oldos2er on 2011-01-07
Don't use 'sudo' to run googleearth.

How did you install googleearth, and which version did you install? If it's the v6 beta, try these instructions: [http://ubuntuguide.net/how-to-install-google-earth-6-beta-in-ubuntu-with-some-problem-fixed](http://ubuntuguide.net/how-to-install-google-earth-6-beta-in-ubuntu-with-some-problem-fixed)

---

### Post by jcolyn on 2011-01-07
Proper way to install Googleearth:

If you want to install the latest current version of Googleearth follow these simple steps and you will have it up and running in no time.

First though you will need to purge any installs or attempts at installing Googleearth.

These terminal entries have to be entered exactly as typed below so you may want to copy/paste into your terminal.

To start: Open a terminal and enter ```
sudo apt-get install lsb-core
``` Once done enter ```
sudo apt-get install googleearth-package
``` After the package is installed enter ```
sudo make-googleearth-package --force
``` This process will take several minutes and you will see many warning notices but ignore them.

Once the above process is completed close the terminal and go to your /home folder where you will find a googleearth_xx.deb package. Double-click it and follow instructions.

Once installed you should have the Googleearth link in your Internet folder.

Enjoy

---

### Post by Trandre on 2011-01-09
Thank you, now it works :-)'

But I cannot find the icon to execute the programm. I got it to run by typing sudo googleerth in terminal. I did not work without admin rights even. I did remove icons following an instruction in trying to get it to work. Do you know how I can enable the icons and get it to run without admin privliges?

---

### Post by Trandre on 2011-01-12
Solved my remaining issues in this post, thanks guys for your help. :-)

---

### Post by lads on 2012-01-13
I stumbled upon this thread after hitting the same issue. I followed Colyn's recipe, which looked very promising, but things have remained more or less the same: 

```
$ googleearth %f
/usr/bin/googleearth: 14: /usr/lib/googleearth/googleearth-bin: not found
$ ls -la /usr/lib/googleearth/googleearth-bin
-rwxr-xr-x 1 root root 5452 2011-05-17 09:42 /usr/lib/googleearth/googleearth-bin
```

Any further insight appreciated. Best.

---

