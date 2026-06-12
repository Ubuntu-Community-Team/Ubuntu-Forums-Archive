---
title: "Dropbox troubles"
date: 2010-06-27
forum: New to Ubuntu
---

### Post by afroman10496 on 2010-06-27
Hello all,
I am using the latest dropbox version and I cannot figure out how to remove the ugly icon:
[[IMG]http://img13.imageshack.us/img13/3323/screenshotbe.png[/IMG]](http://img13.imageshack.us/i/screenshotbe.png/)

I tried to change the pictures to monochrome by changing the pics in the /~/.dropbox-dist/icons folder, but it doesnt seem to work. I restarted dropbox and even rebooted my laptop but it doesnt change the icon in the notificaton area. any ideas?:confused::confused::confused:

---

### Post by Sonsum on 2010-06-27
This page seems like it could be of help, it provides other icons, and I'm sure theres help for installing it.

[http://www.omgubuntu.co.uk/2010/05/5-replacement-dropbox-icon-sets.html]("http://www.omgubuntu.co.uk/2010/05/5-replacement-dropbox-icon-sets.html")

Let me know how this works, I'd like a pretty dropbox icon :p

---

### Post by afroman10496 on 2010-06-27
Wow dude thanks- it works perfectly, but you have to do a couple of things  before that:

1- you have to upgrade to the latest experimental build, 0.8.55. to do this, install the .deb and then enter these commands in order:
```
dropbox stop
cd ~
wget http://dl-web.dropbox.com/u/17/dropbox-lnx.x86-0.8.55.tar.gz
tar -xvf dropbox-lnx.x86-0.8.55.tar.gz
```

and then 
```
dropbox start
```

2- to actually change the icons, you have to download the mono icons (i reccomend going here [http://www.omgubuntu.co.uk/2010/05/5-replacement-dropbox-icon-sets.html](http://www.omgubuntu.co.uk/2010/05/5-replacement-dropbox-icon-sets.html) for a guide)

3- when the archive download is done, open it. it will probably have a folder named "icons" in it. go to extract it, but first navigate to your home folder, use the keyboard combo **ctrl H** to show hidden files, navigate to your "dropbox-dist" folder, and extract the archive into it.

4- then reload dropbox- it will not look so blue and ugly- yay!

hoped this helped for everyone else! btw this is for 32bit Ubuntu's.

---

