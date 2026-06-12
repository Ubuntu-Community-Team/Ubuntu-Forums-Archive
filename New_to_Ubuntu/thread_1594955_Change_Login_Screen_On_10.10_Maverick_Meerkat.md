---
title: "Change Login Screen On 10.10 Maverick Meerkat"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by spikoley on 2010-10-12
How do I change the background image for the login screen?

---

### Post by rogueleader12345 on 2010-10-12
i don't think you can anymore, pretty sure they did away with changeable login screens after 8.10, but not 100% sure

---

### Post by JustinR on 2010-10-12
> **spikoley said:**
> How do I change the background image for the login screen?

Hi,

_Logout_ of Ubuntu
Press the keys '**Ctrl + ALT + F1**'
Login with your username and password, and then you'll have a terminal like prompt. and enter this in:
```

export DISPLAY=:0.0
sudo -u gdm gnome-control-center

```

Press '**Ctrl + ALT + F7**'
A control panel will pop up - you can customize the appearance including background + theme. Click the 'Appeance' button. When your done, exit out of the control center and log back in.

---

### Post by rogueleader12345 on 2010-10-12
can you still switch the login screen to a custom one, or can you just switch the background image?

---

### Post by spikoley on 2010-10-12
> **JustinR said:**
> Hi,

_Logout_ of Ubuntu
Press the keys '**Ctrl + ALT + F1**'
Login with your username and password, and then you'll have a terminal like prompt. and enter this in:
```

export DISPLAY=:0.0
sudo -u gdm gnome-control-center

```

Press '**Ctrl + ALT + F7**'
A control panel will pop up - you can customize the appearance including background + theme. Click the 'Appeance' button. When your done, exit out of the control center and log back in.

I tried that and after running the command it said can't open display.  When I Ctrl + ALT + F7 it brought me to a screen that said Ubuntu 10.10 and it would not let me do anything.

Any ideas?

---

### Post by Dennis N on 2010-10-12
You can easily change the log-in screen background image by using Ubuntu Tweak.

Edit: Use the PPA at [https://launchpad.net/~tualatrix/+archive/ppa](https://launchpad.net/~tualatrix/+archive/ppa)

[There is a Maverick Version.]

---

### Post by JustinR on 2010-10-12
> **spikoley said:**
> I tried that and after running the command it said can't open display.  When I Ctrl + ALT + F7 it brought me to a screen that said Ubuntu 10.10 and it would not let me do anything.

Any ideas?

This should be working fine - it works on my Maverick installation - are you sure you typed the commands correctly?

As far as I know, you can switch login managers to have complete customization, but with this method you can change most of the login screen's appearance.

---

### Post by JustinR on 2010-10-12
> **JustinR said:**
> This should be working fine - it works on my Maverick installation - are you sure you typed the commands correctly?

As far as I know, you can switch login managers to have complete customization, but with this method you can change most of the login screen's appearance.

Sorry - I typed one of the last commands wrong.

Logout of Ubuntu
CTRL + ALT + F1
Login in the terminal
```

export DISPLAY=:0.0
sudo -u gdm gnome-control-center
[COLOR="Red"]*Enter Password*[/COLOR]

```
Switch back using
**CTRL + ALT + F8**
Change the appearance of the login screen, exit out of GNOME Control Center and log back in.

---

### Post by spikoley on 2010-10-12
I ended up installing Ubuntu-tweak and I recommend it for updating the login screen.

To install the repository:
```
sudo add-apt-repository ppa:tualatrix/ppa
```
Update the repository list:
```
sudo apt-get update
```
Install Unbuntu-tweak
```
sudo apt-get install ubuntu-tweak
```

Then you can run it from Applications> System Tools> Ubuntu Tweak

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
[https://launchpad.net/~tualatrix/+archive/ppa?field.series_filter=maverick](https://launchpad.net/~tualatrix/+archive/ppa?field.series_filter=maverick)

---

### Post by Ctrl-Alt-F1 on 2010-10-12
Alternative method for those that don't want to install a program:  The ubuntu background wallpaper is in /usr/share/backgrounds/warty-final-ubuntu.png.

Moving any file to that location will change the image.  I don't know if it has to be a .png or not but I always convert them to .png just in case.

---

### Post by spikoley on 2010-10-13
> **Ctrl-Alt-F1 said:**
> Alternative method for those that don't want to install a program:  The ubuntu background wallpaper is in /usr/share/backgrounds/warty-final-ubuntu.png.

Moving any file to that location will change the image.  I don't know if it has to be a .png or not but I always convert them to .png just in case.

I tested this method and it worked.  I just saved the new image as warty-final-ubuntu.png and placed it into /usr/share/backgrounds/.

---

### Post by Alex22 on 2010-10-13
> **Ctrl-Alt-F1 said:**
> Alternative method for those that don't want to install a program:  The ubuntu background wallpaper is in /usr/share/backgrounds/warty-final-ubuntu.png.

Moving any file to that location will change the image.  I don't know if it has to be a .png or not but I always convert them to .png just in case.

It works! After 3 hours of messing with gconf-editor and gnome-control-center - such a hacking method from the early nineties' PC games :]

Cool method, thanks Ctrl-Alt F1.

Notabene, no such a feature in Ubuntu 10.10 is a scandal for me. :)

---

### Post by rsazal on 2010-10-14
> **Alex22 said:**
> It works! After 3 hours of messing with gconf-editor and gnome-control-center - such a hacking method from the early nineties' PC games :]

Cool method, thanks Ctrl-Alt F1.

Notabene, no such a feature in Ubuntu 10.10 is a scandal for me. :)


BUT, i can't change it . why ? does it need any administrator allowance ?

---

### Post by spikoley on 2010-10-14
> **rsazal said:**
> BUT, i can't change it . why ? does it need any administrator allowance ?

Because you are outside of your /home directory.

---

### Post by Sub101 on 2010-10-14
The image also cannot be a jpg. 

Seems like the login screen cant use it.

---

### Post by spikoley on 2010-10-14
> **Sub101 said:**
> The image also cannot be a jpg. 

Seems like the login screen cant use it.

Just rename it to a .png.  It worked for me.

---

### Post by Ctrl-Alt-F1 on 2010-10-14
> **rsazal said:**
> BUT, i can't change it . why ? does it need any administrator allowance ?

Yes, when you do the mv command you must put sudo in front of it.
For example I keep all my wallpaper images in a folder in my home directory called Theming, therefore:

sudo mv [COLOR="Red"]~/Theming/wallpaper.png[/COLOR] [COLOR="Lime"]/usr/share/backgrounds/warty-final-ubuntu.png[/COLOR]

You would have to change the first part of the command (red) to whatever the location of your image is.  The green part will be the same for everyone.

Remember to use tab completion (hit tab when you are typing in the name of the directories to automatically finish them).  This will prevent moving the wrong file to the wrong directory.

---

### Post by blackcobra on 2010-10-17
alt-F2 (run application)

gksudo ubuntu-tweak
it will ask you for your password:
Enter
and walla

Ubuntu tweak has a load of other things that you can mess round with.

---

### Post by peterbe on 2010-12-04
> **Ctrl-Alt-F1 said:**
> Alternative method for those that don't want to install a program:  The ubuntu background wallpaper is in /usr/share/backgrounds/warty-final-ubuntu.png.

Moving any file to that location will change the image.  I don't know if it has to be a .png or not but I always convert them to .png just in case.
I just did that on 11.04 natty alpha-1 - Looking at the old /usr/share/backgrounds/warty-final-ubuntu.png file with the 'file' command, it is actually a .jpg file. But I replaced it with an actual .png file, so it's only the name and extension that matters.

---

### Post by uk_dhacker on 2011-01-27
> **JustinR said:**
> Sorry - I typed one of the last commands wrong.

Logout of Ubuntu
CTRL + ALT + F1
Login in the terminal
```

export DISPLAY=:0.0
sudo -u gdm gnome-control-center
[COLOR=Red]*Enter Password*[/COLOR]

```Switch back using
**CTRL + ALT + F8**
Change the appearance of the login screen, exit out of GNOME Control Center and log back in.


It threw the following errors when i tried
No protocol specified
Cannot Open Display:

Some body help.. I wanna change ma login screen

---

### Post by tad1073 on 2011-01-27
The link below will help you.


[http://ubuntuforums.org/showthread.php?p=8362591#post8362591](http://ubuntuforums.org/showthread.php?p=8362591#post8362591)

---

### Post by sasindu on 2011-02-17
> **spikoley said:**
> I ended up installing Ubuntu-tweak and I recommend it for updating the login screen.

To install the repository:
```
sudo add-apt-repository ppa:tualatrix/ppa
```Update the repository list:
```
sudo apt-get update
```Install Unbuntu-tweak
```
sudo apt-get install ubuntu-tweak
```Then you can run it from Applications> System Tools> Ubuntu Tweak

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)
[https://launchpad.net/~tualatrix/+archive/ppa?field.series_filter=maverick]("https://launchpad.net/%7Etualatrix/+archive/ppa?field.series_filter=maverick")

thanks..........it worked

---

