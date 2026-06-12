---
title: "Ubuntu Tweak"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by Avidanborisov on 2011-02-02
Hi.
Some friends recommended me to install ubuntu tweak because it is safer than to do things in gconf-editor as I did recently. so I installed it through the PPA but now I get some errors about ubuntu sources but they don't really change something so I just ignore them...
My question is - 
Ubuntu Tweak is safe? Can I use it without being worried?
And can I use its update manager and configuration settings instead of ubuntu's ones?

---

### Post by Paqman on 2011-02-02
Personally I don't use anything like Ubuntu Tweak. Most of what it does can be done with the normal tools Ubuntu comes with, or using apps from the official repos. Ubuntu Tweak also adds a lot of 3rd party repos, the quality of which may be variable. 

If you tell us what you're trying to achieve, we can probably show you how to do it without needing to install 3rd party software.

What is the exact error you get when trying to update your sources?

---

### Post by Avidanborisov on 2011-02-02
> **Paqman said:**
> Personally I don't use anything like Ubuntu Tweak. Most of what it does can be done with the normal tools Ubuntu comes with, or using apps from the official repos. Ubuntu Tweak also adds a lot of 3rd party repos, the quality of which may be variable. 

If you tell us what you're trying to achieve, we can probably show you how to do it without needing to install 3rd party software.

What is the exact error you get when trying to update your sources?

Actually all I wanted to do is change the default font of GNOME to Arial and I did it successfully with gconf-editor.
But my friends said that working with such tools is unsafe and that I should try Ubuntu Tweak because it is easy and it has lots of options.
I don't remember the exact error but it said that it couldn't fetch some things and that some files have been deleted or ignored.
Also I would like you to tell me how can I change the login screen background and login logo (ubuntu logo).

---

### Post by Avidanborisov on 2011-02-02
someone?

---

### Post by NightwishFan on 2011-02-02
Ubuntu Tweak is a lot more useful then it was in the past. I personally have had no problems with it and install it every time I reinstall my system. Ubuntu tweak can change the background and the logo of the log-in screen, but not the theme as far as I know. It also disables that blasted drum sound when the log-in screen loads.

---

### Post by Zlatan on 2011-02-02
> **Avidanborisov said:**
> Actually all I wanted to do is change the default font of GNOME to Arial and I did it successfully with gconf-editor.
But my friends said that working with such tools is unsafe and that I should try Ubuntu Tweak because it is easy and it has lots of options.
I don't remember the exact error but it said that it couldn't fetch some things and that some files have been deleted or ignored.
Also I would like you to tell me how can I change the login screen background and login logo (ubuntu logo).

You can change fonts in System>Preferences>Appearance

---

### Post by Paqman on 2011-02-02
> **Avidanborisov said:**
> Actually all I wanted to do is change the default font of GNOME to Arial and I did it successfully with gconf-editor.

You can also change that in System > Prefs > Appearance > Fonts

> 
But my friends said that working with such tools is unsafe and that I should try Ubuntu Tweak because it is easy and it has lots of options.

gconf-editor doesn't have a very friendly interface, but is safe to use if you know what you're editing. Ubuntu Tweak gathers lots of settings into one place and gives it a helpful interface, but the downside is that if you're switching to using 3rd party repos you can no longer have confidence in the software you're installing. Some of it may be less stable than getting things from the default repos.

> 
I don't remember the exact error but it said that it couldn't fetch some things and that some files have been deleted or ignored.


Open up Synaptic and hit "reload" and paste the error here.

> 
Also I would like you to tell me how can I change the login screen background and login logo (ubuntu logo).

Do you want to change them to something in particular? You can change the theme on both of those. The login screen is called GDM, you can get GDM themes from gnome-look.org. By the login logo I assume you mean the Plymouth splash screen (the one with the dots?). There are some Plymouth themes in the repos, but it's a pretty new package and i'm not sure how customisable it is yet.

---

### Post by NightwishFan on 2011-02-02
> **Paqman said:**
> gconf-editor doesn't have a very friendly interface, but is safe to use if you know what you're editing. Ubuntu Tweak gathers lots of settings into one place and gives it a helpful interface, but the downside is that if you're switching to using 3rd party repos you can no longer have confidence in the software you're installing. Some of it may be less stable than getting things from the default repos.

I agree with this, I would avoid using any of the package management or software installation features of Ubuntu Tweak just because its generally not needed. The customization parts are all pretty ok, though many options are useless.

---

### Post by kn0w-b1nary on 2011-02-02
In my experience, Ubuntu Tweak works well when adding other repositories like Skype, Swiftfox, or Adobe Flash. A lot easier than manually checking the website for updates manually. I like it, but as with all 3rd party software, use at your own risk.

---

### Post by Avidanborisov on 2011-02-02
Thats the error:
> Failed to fetch [http://ppa.launchpad.net/canonical-dx-team/une./ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/canonical-dx-team/une./ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/canonical-dx-team/une./ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/canonical-dx-team/une./ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

I dont want to change the theme, just the login screen background and ubuntu logo on the middle.
I changed it with ubuntu tweak but I dont know if it is safe so I prefer to do it in other way. 
Sorry for being noob.

---

### Post by Avidanborisov on 2011-02-02
Hello?

---

### Post by plucky on 2011-02-03
This is the location it is trying to get to.

[http://ppa.launchpad.net/canonical-dx-team/une./ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/canonical-dx-team/une./ubuntu/dists/maverick/main/source/Sources.gz)

This is where it actually needs to go

[http://ppa.launchpad.net/canonical-dx-team/une/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/canonical-dx-team/une/ubuntu/dists/maverick/main/source/Sources.gz)

Notice the difference is a . after une in the address line.

To fix it you probably have to edit either your sources.list file or the PPA file located in sources.list.d directory.

Please post the output from a terminal of ```
cat /etc/apt/sources.list
ls -l /etc/apt/sources.list.d/
```

Good Luck

---

### Post by Paqman on 2011-02-04
> **Avidanborisov said:**
> 
Sorry for being noob.

Nothing to apologise for. Everybody was a noob once.

---

