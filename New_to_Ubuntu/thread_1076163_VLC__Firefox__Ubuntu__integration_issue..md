---
title: "VLC / Firefox / Ubuntu  integration issue."
date: 2009-02-21
forum: New to Ubuntu
---

### Post by linux4fun on 2009-02-21
Hi I have Vlc media player correctly installed on Hardy and the player works well and does what I want if accessing local files.

My issue concerns clicking on links via remote sources using Firefox

eg If I want to listen to a mp3 stream a dialogue box appears that lists "movie player as the default option  obviously this is not what I want
sadly neither VLC or any of the other installed apps are offered as an alternative.

There is an option to browse for the application but what am I looking for!
on Windows it would be an exe file for Vlc.

It seems strange that installed applications are not integrated into the dialogue box thus allowing the user to choose how they want a weblink handled  ... I'm not looking for the stream to be in an embedded player  just for VLC to be fired up when the link is accessed  a la as is on Windows or Mac .....

This for me is a serious issue  I'm just a newbie who wants to enjoy my Linux experience but a daft lack of simple features such as this is frustrating ...how do we get the coders to make all installed ups show up as options in dialogue boxes ...  It cannot be that difficult  can it ?

If anyone has a solution I would be very grateful.

PS playing around with Firefox config makes no difference either...

---

### Post by Amarsingh0793 on 2009-02-21
If you create a launcher to VLC on your desktop, you can navigate to that link when the dialogue appears, and then "Open With" VLC.

---

### Post by linux4fun on 2009-02-21
> **Amarsingh0793 said:**
> If you create a launcher to VLC on your desktop, you can navigate to that link when the dialogue appears, and then "Open With" VLC.

Hi Amarsingh

Hmmmm how do I say this politely !!!  I tried that at an early stage ...
my methodology for trying to solve the issue has been logical.

The desktop shortcut for VLC does not facilitate the opening of a WEBSTREAM from within the VLC application when the shortcut address is browsed for and entered into the Dialogue box.

now if there was a way to enter a command into the Dialogue box we might have a solution  but guess what  we don't appear to have that option.

It's missing or is not obvious .... and that is the crux of the problem.

I don't want streaming media from remote sites /locations opened locally by the default player  I want my own choice ....  this is logical and would be on a any reasonable system/OS 

Ok lets have some more input ... while we are at it how do we lose the USA english spell check on the forums ... I am in UK and am fed up of red lines under my spelling of Dialogue .. It's correct   just about sums it up eh !!!!

---

### Post by linux4fun on 2009-02-21
Please Board Moderators

Could you possibly ask an advanced member of the Ubuntu community to have a look at my thread in order that we could solve this really simple issue ...  If Ubuntu is so good it must have a solution !!!

Otherwise anybody like me who wants to Listen/View streaming media online is obviously not going to migrate to this PLATFORM.

---

### Post by benerivo on 2009-02-21
> **linux4fun said:**
> ...I want to listen to a mp3 stream a dialogue box appears that lists "movie player as the default option  obviously this is not what I want
sadly neither VLC or any of the other installed apps are offered as an alternative.

There is an option to browse for the application but what am I looking for!...

vlc should be installed in /usr/bin/vlc so you shoukd be able to pick it from that firefox 'browse for app' dialogue.

---

### Post by linux4fun on 2009-02-21
> **benerivo said:**
> vlc should be installed in /usr/bin/vlc so you shoukd be able to pick it from that firefox 'browse for app' dialogue.

This is very true Firefox is indeed installed at the location above
but the dialogue box will not accept a FOLDER it seems to want a particular file ...

There are a number of Firefox files at this location and at other
addresses in the file system.

Perhaps we could ask  which file do we have to double click on in system files  excluding shortcuts in order to fire up the application ... where is the excutable ? I have looked everywhere and cannot see one .. including hidden and root files ...

This is just plain stupid and whoever released this distro needs a kick up the A@@@ 

Expecting newbies to be able to wade throuch crucial parts of a system in order to change a default media player is crazy !!!!

OK  do we have any more budding Einstein's out there  A nobel prize is on offer to whoever can make VLC the default media player of choice on my version of Ubuntu ...

Lets recap  This is what I want it to do ....

Surf Web using Firefox  Click on .Pls/.wmv/etc etc link on page ... 
VLC then opens ..plays the stream  (Standalone player)
this process is simplicity itself on Windows and Mac ...

If this cannot be done Ubuntu is no good for Streaming Media !!!!

---

### Post by ag65151 on 2009-02-21
Have you tried going to 

System->Preferences->Preferred Applications

And set your multimedia player there?

---

### Post by KhaaL on 2009-02-21
linux4fun, have you tried this:

sudo apt-get install mozilla-plugin-vlc


and in that case, what happened?

---

### Post by linux4fun on 2009-02-21
> **ag65151 said:**
> Have you tried going to 

System->Preferences->Preferred Applications

And set your multimedia player there?

Yes !   been there done that .... Only changes the way local files on the system are handled ..anything accessed via the web browser still brings up movie player and the dialogue box ..

---

### Post by benerivo on 2009-02-21
> **linux4fun said:**
> ...anything accessed via the web browser still brings up movie player and the dialogue box ..
Going back to that dialog box, i assume it asks you for a program file to launch when you click on a media link (eg. mp3 stream). The /usr/bin/vlc link i mentioned, is a file, and it should be a suitable choice from this firefox dialog box.

See the last post in [this thread]("http://ubuntuforums.org/archive/index.php/t-931964.html").

---

### Post by linux4fun on 2009-02-21
Just another thought ..

Rhythm Box and Banshee have also both been imstalled on this Hardy distro .. How come neither show up in the other applications option
when trying to access the remote stream .

VLC and at least one of the others installed can handle a web .pls link ...

Perhaps Ubuntu is more like use Movie Player (TOTEM) or get stuffed
If the rest of the world was just Ogg or Theora based then fine.

but I need VLC and it's advanced features ...

---

### Post by linux4fun on 2009-02-21
> **KhaaL said:**
> linux4fun, have you tried this:

sudo apt-get install mozilla-plugin-vlc


and in that case, what happened?


Here is what happened a few minutes ago


root@ubuntu-laptop:~# apt-get install mozilla-plugin-vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mozilla-plugin-vlc is already the newest version.
The following packages were automatically installed and are no longer required:
  libboost-thread1.34.1 libboost-date-time1.34.1 gnash-common
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 298 not upgraded.
root@ubuntu-laptop:~# 
 ?
As you can see the plugin is already installed ....


Any more ideas anyone

---

### Post by linux4fun on 2009-02-21
Ok I have solved the issue .. 

There is an executable in the file system that can be linked to which performs the function that was desired ..

Many thanks to those that sent ideas ...

However I still think that Dialogue Boxes that refer to choosing helper applications would be best served by having a choice of installed apps rather than asking Newbies to dive into system folders ...

I had to create a root account in order to access the necessary VLC file.
this is just plain stupid.

---

