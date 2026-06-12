---
title: "Broadcom B43 issues"
date: 2008-09-21
forum: Networking &amp; Wireless
---

### Post by Sup3rkirby on 2008-09-21
This seems to be a very common problem.  Of course the reason I'm making a new thread is because of my situation is a bit different, and i have different questions to ask(plus i don't see an answer to my specific problem yet either).

So I like Kubuntu(8.04), but the problem is I can't get wireless working on my laptop that I am trying to install it on.  And well, the laptop is a bit useless with no internet.


When I first ran the live CD, and after everything had loaded, a thing on the 'restricted drivers' or whatever came up for the Broadcom B43 driver.  The driver is included but the firmware is not.  So if i check the 'use' box(not sure if that is the EXACT name, but it is close and has the same point), then I get a short message about downloading the firmware.  I click 'OK' and then at adept batch program comes up.  Well, the first time actually nothing happened.  Because there was no internet(makes since huh, no wireless).

I later went and got some ethernet and went over to my router and hooked up the laptop.  I can't remember how many times I had run that adept batch though.  But basically, I was connected to the internet, the update ran but at the end an error came up about commiting changes.  I simply clicked 'OK'.  But I found a site that helps with the firmware.
[http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware)

Using this site I ran the command and the firmware was downloaded and installed.  And then I disconnected the ethernet and the wireless picked up my network.


The problem is that when I went to install Kubuntu, it would not work.  Nothing came up at all.  So eventually after 20 minutes or so and several attempts to open the installer, I rebooted(strange, on the logout, once the GUI seemed to be gone, several restricted driver windows came up(ones that didn't show up when i tryed to open it from the tray)).  And then I got a message and had to click ok to close stuff in order to reboot.  I then proceeded to install right from the grub menu rather than load the live cd.

Well, once Kubuntu was installed, the real problems came up.


Now, I had to insert the CD and change some adept resources to get the rescricted drivers to come up for my broadcom b43 wireless card.  Once this was done, it has failed to load the firmware from adept(with ethernet connected) and when I run the sudo command in konsole, it says it was successfully installed, and I can enable the card, but it has yet to work.  No networks have been detected and I can't even connect by manually inputing the settings.

I read that Kubuntu KDE4 still uses a KDE3 version of adept and so this can cause errors.  I also know I've gotten plenty of crash reports on adept when trying to load the firmware download batch.


Now, why won't it work anymore.  It seems to have only worked once, and I can't even get it to work from the live CD anymore.  Even if I could, I am not sure it would install from there.  I even tried KDE 3.5 though, and the results are the same.  If the firmware batch downloader actually gets anything, it will give me that message about commiting changes, and then nothing happens.  I can use the sudo command, but that does nothing other than move text around and make a claim that the firmware has been installed.

---

### Post by Ayuthia on 2008-09-21
> **Sup3rkirby said:**
> This seems to be a very common problem.  Of course the reason I'm making a new thread is because of my situation is a bit different, and i have different questions to ask(plus i don't see an answer to my specific problem yet either).

So I like Kubuntu(8.04), but the problem is I can't get wireless working on my laptop that I am trying to install it on.  And well, the laptop is a bit useless with no internet.


When I first ran the live CD, and after everything had loaded, a thing on the 'restricted drivers' or whatever came up for the Broadcom B43 driver.  The driver is included but the firmware is not.  So if i check the 'use' box(not sure if that is the EXACT name, but it is close and has the same point), then I get a short message about downloading the firmware.  I click 'OK' and then at adept batch program comes up.  Well, the first time actually nothing happened.  Because there was no internet(makes since huh, no wireless).

I later went and got some ethernet and went over to my router and hooked up the laptop.  I can't remember how many times I had run that adept batch though.  But basically, I was connected to the internet, the update ran but at the end an error came up about commiting changes.  I simply clicked 'OK'.  But I found a site that helps with the firmware.
[http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware)

Using this site I ran the command and the firmware was downloaded and installed.  And then I disconnected the ethernet and the wireless picked up my network.


The problem is that when I went to install Kubuntu, it would not work.  Nothing came up at all.  So eventually after 20 minutes or so and several attempts to open the installer, I rebooted(strange, on the logout, once the GUI seemed to be gone, several restricted driver windows came up(ones that didn't show up when i tryed to open it from the tray)).  And then I got a message and had to click ok to close stuff in order to reboot.  I then proceeded to install right from the grub menu rather than load the live cd.

Well, once Kubuntu was installed, the real problems came up.


Now, I had to insert the CD and change some adept resources to get the rescricted drivers to come up for my broadcom b43 wireless card.  Once this was done, it has failed to load the firmware from adept(with ethernet connected) and when I run the sudo command in konsole, it says it was successfully installed, and I can enable the card, but it has yet to work.  No networks have been detected and I can't even connect by manually inputing the settings.

I read that Kubuntu KDE4 still uses a KDE3 version of adept and so this can cause errors.  I also know I've gotten plenty of crash reports on adept when trying to load the firmware download batch.


Now, why won't it work anymore.  It seems to have only worked once, and I can't even get it to work from the live CD anymore.  Even if I could, I am not sure it would install from there.  I even tried KDE 3.5 though, and the results are the same.  If the firmware batch downloader actually gets anything, it will give me that message about commiting changes, and then nothing happens.  I can use the sudo command, but that does nothing other than move text around and make a claim that the firmware has been installed.

Let's start by checking to see what your network card is trying to use.  Please open up the Konsole and post the results of the following:
```
lshw -C network
```It will provide some information about what driver your wireless is trying to use and whether the firmware is being used.

---

### Post by Sup3rkirby on 2008-09-23
Well, it seems I found a 'solution' to this problem, if you want to call it that.

1) Go to the restricted drivers screen.  The Broadcom B43 should show up here.
2) Make sure you have an ethernet cable connected at this point and click on the 'enable' checkbox.
3) click the 'OK' button(or equivalent) and then wait for the adept batch to run.
4) It seems(at least for me) at this point this screen will remain at 0%. So from here I click this 'enable' check box once more.  You should recieve the message again, and then click 'OK' again.
5) A second adept batch will open, but this one should actually work.
6) You can then follow the steps at [http://linuxwireless.org/en/users/Drivers/b43#devicefirmware](http://linuxwireless.org/en/users/Drivers/b43#devicefirmware)
7) Disconnect the ethernet and the wireless networks should be detected at the wireless card should work.

I tried it in the Live CD(then the install wouldn't load) and I tried it a second time after installing and it still worked.

I am not sure why adept has so many problems though.  While trying to do updates or install more packages, I constantly recieve a message about failing to commit changes(at it would break the packages, or whatever).  Until just yesterday I was unable to update Kubuntu.  Then magically, it worked with no error.  Odd.

---

