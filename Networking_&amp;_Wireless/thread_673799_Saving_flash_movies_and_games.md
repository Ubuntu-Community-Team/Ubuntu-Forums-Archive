---
title: "Saving flash movies and games"
date: 2008-01-21
forum: Networking &amp; Wireless
---

### Post by luisjorge on 2008-01-21
Hello!

I was just wondering... Does anyone know how to save flash movies and/or games? I know it could be done by checking the Page Info on Firefox, and saving the ".swf" embedded item on the page, but it says "not cached" so nothing is saved.
Is there a way of doing this? Is there a cache folder where all these things are saved for playing?

Thanks in advance!

Luis Jorge.

---

### Post by holbech on 2008-01-21
Not ubuntu specific, firefox specific, but all browsers have similar ways

Firefox for Newbies
a. Click Tools - Page Info
b. Click the Media Tab on the Page Info Windows
c. The media tab has a complete list (with preview) of Images, CSS Files and Shockwave Flash files that were downloaded by the Firefox browser while rendering (loading) the page.
d. Scroll down the list and locate the swf file.
e. Click the "Save As" button. Select some directory on your hard drive and save the file (No need for a third-party plug-in)

Firefox for Geeks and Power Users
a. Type about:blank in the Firefox address bar
b. Now click List cache entries or directly type about:cache?device=disk (Disk cache device)
c. Press Ctrl+F and try to location the flash file by typing some part of website URL or the flash file name or just .swf. After some hit and trial, you should be able to locate the swf file URL
d. Click the SWF URL to open the Cache Entry Information page. Right click on the link and choose "Save link as"

Taken from [http://labnol.blogspot.com/](http://labnol.blogspot.com/)

Or perhaps easier, with the forefox web developer extension installed:

Information->view Page information -> media -> save as 

:-)

---

### Post by luisjorge on 2008-01-27
Hi! Thanks for the info!
Indeed, I was able to download the .swf files, but I can't play them. I downloaded gnash player, but the movies play with very weird colors, all pink or all green, and I can't really see anything. If I chose to open them with Firefox, it "downloads" the movie again, and just copies it in my desktop, but doesn't play it.

Any ideas?

Thanks very much!

Luis Jorge.

---

### Post by nyinge on 2008-01-27
This firefox [addon]("https://addons.mozilla.org/en-US/firefox/addon/3006") will help you with downloading flash videos.

Not so sure if [vlc player]("http://www.videolan.org/") will play swf files, but it does play flv files well.  You can also check out the standalone player [here]("http://download.macromedia.com/pub/flashplayer/updaters/9/flash_player_9_linux_dev.tar.gz").

---

### Post by luisjorge on 2008-01-28
Hi! Thanks for the tip! The addon works fine, and the standalone player works perfectly!
Still, I have problems with games, because I can play them, but the keyboard doesn't work within the game.
Also, do you have the web page from which I can download the standalone player? Just for reference.

Thanks very much!

Luis Jorge.

---

### Post by nyinge on 2008-01-28
For vlc?  It's in the Ubuntu's Universe repositories.  I'm not sure about keyboard not working for the games.

---

### Post by luisjorge on 2008-01-28
Sorry, I meant the standalone Adobe Flash player you included in the link. It links to the file, but not to the source of the file :)

Thanks!

---

### Post by nyinge on 2008-01-29
Right.  There are a few others in the zip file.  

- Extract the zip file.  Right-click on the file and extract.  (I'm guessing here since I'm using KDE.)
- Navigate to the source file.  (Picture attached!)
- Extract it again, and just double-click on the extracted file.

Hope that helps.

---

