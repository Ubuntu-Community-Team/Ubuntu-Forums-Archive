---
title: "Keep/move rhythmbox playlists from one distro to another"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by Rodemire on 2010-04-25
Hallo,
Does anyone know if its possible to keep/move your playlists when u migrate from one ubuntu distro to another?

I have Karmic now and as Lucid is coming out soon i was thinking of giving it a try. I plan on doing a fresh install of Lucid on another harddrive and if i like it i wil use it permanently. I have a lot of playlists in rhythmbox and copying them/ transfering them looks daunting. Is there an easy, or less stressful way other than redoing the playlists? 

My music is on a separate partition from /home, i have been using Linux/Ubuntu for a year and am not afraid of the terminal ;-). I've looked through the forums and havent found something i could use.

All help is appreciated.

---

### Post by undecim on 2010-04-25
If you leave your /home directory alone when installing, your rhythmbox database, playlists, and settings will stay right where they are. Rhythmbox stores it's config files in ~/.local/share/rhythmbox/

Just make sure that when you are installing, you choose to use your /home directory as ext4 on /home/, but DO NOT format it (double check this at the final screen, too).

---

### Post by Rodemire on 2010-04-25
Thanx a lot,i will give that a try. I knew that the /home partition could be maintained, i hope i can do it when the time comes. I will make sure i wont format it.

---

### Post by rabiabidabi on 2010-04-25
In Rhythmbox, you can select each playlist and save as an m3u file. Put it on a flash stick, sd card, any external drive. When you do your fresh install, Rhythmbox can import your playlists.

---

