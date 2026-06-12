---
title: "I seem to have messed up GNOME"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by bledsoe on 2010-05-08
I've been running Ubuntu for about 2 years as a dual boot on my Toshiba laptop and it's been great.  Yesterday I began getting messages that my disk space was filling up; I had created a bunch of video files a while back and forgot to delete them, so I deleted several of them to free up some disk space.  I rebooted my machine and the GRUB screen appeared as usual, but when my Ubuntu login screen appeared, it was hugely distorted.  I could tell the machine was trying to display the login screen, but all the fonts were like three inches high and the different sections of the screen were overlapping each other.

From this "distorted" login screen, I can click on my username and enter my password, and it appears to be trying to boot, but then it just goes back to the same distorted screen.

I can also restart and select the "recovery mode" option from GRUB, which takes me to the "Recovery Menu", but I've tried selecting each of the options (resume, clean, dpkg, etc.) and none seem to fix my problem.  I assume that if I enter the proper commands at a shell prompt, I could fix this, but I'm not sure what to enter.

Also, I can select one of the older boot options from the GRUB screen (non-recovery mode), and after displaying some command-line type stuff (including some error messages?), it goes to a (mostly) normal-looking login screen, which has a dialog box in the lower right corner which reads "Install Problem! The configuration defaults for GNOME Power Manager have not been installed correctly. Please contact your computer administrator."  I can login here, but after churning for a few seconds it just takes me back to the same login screen with the same "Install Problem" error.

FWIW, I can still boot to Windows just fine.

Any help greatly appreciated.

---

### Post by r-senior on 2010-05-08
How about checking for broken packages in Synaptic?

Open Synaptic, click on the Custom Filters button in the bottom left corner and then choose Broken from the panel on the left.

If nothing is marked as broken, while you are in Synaptic, you could could try reinstalling gnome-power-manager?

---

### Post by kio_http on 2010-05-08
> **bledsoe said:**
> I've been running Ubuntu for about 2 years as a dual boot on my Toshiba laptop and it's been great.  Yesterday I began getting messages that my disk space was filling up; I had created a bunch of video files a while back and forgot to delete them, so I deleted several of them to free up some disk space.  I rebooted my machine and the GRUB screen appeared as usual, but when my Ubuntu login screen appeared, it was hugely distorted.  I could tell the machine was trying to display the login screen, but all the fonts were like three inches high and the different sections of the screen were overlapping each other.

From this "distorted" login screen, I can click on my username and enter my password, and it appears to be trying to boot, but then it just goes back to the same distorted screen.

I can also restart and select the "recovery mode" option from GRUB, which takes me to the "Recovery Menu", but I've tried selecting each of the options (resume, clean, dpkg, etc.) and none seem to fix my problem.  I assume that if I enter the proper commands at a shell prompt, I could fix this, but I'm not sure what to enter.

Also, I can select one of the older boot options from the GRUB screen (non-recovery mode), and after displaying some command-line type stuff (including some error messages?), it goes to a (mostly) normal-looking login screen, which has a dialog box in the lower right corner which reads "Install Problem! The configuration defaults for GNOME Power Manager have not been installed correctly. Please contact your computer administrator."  I can login here, but after churning for a few seconds it just takes me back to the same login screen with the same "Install Problem" error.

FWIW, I can still boot to Windows just fine.

Any help greatly appreciated.

Open terminal or do a console login.

then
you should be in your home folder, if not. (Even if you already are no harm)
```
cd /home/yourusername
```
where you should replace yourusername with your user name.
then 
```
rm -rf .gnome
```
then
```
rm -rf gconf
```
then
```
rm -rf gconf2
```

[COLOR="Red"]Warning:[/COLOR]This will restore GNOME to the settings as it was when you first booted ubuntu.
Your documents, will stay, pictures etc will stay. However settings for GNOME (Not other) applications will go.

E.g If you set your wallpaper to something else, you have to go in settings and change it again.

---

### Post by bledsoe on 2010-05-08
Thanks r-senior and kio_http.

kio, I executed all of your code suggestions from a command prompt, and they all appeared to execute fine (I didn't get any error messages; in fact, I got no indication of anything at all after executing each command), but after rebooting, my machine still works exactly the same as before.  Those commands didn't seem to do anything at all.

r-senior, I would try your suggestions, but don't I have to be in gnome to access Synaptic?  How exactly do I reinstall gnome power manager from the command line?

---

### Post by booshire on 2010-05-08
You can use apt-get to reinstall the power manager. It appears in 
the repo as gnome-power-manager. Try doing:

sudo apt-get reinstall gnome-power-manager

You can also try to purge and then install:

sudo apt-get purge gnome-power-manager
sudo apt-get install gnome-power-manager

---

### Post by bledsoe on 2010-05-08
Hi booshire, thanks for the suggestion.  I tried doing the purge and got an error message that said something about not having enough disk space to compete the command, and since not having enough disk space was the problem that started all this, I deleted a couple of big files and tried again.

The purge command then seemed to work okay.  However, the install command gave me some error messages.  In particular, it says "Could not resolve us.archive.ubuntu.com" and then I got a "Failed to fetch..." message.

Am I not connected to the internet or something?

---

### Post by bledsoe on 2010-05-08
Wait, there's something else that's slightly different now, too.  Now when I select the older boot option from the GRUB screen (non-recovery mode), I don't get the dialog box that says there's a problem with my Power Manager.  Presumably because I purged the power manager with booshire's "sudo apt-get purge gnome-power-manager" command?

Is this progress?

I still can't log in, though.  I enter my password and it thinks for a minute, then just takes me back to the login screen.

---

### Post by bledsoe on 2010-05-08
Okay, so I made sure I was connected to the internet by plugging a cable directly into my router (I guess my wireless wasn't working given whatever's wrong with Ubuntu on my laptop), and then I ran the "sudo apt-get install gnome-power-manager" command.  It appeared to work, but nothing seems to have changed as far as me being able to log in and get a GUI (except that now the dialog box that says there's a problem with my Power Manager is back).

Other suggestions?

---

### Post by kio_http on 2010-05-08
> **bledsoe said:**
> 
Other suggestions?

Install Kubuntu-desktop, don't worry it won't remove GNOME.

```
sudo apt-get install kubuntu-desktop
```

When prompted in console itself, chose KDM.
Temporarily, you can use KDE and have access to GUI.

---

### Post by kio_http on 2010-05-08
2 years! Once you get KDE running, I would suggest upgrading to lucid lynx.

---

### Post by bledsoe on 2010-05-08
Okay, I ran the "sudo apt-get install kubuntu-desktop" command and installed the kubuntu desktop.  Now, when I get to the login screen from my "regular" GRUB boot selection, I still get the 3-inch high distorted letters, only now they're with the kubuntu login screen instead of my vanilla ubuntu (gnome?).  And it still won't let me log in.  I can enter my name and password, but it just thinks for a minute and then displays the login screen again.

If, from the GRUB screen, I scroll down to a previous installation, I get a normal looking kubuntu login screen, but it still won't log me in, just thinks for a minute and then takes me back to the login screen.

---

### Post by kio_http on 2010-05-09
On the login screen, one of the buttons is for session type.
Click it.

You should see a menu.
Select session type KDE.

Now login.

---

### Post by bledsoe on 2010-05-09
Okay, I can now log in to my laptop and all my stuff is (mostly) accessible, but I still can't get there thru the default login path.  Here's what I finally came up with:

1. When the GRUB screen comes up, I choose the first "recovery mode" boot selection.
2. When the boot mode selection screen comes up, I choose the netroot option ("Drop to root shell prompt with networking").
3. Since this logs me in as root, as soon as I get to the command prompt I type "su bledsoe" to change to my standard login id.
4. Then I type "startx" to start my GUI (currently KDE, though I suspect this would have worked even before I changed it from gnome).

This brings up my standard Ubuntu operating environment and I now have access to all my files, email, internet, etc., so my main problem has been solved; thanks to all of you who offered suggestions, they were very helpful.

There are still a few miscellaneous things that are messed up, however, and I don't yet know how to fix them.  In particular:

a) I can't print.  I tried running the printer configuration tool from the System->Administration menu, but there's no "New Printer" icon.  Also, while trying to get it working, I managed to generate a "The cups scheduler is not running" error message.
b) I can't mount a USB drive.  Every time I plug one in, I get an error message that says "Unable to mount drive, not authorized."

Also, there's the basic problem of still not being able to login without going thru my 4-step workaround.  If anyone has suggestions related to any of these problems, feel free to share.

Thanks,

---

