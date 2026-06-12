---
title: "Play mp3 through network shares"
date: 2006-10-28
forum: Networking &amp; Wireless
---

### Post by exir on 2006-10-28
Hi Folks,

I just cant figure it out how i get it work :S

when i create from my laptop (running ubuntu) an new network share to my windows pc and then open an mp3 file on the network share, it doesnt start playing the music. It will be listed in the xmms playlist but i cannot start it.

Does one of you know how i can fix this problem so that i can play mp3 files over the network?

thnx alot!

---

### Post by lazyart on 2006-10-28
Here's a thread to look over: [http://www.ubuntuforums.org/showthread.php?t=273206&highlight=open+samba+files](http://www.ubuntuforums.org/showthread.php?t=273206&highlight=open+samba+files)

Another thing... XMMS player won't play them for me, but movie player will, and this is without doing the above...

---

### Post by meng on 2006-10-28
For playing media files on shares, you'd be best to mount the samba shares properly rather than just view them through a browser.
e.g.
sudo mount -t smbfs -o username=***,password=*** //path/to/share /mount/point

(if you haven't already done so, install smbfs)
sudo aptitude install smbfs

---

### Post by dmsn on 2006-10-28
Hey doesnt asking for samba or someting like that.
I have same problem as he, he want to stream  over network.
We put the track in xmms and see it but it doesnt start.
I must download to my laptop for play it but i want stream.

How can we fix it out?

thanks

---

### Post by meng on 2006-10-28
The best solution is to mount the network share as smbfs, see the above posts.

---

### Post by Christian Heldal-Lund on 2006-10-28
Thanks, that helped. Just what I needed!!!

---

### Post by exir on 2006-10-29
thnx for the reactions, but unfortunately it doesnt work by me..
when i try to mount the share as you type then i get a screen full of options about mounting.

What i have done so far is go to places - connect to server - windows share. over here i created an mount at my desktop to the share. Isnt this the same as you mean but than at the gui way?

---

### Post by exir on 2006-11-02
does anyone have an solution for this one:confused: :confused:

---

