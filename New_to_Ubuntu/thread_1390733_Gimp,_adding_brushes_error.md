---
title: "Gimp, adding brushes error"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by noseshark on 2010-01-26
[FONT=Century Gothic][SIZE=2]Im trying to add brushes to Gimp but this error keeps showing up:

[IMG]http://i982.photobucket.com/albums/ae305/noseshark/Screenshot2.png[/IMG]

I am dropping them into the brushes folder, Also there is a Thumbs.db file in every brush set I downloaded do I add this to the folder as well?
[/SIZE][/FONT]

---

### Post by 311005901 on 2010-01-27
Sorry you're having trouble... :( But I may be able to help! :)

"/usr/share/gimp" is a directory owned by root. To get the brushes to appear in GIMP, there are two things you can do.

First: If you're the only one using the computer, you can just put it in your home directory. In the top left panel, click on "Places>Home Folder" and press 'Control+H' to see hidden folders. Open a folder called ".gimp-2.6". Your folder may be named differently depending on which version of GIMP you have installed. Then, open up the "brushes" folder and copy and paste your brushes there. 

Second: If there are others using the computer and you want to share the brushes with every user, you have to put it in the directory you were talking about. You can do this, but it's a little more difficult and you have to be the administrator:
Press 'Alt+F2' to open up the run dialog. Type in "gksu nautilus" and press enter. (The 'gksu' allows you to be root (administrator) and 'nautilus' is the file browsing program.)
[COLOR="Red"]Be careful! If you don't know what you're doing, you can really harm your system![/COLOR]
Once you have root access, click on "File System" on the left panel and navigate to '/usr/share/gimp/2.0/brushes' and copy and paste the brushes into there.

Note: You'll have to restart GIMP to be able to use the brushes.

Hope that helped you! :popcorn:

Oh. And 'Thumbs.db' is not needed in GIMP. That file is just a Windows system file.

---

### Post by rakete on 2010-01-27
or you can just get a terminal window and enter some commands, here we go:

change to gimp brushes folder (adjust the Version number if you use an older version)
```
cd ~/.gimp-2.6/brushes
```download brushes with wget command, mostly you will get a tarball, this is just an example url, but it works..
```
wget http://crunchbang.org/misc/ubuntu-logo-gimp-brushes.tar.gz
```extract it like that:
```
tar xvf ubuntu-logo-gimp-brushes.tar.gz
```afterwards you can delete your downloaded tarball:
```
rm ubuntu-logo-gimp-brushes.tar.gz
```brushes will show up in Gimp...

example taken from here: [URL="http://crunchbang.org/archives/2008/01/20/ubuntu-logo-gimp-brushes/"]http://crunchbang.org/archives/2008/01/20/ubuntu-logo-gimp-brushes/
[/URL]

---

### Post by 311005901 on 2010-02-06
Were we able to help you with your issue? :)

---

