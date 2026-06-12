---
title: "firefox 3.5 how do i loaded it on to my system"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by blake7 on 2009-06-30
hi i have just down loaded 3.5 from the firefox site how do i gewt it to run.

---

### Post by The Cog on 2009-06-30
This is what I did:
Download the tar.bz2 file to my desktop. Then these commands:
> cd Desktop
tar xjf firefox-3.5.tar.bz2
sudo cp -r firefox /opt/firefox-3.5
sudo ln -s /usr/local/bin/firefox /opt/firefox-3.5/firefox

This leaves the original firefox there, but links the new one into /usr/local/bin which is searched before /usr/bin and therefore takes precedence.

---

### Post by lovinglinux on 2009-06-30
For instructions on how to install Firefox 3.5 or upgrade the 3.0.11 version, check the [color=#CC0000]**Firefox Alternatives & Newer Versions**[/color] section of the [**[color=#CC0000]Firefox optimization and troubleshooting thread[/color]**](http://ubuntuforums.org/showthread.php?t=1193567).

For a list of other threads talking about the same subject, visit [http://ubuntuforums.org/showthread.php?t=1200781](http://ubuntuforums.org/showthread.php?t=1200781)

---

### Post by blake7 on 2009-07-01
this did not work any other iders

---

### Post by Merk42 on 2009-07-01
> **blake7 said:**
> this did not work any other iders

Which didn't work?
What happened when you tried them?

If you're running Jaunty and tried lovinglinux's idea, did you look in the GNOME Applications menu for *Shiretoko*, not Firefox, under Internet?

---

### Post by ak331 on 2009-07-01
> **The Cog said:**
> This is what I did:
Download the tar.bz2 file to my desktop. Then these commands:


This leaves the original firefox there, but links the new one into /usr/local/bin which is searched before /usr/bin and therefore takes precedence.
It is the same thing. it depends where you decompressed the folder and just point it to the place where it is located and now I have firefox 3.5 at three locations 
/desktop/firefox
/user/home/firefox
/user/lib/firefox

no matter where the icon points to it. It will run that copy.

---

### Post by lovinglinux on 2009-07-01
> **ak331 said:**
> It is the same thing. it depends where you decompressed the folder and just point it to the place where it is located and now I have firefox 3.5 at three locations 
/desktop/firefox
/user/home/firefox
/user/lib/firefox

no matter where the icon points to it. It will run that copy.

Have you read the my reply on the other thread?

As I said, there is no **/user/home** folder or **/user/lib/firefox**, you are mixing things. 

The folders or files you are referring to are **/home/[color=#CC0000]ak331[/color]/firefox**, **/home/[color=#CC0000]ak331[/color]/Desktop/firefox**,  **/[color=#CC0000]usr[/color]/lib/firefox** and **/opt/firefox-3.5**. There is also **/[color=#CC0000]usr[/color]/lib/firefox-3.0.11** and possibly **/[color=#CC0000]usr[/color]/lib/firefox-3.5**

Please notice that I have replaced all **[color=#CC0000]user[/color]** above with **[color=#CC0000]ak331[/color]** or **[color=#CC0000]usr[/color]** to avoid confusion. You should replace **[color=#CC0000]ak331[/color]** with whatever username you use to login on Ubuntu, whenever it appears in the codes below.

So, delete these folders and files:

/home/**[color=#CC0000]ak331[/color]**/firefox
/home/**[color=#CC0000]ak331[/color]**/Desktop/firefox

Then run the command below to delete the file **/[color=#CC0000]usr[/color]/local/bin/firefox**. This is a file path, not the same as the other firefox folders. This is because Linux doesn't need the extension most of the time, so when I write the path here it looks like a folder, but it is actually a file.

```
sudo rm -f /usr/local/bin/firefox
```

> [color=#CC0000]**How to run commands in a Terminal: **[/color]Open "Applications >> Accessories >> Terminal", then type or paste the code (CTRL+SHIFT+V) and hit *Enter*. You might be prompted to enter your password. You cannot see it while you type, but it is there. Then just hit *Enter* again to run the command. Please do not run commands without knowing what they do. If you do not understand what a command does, ask for explanations.

Then this command:

```
sudo rm -fr /opt/firefox-3.5
```

Now run the following command:

```
sudo apt-get purge firefox-3.5
```

Then change the path of the firefox launcher (I know you know how to do it) to this:

```
firefox %u
```

Now click the Firefox launcher and check the version of Firefox. It should say Firefox 3.0.11. Basically we have reset all your changes.

Now, download [this file](http://www.mozilla.com/en-US/firefox/upgrade.html?from=getfirefox) and save in your home directory **/home/[color=#CC0000]ak331[/color]/** 
Don't put it inside any folder and don't extract it. Just save it there.

Then run this commands:

```
cp -R ~/.mozilla ~/.mozilla.backup
sudo tar -jxvf firefox-3*.tar.bz2 -C /opt
rm firefox-3*.tar.bz2
sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup
sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
```

Click the Firefox launcher and check the version of it again, it should say Firefox 3.5

That's it.

---

### Post by steveneddy on 2009-07-01
I thought that if you are running anything past Intrepid that you could just

```
sudo apt-get install firefox-3.5
```

or am I wrong

actually I run Hardy and I just added the ppa, did a 

```
sudo apt-get update
```

then a

```
sudo apt-get install firefox-3.5
```

[linky]("http://webupd8.blogspot.com/2009/06/firefox-35-rc-1-ubuntu-repository-deb.html")

---

### Post by ak331 on 2009-07-01
> **lovinglinux said:**
> Have you read the my reply on the other thread?

As I said, there is no **/user/home** folder or **/user/lib/firefox**, you are mixing things. 

The folders or files you are referring to are **/home/[color=#CC0000]ak331[/color]/firefox**, **/home/[color=#CC0000]ak331[/color]/Desktop/firefox**,  **/[color=#CC0000]usr[/color]/lib/firefox** and **/opt/firefox-3.5**. There is also **/[color=#CC0000]usr[/color]/lib/firefox-3.0.11** and possibly **/[color=#CC0000]usr[/color]/lib/firefox-3.5**

Please notice that I have replaced all **[color=#CC0000]user[/color]** above with **[color=#CC0000]ak331[/color]** or **[color=#CC0000]usr[/color]** to avoid confusion. You should replace **[color=#CC0000]ak331[/color]** with whatever username you use to login on Ubuntu, whenever it appears in the codes below.

So, delete these folders and files:

/home/**[color=#CC0000]ak331[/color]**/firefox
/home/**[color=#CC0000]ak331[/color]**/Desktop/firefox

Then run the command below to delete the file **/[color=#CC0000]usr[/color]/local/bin/firefox**. This is a file path, not the same as the other firefox folders. This is because Linux doesn't need the extension most of the time, so when I write the path here it looks like a folder, but it is actually a file.

```
sudo rm -f /usr/local/bin/firefox
```



Then this command:

```
sudo rm -fr /opt/firefox-3.5
```

Now run the following command:

```
sudo apt-get purge firefox-3.5
```

Then change the path of the firefox launcher (I know you know how to do it) to this:

```
firefox %u
```

Now click the Firefox launcher and check the version of Firefox. It should say Firefox 3.0.11. Basically we have reset all your changes.

Now, download [this file](http://www.mozilla.com/en-US/firefox/upgrade.html?from=getfirefox) and save in your home directory **/home/[color=#CC0000]ak331[/color]/** 
Don't put it inside any folder and don't extract it. Just save it there.

Then run this commands:

```
cp -R ~/.mozilla ~/.mozilla.backup
sudo tar -jxvf firefox-3*.tar.bz2 -C /opt
rm firefox-3*.tar.bz2
sudo mv /opt/firefox/plugins /opt/firefox/plugins.backup
sudo ln -s /usr/lib/xulrunner-addons/plugins /opt/firefox/plugins
sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox
sudo ln -s /opt/firefox/firefox /usr/bin/firefox
```

Click the Firefox launcher and check the version of it again, it should say Firefox 3.5

That's it.
Thanks again. I guess mine was a round about way.

---

### Post by lovinglinux on 2009-07-01
> **steveneddy said:**
> I thought that if you are running anything past Intrepid that you could just

```
sudo apt-get install firefox-3.5
```

or am I wrong

actually I run Hardy and I just added the ppa, did a 

```
sudo apt-get update
```

then a

```
sudo apt-get install firefox-3.5
```

[linky]("http://webupd8.blogspot.com/2009/06/firefox-35-rc-1-ubuntu-repository-deb.html")

Jaunty comes with Firefox 3.5 beta (Shiretoko) in the repositories, but you need to add the *[ubuntu-mozilla-daily](https://help.ubuntu.com/community/FirefoxNewVersion)* PPA if you want to update it to the final version. Final version became available in that PPA only a couple of hours ago.

Nevertheless, there are other methods, like using [Ubuntuzilla](http://ubuntuzilla.wiki.sourceforge.net/) or the one described on this thread. It seems the OP prefer this method.

I have tried the PPA and Ubuntuzilla. Both work like a charm, but I ended compiling from source and gained 30% in performance ;)

---

### Post by colau on 2009-08-15
Easiest way to install firefox-3.5!
[psychocats]("http://www.psychocats.net/ubuntu/firefox")

---

