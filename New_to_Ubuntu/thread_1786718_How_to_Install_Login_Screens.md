---
title: "How to Install Login Screens"
date: 2011-06-20
forum: New to Ubuntu
---

### Post by wisekal on 2011-06-20
Hello,

I'm a first time user of Ubuntu 11.04. I just installed this yesterday. Been exploring a lot and love it so far. How ever, I have a question that I'd assume has been asked a kazillion times but I cannot seem to find an answer. So my question is...

"Trying to personalize my desktop a little. Exploring some themes on [http://art.gnome.org/themes/](http://art.gnome.org/themes/) and wondering how I go about installing a 'Login Screen' after downloading it?"

Tried making my post as "keyword specific" as possible because searching this I found little successful help. Thanks in advance for any help you can offer.

- Bryce

---

### Post by Matt__ on 2011-06-20
I think [SLiM]("http://ubuntuguide.net/customize-ubuntu10-0410-1011-04-login-screen-appearance-via-slim-login-manager") is what you're after.

Or you could use [GDM Tweaker](http://www.webupd8.org/2011/05/change-gdm-theme-background-in-ubuntu.html)[URL="http://ubuntuguide.net/manage-login-interfacegdm-theme-in-new-gnome-with-gdm2setup"]
[/URL]

---

### Post by wisekal on 2011-06-20
> **Matt__ said:**
> I think [SLiM]("http://ubuntuguide.net/customize-ubuntu10-0410-1011-04-login-screen-appearance-via-slim-login-manager") is what you're after.

Or you could use [URL="http://ubuntuguide.net/manage-login-interfacegdm-theme-in-new-gnome-with-gdm2setup"]GDM Tweaker
[/URL]

Thank you, I will look at these sites in a bit. Appreciate the pointers.

---

### Post by shibu_sawyer on 2011-06-20
> **wisekal said:**
> Hello,

I'm a first time user of Ubuntu 11.04. I just installed this yesterday. Been exploring a lot and love it so far. How ever, I have a question that I'd assume has been asked a kazillion times but I cannot seem to find an answer. So my question is...

"Trying to personalize my desktop a little. Exploring some themes on [http://art.gnome.org/themes/](http://art.gnome.org/themes/) and wondering how I go about installing a 'Login Screen' after downloading it?"

Tried making my post as "keyword specific" as possible because searching this I found little successful help. Thanks in advance for any help you can offer.

- Bryce

try ubuntu tweak, for a hand-tip refer this blog
[http://blog.sudobits.com/2011/05/15/how-to-change-login-screen-in-ubuntu-11-04/](http://blog.sudobits.com/2011/05/15/how-to-change-login-screen-in-ubuntu-11-04/)

---

### Post by sikander3786 on 2011-06-20
Or this might help as well.

[http://ubuntu4beginners.blogspot.com/2011/05/customize-gdm-plymouth-grub2.html](http://ubuntu4beginners.blogspot.com/2011/05/customize-gdm-plymouth-grub2.html)

---

### Post by inameiname on 2011-06-20
If you are curious, here are the more technical/manual ways to go about installing a particular Login screen. I also added the manual way to install Plymouth Splash screen. However, I too recommend just using Ubuntu Tweak.:

```

To Change Login Screen Theme and Background (if desired):

1. Move your favorite login wallpaper to the system wallpaper directory. (Make sure that it is of .jpg format):
    sudo mv ~/your-wallpaper-name.jpg /usr/share/backgrounds

2. Activate the Appearance window upon login:
    sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow

3. Close the terminal and log out. At the login screen, the Appearance window will show up. Select your favorite theme and background. Then, log back in.

4. Open a terminal. Type the following command to deactivate the Appearance window upon login:
    sudo unlink /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop


To Change Ubuntu Logo at Boot:
    Plymouth themes are installed in /lib/plymouth/themes (some themes may require plugins installed (as .so files) into /lib/plymouth)

1. Search the archive for packages named plymouth-theme-*:
    sudo apt-cache search plymouth
    sudo apt-get install 'whatever one you choose'
    ...or...
1. Find the packages online and manually install:
    Put the folder and all of it's contents into /lib/plymouth/themes
    sudo update-alternatives --install /lib/plymouth/themes/default.plymouth default.plymouth /lib/plymouth/themes/space-sunrise/space-sunrise.plymouth 200

2. To change the current theme:
    sudo update-alternatives --config default.plymouth
    sudo update-initramfs -u
    sudo update-grub

3. To restore the default theme:
    sudo update-alternatives --auto default.plymouth
    sudo update-initramfs -u
    sudo update-grub

4. Reboot

```

---

### Post by meeples on 2011-06-20
The themes you see at art.gnome.com are no longer compatible with ubuntu, the most you can do is change the window theme and background at the moment.

We're moving to a different login system next release which is much more customisable though :)

---

### Post by wisekal on 2011-06-20
> **shibu_sawyer said:**
> try ubuntu tweak, for a hand-tip refer this blog
[http://blog.sudobits.com/2011/05/15/how-to-change-login-screen-in-ubuntu-11-04/](http://blog.sudobits.com/2011/05/15/how-to-change-login-screen-in-ubuntu-11-04/)

Hello,

Downloaded the Ubuntu Tweak as instructed and installed it. Followed all the given instructions. Now I have Ubuntu Tweak open and inside the "Login Settings" but this only gives me options to change the background image and the icon. Is that all the login screen is... is a background?

When downloading a login screen from [http://art.gnome.org/themes/gdm_greeter](http://art.gnome.org/themes/gdm_greeter) - None in particular, what would be my next step in applying that downloaded theme?

Sorry for my ignorance here. Having some difficulties in figuring this out but it's a learning process and I appreciate all the responses so far. Thank you all.

*EDIT: Read the previous response AFTER posting this. Thank you.

---

### Post by wisekal on 2011-06-20
> **meeples said:**
> The themes you see at art.gnome.com are no longer compatible with ubuntu, the most you can do is change the window theme and background at the moment.

We're moving to a different login system next release which is much more customisable though :)

Hi there,

Fantastic, thank you so much for this response. That basically cancels out my last reply :) I appreciate your assistance and all the previous replies.

---

