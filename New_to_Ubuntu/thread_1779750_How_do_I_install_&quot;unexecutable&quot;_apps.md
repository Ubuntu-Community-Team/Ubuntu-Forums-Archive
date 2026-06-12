---
title: "How do I install &quot;unexecutable&quot; apps?"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by geoff_sct on 2011-06-10
I would like to install Reaper (audio daw) using WINE but still do not understand how to install an app that's not in the repository. I've read posts that say things like "install it under sudo" and things like that. I think if I were walked through the process step by step I'd have it down for other apps too. Please don't tell me to do it under sudo. I don't know how. I've downloaded the Reaper app and I have WINE installed but the Reaper set up won't start. I just get the message that it's not from a trusted source and is unexecutable. Where do I go from there? Thanks for any help.

---

### Post by dFlyer on 2011-06-10
You might want to install playonlinux. It makes installing windows programs much easier.

sudo apt-get install playonlinux

---

### Post by nitstorm on 2011-06-10
Firstly make sure your Windows App runs on Wine. Not all windows programs run on Wine. You can see if your app runs on Wine by going through the [WineHQ]("http://ubuntuforums.org/www.winehq.org/") site.

---

### Post by geoff_sct on 2011-06-10
Hi, thanks for the quick reply. Do I need to uninstall WINE before installing Playonlinux? Also does Playonlinux give instructions on how to install apps that Ubuntu isn't familiar with?

Nitstorm, yes I've checked and Reaper runs quite well (Platinum) under WINE.  If I could just figure out how to install it.

---

### Post by geoff_sct on 2011-06-10
Aha! got it!!  Now I'll have to get WINEASIO for the audio.  I'll try this: sudo apt-get install wineasio   Shoot it's unable to locate wineasio.  Well thanks for getting me this far. It looks like Playonlinux is the way for me to go.

---

### Post by jerrynewt on 2011-06-10
Right click on the Reaper app you downloaded and go to permissions and checkmark the executable box at the bottom. The file will become executable and you can run with wine program loader (after closing the window and right clicking on it again and choosing open with wine program loader).

---

### Post by 3rdalbum on 2011-06-11
Geoff: I suspect that you've not had any good advice yet from anyone who has had recent practical experience with Wine.

Installing software on Wine is pretty easy. Open a terminal and type 'wine' (without the quotes) and press the space bar so there's a space character afterwards. Now drag the Reaper installer to the terminal window. It will fill in its location in the terminal window. Click on the terminal window to bring it to the front, and then press Enter. This will run Wine with the Reaper installer program.

When installed, Reaper should appear in the Applications lense or in your Applications menu (in classic Gnome), and can be easily run from here.

Not all programs work in Wine. Probably about 20% of them work well enough for you to use. Wherever possible, you should be using native Linux software rather than flaky emulation.

---

### Post by Swagman on 2011-06-11
> **3rdalbum said:**
> Geoff: I suspect that you've not had any good advice yet from anyone who has had recent practical experience with Wine.

Installing software on Wine is pretty easy. Open a terminal and type 'wine' (without the quotes) and press the space bar so there's a space character afterwards. Now **drag the Reaper installer to the terminal window. It will fill in its location in the terminal window.** Click on the terminal window to bring it to the front, and then press Enter. This will run Wine with the Reaper installer program.


lol

Even I didn't know you could do that in the terminal

---

### Post by 3rdalbum on 2011-06-11
> **Swagman said:**
> lol

Even I didn't know you could do that in the terminal

I'm a former Mac user. Mac users drag and drop, Windows users don't. I impressed a Windows sysadmin by dragging and dropping a file onto a running program on Windows, once.

The drag and drop trick for the terminal works in Konsole and Xfterm, too, not just gnome-terminal.

---

