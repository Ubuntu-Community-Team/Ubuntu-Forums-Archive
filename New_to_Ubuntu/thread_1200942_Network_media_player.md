---
title: "Network media player"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by Dukilla on 2009-06-30
Hey im looking to setup a Ubuntu box, and i want to store all the my music on it. I have multiple computers on my network and want to use a open source media player that will auto update the playlists on all of the computers whenever someone rips music to the server. 

any ideas?

thanks

---

### Post by K.Y.A on 2009-06-30
> **Dukilla said:**
> Hey im looking to setup a Ubuntu box, and i want to store all the my music on it. I have multiple computers on my network and want to use a open source media player that will auto update the playlists on all of the computers whenever someone rips music to the server. 

any ideas?

thanks

This is what you do:

Setup Ubuntu on the machine. Then, install nfs-kernel-server. After that you edit the file /etc/exports and add the path to the directory that you will put the music in. For instance, if you rip your music to /home/username/Music, then add this to the file:
```

/home/username/Music 192.168.1.1/24
```

Obviously replace username with your username on the server. THen, install nfs-kernel-server on the other linux computers on your network. After you do that, go on one of the pcs and run:

```
sudo mount XXX.XXX.XXX.XXX:/home/username/Music ~/Music
```

Replace username iwth your username again. And replace the XXX.XXX.XXX.XXX with the ip address of the server. Then your server's music folder will be your desktop's music folder. Your music on the client computer may appear to be missing , but don't worry, it will come back once the server is unmouted. 

When you put more music on the server, it will appear on the other computers. Just use any media player to play the music, I prefer Banshee or XBMC.

---

### Post by Dukilla on 2009-06-30
my only other problem is that i don't just have Linux computers, i have a couple macs, and a couple PCs as well. anything that will work for all three ?

---

### Post by K.Y.A on 2009-06-30
> **Dukilla said:**
> my only other problem is that i don't just have Linux computers, i have a couple macs, and a couple PCs as well. anything that will work for all three ?


If you could get NFS on those other computers, then sure, if not, sucks for them.:lolflag:

---

### Post by Mornedhel on 2009-06-30
Alternate solution.

Install MPD (there are plenty of instructions on [http://mpd.wikia.com](http://mpd.wikia.com)) on the music server and configure it so it's accessible from the computers you will listen from.

There are plenty of clients, including for Windows.

---

### Post by Dukilla on 2009-06-30
But my other question is will this automatically update all the clients say if someone decides to rip a cd to the server. I want it to push all those new songs to everyones computer.

---

### Post by K.Y.A on 2009-06-30
> **Dukilla said:**
> But my other question is will this automatically update all the clients say if someone decides to rip a cd to the server. I want it to push all those new songs to everyones computer.

YES. Both of these solutions, if not all, will do that. What my suggestion, and probably the easiest, was to share the server's music folder to the other computers with the NETWORK FILESYSTEM and then mount it on the other computers. This is live. Same as remote storage, except you just use a media player instead of a file browser...

---

### Post by ainsworth_t on 2009-06-30
You might also want to check out gnump3d, it's a server for streaming media files. Not sure if it automatically updates the playlists, but since the playlists are hosted server side, I'm sure you can script something and schedule a cron job to do the updates.

---

### Post by Mornedhel on 2009-06-30
If someone adds media to MPD's media directory, you just need to tell the MPD daemon to update its database, and everyone connected to MPD will be able to see the new tracks.

If you do go through the MPD route, I suggest you install it on your machine first and run a graphical client on the same machine (connecting on localhost). If you have a Linux installation somewhere, I recommend GMPC for the client, particularly for Gnome environments.

If not, you can install MPD (the server) on MacOSX, or even on Windows, though the latter requires very heavy tinkering. As said before, there are native clients for every platform.

---

### Post by LowSky on 2009-06-30
couldn't you use SAMBA instead of NFS, SMB is the default for Windows, and I believe Macs can also use the protocol.

---

### Post by K.Y.A on 2009-06-30
> **LowSky said:**
> couldn't you use SAMBA instead of NFS, SMB is the default for Windows, and I believe Macs can also use the protocol.

Good Idea too. Although, NFS is a bit more efficient, and I am an efficiency junky..:KS

---

### Post by Dukilla on 2009-06-30
i dont need to have it stream the music, and i do plan on mounting the drive to all the computers. I guess the main thing that i need is a auto updating library in a media player. but i do not want to use itunes.

---

### Post by K.Y.A on 2009-06-30
> **Dukilla said:**
> i dont need to have it stream the music, and i do plan on mounting the drive to all the computers. I guess the main thing that i need is a auto updating library in a media player. but i do not want to use itunes.

Banshee works on the Linux and Mac os X machines. Just find a client for the Windows ones, and i think Windows Media Player will do the job there.

---

### Post by DownTown22 on 2009-06-30
One question on this method....

When mounting your network drive this way, will it automatically mount on startup?
I know I had problems with my NAS drive mounting/unmounting - but maybe that was a samba thing.

To work around it, I followed this guide:
[http://www.marcus-furius.com/?p=59]("http://www.marcus-furius.com/?p=59")

EDIT:  Also, for media players on my network I use Rhythmbox, Banshee and XMBC and they all update libraries, etc just fine.

---

### Post by K.Y.A on 2009-06-30
> **DownTown22 said:**
> One question on this method....

When mounting your network drive this way, will it automatically mount on startup?
I know I had problems with my NAS drive mounting/unmounting - but maybe that was a samba thing.

To work around it, I followed this guide:
[http://www.marcus-furius.com/?p=59](http://www.marcus-furius.com/?p=59)

EDIT:  Also, for media players on my network I use Rhythmbox, Banshee and XMBC and they all update libraries, etc just fine.

No, I just link an icon or button somewhere on my screen to the mounting command. I also have aliases in bash, so when I type "server2" it mounts the servers first share and when I type "server3" it mounts its second share.

---

### Post by Dukilla on 2009-07-01
ok ill look into those and see what i can find. What do you all think of firefly media server?

---

