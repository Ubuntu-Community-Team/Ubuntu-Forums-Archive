---
title: "Cant drag programs to unity bar"
date: 2011-06-09
forum: New to Ubuntu
---

### Post by gogogo111 on 2011-06-09
Hey guys. I'm absolutely in love with 11.04 so far. I'm a Windows 7 convert and I love banshee, how clutterfree the interface is in a program and everything is absolutely sweet.

However there is one thing I can't seem to get working. I cannot drag applications to the unity bar. I've looked up videos online and people seem to just click + drag the app to the bar and the programs move out of the way for the new one to be dropped...but when I do that my whole unity bar just turns transparent and doesn't allow me to drop the app on the bar.

Also, "Keep in launcher" doesn't work. 

Any help? :(

---

### Post by wildmanne39 on 2011-06-09
> **gogogo111 said:**
> Hey guys. I'm absolutely in love with 11.04 so far. I'm a Windows 7 convert and I love banshee, how clutterfree the interface is in a program and everything is absolutely sweet.

However there is one thing I can't seem to get working. I cannot drag applications to the unity bar. I've looked up videos online and people seem to just click + drag the app to the bar and the programs move out of the way for the new one to be dropped...but when I do that my whole unity bar just turns transparent and doesn't allow me to drop the app on the bar.

Also, "Keep in launcher" doesn't work. 

Any help? :(
Hi, open the application you want in there and go to the icon in the launcher and right click on it and click keep in launcher. Also you can look at the guides in my signature for some great tips for natty.

---

### Post by beew on 2011-06-09
> **wildmanne39 said:**
> Hi, open the application you want in there and go to the icon in the launcher and right click on it and click keep in launcher. Also you can look at the guides in my signature for some great tips for natty.

Actually some launchers don't work if you just right click and keep in launcher bar (MIro, e.g, click the launcher thus created it just flashes and nothing happens) You have to drag it from the dash and place it there.  If that doesn't work, reboot sometimes may solve the problem.

This thing is really buggy man.

---

### Post by migs73 on 2011-06-09
Yeah I've the same problem with Potato Guy (a game for the kids....honest!). I'll need to try the right click keep in launcher though.

---

### Post by gogogo111 on 2011-06-09
As I said in the original post...Right click > Keep in Launcher doesn't work. Anyone else have any other solutions?

---

### Post by beew on 2011-06-09
> **gogogo111 said:**
> As I said in the original post...Right click > Keep in Launcher doesn't work. Anyone else have any other solutions?

You may want to try Gone Fishing's method.
[URL="http://ubuntuforums.org/showthread.php?t=1760545"]http://ubuntuforums.org/showthread.php?t=1760545
[/URL]

---

### Post by gogogo111 on 2011-06-09
That didn't seem to work either. Maybe I did something wrong but I shouldn't have to boot to classic mode to drag something to a menu. -_- Why is this even a problem? What exactly is Unity doing to not accept me dragging the program to the bar? Any way I can file a bug report?

:confused:

---

### Post by wildmanne39 on 2011-06-09
> **gogogo111 said:**
> That didn't seem to work either. Maybe I did something wrong but I shouldn't have to boot to classic mode to drag something to a menu. -_- Why is this even a problem? What exactly is Unity doing to not accept me dragging the program to the bar? Any way I can file a bug report?

:confused:
Hi, unity does not allow dragging to the launcher, if you look at my previous post that is how you make it stay in the launcher, but there are some that have to be done another way as listed in the other post just take another look at them please, one of those two should work unless you are having a malfunction with natty.

---

### Post by beew on 2011-06-10
> **wildmanne39 said:**
> Hi, unity does not allow dragging to the launcher, if you look at my previous post that is how you make it stay in the launcher, but there are some that have to be done another way as listed in the other post just take another look at them please, one of those two should work unless you are having a malfunction with natty.

It does allow it. Actually if you make a launcher by opening the application and make it stay the launcher may not work correctly for some applications. Example, gnome-mplayer, if you create a launcher that way you cannot restore the running instance of gnome-mplayer which has been minimized, clicking the launcher will open a new instance while the old instance still running hidden somehwere. Dragging the launcher from the dash in the launcher solved the problem for me.

---

### Post by wildmanne39 on 2011-06-10
> **beew said:**
> It does allow it. Actually if you make a launcher by opening the application and make it stay the launcher may not work correctly for some applications. Example, gnome-mplayer, if you create a launcher that way you cannot restore the running instance of gnome-mplayer which has been minimized, clicking the launcher will open a new instance while the old instance still running hidden somehwere. Dragging the launcher from the dash in the launcher solved the problem for me.
Hi, yes I was referring to your post #3 when I told the person that the other post had another way of doing it, when I said it did not allow it I was talking about from the desktop,not from dash sorry for the confusion. I know that for a lot of the apps you can just open the app and then right click on the icon in the launcher and put a check next to keep in launcher. In my signature called power users guide for natty tells how to make icons for the launcher.

---

### Post by beew on 2011-06-10
> **gogogo111 said:**
> That didn't seem to work either. Maybe I did something wrong but I shouldn't have to boot to classic mode to drag something to a menu. -_- Why is this even a problem? What exactly is Unity doing to not accept me dragging the program to the bar? Any way I can file a bug report?

:confused:

You actually don't have to log in to the Classical Desktop. The logic is to drag the .desktop file  to the Unity bar. It  is just easy to get hold of the desktop file by dragging it from the panel launcher in the Classic Desktop.

You can also do it in Unity as follows:

The .desktop file is probably in /usr/share/applications (or /usr/local/share/applications) but you can't drag and drop it because of permission issue.

so you need to create a local version and make it executable by non root user.

```
sudo cp /usr/share/applications/xxx.desktop  ~/.local/share/applications/xxx.desktop

sudo chown username  ~/.local/share/applications/xxx.desktop

```Then you can open ~/.local/share/applications and drag the xxx.desktop file to the Unity bar and see if it works.

~/.local is a hidden file, you access it go to /home/username and in View click "Show Hidden Files"


I agree, this is buggy and launchers don't behave consistently.

---

### Post by smcrossman on 2011-06-10
Being a real newbie myself the unity launcer bar is one of the things I've found most difficult. 

First, dragging an app doesn't work for me....if I create a launcher on the desktop I CAN drag and drop it onto the launcher.  

Second, I can only lock or get Keep in Launcher to work on a program that is currently open.  Another option is when you install something using Software Center it should give you the option to add it to launcher. Do that then if you DON'T want it later it is easier to REMOVE it than try to ADD it later.

Third, there are some shortcuts that are automatically installed with apps that just don't work.  I can't remember which app it was, but I did a quick search on one earlier this week and found that was the case.  If you go into Terminal and enter the command the app runs fine but the default launcher does nothing in unity.

I AM running in x64 on one machine and x32 on another.  Issues seem to be consistent on both (although other issues aren't). 

My solution for Unity bar issues has been to install Panel (Gnome Panel) and use it for an additional shortcut or indicator bar.  I've found the Unity bars hard to adjust to and not very user-accommodating.  So as I learn the tricks and such I have a panel with the missing launchers and additional indicators to help with the transition.  Panel can be opened and closed as needed and location/coloring, etc can be adjusted to your preferences. It can auto hide, or not. Of course Unity launcher can be set to autohide, stay hidden or stay visible.  

No actual solutions to your issue, but some other tips from a newbie that might help with this or other issues.  hope i didn't waste your time!

---

### Post by beew on 2011-06-11
You may find this interesting.

[http://ubuntuguide.net/use-classic-menu-in-ubuntu-11-04-unity-launcher](http://ubuntuguide.net/use-classic-menu-in-ubuntu-11-04-unity-launcher)

---

