---
title: "Desktop Trash icon spams me with Starting File Manager"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by Lovell on 2010-08-11
Hello,

I'm running Ubuntu 10.04 LTS 32-bit. I'm trying to simply put a Trash bin icon on my desktop. I've read posts and blogs about how to do it, but I encounter a problem that I can't figure out.

I can go to the terminal and type
```
gconf-editor
```
and go to apps>mautilus>desktop and check trash_icon_visible, but nothing happens. Same thing with or without sudo.

So I downloaded Ubuntu Tweaks and tried to enable like that. When I do this, I get spammed with windows titled Starting File Manager in the system bar and all my current desktop icons disappear. I continue to get spammed with new windows until I uncheck trash_icon_visible. After that the windows start closing and my icons return to the desktop.

Here's a screenshot of the Configuration Editor:
[img]http://img191.imageshack.us/img191/8796/naut.png[/img]

Anyhow have any clue how to fix this and get it working?

Thanks

---

### Post by Lovell on 2010-08-12
:(

---

### Post by lkjoel on 2010-08-12
> **Lovell said:**
> Hello,

I'm running Ubuntu 10.04 LTS 32-bit. I'm trying to simply put a Trash bin icon on my desktop. I've read posts and blogs about how to do it, but I encounter a problem that I can't figure out.

I can go to the terminal and type
```
gconf-editor
```
and go to apps>mautilus>desktop and check trash_icon_visible, but nothing happens. Same thing with or without sudo.

So I downloaded Ubuntu Tweaks and tried to enable like that. When I do this, I get spammed with windows titled Starting File Manager in the system bar and all my current desktop icons disappear. I continue to get spammed with new windows until I uncheck trash_icon_visible. After that the windows start closing and my icons return to the desktop.

Here's a screenshot of the Configuration Editor:
[img]http://img191.imageshack.us/img191/8796/naut.png[/img]

Anyhow have any clue how to fix this and get it working?

Thanks
First, download LinuxEssentials, and extract it inside your homedir. (available in my sig.)
Then when the spamming happens, open up a Terminal, then type this in:
```
killall nautilus
cd ~
./FASTGNOME.sh
```

---

### Post by Lovell on 2010-08-13
Thanks for the reply lkjoel.

I downloaded LinuxEssentials and extracted them to my home folder, ran Ubuntu Tweaks and clicked "Show Trash icon on desktop". When it started spamming me again, I did what you said to in the terminal and it did kill the spam.

But now I have no icons at all on my desktop :(

Any ideas?

---

### Post by lkjoel on 2010-08-13
Where did you get the Ubuntu Tweaks?
You might have gotten it from a wrong place.

---

### Post by Lovell on 2010-08-14
Hi lkjoel

I got Ubuntu Tweak from: [http://ubuntu-tweak.com]("http://ubuntu-tweak.com/")

I don't thinks it is that though because the built-in configuration editor in Ubuntu doesn't put the icon on the desktop at all, like it should.

I just don't understand what is wrong here. I haven't changed much in Ubuntu but the theme, and I've tried changing the theme back but that didn't fix this.

Thanks again  lkjoel.

---

### Post by lkjoel on 2010-08-14
Try this in a terminal:
```
sudo apt-get update
sudo apt-get dist-upgrade
```
And you got Ubuntu Tweaks from the correct website.

---

### Post by lkjoel on 2010-08-22
I found the solution.
Remove that setting.
Make a link on your desktop to a folder named: ~/.local/share/Trash/files.

---

### Post by sd73ta on 2010-10-13
Im having the same problem with the starting file manager over and over.  I was also getting an error about OAFIID:GNOME_Indicator do I want to delete which I did but I am still getting hammered with nautilus.  I keep using killall which is fine but i cant get the FASTGNOME.sh to work.  Any help would be appreciated.

P.S. This happened on a fresh install of 10.10

---

### Post by JustinR on 2010-10-13
> **sd73ta said:**
> Im having the same problem with the starting file manager over and over.  I was also getting an error about OAFIID:GNOME_Indicator do I want to delete which I did but I am still getting hammered with nautilus.  I keep using killall which is fine but i cant get the FASTGNOME.sh to work.  Any help would be appreciated.

P.S. This happened on a fresh install of 10.10

You could reset all of your GNOME settings to see if that works.

---

Press ALT + F2; type in 'gksudo nautilus /home/USERNAME'; Press OK
Press 'CTRL + H' to view hidden files
Delete the folders:
> 
.gnome2
.gnome2_private
.gconfd
.gconf


---

### Post by sd73ta on 2010-10-13
> **JustinR said:**
> You could reset all of your GNOME settings to see if that works.

---

Press ALT + F2; type in 'gksudo nautilus /home/USERNAME'; Press OK
Press 'CTRL + H' to view hidden files
Delete the folders:

This worked for the GNOME error but not the uncontrolled starting file manager.

---

### Post by Korenwolf on 2010-10-13
Hello all,

Ive got the same problem after installing the official ubuntu tweaks.
I can't get into my file manager anymore, because it keeps starting the file manager....

I did not alter anything with ubuntu tweak

---

### Post by sd73ta on 2010-10-14
anyone???

---

### Post by Korenwolf on 2010-10-15
Hi All,

Just did a kind of an amazing discovery.

I had the problem of starting file manager spam on my laptop after installing ubuntu tweak.

When I started my laptop today it was gone, and the only thing changed was that I didn't have my external monitor plugged in.

When I tried it again with the monitor plugged back in, the problem returned.

As I don't really need the second monitor, my problem is almost solved. But it is still an interesting phenomena.

Cheers,
Erwin

---

### Post by lkjoel on 2010-10-17
Try using Ubuntu 10.10, remove Ubuntu Tweaks, then try it again.

---

### Post by sd73ta on 2010-10-18
i stopped by this thread and tried that [solution]("http://ubuntu-ky.ubuntuforums.org/newreply.php?do=newreply&p=9896015") but to no avail.  I dont have ubuntu tweak and this happens regardless of dual or not monitors.  I am on ten ten fresh install.  Please throw me some more suggestions.  One last thing I havent touched my trash and have no items on the desktop so I dont think this problem is specific to that

---

### Post by lkjoel on 2010-10-19
Type this into a Terminal window to get the Trash icon.
```
ln -s ~/.local/share/Trash/files ~/Desktop
mv ~/Desktop/files ~/Desktop/Trash

```

---

### Post by sd73ta on 2010-10-21
Does anyone have any more suggestions about the uncontrolled starting file manager?  I have noticed during boot up an error flashes on screen for half a second before I get to the log in window.  Should I just reinstall??:(

---

### Post by boot_sectorz on 2010-10-24
Adding my voice to the issue. I didn't do any of the things otrher people did to get the starting file manager spam. This is a fresh install of 10.10 (bearly 12hrs running). 
I tried deleting a file on my flash disk, and was hit. Since nothing major was running, I logged off, but a log back in started. Had no choice but restart the laptop. After I restarted, the problem has not yet resurfaced and was doing my research on the issue when I came to this thread.
Anyone figured it out yet?

---

### Post by Jeff_Syr on 2010-10-27
Having the same issue at startup, although I have not made any changes to gnome settings.  Upgraded early to 10.10 from 10.04 and have fully updated.  About 1 week ago, Starting File Manager error started.  After login, the entire lower panel fills with Starting File Manager... and after a few moments they all disappear.  I have made no configuration changes to the system other than standard updates.  I don't think this problem has anything to do with adding trash icon to the desktop.  - Jeff

---

### Post by Chazz44able on 2010-11-04
> **Lovell said:**
> Hello,

I'm running Ubuntu 10.04 LTS 32-bit. I'm trying to simply put a Trash bin icon on my desktop. I've read posts and blogs about how to do it, but I encounter a problem that I can't figure out.

I can go to the terminal and type
```
gconf-editor
```and go to apps>mautilus>desktop and check trash_icon_visible, but nothing happens. Same thing with or without sudo.

So I downloaded Ubuntu Tweaks and tried to enable like that. When I do this, I get spammed with windows titled Starting File Manager in the system bar and all my current desktop icons disappear. I continue to get spammed with new windows until I uncheck trash_icon_visible. After that the windows start closing and my icons return to the desktop.

Here's a screenshot of the Configuration Editor:
[IMG]http://img191.imageshack.us/img191/8796/naut.png[/IMG]

Anyhow have any clue how to fix this and get it working?

Thanks



Thanks, this has given me back my "Trash bin", i lost it when i deleted my panel at the bottom and was not able to access it from my "Places" - i didn't think about using the Configuration Editor

---

### Post by lkjoel on 2010-11-05
> **sd73ta said:**
> i stopped by this thread and tried that [solution]("http://ubuntu-ky.ubuntuforums.org/newreply.php?do=newreply&p=9896015") but to no avail.  I dont have ubuntu tweak and this happens regardless of dual or not monitors.  I am on ten ten fresh install.  Please throw me some more suggestions.  One last thing I havent touched my trash and have no items on the desktop so I dont think this problem is specific to that
That solution is just a simplified (and not as working) version of Linux Essentials.
Use Linux Essentials instead.
The link is in my signature.

---

### Post by lkjoel on 2010-11-05
> **Jeff_Syr said:**
> ... I don't think this problem has anything to do with adding trash icon to the desktop.  - Jeff
It may or it may not.
It happens sometimes after using LinuxEssentials.
You just have to re-run it to stop it, so that could be one solution.

---

