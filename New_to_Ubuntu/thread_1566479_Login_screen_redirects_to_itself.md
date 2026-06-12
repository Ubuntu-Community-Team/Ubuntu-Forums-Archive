---
title: "Login screen redirects to itself"
date: 2010-09-02
forum: New to Ubuntu
---

### Post by novateando on 2010-09-02
Hi,

I have recently installed Ubuntu 10.4 on my MacBook Pro (and its great!) and after just having installed broadcom drivers (which worked) and upgrading alsa (I couldn't check if it worked or not), I cannot log in into my account. The thing is that when I get the login screen I insert my password, which is accepted, and then the screen goes black and the login screen reappears again. I suspected that I had made a mess when trying to make an startup application of the broadcom driver's, so I booted in recovery mode and deleted all the files from the folder of the drivers. The problem was not solved, so I went into the folder of startup applications and deleted alsa-drivers. Of course, the problem is not solved and I have not the slightest idea of what I have done.

Any idea?

---

### Post by diablo75 on 2010-09-02
ALSA.... Did you uninstall PulseAudio?

How exactly did you install the wireless drivers and what did you tell it to autorun at login?  Wireless drivers usually take care of themselves once you enable them; I've never heard or seen anybody have to put anything in the starup programs manager to get it to work...

---

### Post by novateando on 2010-09-02
I followed [these instructions]("http://www.broadcom.com/support/802.11/linux_sta.php") (all the other broadcom drivers failed for my version) to install the network drivers (README file). In particular, I failed when I reached this point: 
 [...] 3: Setup to always load at boot time.

The procedure to make a module load at boot time varies from distro to
distro.  Consult the docs for your specific distro to see how.  The 
following seems to work for my setup on Fedora and Ubuntu.  Check your 
docs to see the procedure for your distro.

Follow these steps to have the driver load as part of the boot process:

# load driver as described above [...]

the first step didn't work, and as I already checked, the drivers didn't boot automatically, so I had to do all the process once and again. As I couldn't find any other way to make the drivers boot, I tried something in the "Startup applications", but I don't remember exactly what I wrote in the command line, but it was something from the README file.

And the Alsa drivers that I installed were those 1.0.23, following t[hese instruction]("http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/")s.

---

### Post by novateando on 2010-09-02
I'm going to reinstall Ubuntu. It might be easier than trying to resolve a problem of unknown origin...

Thanks, anyway!

---

### Post by apmcd47 on 2010-09-02
Before you reinstall Ubuntu, press Ctrl-Alt-F1 to take you to a tty terminal (virtual terminal?) and try logging in from there. If it is a problem with your profile you will at least get some idea of the problem and be able to edit your profile. 

Andrew

---

### Post by novateando on 2010-09-02
I already tried that, but the problem of being using a Mac keyboard is that to press F1 I have to press function, and the command doesn't seem to work...

---

### Post by novateando on 2010-09-03
It seems the problem was the I removed evolution and its related packages!

---

### Post by D.J.H. on 2010-10-27
How did you solve it?

I have the same problem.
I already tried CTRL+ATL+F1: I can login there however I cannot seem to open the /home/<user>/.xsession-errors file it says access is denied.

Is there any way I can change this or that I can solve the login problem?
I'm totally new to linux, so a more comprehensive explanation would bne appreciated?:)

---

### Post by novateando on 2010-10-28
I am sorry, I did not solve it. In my case, it was finally clear that the problem was that I deleted some packages related with Evolution and Gnome Desktop. I think I could have reinstalled them from root but I couldn't manage with my first efforts, so I decided to save my documents (from root) and reinstall ubuntu.

---

### Post by roaftech on 2010-10-28
I am having a similar problem - the login just loops round.

Process from boot:

[LIST=1]
[*]BIOS screen
[*]purple Ubuntu 10.10
[*]splash screen with short roll of drums
[*]login screen < correct login
[*]splash screen with long roll of drums
[*]brief glimpse of menu bar, then screen goes black
[*]loops back to#3 above
[/LIST]
as infinitum.

This is a new clean installation onto a laptop that was running U9 without any probs. When used as a live disk a similar process occurred, apparently asking for the previous username and password, but looping round back to the login. So I tried a clean installation. This is a stand-alone machine with no internet connection and no other software loaded.

I have re-installed 10.10 about 8 times, running WipeDisk in between. The latest installation completed ok without any notifiable probs, but it still won't get past the loop.


> **apmcd47 said:**
> Before you reinstall Ubuntu, press Ctrl-Alt-F1 to take you to a tty terminal (virtual terminal?) and try logging in from there. If it is a problem with your profile you will at least get some idea of the problem and be able to edit your profile. 

Andrew

I have just tried this, and I can log-in ok at the DOS prompt - then what? How do I recover the GUI?

---

### Post by worm1337 on 2010-11-28
ok, same problem here after installing 10.10

i have a rough solution just to make it work, but i would really appreciate anything more elegant

while in login screen press CTRL + ALT + F1 in order to enter console

login using your usual username and password

now you have to close gdm by typing:  
```
sudo /etc/init.d/gdm stop
```

and just restart it:
```
startx
```

cheers

---

### Post by tajiknomi on 2010-11-28
> **novateando said:**
> I'm going to reinstall Ubuntu. It might be easier than trying to resolve a problem of unknown origin...


[SIZE=2]If you had decided to reinstall Ubuntu, so take one step before it...
  
Go to your *home-directory* and Delete the file named "***.profile"*** and then reboot....

  Hope this work...:razz:[/SIZE]

---

