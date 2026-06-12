---
title: "How do i get lucid working again?"
date: 2011-06-09
forum: New to Ubuntu
---

### Post by mr.xulu on 2011-06-09
Hi! I'm using a neo laptop on dual boot with windows xp and ubuntu 10.04.

I was trying to upgrade to firefox 4 stable release using the terminal commands that I got from the "sticky: firefox 4 mega thread":
sudo add-apt-repository ppa:mozillateam/firefox-stable sudo apt-get update sudo apt-get upgrade sudo apt-get install firefox 

When I got to "sudo apt-get upgrade" the upgrade was taking quite some time so I left it for while. When I went back to check on the progress, on the terminal was displayed something about "ms ttf corefonts reconfiguring installer" on its heading (sorry i can't remember the exact wording). Below that was microsoft license agreement with a grey background with an "ok" at the bottom. I was trying to press "enter" on the "ok" button and even tried clicking on it with the mouse but nothing was happening. I thought it froze so i closed the window terminal. A window popped up giving a waring saying something like a process was ongoing. But thinking that it froze, I closed it anyway.

When it closed, the desktop changed to a grey theme like the older releases of ubuntu (please see attached image).

1. I lost the wifi icon.
2. I can't type anything on terminal, apps, or enter my password to connect to internet.
3. I have to unplug and replug my usb mouse to be able to use it.
4. I can't change the theme.
5. When I click on "shutdown", it doesn't shutdown but instead it logs out and I get the log in window. Since I can't type anything, I can't log back in either. And I have to manually press the power button to shut it off.

I have an ubuntu 10.04 and 11.04 live usb in case that would help to fix this.

Hope somebody can help. :(

Thanks a lot!

---

### Post by Random_Dude on 2011-06-09
I'm not sure how to help you with this, but if you know which packages are broken, you can try to reinstall them.

You can log in using the command line, just press Ctrl+Alt+F1

You can connect to the Internet using the command line: [http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/](http://www.ghacks.net/2009/04/14/connect-to-a-wireless-network-via-command-line/)

Once you are on-line in the command line, you can try to reinstall the broken packages by running:

```
sudo apt-get install <package>
```


Also, to shutdown through the command line you can type
```
sudo shutdown 0
```
or something like that....

Cheers :cool:

---

### Post by matt_symes on 2011-06-09
Hi

It sound like you have damaged your current install dramatically. 

First things first. Never power off using the power button. That is a sure fire way to completely bork your system. That would damage most modern OSs out there.

If your system becomes completely unresponsive then try this before a hard power down.

Press (and keep pressing) ATL +SysRq at the same time and type R E I S U B one after another with your other hand.

Unless you kernel has locked up, this will safely reboot for you. Leave three seconds between each key press.

As for the ms-ttf-core-fonts dialog in the terminal. What you need to do is press the TAB key to move to the OK button and then hit enter. The TAB key will move around those dialogs in a terminal.

As for your current situation, it might be easier to backup and reinstall if it's a new install as it seems you have a number of issues that might take a while to track down.

That being said, what happens when you first boot the PC and get to the login screen. Can you log into Ubuntu or is the keyboard unresponsive at that point ?

Kind regards

---

### Post by mr.xulu on 2011-06-09
Thanks Random-dude and matt_symes for all the tips and commands!


"As for your current situation, it might be easier to backup and reinstall if it's a new install as it seems you have a number of issues that might take a while to track down.

That being said, what happens when you first boot the PC and get to the login screen. Can you log into Ubuntu or is the keyboard unresponsive at that point ?

Kind regards[/QUOTE]"


matt_symes,

the keyboard is unresponsive once i get into ubuntu. but it's fine at the grub window.

since it looks very bad. i guess i'll just go for a reinstall.


I wanna try installing natty. I'd like to ask some questions about installing it. it works fine when i boot it using live usb. when I click on the "install" icon from natty the install window gives me several choices:

1. erase ubuntu 10.04.2 and reinstall
2. upgrade 10.04.2 to 11.04
3. erase everything and reinstall
4. something else

i've read something in the forums that you can't upgrade 10.04.2 strait to 11.04. and I wanna keep my windows xp as it is. so options 2-4 are out.

would option "1" be safe? it's supposed to not touch my windows xp install. I've backed up my lucid files already. Is there a risk that something can happen to my windows xp with option "1"?

Thanks again! :)

---

### Post by matt_symes on 2011-06-09
Hi

From what i have read, option 1 should be all right; however, in the past it has been known to cause issues so that is a qualified should.

What i tend to do, for peace of mind, is to manually specify the partitions using option 4. If you know where your Ubuntu partitions are then this will be more secure.

I always advise imaging the entire hard drive using something like Clonezilla before an install or upgrade, so you have a fallback position.

Kind regards

---

### Post by mr.xulu on 2011-06-09
> **matt_symes said:**
> Hi

From what i have read, option 1 should be all right; however, in the past it has been known to cause issues so that is a qualified should.

What i tend to do, for peace of mind, is to manually specify the partitions using option 4. If you know where your Ubuntu partitions are then this will be more secure.

I always advise imaging the entire hard drive using something like Clonezilla before an install or upgrade, so you have a fallback position.

Kind regards



Thanks a lot! :)

---

### Post by mr.xulu on 2011-06-09
> **mr.xulu said:**
> Thanks a lot! :)

I've installed natty successfully. Really happy with it. Thanks again for all the help!

---

