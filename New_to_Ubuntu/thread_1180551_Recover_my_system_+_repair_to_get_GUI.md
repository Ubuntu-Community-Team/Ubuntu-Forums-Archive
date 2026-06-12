---
title: "Recover my system + repair to get GUI"
date: 2009-06-06
forum: New to Ubuntu
---

### Post by Naif.1 on 2009-06-06
I am having a problem with my Ubuntu system, I am new to ubuntu so please be clear when you answer me :)

My ubuntu was working great. But I was trying to uninstall some of the programs and components to make my ubuntu run faster.. the problem is when I finished uninstalling some programs and restarted my computer.

My ubuntu do boot and it keep booting until it get to the brown background(before asking user-name and password), and then it stop!

Now, I have my files on the ubuntu desktop and I want to repair the system. I am wondering if there is a way to repair and recover my ubuntu.. I have been searching the last two days but couldn't get a clear answer or solution's!! 

Thanks :)

Edit: I have Ubuntu 9.04  >

---

### Post by Mark Phelps on 2009-06-07
What you can try (it may work) is that when you get the GRUB menu, select the recovery option instead of the default one.  That might work.

If it doesn't, there's the likelyhood that you'll have to do a complete reinstall.

---

### Post by Naif.1 on 2009-06-07
Thanks Mark.


So far, I can get access to the username and password window.. but after I enter my user name and password I just get the brown background with nothing else(no desktop or menu-bar....). 

When I try to press some keys on the keyboard I get the terminal window. How can I start the GNOME session and the desktop from the terminal?


Waiting,,,,, Thanks :)

---

### Post by Naif.1 on 2009-06-07
.
.
hey guys,

how would I recover my system? I really have no idea if there is a way to recover my system like I do in windows? I am wondering if there is a terminal command that would kill the GNOME and re run it?

My problem is (i think) with the GNOME and desktop since I can't see them after I enter my username and password!!

Any help would be appreciated...


:)

---

### Post by nothingspecial on 2009-06-07
When you reboot press escape when you see the text - grub loading. This will bring up a menu that allows you to boot into recovery mode.

From there You can copy any important data to external media. It is also possible to fix your system but it would be handy to have some idea of what you have done.

---

### Post by anewguy on 2009-06-07
If you can tell us EXACTLY what you've done, step by step, we may be able to have you run some command line things to restore what you've done - we just need to see it first as we can't guess at what you've done and we can't guess at what might need to be done because of it.

Dave :)

---

### Post by Naif.1 on 2009-06-07
> **anewguy said:**
> If you can tell us EXACTLY what you've done, step by step, we may be able to have you run some command line things to restore what you've done - we just need to see it first as we can't guess at what you've done and we can't guess at what might need to be done because of it.

Dave :)

Dave,

I really don't know EXACTLY what I did, I only was trying to remove some of the programs and components from the system package(I don't know what is called, but it is where you remove programs from)

I really don't know if there is a way to repair the GNOME or restart it from the terminal.(after I enter my username and password, I just get the brown background with no desktop or bars!!)


Thank... any help would be appreciated!

:)

---

### Post by presence1960 on 2009-06-07
> **Naif.1 said:**
> Dave,

I really don't know EXACTLY what I did, I only was trying to remove some of the programs and components from the system package(I don't know what is called, but it is where you remove programs from)

I really don't know if there is a way to repair the GNOME or restart it from the terminal.(after I enter my username and password, I just get the brown background with no desktop or bars!!)


Thank... any help would be appreciated!

:)

well if you can't specifically tell us what you have done, we can't tell you anything that may help. You have to help us out here or you will have to do a reinstall. There is no system restore function like there is in windows.

---

### Post by anewguy on 2009-06-07
I'm going to try something here - it may not do any good, but since you don't seem to know what you deleted, let's start with this stuff.  There'll be more than you might actually need, but let's just go with it.  You'll want to copy/paste the command.  Let us know if there is an error or what other result you have (just reboot when this finishes):

Do all of these from a terminal window (either use recovery mode of hold down ctrl, alt and press F1.

sudo apt-get install gnome-desktop-environment metacity metacity-common libmetacity0 compiz-core compiz-gnome compiz  python-compizconfig compizconfig-settings-manager compiz-plugins compiz-wrapper libdecoration0 compiz-fusion-plugins-main compiz-fusion-plugins-extra compizconfig-backend-gconf


Also, it may be that you wiped out a display driver, so also post back the output of:

lspci


I guess we'll just wait until we see if that helps any or not.  I'm having you re-install the gnome desktop since you keep mentioning gnome, but be aware there are MANY things that can cause your desktop not to work.  As a word of caution, when you eventually get this all sorted out, do not delete anything with any package manager, etc., unless you are absolutely CERTAIN it can be deleted with no ill effects.  If you were worried about performance, you should have posted here first - we would have done things like ask for your computer specs and to run a top command as well as ps -e  so we could see what was actually running on your computer and IF any of it needed/could be deleted.

Dave :)

---

### Post by kansasnoob on 2009-06-07
Actually when you reboot just hit the esc key after the system display shows, that should bring you to GRUB, choose recovery mode, then when it's done you'll get a list of options.

Choose drop to root shell prompt, then type this:

```
sudo apt-get install --reinstall ubuntu-desktop && sudo apt-get install -f install
```

Obviously it must be typed just right! One typo will hose the works! I hope I didn't make any!

---

### Post by anewguy on 2009-06-08
Did you have any luck with what kansasnoob or myself suggested?  We're curious to know if you got things working, and if so, how - even if it meant a complete reinstall.

Dave :)

---

### Post by Naif.1 on 2009-06-11
Dave, :)

Thank you, I really appreciate your reply..

 I am replying from my ubuntu.

since your terminal command was loong :) .. I tried this command first: [http://ubuntuforums.org/showpost.php?p=7416875&postcount=5](http://ubuntuforums.org/showpost.php?p=7416875&postcount=5)

and yes, after rebooting it works great.

thanks, and I will try to corrupt my GNOME to try your command :D


Naif :)

---

### Post by manoj87 on 2011-01-18
Guys I have the same problem.
When I tried [kansasnoob]("http://ubuntuforums.org/member.php?u=554595") command it says "command line option 'e'(from -desktop) is not known.
Thanks
Manoj

---

### Post by manoj87 on 2011-01-18
@Dave..anewguy.
I tried your option and it says "The following packages have unmet dependencies:
gnome-desktop-environment:Depends:fast-user-switch-applet(>=2.22.6) but is is not installable
Reommends:fam but it is not going to be installed.

---

### Post by manoj87 on 2011-01-18
Hi Naif.1...
I cannot find any command in your link. Can you tell me what command you used to recover gnome?
Thank you
Manoj

---

### Post by gandalf69 on 2011-01-18
> **kansasnoob said:**
> Actually when you reboot just hit the esc key after the system display shows, that should bring you to GRUB, choose recovery mode, then when it's done you'll get a list of options.

Choose drop to root shell prompt, then type this:

```
sudo apt-get install --reinstall ubuntu-desktop && sudo apt-get install -f install
```Obviously it must be typed just right! One typo will hose the works! I hope I didn't make any!

Esc doesn't seem to do anything useful but I just tried the above (see my post Low graphics mode failure) and after about 50Mb of downloading it got to:
Building dependency tree
Reading state information....done
E: Couldn't find package install

So I rebooted and [SIZE=5]**It worked**[/SIZE]:D Thanks heaps.

It doesn't appear to have lost anything either.

---

### Post by jfreak_ on 2011-01-18
@Manoj87 Start a new thread for your problem. Its more likely to get solved that way

---

### Post by pnewbie on 2011-02-02
Thanks Kansasnoob.....
It worked for me.............................:guitar:
Thanks very very much):P

---

