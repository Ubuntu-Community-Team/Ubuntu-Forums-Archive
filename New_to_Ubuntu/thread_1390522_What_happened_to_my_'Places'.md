---
title: "What happened to my 'Places'?"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by tom.swartz07 on 2010-01-25
Hi everyone,


Earlier yesterday, I turned on my computer and noticed that my "places" that I had bookmarked with Nautilus have disappeared, and will not persist from session to session.


I tried restoring them by adding them again (They were only a few; Home folder, Dropbox, Ubuntu One, Documents), but they disappear every time I log out and back in.


Is the file that says what locations are pointed to corrupt? How would I investigate further, or restore my previous bookmarks?

---

### Post by warfacegod on 2010-01-25
Have you moved the folders that they pointed to?



I've been meaning to ask, is that a gorilla high fiving a great white?

---

### Post by tom.swartz07 on 2010-01-25
> **warfacegod said:**
> Have you moved the folders that they pointed to?



I've been meaning to ask, is that a gorilla high fiving a great white?

Nope, Havent moved them at all. Ive probably edited some files in the folders, but thats it.


Yep, thats a gorilla hi-5-ing a shark in front of an explosion. Nice.


Im completely baffled by why they disappeared and will not stay now.. They wont show up in "places" on the panel, nor in Docky or AWN, nor the sidebar in Nautilus.

---

### Post by warfacegod on 2010-01-25
> **tom.swartz07 said:**
> Nope, Havent moved them at all. Ive probably edited some files in the folders, but thats it.


Yep, thats a gorilla hi-5-ing a shark in front of an explosion. Nice.


Im completely baffled by why they disappeared and will not stay now.. They wont show up in "places" on the panel, nor in Docky or AWN, nor the sidebar in Nautilus.

Try purging and reinstalling.

---

### Post by warfacegod on 2010-01-25
It's like purging before the binge.

---

### Post by tom.swartz07 on 2010-01-25
> **warfacegod said:**
> Try purging and reinstalling.

pshoooooooooo--- thats just what I didnt want to hear. I just reinstalled my system last week after I switched to a new hard drive.


It was working for the longest time, even after the new install, up until just the other day.

---

### Post by warfacegod on 2010-01-25
> **tom.swartz07 said:**
> pshoooooooooo--- thats just what I didnt want to hear. I just reinstalled my system last week after I switched to a new hard drive.


It was working for the longest time, even after the new install, up until just the other day.

I don't mean reinstall the entire OS, just the panel.

---

### Post by warfacegod on 2010-01-25
```
sudo apt-get purge gnome-panel
```

```
sudo apt-get install gnome-panel
```

---

### Post by tom.swartz07 on 2010-01-25
> **warfacegod said:**
> ```
sudo apt-get purge gnome-panel
```

```
sudo apt-get install gnome-panel
```

AHHH! I see- I did have some little error appear with the panel, but i fixed that just by removing the gconf setting.


Ill try that and let you know

---

### Post by tom.swartz07 on 2010-01-27
Nope still didnt fix it.


I purged and reinstalled gnome-panel but it didnt return any functionality to the places.


I have a pic attached, just for reference. Below Home folder and Desktop, there used to be a list of other folders- documents, dropbox, downloads, ubuntu one, etc.

Additionally, you could see on my docky (left side) the bottom used to have the places/bookmarks also. Ill see if I could dig up a screencap showing how it used to (should) look.

---

### Post by tom.swartz07 on 2010-01-27
Heres an image from a few weeks ago that shows how the places *should* appear on docky also.

[IMG]http://lh6.ggpht.com/_tORug_uHNu4/S0QcUlqn4BI/AAAAAAAAAKw/BlkWrwXTKqY/s400/Screenshot-1.png[/IMG]

---

### Post by warfacegod on 2010-01-27
If you add a Main Menu to the Panel, is Places, in that menu, also messed up?


Very nice desktop. If that were mine, I'd make the menus and Panel translucent. Is that Conky or Widgets?

---

### Post by warfacegod on 2010-01-27
Have you tried fixing Broken Dependancies?

---

### Post by tom.swartz07 on 2010-01-27
> **warfacegod said:**
> If you add a Main Menu to the Panel, is Places, in that menu, also messed up?


Very nice desktop. If that were mine, I'd make the menus and Panel translucent. Is that Conky or Widgets?

Added Main Menu- but still no luck.

Well thank you! I have conky- thats what youre seeing on the right hand side.


Strangely enough, when I went to open synaptic, it wouldnt work- I had a 'Xapian::DatabaseCorruptError' when I tried from the terminal. I was able to fix it with sudo update-apt-xapian-index

There were no broken dependencies to fix after I got synaptic working.


This is getting weird. I have no idea what is going on and why my system seems so strange as of late.

---

### Post by k3lt01 on 2010-01-27
My gut feeling is your PC is about to crash, I have this happen to me before. Take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=1004012"), it may or may not be helpful.

---

### Post by warfacegod on 2010-01-27
You know...the more I think on this, the more apt I am to agree with k3lt01. I think you would be very wise to have a current backup of all the files you value. Let me go hunting around some more and I'll come back.

---

### Post by tom.swartz07 on 2010-01-27
> **k3lt01 said:**
> My gut feeling is your PC is about to crash, I have this happen to me before. Take a look at [this thread]("http://ubuntuforums.org/showthread.php?t=1004012"), it may or may not be helpful.

Hey thanks! Its not too promising to know that I might have a big crash in the future, but at least I know its recoverable. 


What exactly happened to your computer? were you able to check the logs?



Just before this all happened, I had a problem with my filesystem- nothing that a normal fsck couldnt handle. 

Would you suggest that I abandon all problems currently and just re-install the OS? Fortunately, I have a seperate /home partition, so its not a BIG deal to re-install, its just that I would prefer not to do so.

---

### Post by warfacegod on 2010-01-27
After searching, lurking, sneaking, and peeking, I found only one other reference to your issue. I read the site and it turned out to be totally irrelevant. Somebody lost their Places and then remembered later that he deleted the bookmarks himself.

---

### Post by warfacegod on 2010-01-27
Have tried purging Nautilus? Or, even the entire desktop?

---

### Post by tom.swartz07 on 2010-01-27
> **warfacegod said:**
> After searching, lurking, sneaking, and peeking, I found only one other reference to your issue. I read the site and it turned out to be totally irrelevant. Somebody lost their Places and then remembered later that he deleted the bookmarks himself.

HAHA! This is why youre awesome, warface! I too did some creeping and peeking, and although there were several others with similar problems in the past week, there were no legitimate solutions, most of the cases people suggested that you just try to re-bookmark the places again.

I cant figure out why it wont persist from session to session for me.

---

### Post by warfacegod on 2010-01-27
I'm at something of a loss. Not at a loss to explain my awesomeness just your Places thing. I assume you have all your updates. If you give my last post a shot then do each separately. Nautilus first. ubuntu-desktop last.

---

### Post by k3lt01 on 2010-01-27
I would just follow warface's simple suggestions atm. My machine recovered brilliantly after its issue so I wouldn't do a complete reinstall unless you absolutely have to. Just make sure you have a backup of everything you cannot afford to lose just incase your situation is worse than mine was.

Keep us informed.

Edit: sorry, I forgot to answer your question. There was nothing in my logs that suggested my machine was going to have a problem, as far as it was aware the relevant folders were still available in Places, as can be seen in the screenshots on that thread, it just didn't recognise they weren't available on the Desktop itself. After I checked it over after it recovered I never gave the issue another thought until I saw your thread.

---

### Post by k3lt01 on 2010-01-27
You may want to try setting up another user for example a "test" user and copying their basic config files over to your user. I sometimes do that when I don't do a complete new install when a new version comes out. Doing this gives you the newer configurations available without having to manually save everything you have. Yes I am aware it is a cocky attitude but sometimes things have to be done quickly so I take chances with my setup :popcorn: Infact I'll be doing it on my main desktop machine in the morning :)

---

### Post by tom.swartz07 on 2010-01-27
> **k3lt01 said:**
> You may want to try setting up another user for example a "test" user and copying their basic config files over to your user. I sometimes do that when I don't do a complete new install when a new version comes out. Doing this gives you the newer configurations available without having to manually save everything you have. Yes I am aware it is a cocky attitude but sometimes things have to be done quickly so I take chances with my setup :popcorn: Infact I'll be doing it on my main desktop machine in the morning :)

I just made a new user, and strangely enough the bookmarks are there!

What the heck?!

Okay- heres where I need to pick your brains- where would I locate the config file that has the listing for the bookmarked places? Perhaps I could copy this from the 'guest' user and replace the busted ones on my profile?

Obviously theres nothing wrong with the programs themselves- it just seems that whatever file holds my bookmarked places is corrupt. Perhaps its an .xml file, or even a .conf file. I dunno.

---

### Post by k3lt01 on 2010-01-28
> **tom.swartz07 said:**
> Okay- heres where I need to pick your brains- where would I locate the config file that has the listing for the bookmarked places? Perhaps I could copy this from the 'guest' user and replace the busted ones on my profile?One of the threads I have been looking for has the answer to this question, I'll keep looking and post it as soon as I find it.

Edit: [This is the other thread I was looking for]("http://ubuntuforums.org/showthread.php?t=1095538"), read through it to the part that discusses creating the "test" user and try the suggestion made by taavikko in post 17. It may take a little bit of fiddling but hopefully the files you need are in there somewhere. Before I forget to say it, make a backup of your original files so if this doesn;t work and makes a mess of things you can at least replace your originals.

---

### Post by warfacegod on 2010-01-28
You might compare this files from each user account:

/.local/share/gvfs-metadata

---

### Post by tom.swartz07 on 2010-01-28
> **warfacegod said:**
> You might compare this files from each user account:

/.local/share/gvfs-metadata

Whelp, theres quite a few more files in my folder than in the guest folder: ```
tom@karmic-laptop:~$ sudo ls /home/guest/.local/share/gvfs-metadata/
home  home-c85fbf30.log
tom@karmic-laptop:~$ sudo ls /home/tom/.local/share/gvfs-metadata/
afc:host=195cdb5aea5ade9430ff725fb0e88243e300d44a
afc:host=195cdb5aea5ade9430ff725fb0e88243e300d44a-59939063.log
burn:
burn:-52672da7.log
computer:
computer:-22d2d298.log
gphoto2:host=%5Busb%3A001%2C002%5D
gphoto2:host=%5Busb%3A001%2C002%5D-886ded1e.log
home
home-53dede0a.log
home-cc640e0b.log
label-Purchased
label-Purchased-47e338db.log
label-SPACEBALLS_LB
label-SPACEBALLS_LB-4e8d9b9f.log
label-Ubuntu\x209.04\x20amd64
label-Ubuntu\x209.04\x20amd64-07b4ce69.log
label-Ubuntu\x209.10\x20amd64
label-Ubuntu\x209.10\x20amd64-2e94ae04.log
label-Untitled\x20Disc
label-Untitled\x20Disc-429061b3.log
network:
network:-91a97d8f.log
obex:host=%5B00%3A1F%3AE3%3AD1%3A97%3A8E%5D
obex:host=%5B00%3A1F%3AE3%3AD1%3A97%3A8E%5D-2093e7ce.log
root
root-bbc188a8.log
smb-network:
smb-network:-e919a182.log
trash:
trash:-45a1dc61.log
uuid-1A20-0206
uuid-1A20-0206-f36d4867.log
uuid-1E66-01BE
uuid-1E66-01BE-3d8cbe68.log
uuid-1F6208B9145576BB
uuid-1F6208B9145576BB-63b9b4b0.log
uuid-225ac7e1-bc95-4ff4-b8a8-372cb655e9e3
uuid-225ac7e1-bc95-4ff4-b8a8-372cb655e9e3-0516c43d.log
uuid-2ECAB82A4AF206BD
uuid-2ECAB82A4AF206BD-9bfaeeb8.log
uuid-31AD-0095
uuid-31AD-0095-896f6f71.log
uuid-3B4A-56E6
uuid-3B4A-56E6-d08d311d.log
uuid-4889-F96F
uuid-4889-F96F-b0a3ed1c.log
uuid-4C3D-BF0C
uuid-4C3D-BF0C-45e0c942.log
uuid-51dd19f5-97c4-4ef5-a3a6-6ea7d3d73818
uuid-51dd19f5-97c4-4ef5-a3a6-6ea7d3d73818-73b58c7d.log
uuid-7e361299-8389-45a9-a0b7-fc553d6382ee
uuid-7e361299-8389-45a9-a0b7-fc553d6382ee-7fb0bdae.log
uuid-9694318A94316DBD
uuid-9694318A94316DBD-4981b923.log
uuid-9694318A94316DBD-ff2347b8.log
uuid-B654DAA254DA6521
uuid-B654DAA254DA6521-4b460d3f.log
uuid-d17086c1-6898-42a4-8947-5096fbe40ee9
uuid-d17086c1-6898-42a4-8947-5096fbe40ee9-706469ef.log
uuid-D8DC168ADC166354
uuid-D8DC168ADC166354-cd3c3bbb.log
uuid-e06b3173-6da4-4a50-a696-cbf1d7e8c0db
uuid-e06b3173-6da4-4a50-a696-cbf1d7e8c0db-3341c87b.log
uuid-FE35-3F4F
uuid-FE35-3F4F-bba32e87.log
uuid-ff7b0d81-6859-4f97-8cfb-539c5d04c20e
uuid-ff7b0d81-6859-4f97-8cfb-539c5d04c20e-2215fce5.log
tom@karmic-laptop:~$ 

```

As far as I could tell, theyre all just logs for different devices? Im not exactly certain, but thats what it seems like from all of the file names. 

Does this bring up any ideas? Ill look into k3lt01's post here in a minute or two.


I already have my /home folder backed up in a .tgz file on an external thumb drive- I made sure the other day before I started poking around that I did that. haha. Thanks for the heads up though!

---

### Post by warfacegod on 2010-01-28
I thought I'd mention that file because I ran into something vaguely similar to your issue and it turned out that their metadata file was corrupted. They replaced it with a fresh one from a new user account and all was well afterwards.

---

### Post by tom.swartz07 on 2010-01-28
> **warfacegod said:**
> I thought I'd mention that file because I ran into something vaguely similar to your issue and it turned out that their metadata file was corrupted. They replaced it with a fresh one from a new user account and all was well afterwards.

Im beginning to think that its a similar case too. So would you suggest that I just wipe those files and see if it restores them?

---

### Post by warfacegod on 2010-01-28
> **tom.swartz07 said:**
> Im beginning to think that its a similar case too. So would you suggest that I just wipe those files and see if it restores them?

May be to get a fresh one from a new user account instead of just making it blank.

---

### Post by tom.swartz07 on 2010-01-28
> **warfacegod said:**
> May be to get a fresh one from a new user account instead of just making it blank.

Nope didnt work. I think Im going to try a full purge/reinstall of ubuntu desktop this weekend. Im going back up to my University so Ill have a really fast connection to download the package files from.


If you could think of anything in the meantime, I would really appreciate it! :D

---

### Post by warfacegod on 2010-01-28
> **tom.swartz07 said:**
> Nope didnt work. I think Im going to try a full purge/reinstall of ubuntu desktop this weekend. Im going back up to my University so Ill have a really fast connection to download the package files from.


If you could think of anything in the meantime, I would really appreciate it! :D

You purge Nautilus yet?

---

### Post by tom.swartz07 on 2010-01-28
> **warfacegod said:**
> You purge Nautilus yet?

No- I was going to, but it was late I saw that it would break up a few other packages; dropbox, picasa, and a few others. I didnt feel like tracking them down at that point.

I might do that now.

---

### Post by nerdy_kid on 2010-01-28
have you been running gui apps with sudo?  cause this could be a permissions issue....root took ownership blah blah.

---

### Post by tom.swartz07 on 2010-01-28
> **nerdy_kid said:**
> have you been running gui apps with sudo?  cause this could be a permissions issue....root took ownership blah blah.

Not that I know of- last time i ran gksudo with nautilus was to install x64 version of flash. That was months ago....

As far as I could tell, It just wont SAVE the bookmarked places- I could add them and do whatever to them, but after I log out, they disappear

---

### Post by tom.swartz07 on 2010-01-28
Just purged and reinstalled nautilus. no dice.

The only thing that happened is that I had to reinstall the Dropbox daemon.

Ubuntu desktop it is next!

I might do that now- I have to go take care of some laundry and stuff. Ill just set it up and let it rip while im gone. :lolflag:

---

### Post by warfacegod on 2010-01-28
> **tom.swartz07 said:**
> Not that I know of- last time i ran gksudo with nautilus was to install x64 version of flash. That was months ago....

As far as I could tell, It just wont SAVE the bookmarked places- I could add them and do whatever to them, but after I log out, they disappear

An easy way to check is the Properties> Permissions tab of your /home.

That's assuming, of course, that you can *find* it!:rolleyes:

---

### Post by J V on 2010-01-28
Still not fixed?

open gconf editor and go to: /apps/nautilus/desktop-metadata

Are there any folders under there? (Probably a couple hundred from your previous atttempts to make them...)

---

### Post by tom.swartz07 on 2010-01-28
> **warfacegod said:**
> An easy way to check is the Properties> Permissions tab of your /home.

That's assuming, of course, that you can *find* it!:rolleyes:

Just checked the /home folder itself is owned by root, but the /home/tom folder (mine) is owned by me.

> **J V said:**
> Still not fixed?

open gconf editor and go to: /apps/nautilus/desktop-metadata

Are there any folders under there? (Probably a couple hundred from your previous atttempts to make them...)
Just looked and it seems that it doesnt have my previous 'Original' folders there, just a few other ones..

4@46@0@32@GB@32@Filesystem@46@volume
cdrom0@46@volume
Data@46@volume
directory
FreeAgent@32@Drive@46@volume
iPod@46@volume
TOSHIBA@46@volume


What does this mean? They all seem to be removable drives that I had plugged in at one time or another, but nothings in now.

Each of the folders display the options 
icon-scale (value=1)
nautilus-icon-position (value=64,some number)
nautilus-icon-position-timestamp (value=some number)

---

### Post by tom.swartz07 on 2010-01-28
Also, Ive tried copying the files from a new user over, as per the other thread posted here. still no dice.


What if I were to create a new 'tom' user, and just copy my home files there?

I have about 3 gigs of data to copy, thats the only thing stopping me from doing so if its not going to work.

---

### Post by warfacegod on 2010-01-28
4@46@0@32@GB@32@Filesystem@46@volume
cdrom0@46@volume
Data@46@volume
directory
FreeAgent@32@Drive@46@volume
iPod@46@volume
TOSHIBA@46@volume


What does this mean? They all seem to be removable drives that I had plugged in at one time or another, but nothings in now.

Each of the folders display the options
icon-scale (value=1)
nautilus-icon-position (value=64,some number)
nautilus-icon-position-timestamp (value=some number)

That is just information dictating how big and where to put icons on your desktop for those devices. It's nothing important.

---

### Post by k3lt01 on 2010-01-28
Ok try this.

1. Go to your /home folder and click the up arrow, then go into you new test user accounts /home folder. 
2. Now go to View > Show Hidden Files and make sure it is ticked.
3. Look for a file called .gtk-bookmarks, copy it.
4. Navigate back to your own /home folder and paste the copied .gtk-bookmarks to it.
5. Reboot and see if things are in the correct place when you restart.

---

### Post by tom.swartz07 on 2010-01-28
> **k3lt01 said:**
> Ok try this.

1. Go to your /home folder and click the up arrow, then go into you new test user accounts /home folder. 
2. Now go to View > Show Hidden Files and make sure it is ticked.
3. Look for a file called .gtk-bookmarks, copy it.
4. Navigate back to your own /home folder and paste the copied .gtk-bookmarks to it.
5. Reboot and see if things are in the correct place when you restart.

Strange. I dont have one in my home folder, but the guest account has one.

When I try to copy, I get
```
tom@karmic-laptop:~$ sudo cp /home/guest/.gtk-bookmarks /home/tom/
[sudo] password for tom: 
cp: cannot stat `/home/tom/.gtk-bookmarks': Input/output error
```

Let me see if I could get it on there somehow.

---

### Post by k3lt01 on 2010-01-28
Try this

```
sudo cp /home/guest/.gtk-bookmarks /home/tom/.gtk-bookmarks
```

If that doesn't work you may have to copy the contents and create a new file in your /home and paste the contents in it.

---

### Post by warfacegod on 2010-01-28
I hope that works. However, I hate to be the one to point this out but it would only be a fix. It wouldn't explain how this happened in the first place.

---

### Post by k3lt01 on 2010-01-28
> **warfacegod said:**
> I hope that works. However, I hate to be the one to point this out but it would only be a fix. It wouldn't explain how this happened in the first place.Like I said in my initial post, my gut feeling is the PC is/was going to crash. These things don't just disappear without a trigger of some sort, either man made (which I don't think it is) or PC corruption (which I think it is as I have had it happen to me).

---

### Post by tom.swartz07 on 2010-01-28
> **k3lt01 said:**
> Try this

```
sudo cp /home/guest/.gtk-bookmarks /home/tom/.gtk-bookmarks
```

If that doesn't work you may have to copy the contents and create a new file in your /home and paste the contents in it.

Neither one works. I could write whatever I want to the folder, but it WILL NOT let me name a file .gtk-bookmarks.

Im going to reboot and run fsck on the partition to see if I could sort it out. I have a feeling there might be a bad block right where that file is sitting.

---

### Post by k3lt01 on 2010-01-28
> **tom.swartz07 said:**
> Neither one works. I could write whatever I want to the folder, but it WILL NOT let me name a file .gtk-bookmarks There is something very wrong going on with your PC.

Have you tried
```
gksudo gedit /home/tom/.gtk-bookmarks
``` or

```
gksudo gedit ~/.gtk-bookmarks
```

both should do the same thing cause the "~" just means your personal /home folder. If you can open it that way then you should be able to paste/type in the correct entries and save it.

---

### Post by tom.swartz07 on 2010-01-28
Okay- the original file is still there, its just corrupt; I ran ls -lia to see all of the files and their inode numbers.


How do I remove the file using the inode number? 

```
tom@karmic-laptop:~$ ls -lia
ls: cannot access .gtk-bookmarks: Input/output error
total 18112
  8355 drwxr-xr-x  3 tom  tom      4096 2010-01-28 02:01 ~
  8177 drwxr-xr-x 86 tom  tom      4096 2010-01-28 18:31 .
     2 drwxr-xr-x  5 root root     4096 2010-01-27 23:39 ..
.......LOTS OF FILES.............
  2674 -?????????  ? ?    ?           ?                ? .gtk-bookmarks

```

How would I remove the file using the inode number?
Once its deleted, then I could create a new version of the file.

---

### Post by warfacegod on 2010-01-28
> **tom.swartz07 said:**
> Okay- the original file is still there, its just corrupt; I ran ls -lia to see all of the files and their inode numbers.


How do I remove the file using the inode number? 

```
tom@karmic-laptop:~$ ls -lia
ls: cannot access .gtk-bookmarks: Input/output error
total 18112
  8355 drwxr-xr-x  3 tom  tom      4096 2010-01-28 02:01 ~
  8177 drwxr-xr-x 86 tom  tom      4096 2010-01-28 18:31 .
     2 drwxr-xr-x  5 root root     4096 2010-01-27 23:39 ..
.......LOTS OF FILES.............
  2674 -?????????  ? ?    ?           ?                ? .gtk-bookmarks

```

How would I remove the file using the inode number?
Once its deleted, then I could create a new version of the file.

Don't remember the exact code, so I recommend browsing as root and deleting it that way. Don't forget to "show hidden files".

---

### Post by tom.swartz07 on 2010-01-28
> **warfacegod said:**
> Don't remember the exact code, so I recommend browsing as root and deleting it that way. Don't forget to "show hidden files".

Wont show up when I browse as root.
gksu nautilus doesnt have the file, but its obviously there, listed in the terminal?

---

### Post by k3lt01 on 2010-01-28
> **warfacegod said:**
> Don't remember the exact code, so I recommend browsing as root and deleting it that way. Don't forget to "show hidden files".Wouldn't it be something like

```
 rm ~/.gtk-bookmarks
```

or something like that?

---

### Post by tom.swartz07 on 2010-01-28
```
tom@karmic-laptop:~$ find . -inum 2674 -exec rm -i {} \;
find: `./.gtk-bookmarks': Input/output error
```


Thats the method I dug up for deleting using inode number...

What has me puzzled about the situation is that the file is there, but it has no owner, no permissions, nothing!

---

### Post by warfacegod on 2010-01-28
> **k3lt01 said:**
> Wouldn't it be something like

```
 rm ~/.gtk-bookmarks
```

or something like that?

That's what I thought but I didn't want to have him delete the wrong thing. Although I was thinking.

```
sudo -rm .gtk blah, a blah
```

---

### Post by tom.swartz07 on 2010-01-28
> **warfacegod said:**
> That's what I thought but I didn't want to have him delete the wrong thing. Although I was thinking.

```
sudo -rm .gtk blah, a blah
```

Nope, no conventional method will remove the file- Ive even tried with the inode number (mentioned in my last post) 

Anyone have an idea to remove this darn file? haha

---

### Post by mechro on 2010-01-28
**Photorec**? Don't know whether it would work. Worth a try? Maybe?

---

### Post by mechro on 2010-01-28
Create a directory... put the file in there... delete the directory??

---

### Post by tom.swartz07 on 2010-01-28
> **mechro said:**
> **Photorec**? Don't know whether it would work. Worth a try? Maybe?

Nope, wont work- I tried it with testdisk. Photorec is for images anyway. Good thought though!

> **mechro said:**
> Create a directory... put the file in there... delete the directory??
Cant even move the file. I originally tried moving it someplace else, then I tried deleting it, then I tried using inode delete, now Im at a loss..

This freaking file is the reason that I cannot get my bookmarks back. I dont know why it is corrupt, or how it happened, but now it will not go away! :'(

---

### Post by k3lt01 on 2010-01-28
I'm sorry I can't think of anything else that will help atm. I'm starting to think you have 3 options left. 1. ignore the problem, 2. use another profile, make sure you give it admin rights and maybe try to get rid of it from the other profile, 3. Do a clean and total reinstall.

---

### Post by mechro on 2010-01-28
Could you delete it from a LiveCD or perhaps Puppy Linux which I find useful for doing all sorts of weird and wonderful stuff?

---

### Post by tom.swartz07 on 2010-01-28
WAHOO!!

It turns out, when I restarted, the system went to do a fsck of the /home partition and it threw an error- (just like you said it would k3lt01)
I ran fsck on the home partition myself and wouldnt you know it- the darn file for .gtk-bookmarks was corrupt (I KNEW IT!! haha) the fsck ran through and fixed it. 

My guess is, it was corrupted when it was being written on the drive. 


Anyway- now its all sorted out! Thanks for all of the help now guys!

[/solved]

---

### Post by k3lt01 on 2010-01-28
> **tom.swartz07 said:**
> WAHOO!!

It turns out, when I restarted, the system went to do a fsck of the /home partition and it threw an error- (just like you said it would k3lt01)
I ran fsck on the home partition myself and wouldnt you know it- the darn file for .gtk-bookmarks was corrupt (I KNEW IT!! haha) the fsck ran through and fixed it. 

My guess is, it was corrupted when it was being written on the drive. 


Anyway- now its all sorted out! Thanks for all of the help now guys!

[/solved]Well done, I hope that going through that process you were able to avoid a system crash.

---

### Post by tom.swartz07 on 2010-01-28
> **k3lt01 said:**
> Well done, I hope that going through that process you were able to avoid a system crash.

Me too buddy, me too.

Thanks again for all of the help!

---

### Post by warfacegod on 2010-01-29
Glad to hear it. And look on the bright side. You probably know more than you did when you went into this.

---

### Post by tom.swartz07 on 2010-01-29
> **warfacegod said:**
> Glad to hear it. And look on the bright side. You probably know more than you did when you went into this.

Heck yeah! Now I know how to delete using inode numbers. haha

---

