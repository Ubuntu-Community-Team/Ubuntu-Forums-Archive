---
title: "Wanted - Script to update html page automatically"
date: 2011-05-10
forum: New to Ubuntu
---

### Post by jimwill on 2011-05-10
Let's see if I can explain this. 

Basically I am trying to do a script that automates updating an html webpage that has mp3 files on it. These mp3's are from a local radio station's "swap shop" program that I am frequently unable to listen to when it is on. This is for my personal and family use only and is not for the public.

I have a bash script that records the internet radio stream each day at a specific time and puts the resulting mp3 file into a folder. Then it will check for the seven previous days and delete the seventh days mp3. Then it will regenerate the index.html file using echo "<a href=xxxxx>">>index.html and such, including the html header/body/footer info. 

This is a rather awkward mess, and if I manually edit the html to add any notes, it does not preserve the notes the next day.

What I would like to do is have the script just edit the html file, removing the mp3 from seven days ago and adding today's mp3 at the top of the list. By editing instead of regenerating the file it would keep any manually entered notes until the mp3 file was a week old when it would be deleted anyway. I assume this would be either awk or sed or a combination, but don't know where to start!

In addition I am using a lot of "&nbsp;&nbsp;&nbsp;" where I need tabs. Do I need to continue with that for page formatting or is there some way to get rid of them?

Anyone???
Thanks for any help given!

---

### Post by deconstrained on 2011-05-10
Instead of manually updating the page with some kind of script, it may be way easier with a little bit of PHP. These functions would get you a list of files:

[http://php.net/manual/en/function.readdir.php](http://php.net/manual/en/function.readdir.php)
[http://php.net/manual/en/function.opendir.php](http://php.net/manual/en/function.opendir.php)
[http://php.net/manual/en/function.scandir.php](http://php.net/manual/en/function.scandir.php)

Once you have an array of mp3 filenames, displaying the list of MP3 files will be nothing more fancy than a "foreach" loop.

If the load on the server becomes too great, you can just use the same PHP code to generate static pages, and manually update/replace. But since it's just for you and your family I doubt this will be the case, so all the more reason to have PHP do it all automatically.

---

