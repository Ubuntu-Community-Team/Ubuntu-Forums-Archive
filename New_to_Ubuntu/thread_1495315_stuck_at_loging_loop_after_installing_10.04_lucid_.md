---
title: "stuck at loging loop after installing 10.04 lucid lynx"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by NewbuntuUser777 on 2010-05-27
Hi,

I installed lucid lynx on an old machine and logged in and out several times before getting stuck in a login loop.

I did:
sudo apt-get remove gdm
sudo apt-get install kdm

That worked for awhile though I noticed I would have to login twice to get to the desktop, but I was able to get there at least.  I ran all the updates I could find, rebooted a half dozen times or so, and then a few days later, I'm stuck at the kdm login screen again.

I'm not sure what to try now besides going back to an earlier release, which I really don't want to do, and I don't even know that that would solve the problem since in theory it's likely to be hardware related.

Any thoughts or advice?

---

### Post by NewbuntuUser777 on 2010-05-27
And I should add that failsafe mode does work.

---

### Post by WinRiddance on 2010-06-01
**Well, failsafe absolutely positively did not work** on our Son's laptop who was hit with this phenomena after successfully upgrading to 10.04 and using it daily for a couple of weeks. It's a fairly new laptop, less than a year old, with an Intel GM4500 graphic chip, plenty of Ram and a 250 GB disk. No Windows either, just Ubuntu.

**We tried everything** that we could find in several forums and blog posts ...

1. Repair as well as low graphics mode from the terminal after a restart.
2. Removing conflicting files as well as a couple of possibly conflicting apps.
3. Removing gdm altogether with a purge, followed by installing gdm from scratch.
4. Reinstalling gdm within the existing system.
5. Etc. etc. etc. etc.

What did finally work 100% is an **installation of KDE4** from the terminal, but without the sources lists for updates since our Son knew that he'd eventually want to get his beloved gnome desktop back. So we initiated the installation of KDE with this command (read to end though):

> sudo aptitude install kubuntu-desktopThis worked from the main recovery terminal under the first boot option of the grub boot loader. If you only have one partition and no grub loader then just **cold start your computer** and as soon as you do keep on tapping _your left shift key_ every couple of seconds. Didn't work with the right shift key for whatever reason. Once you have the grub loader, select the second line **for recovery options** with your arrow keys. A bunch of stuff will appear on your screen and eventually you'll be able to select an option from a blue menu on your screen. Here you need to select the option for a terminal session **with included** networking. Use an ethernet cable if you have to, but in our case the WiFi was recognized without a problem.

To get the KDE desktop working apx. 350 MB of data had to be installed. **The entire process was automatic** and original user name/password were preserved as before. Once our Son logged into the KDE environment he quickly decided that he hated it (to each their own, right?) and within less than an hour decided to uninstall KDE again even though everything was actually working (WiFi, Email, Firefox, and so on). As soon as he reverted back to Gnome by using these directions from psychocats.net ....

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

... everything worked 100% fine again. Make sure that you copy/paste the entire content of that text box - it fills an entire page and then some - but needs to be pasted in its entirety to your terminal screen in KDE. This worked like a charm and took about 60 to 90 minutes from beginning to end, including all downloads. Firefox even saved the previous KDE session. **Login, password, apps, colors, theme, it all was back just like before.** So apparently _removing KDE left something ??? from Gnome behind_ which was missing even though we'd installed, purged, reinstalled gnome without any warnings previously. Make a note of the fact that **we did not** have to reinstall gnome, nor did we reinstall Ubuntu 10.04

---

