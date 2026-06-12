---
title: "Installing Seamonkey 2.1 in Ubuntu 9.04"
date: 2011-06-17
forum: New to Ubuntu
---

### Post by Bamboozled on 2011-06-17
This may be better posted elsewhere, but as an idiot I'm after an answer worded in the easiest and simplest way possible. 

I am struggling to install Seamonkey 2.1. Have been googling for hours and trying out different methods and typing in various gobbledygook in the terminal. I did install and use an older version of Seamonkey some time ago. For the record I would prefer to stick with Ubuntu 9.04 as I like it. 

Here's what I done: 

I downloaded seamonkey-2.1.tar.bz2 

I followed the first part of the README information - all this :

```

To install SeaMonkey by downloading the tar.bz2 file:

  1. Create a directory named "seamonkey" (mkdir seamonkey) and change
     to that directory (cd seamonkey).

  2. Click the link on the site you're downloading SeaMonkey from to
     download the package (seamonkey*.tar.bz2) file into the seamonkey
     directory.

  3. Change to the seamonkey directory (cd seamonkey) and decompress the
     file with the following command:

       tar jxvf sea*.tar.bz2

     This creates a "seamonkey" directory under your seamonkey directory.

  4. Change to the seamonkey directory (cd seamonkey).

  5. Run SeaMonkey with the following run script:

    ./seamonkey


```

So far, so good. Easy peasy. 

Next, I typed something (and I can't remember what it was) into the terminal and I got the Seamonkey browser. 

Now I am stuck.

How do I get Seamonkey to appear in the Applications menu? The instructions for this in the README file is for a Gnome Panel and I am unsure how to apply the information.

---

### Post by Rex Bouwense on 2011-06-17
It has been a while since I used Jaunty 9.04 and I believe that it has reached its end of life, but wasn't Seamonkey in the repository?  It certainly would have been easier to install it through the Ubuntu Software Center.

---

### Post by pricetech on 2011-06-17
Seamonkey is in the repositories.  I'm pretty sure they offer a deb as well, though I won't swear to it.

If you don't find it listed in the software center, I know you'll find it in Synaptic.

---

### Post by dcsoldschool53 on 2011-06-17
> **Bamboozled said:**
> This may be better posted elsewhere, but as an idiot I'm after an answer worded in the easiest and simplest way possible. 

I am struggling to install Seamonkey 2.1. Have been googling for hours and trying out different methods and typing in various gobbledygook in the terminal. I did install and use an older version of Seamonkey some time ago. For the record I would prefer to stick with Ubuntu 9.04 as I like it. 

Here's what I done: 

I downloaded seamonkey-2.1.tar.bz2 

I followed the first part of the README information - all this :

```

To install SeaMonkey by downloading the tar.bz2 file:

  1. Create a directory named "seamonkey" (mkdir seamonkey) and change
     to that directory (cd seamonkey).

  2. Click the link on the site you're downloading SeaMonkey from to
     download the package (seamonkey*.tar.bz2) file into the seamonkey
     directory.

  3. Change to the seamonkey directory (cd seamonkey) and decompress the
     file with the following command:

       tar jxvf sea*.tar.bz2

     This creates a "seamonkey" directory under your seamonkey directory.

  4. Change to the seamonkey directory (cd seamonkey).

  5. Run SeaMonkey with the following run script:

    ./seamonkey


```So far, so good. Easy peasy. 

Next, I typed something (and I can't remember what it was) into the terminal and I got the Seamonkey browser. 

Now I am stuck.

How do I get Seamonkey to appear in the Applications menu? The instructions for this in the README file is for a Gnome Panel and I am unsure how to apply the information.
  Click on this link, it will tell you how to do it, and especially view the attached thumbnails too.
[http://ubuntuforums.org/showpost.php?p=10805473&postcount=5](http://ubuntuforums.org/showpost.php?p=10805473&postcount=5)

Now as for your Icons, they will be in the /seamonkey/chrome/icons/default folder. In a terminal you will have to sudo cp them from the /seamonkey/chrome/icons/default folder to /usr/share/pixmaps folder.

Right now, I have to leave for work, but when I get off this evening. I will look for your thread if you need further help.

---

### Post by Bamboozled on 2011-06-17
> **pricetech said:**
> Seamonkey is in the repositories.  I'm pretty sure they offer a deb as well, though I won't swear to it.

If you don't find it listed in the software center, I know you'll find it in Synaptic.

The very reason I am using the terminal is Synaptic failed. Here's the message that comes up: 

```



W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/universe/s/seamonkey/seamonkey-browser_2.0.9+build1+nobinonly-0ubuntu0.9.04.1_i386.deb
  404 Not Found [IP: 91.189.92.166 80]


W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/universe/s/seamonkey/seamonkey-mailnews_2.0.9+build1+nobinonly-0ubuntu0.9.04.1_i386.deb
  404 Not Found [IP: 91.189.92.166 80]


W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/universe/s/seamonkey/seamonkey_2.0.9+build1+nobinonly-0ubuntu0.9.04.1_all.deb
  404 Not Found [IP: 91.189.92.166 80]


W: Failed to fetch http://security.ubuntu.com/ubuntu/pool/universe/s/seamonkey/seamonkey-chatzilla_2.0.9+build1+nobinonly-0ubuntu0.9.04.1_all.deb
  404 Not Found [IP: 91.189.92.166 80]


```

```

Click on this link, it will tell you how to do it, and especially view the attached thumbnails too.
http://ubuntuforums.org/showpost.php...73&postcount=5

Now as for your Icons, they will be in the /seamonkey/chrome/icons/default folder. In a terminal you will have to sudo cp them from the /seamonkey/chrome/icons/default folder to /usr/share/pixmaps folder.


```

dcsoldschool53, I am understanding the instructions, but embarrassingly the copying from  /seamonkey/chrome/icons/default folder to /usr/share/pixmaps folder is giving me gyp. Keep getting this message:

```
 

cp: cannot stat `/seamonkey/chrome/icons/default': No such file or directory


```

Life would be easier if I could just copy and paste the seamonkey folder to the usr one.

---

### Post by dcsoldschool53 on 2011-06-18
Type this into a terminal```
locate default48.png
```This will tell you where your seamonkey and some other icon are located. Now I am going to put the output from my PC on here to show you how to do it. Remember this is an example only.```
/usr/lib/firefox-4.0.1/chrome/icons/default/default48.png
/usr/lib/xulrunner-1.9.2.17/chrome/icons/default/default48.png
/usr/local/seamonkey/chrome/icons/default/default48.png
```Now your computer output will be different from mines, but you can still see where the seamonkey icon is located. Copy your seamonkey's icon location. 

In the terminal, type```
sudo cp /paste/your/seamonkey's/icon/location/here /usr/share/pixmaps
```This is an example using my system```
sudo cp /usr/local/seamonkey/chrome/icons/default/default48.png /usr/share/pixmaps
```**Do not copy and paste my example to your system. It will not work for your system unless you have it setup the way that mines is setup. I can tell you now that it is not.**

Pixmaps is one of many places that Ubuntu store icons that the user or the system can use. There are many others as you will see.

Now it is time to attach the icon to the launcher. See my attachment's thumbnails. The first one is the pop up launcher. See the icon of the screw, click on it.  It will open up nautilus in a place where many of the system and user icons are stored.

The next attachment will show you the location of the pixmaps folder. Look in nautilus and find that folder and click on it.

The third attachment will show you the icon that we are going to attach to seamonkey. Find it and click on it. Then click open, and now you have a icon for seamonkey.

Fill in the rest of the information: ```
name: Seamonkey
``````
command /Path/to/file
```and ```
comment: if you want to put one there
``` Click ok, and then wait a couple of minutes for it to appear. Now close alacarte. 
Look for seamonkey in Application Menu and click it to see if it launches. Forgive me for long reply, and I hope this will help you.

---

### Post by dcsoldschool53 on 2011-06-18
The easy way to do it in a terminal, is to type gksu nautilus /usr/local/seamonkey/chrome/icons/default. Nautilus would have opened in that directory for us. Then we would have to look for the icon. Right click to copy it. Then navigate to the /usr/share/pixmaps folder to paste it there. Close Nautilus.

Then, do the rest of what I wrote. If this does not work then I know what to do for your system now.

---

### Post by Bamboozled on 2011-06-18
I got most of that but I am unsure what to put in the command box bit in the launcher.  I have the Seamonkey icon in the applications menu, but am getting an error message about Failed to execute child process.

---

### Post by Bamboozled on 2011-06-18
Problem solved. I was typing the correct blah/blah/blah into that command box, but I redid it as root and it is now working.

dcsoldschool53, Thanks very much for your help. I worship the ground upon which you walk.

---

