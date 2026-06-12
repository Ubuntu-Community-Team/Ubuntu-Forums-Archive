---
title: "How to open text editor as root"
date: 2010-07-19
forum: New to Ubuntu
---

### Post by mid_life_crisis on 2010-07-19
The source of the problem is that I am running the latest version from a USB drive and having a sound problem.  I have attempted to use various forms of Linux (including Ubuntu) in the past and been very frustrated.  This time, things are going much better.  I am able to get the wireless network running, which I was never able to do before (actually, I couldn't get any networking to function before) so right there is a huge, encouraging improvement.  
The last hardware hurdle this time is sound.  When I plug in headphones under Ubuntu the main speakers stay on.  I have found numerous things to try, but the most promising (and simple) approaches require editing what amounts to an ini file.
Unfortunately this requires root login.  I don't want to have to create multiple logins for this system.  I don't want to log in as root all the time for security reasons while online, but I also like not having to enter username and password every time I open the computer at home.  If I understand this correctly, once I enable root, I also need to create a limited account for "normal" operations that don't require root privileges. How can I do things as root when I need to but otherwise be able to just open the computer and start working without all the login nonsense?  It doesn't help that I'm fifty and have enough IDs and passwords to remember as it is without adding unnecessary ones to the list.
Thank you

---

### Post by takisan on 2010-07-19
A simple **sudo gedit **should do the trick. All you do is type your password (but don't close out of the terminal.

---

### Post by WRDN on 2010-07-19
If you want to enable the root account (not advised), then you can Google for it, but it is against the Forum Rules to show how here.

You can temporarily become a super user using sudo (Super User DO).
gksudo is the graphical version. So, for example, if you want to open "nano", a terminal text editor, as a super user, you could type:

```
sudo nano
```

Or with a file:

```
sudo nano /path/to/my/file
```

For a graphical text editor, such as gedit:

```
gksudo gedit
```

Or:

```
gksudo gedit /path/to/my/file
```


Hope this helps :)

---

### Post by anaconda on 2010-07-19
I have one machine, where the speaker sound stays on after plugging headphones in..

And I "solved" the problem by manually selecting headphones as the audio out device, when I want the sound to come only from headphones..

the setting can be found from:  (in 9.10 or 10.04)
System>preferences>sound  


(installing 10.04 would solve my problem properly)

---

### Post by louis--taylor on 2010-07-19
> **anaconda said:**
> I have one machine, where the speaker sound stays on after plugging headphones in..

And I "solved" the problem by manually selecting headphones as the audio out device, when I want the sound to come only from headphones..

the setting can be found from:  (in 9.10 or 10.04)
System>preferences>sound  


(installing 10.04 would solve my problem properly)

Wrong thread?

---

### Post by mid_life_crisis on 2010-07-19
> **louis--taylor said:**
> Wrong thread?

The response is to the root cause of my problem.

---

### Post by mid_life_crisis on 2010-07-19
> **anaconda said:**
> I have one machine, where the speaker sound stays on after plugging headphones in..

And I "solved" the problem by manually selecting headphones as the audio out device, when I want the sound to come only from headphones..

the setting can be found from:  (in 9.10 or 10.04)
System>preferences>sound  


(installing 10.04 would solve my problem properly)

I am on 10.04 and do not have that option under audio properties.  I found any number of posts with a line to add but have been unable to edit thus far.
I'll try the offered advice regarding Sudo tonight.

---

### Post by mid_life_crisis on 2010-07-19
> **WRDN said:**
> /snip/
You can temporarily become a super user using sudo (Super User DO).
/snip/

Interesting.  I had assumed sudo was something clever like an alternate spelling for "pseudo root".
I've seen this command before but have had trouble making it work.  I'll give a whack at opening gedit from a command line tonight.
Thank you.

---

### Post by da burger on 2010-07-19
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) << That explains how ubuntu's root/sudo system works.

---

### Post by khushalb on 2010-07-20
Well can we login as an administrator itself during startup. I think there's this option of gdm.conf but its not available on the new ubuntu 10.04. Any solutions to login as a root? is it recommended.

---

### Post by da burger on 2010-07-20
There is no reason to want to log in as root, anything you need to do as admin can be done with sudo and gksudo. In fact it's against forum policy to give tutorials on logging in as root graphically.

---

### Post by bodhi.zazen on 2010-07-20
> **WRDN said:**
> If you want to enable the root account (not advised), then you can Google for it, but it is against the Forum Rules to show how here.

You can temporarily become a super user using sudo (Super User DO).
gksudo is the graphical version. So, for example, if you want to open "nano", a terminal text editor, as a super user, you could type:

```
sudo nano
```Or with a file:

```
sudo nano /path/to/my/file
```For a graphical text editor, such as gedit:

```
gksudo gedit
```Or:

```
gksudo gedit /path/to/my/file
```
Hope this helps :)

If you are going to use nano/vim or an editor in your terminal, all your sudo commands can be shortened

```
sudo -e /path/to/my/file
```

I believe Ubuntu 10.04 now uses nano as default, if not, and you want to change, set an editor in ~/.bashrc

```
export EDITOR='nano'
```

---

### Post by irv on 2010-07-20
I have some script files on my server you can download and put in your /home/user-name/.gnome2/nautilus-scripts/ directory. When you open up nautilus and right click on it and go to scripts it will list all the scripts you have in this directory. See screen shop.
Here is the link to download them: [http://wabasha-server.net/Nautilus%20Scripts/]("http://wabasha-server.net/Nautilus%20Scripts/")
Make sure you set them all for read/write and execution or they will not show up in the list.
[ATTACH]164049[/ATTACH]

---

