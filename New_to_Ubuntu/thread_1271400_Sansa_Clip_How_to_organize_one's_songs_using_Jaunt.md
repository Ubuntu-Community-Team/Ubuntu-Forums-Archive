---
title: "Sansa Clip: How to organize one's songs using Jaunty?"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by swarup on 2009-09-20
My Sansa Clip mounts and is recongized just fine in Jaunty. But I haven't been able to figure out how to *organize* my sound files on it. Let's say one has 350 mp3 files, and one wants to divide them up into folders so as to make the files easily and quickly accessible. Using Jaunty one can create, say, 20-30 separate folders in the Sansa Clip's root directory, and dump one's mp3 files into them according to category. But when one disconnects the Sansa Clip and goes to access the mp3 files, the folders do not appear! All the mp3 files are lumped together in one big group, under "Music". This means one has to scroll through i.e. 280 files in order to get to the 281st one. I tried creating folders and putting them into the Sansa Clip's "Album" folder, but so doing simply makes the mp3 files therein disappear completely so one cannot access them at all! So, what is the solution to organizing mp3 files on the Sansa Clip using Jaunty?

---

### Post by Garrovick on 2009-09-20
Sansa players do not do "folders".  Create play lists or sort them by genre.

---

### Post by swarup on 2009-09-20
> **Garrovick said:**
> Sansa players do not do "folders".  Create play lists or sort them by genre.

Actually, I have a Sansa Fuze and that works with folders just fine. The Fuze has a category in its menu called "folders", and whatever folders you create (using *any* OS) and add to the Fuze, will be found there. Works great.

In the Sansa Clip, how does one use Jaunty to create play lists, or sort by genre? Let me also explain, that I do not listen to any professional albums-- or music at all for that matter. All of my mp3 files are personally recorded files of various lectures and discussions. So would I use nautilus for creating these playlists and genres, and if so, how? I do not see any options for so doing.

---

### Post by Garrovick on 2009-09-20
From the Sansa Forums.  Maybe a trip there could help?  I use Vista to manage my E280 and iPod video. All Linux can do is "stack" mp3s on a chip or hard drive that plays sounds.  There is no true functionality.


> Got the playlists working, using Rhythmbox. It's a little more complicated than just changing the characters that end the lines, but not too difficult. To hopefully save others a little trouble, here's the procedure I used:

 

1) In Rhythmbox, choose Music--Playlist, and choose Save to File

2) If playlist format isn't set to MPEG (*.m3u) then make that change

3) Save the file to the Music folder on the Clip+

4) Open the playlist file saved to the Clip+ in a text editor

5) Remove the path from each line - see below for more explanation

6) Search and replace / with \ for whole document

7) Save file, making sure to use CRLF as line ending format

 

About removing paths: The path that should be in the playlist on the Clip+ should be relative to the location of the m3u file, which is in the Music directory. For example, the original path from Rhythm box will be something like "/home/user/music/artist/album/song.mp3". Assuming that you copied the artist directory to the Clip+, along with all albums and songs contained in it, the path that should be in the playlist should be "artist\album\song.mp3".



---

### Post by swarup on 2009-09-20
> **Garrovick said:**
> From the Sansa Forums.  Maybe a trip there could help?
Yes, thanks. I had actually been there, and used their guidance to update the Sansa firmware on the Clip. I saw a few discussions of the playlists, but was looking at the time for some way of making the "folder" concept work since I knew it works on the Fuze. But I'll go back and look again at the playlist discussions.  

> **Garrovick said:**
> I use Vista to manage my E280 and iPod video. All Linux can do is "stack" mp3s on a chip or hard drive that plays sounds.  There is no true functionality.

Thanks for the rhythmbox info-- I may give it a shot. My laptop is actually an Apple MBP, which I have set up as a dual boot with OSX/Jaunty. I could add Vista and have a triple boot, but the thought of doing that just for organizing my Sansa Clip is not so inspiring.

---

