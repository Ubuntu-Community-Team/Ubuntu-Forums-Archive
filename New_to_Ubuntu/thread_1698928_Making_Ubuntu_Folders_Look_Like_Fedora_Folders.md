---
title: "Making Ubuntu Folders Look Like Fedora Folders?"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by Learning Linux 2011 on 2011-03-02
Hello,

I am new to Linux and Ubuntu.

I like the look of Fedora 14, but I prefer the functionality of Ubuntu.

Is there any way I can get Ubuntu folders to look like the blue Fedora folders?

I think I have figured out that Fedora uses "Clear Looks", but the folders and desktop background are different.  I have figured out that the desktop background is just an image file, but I don't understand the folders.

Can anyone help?

---

### Post by I8NY on 2011-03-03
well you can replace the current images used for the folders with the Fedora ones.  or you can look at [http://gnome-look.org/](http://gnome-look.org/) to see if there is a theme already made with the images you want.  If both don't work you can try to customize a theme or make a new one under appearance.

---

### Post by Learning Linux 2011 on 2011-03-03
How would I replace them?

I think that was my first thought, but I am new to Linux and don't understand the file structure or where the files would be located.

Where are the "folders" stored?  Do you just swap files or do you edit the colors/shape?
Can I just put the Fedora folders on a flash drive or something and then directly copy them to Ubuntu?

If so, where do I find them and where do I put them?

And do I need to do something else to make it work?

---

### Post by PhilGil on 2011-03-03
It appears that Fedora uses the gnome-brave icon set, which is available in the repository. You don't have to download it from Gnome Look and manually install. You can install it from the Software Center or by opening a terminal window and entering

```
$ sudo apt-get install gnome-brave-icon-theme
```After installing the theme, go to System-->Preferences-->Appearance in the menu, click the "Customize" button on the Themes tab, select the Icon tab in the Customize widow, and select the Gnome Brave icons.

---

### Post by Hedgehog1 on 2011-03-03
> **PhilGil said:**
> It appears that Fedora uses the gnome-brave icon set, which is available in the repository. You don't have to download it from Gnome Look and manually install. You can install it from the Software Center or by opening a terminal window and entering


Thanks PhilGil!  I like those icons too.

Hey **OUTSTANDING** photography on your web site!

***The Hedge***

:KS

---

### Post by PhilGil on 2011-03-03
> **Hedgehog1 said:**
> 
Hey **OUTSTANDING** photography on your web site!
Thanks. Nice to see other Oregonians around here.

---

### Post by maqtanim on 2011-03-03
You can download the icons from the following link:
[https://launchpad.net/ubuntu/karmic/+source/humanity-icon-theme/0.4.1ubuntu5/+files/humanity-icon-theme_0.4.1ubuntu5.tar.gz](https://launchpad.net/ubuntu/karmic/+source/humanity-icon-theme/0.4.1ubuntu5/+files/humanity-icon-theme_0.4.1ubuntu5.tar.gz)

Or also try the following link (though it seems testing version)
[https://wiki.ubuntu.com/Artwork/Incoming/Karmic/Humanity_Icons](https://wiki.ubuntu.com/Artwork/Incoming/Karmic/Humanity_Icons)

---

### Post by Learning Linux 2011 on 2011-03-23
I put this on the back burner for awhile, but I figured out how to do it.

The Fedora icon theme is called "Mist" and it is located in "/usr/share/icons/"

I created a ".zip" file in Fedora and then copied it over to Ubuntu.

Since the /usr/share/icons/ folder needs root privileges, I used the Terminal to log in as root and move the Mist folder into the Ubuntu icon folder by typing "sudo mv Mist /usr/share/icons"

Then I just went into "Appearance" and set the theme to Clearlooks and the icons to Mist. Viola!

If you really want to make Ubuntu look like Fedora, copy the background from /usr/share/background/ into Ubuntu's /usr/share/background folder.  The Fedora background is called "laughlin"

Use the "Sans" 10 pt font for Application, Document, and Desktop fonts, Sans bold for Window title font and monospace 10 for Fixed width font.

---

### Post by mcduck on 2011-03-24
> **Learning Linux 2011 said:**
> I put this on the back burner for awhile, but I figured out how to do it.

The Fedora icon theme is called "Mist" and it is located in "/usr/share/icons/"

I created a ".zip" file in Fedora and then copied it over to Ubuntu.

Since the /usr/share/icons/ folder needs root privileges, I used the Terminal to log in as root and move the Mist folder into the Ubuntu icon folder by typing "sudo mv Mist /usr/share/icons"

Then I just went into "Appearance" and set the theme to Clearlooks and the icons to Mist. Viola!

If you really want to make Ubuntu look like Fedora, copy the background from /usr/share/background/ into Ubuntu's /usr/share/background folder.  The Fedora background is called "laughlin"

Use the "Sans" 10 pt font for Application, Document, and Desktop fonts, Sans bold for Window title font and monospace 10 for Fixed width font.

...or you could have just installed the *gnome-themes* -package from the repositories, it includes the Mist theme & icons. ;)

---

### Post by Learning Linux 2011 on 2011-03-24
> **mcduck said:**
> ...or you could have just installed the *gnome-themes* -package from the repositories, it includes the Mist theme & icons. ;)


How does that work? From the terminal or software update?
Do you use the sudo command?  In this case for example, what would I do exactly?
(I'm new to Ubuntu and Linux)

---

### Post by mcduck on 2011-03-24
> **Learning Linux 2011 said:**
> How does that work? From the terminal or software update?
Do you use the sudo command?  In this case for example, what would I do exactly?
(I'm new to Ubuntu and Linux)

You can use whatever package management tool you want (except the update tool, since it only handles updates). Search in the Software Center should work, and so would using Synaptic Package Manager. Or running "sudo apt-get install gnome-themes" in a terminal.

Or the easy way, just click this link: [apt:gnome-themes]("apt:gnome-themes") :)

---

