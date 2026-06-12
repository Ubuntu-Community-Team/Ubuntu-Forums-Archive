---
title: "[SOLVED] Shared folders permissions with mediatomb (PS3) &amp;amp; Samba (laptop)"
date: 2008-06-30
forum: Networking &amp; Wireless
---

### Post by marriedman on 2008-06-30
I am having a heck of a time getting this to work correctly. I have a hard drive on my desktop that houses all my media; Photo's, Music, Video's, and Wallpaper's. I have it mounted as /media/Omni and I have set the permissions thusly: chmod 777 /media/Omni -R . That should make all the files on the drive accessable by anyone.

From my laptop I can access any file and open it fine via a network resource (samba). From my PS3 I can access my Photo's and Video's (mediatomb). But for some damn reason I cannot play a single song. I keep getting the error that the folder may have been deleted. I can browse the folders, see the song titles and thumbnails of the album covers, but nothing plays. WTH? 

Any tips would really be appreciated.

---

### Post by superprash2003 on 2008-06-30
do you require to type a passworde in the laptop to access the samba share?

---

### Post by marriedman on 2008-06-30
If I am using windows (shudder) I have to use my username and password to access the shared folder. However I never do on Ubuntu. I had not thought about that for the PS3.

However, if that were the case, I shouldn't be able to see the video's, photo's, nor the file structure of the music, right?

---

### Post by superprash2003 on 2008-06-30
true but you could try allowing full access to the shares i.e. without username and password..

---

### Post by marriedman on 2008-07-01
By pure dumb luck I solved the problem. Turns out that it was nothing so complicated as I was making it out. See the following link to the mediatomb forums: 
[http://sourceforge.net/forum/forum.php?thread_id=2081120&forum_id=440751](http://sourceforge.net/forum/forum.php?thread_id=2081120&forum_id=440751)

Long story short, this is a known bug when you have mp3's with embedded album art AND have inotify enabled. 

I am SOOOO glad it wasn't me!

---

