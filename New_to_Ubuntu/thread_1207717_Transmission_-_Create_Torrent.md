---
title: "Transmission - Create Torrent"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by Elep.Repu on 2009-07-08
I've googled around and haven't found.

I've done a lot of torrenting, so I know what I'm doing. 
Transmission runs fine, I've just gone to create a torrent for the first time (latest version)-

Says "Torrent created" but I never see it show up in the app. (I've done a search)

The file is different, so none of the others are interfering. (private tracker) 

So far Transmission works fine, I've got 1300 going, so.. :roll:

---

### Post by starcraft.man on 2009-07-08
I'm a little confused by your explanation. It doesn't automatically show up in the client. The program creates a .torrent file that is on your desktop (with the name you gave it), then you can share it with whoever or upload it to a tracker. You want to seed it so just drag the torrent file onto the transmission window and you'll start seeding. I don't see any reason it wouldn't work, just make sure your putting in a proper tracker in the trackers section.

Side note, you don't really have 1300 separate torrents on the same client, do you? If so, Great Zombie Jesus!

---

### Post by Elep.Repu on 2009-07-08
> **starcraft.man said:**
> I'm a little confused by your explanation. It doesn't automatically show up in the client. The program creates a .torrent file that is on your desktop (with the name you gave it), then you can share it with whoever or upload it to a tracker. You want to seed it so just drag the torrent file onto the transmission window and you'll start seeding. I don't see any reason it wouldn't work, just make sure your putting in a proper tracker in the trackers section.

Side note, you don't really have 1300 separate torrents on the same client, do you? If so, Great Zombie Jesus!

Um, 
I'm not seeing anything on the desktop sir, is there a conf file where I can see this configuration?

I can't find anything in the settings unfortunately, and I've looked around the home dir. 
No **.transmission**...

I've perused the normal download dir's for the torrents and no give. No reaction.
Any recommendations?

---
Default (at least for me) dir was the folder, above the folder:
/here/seeded folder/


Kinda lame. And no setting to change it. (**Is there?**)

---

### Post by starcraft.man on 2009-07-08
Well, I don't know why. This is how ya do it step by step.

1. Make folder with files to share.

2. Open Transmission, File > New. Click Folder next to the source bar and navigate to the folder in question. Select the folder and add.

3. Click add next to tracker, and add as many public or private trackers as you want. You need to have at least one, you don't need to upload the .torrent file but you do need it to be tracked on a server.

4. Extras, you can add a comment, or click private torrent, not sure what the latter does. I only make public torrents with friends, if it need be private I send over MSN file transfer. Keeping the .torrent file and tracking on a private server is enough I suppose.

5. Push New at the bottom, it will say torrent created! Then look on desktop (not home directory, the desktop), the name of the file will be the name of the initial source folder (step 1) with .torrent file extension. Send .torrent file to people you want to share with by whatever means and add it to your own client to seed.

Tell me if there's any complications, but it should work without trouble.

---

### Post by servicetech on 2009-07-08
I too am having the same issue, .torrent file is created but doesn't show up on desktop. I have no idea where it's putting the created file...

---

### Post by synapsys on 2009-07-08
Your main problem is Transmission (no offense) 
It's just not a full featured program.

Try Deluge, you'll be much happier with it. 
You can easily seperate your .torrent files from your real downloaded files.
Specify specific directories. 
Basically, you have a lot more control (Desktop is not the only option)

---

### Post by servicetech on 2009-07-08
Just downloaded Deluge, I already like it better. Simple but also full featured. Is there an easy way to import all of my torrents for Transmission?

---

### Post by starcraft.man on 2009-07-08
> **synapsys said:**
> Your main problem is Transmission (no offense) 
It's just not a full featured program.

Try Deluge, you'll be much happier with it. 
You can easily seperate your .torrent files from your real downloaded files.
Specify specific directories. 
Basically, you have a lot more control (Desktop is not the only option)

Uh, you can specify the destination and torrent directories with Transmission. Edit > Preferences > Torrents Tab.

Add torrents from: Should be set to where you download things with firefox to. This is also where your created .torrent files go I believe, by default it's desktop because that's where firefox also defaults to no?

Destination folder: Should be where you want them to end up when downloaded.

Transmission doesn't do everything, but it's enough for me. And there are no bugs with this torrent creation feature as far as I know, works fine on any of my machines.

---

### Post by synapsys on 2009-07-08
> **servicetech said:**
> Just downloaded Deluge, I already like it better. Simple but also full featured. Is there an easy way to import all of my torrents for Transmission?

I think the best way would be to tell it to 'autoadd' .torrents from wherever they are. Make sure it knows where your downloaded files are too. (preferences)

**@starcraft.man:** To each his own I suppose. I never really took the time to learn about transmission. Didn't like it from the get-go. Also it kept telling me that my incoming tcp port was closed when I knew damn sure it was open.

---

### Post by servicetech on 2009-07-08
I actually liked Transmission when I first used it. Very easy to use, quick learning curve. If you never need any advanced features it's perfect. Also I tried ktorrent and didn't care for the GUI.

---

### Post by synapsys on 2009-07-08
I guess the main reason I don't like transmission is that it doesn't let you seperate current and completed downloads. I like to be able to open a folder with only complete downloads without having to sift through half-done downloads.

---

### Post by servicetech on 2009-07-09
> **synapsys said:**
> I guess the main reason I don't like transmission is that it doesn't let you seperate current and completed downloads. I like to be able to open a folder with only complete downloads without having to sift through half-done downloads.

+1, I did hate that about Transmission. Not a problem until you start getting a few torrents.

---

### Post by martimcfly on 2009-08-04
In my case transmission put the .torrent file in the parent folder of the folder I "torrented". Check there.

---

### Post by llamabr on 2009-08-04
In case anyone was wondering, you can make your .torrent on the cli with a program called btmakemetafile, which comes in the 'bittorrent' package, from apt.  

I've always run torrents on cli, until recently, when I discovered deluge, which I also like very much.

---

### Post by Charles Kerr on 2009-08-16
> **synapsys said:**
> I guess the main reason I don't like transmission is that it doesn't let you seperate current and completed downloads. I like to be able to open a folder with only complete downloads without having to sift through half-done downloads.

One workaround is to sort by progress, so that all the completed torrents are at the top of the list.

---

