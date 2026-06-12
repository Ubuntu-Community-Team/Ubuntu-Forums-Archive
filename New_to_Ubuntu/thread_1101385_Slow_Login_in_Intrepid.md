---
title: "Slow Login in Intrepid"
date: 2009-03-20
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-03-20
My boot-up time (from BIOS till I can enter my username and password) is: between 55s and 1 min.

My login time (from where I hit enter after putting in my password and till the time the disk activity light stops) is 29s (without compiz) and 35s (with compiz).

Why is my login time so slow?

Following are my start-up programs:
Gnome Do
Gnome Keyring Daemon Wrapper
Gnome Settings daemon
Network Manager
Nvidia Power (a special NVidia script from here: [http://ubuntuforums.org/showthread.php?t=828369](http://ubuntuforums.org/showthread.php?t=828369)) - this shouldn't be a problem as it was as slow before
PulseAudio Session Management
Update Notifier
User Folders update
Volume Manager
Window Manager

EVERYTHING else has been disabled (e.g. I don't use tracker so I have disabled that).

I am using the Mac4Lin custom theme.

So, any ideas on why this is taking so long?

Thanks!

---

### Post by ivanvajar on 2009-03-20
Your boot time seems OK. As far as I know, Interpid Ibex doesn't boot quicker than that. Correct me if I'm wrong.

---

### Post by abhiroopb on 2009-03-20
I guess thats fine then, I mean I wasn't sure. 

Its the login time that really annoys me! In total it can take almost 2 minutes before I can use my computer!!!

---

### Post by bobbob1016 on 2009-03-20
Jaunty, at least the alpha, is MUCH faster.  I installed it on a spare machine, and used ext4, which is supposed to make the boot even faster.  But it still should be much faster, as in 20-30 seconds from cold boot to login.

---

### Post by gali98 on 2009-03-20
What you might try doing is when the login screen first comes up, switch to a terminal with Ctrl + Alt + F1 and log in. Then run the command top.
Switch back by hitting Ctrl + Alt + F7 (it's usually F7, but sometimes it's another Fkey close to that.)
Log in.
Switch back to the terminal with Ctrl + Alt + F1 and see if any processes are hogging your CPU or Memory while it is logging in.
You might also use Htop (sudo apt-get install htop) which has a nicer interface.
I'm not sure if that will work or not, but you could always try it.
Kory

p.s Sorry if I make you sound like a newbie... I'm not sure how much you know, plus it might help someone in the future. :)

---

### Post by abhiroopb on 2009-03-20
Will try that. Are there any known issues regarding this? Can't wait for jaunty and ext4!

---

### Post by gali98 on 2009-03-20
None that I have dealt with... Another thing you might try is to see if the tty login (the Ctrl + Alt + F7 thing) and see if the text login takes a long time... It should take maybe 3-5 seconds... if it takes longer, you might strace it.
Kory

---

### Post by abhiroopb on 2009-03-20
> **gali98 said:**
> What you might try doing is when the login screen first comes up, switch to a terminal with Ctrl + Alt + F1 and log in. Then run the command top.
Switch back by hitting Ctrl + Alt + F7 (it's usually F7, but sometimes it's another Fkey close to that.)
Log in.
Switch back to the terminal with Ctrl + Alt + F1 and see if any processes are hogging your CPU or Memory while it is logging in.
You might also use Htop (sudo apt-get install htop) which has a nicer interface.
I'm not sure if that will work or not, but you could always try it.
Kory

p.s Sorry if I make you sound like a newbie... I'm not sure how much you know, plus it might help someone in the future. :)

Tried this out, bunch of processes come up, is there any way to record them? And post them here for someone to have a look at?

Thanks

---

### Post by abhiroopb on 2009-03-20
> **gali98 said:**
> None that I have dealt with... Another thing you might try is to see if the tty login (the Ctrl + Alt + F7 thing) and see if the text login takes a long time... It should take maybe 3-5 seconds... if it takes longer, you might strace it.
Kory

text login is very fast

---

### Post by abhiroopb on 2009-03-20
Ok so I cleaned a lot of files out, deleted my home folder and re-set all the settings (gconf, etc), and I removed my panel applets and its still just as slow. Seems there is some application that is slowing it down. Is there anyway to track what htop is doing while I log in?

---

### Post by gali98 on 2009-03-21
I can't think of any way to really log Htop... But I just had an idea... maybe you should create a new test user to see how the login time is... If it is still long, then you can nail that down to some system service, and not anything user specific...
Kory

---

### Post by abhiroopb on 2009-03-21
> **gali98 said:**
> I can't think of any way to really log Htop... But I just had an idea... maybe you should create a new test user to see how the login time is... If it is still long, then you can nail that down to some system service, and not anything user specific...
Kory

OK so I tried a few things (took me most of today).

1. Standard settings with/without compiz - no difference

2. New user - slightly faster (but still about 25s). With compiz its slightly slower (but no real difference).

3. Deleted ubuntu/gnome/metacity and installed xubuntu/xfce - speed is about 12s. With compiz its about 30s.

I'm not surprised that compiz is slowing things down, but it still seems very slow especially since I am using xfce! And compiz is important to me.

---

### Post by gali98 on 2009-03-22
Man something is up... 
My system only has a bit more power than yours and actually less graphics power although I do not use compiz. And login probably only takes 10 seconds max using metacity...
Compiz, with your 256mb card, should not take a extra 20 second bite out of load time...
Are you using restricted drivers?
Have you tweaked your xorg.conf a lot?
You mentioned your nvdia script... Have you tried disabling it?
Just a few questions that might head you in the right direction... I really don't know where to go from here... :(
Kory

---

### Post by abhiroopb on 2009-03-22
1. Yes I am using restricted drivers (for nvidia) but this is pretty standard as far as I know?

2. I do use xorg.conf, but that is only when I had dual monitors. I thought this might be the problem so I deleted xorg.conf and used one monitor and let ubuntu set it up for me. Still as slow.

3. Well it was slow even with the script and its pretty simple the script:
```

while true; do
    if on_ac_power; then
        nice /usr/bin/nvidia-settings -q all > /dev/null
    fi
    sleep 25;
done

```

Not the most complicated of scripts. Its just supposed to max out my graphics otherwise nvidia flickers a lot when using compiz. I did disable it and it didn't make much notice.

Thanks for the thoughts, but I think I've looked into these issues. If there is anything else that anyone can suggest I'd appreciate it a lot.

It just seems that its been slow for a while, and it hasn't improved. I have a feeling that its some vague application somewhere (e.g. I noticed **seahorse** starting up) that I installed and so it keeps starting up, but since I don't know I can't disable it!

---

