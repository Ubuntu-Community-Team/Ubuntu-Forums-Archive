---
title: "Remote Desktop"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by liferocket on 2009-02-10
for give me for sounding like a total Noob, but when it comes to Linux I basically am.  I just installed Ubuntu 8.10 on my Jukebox system (it's in the other room, hooked up to my stereo).  I want to be able to Remote Desktop into it from a WinXP system in the office, so I can control the music.  I tells me what Command to use to do it, but I don't know where to put that command in. please help!

---

### Post by yeats on 2009-02-10
What's the command?  Just curious.

There are a couple of possibilities.  The easiest way is to download and install tightvnc ([http://www.tightvnc.com/)]("http://www.tightvnc.com/") on your Windows machine, set it up with a password, then in Ubuntu, hit Alt-F2 and type 

```
vinagre
```

Then click the connect button and enter the LAN IP for your Windows machine.  If it doesn't connect, make sure your firewall will allow those connections through.

---

### Post by MrWES on 2009-02-10
> **liferocket said:**
> for give me for sounding like a total Noob, but when it comes to Linux I basically am.  I just installed Ubuntu 8.10 on my Jukebox system (it's in the other room, hooked up to my stereo).  I want to be able to Remote Desktop into it from a WinXP system in the office, so I can control the music.  I tells me what Command to use to do it, but I don't know where to put that command in. please help!

This is what I did; I installed mt-daap, now called Firefly:

[https://wiki.ubuntu.com/UbuntuHomeMediaServer]("https://wiki.ubuntu.com/UbuntuHomeMediaServer")

On my linux 8.04 desktop, I can share the music via my network and use iTunes to see the shared music. Or if you don't want to use iTunes, I believe Songbird is cross platform and is daap capable. Works very well

Bill

Update: I attached a screen shot of Rhythmbox; look at the lower left hand corner, you can see 'MyJukeBox on bill-desktop' under 'shared'

---

### Post by liferocket on 2009-02-10
thx guys. i'll try it tomorrow!

---

### Post by SteveHillier on 2009-02-10
I get the feeling from the originator that you want to go from Win XP into Ubuntu.  Chrissharp123 goes the other way round ie from Ubuntu into Win XP.
Something is nagging the back of my brain about this.  When I first was messing around with this.  I think that Win XP home does not accept incoming Remote Desktop commands although I think it can attach to other machines as Remote Desktop Client.
XP Pro can receive incoming Remote Desktop but the user you are trying to attach as must have a password and you have to allow incoming by going to Control Panel -> System -> Remote and make sure there is a check mark in the second tick box down.
It then won't matter if you use the MS or the Linux remote desktop client.
Connecting to a Linux host I don't know off hand but others will let you know what might work.

ps.  I forgot to add, I don't know how Win XP media edition would work here.

---

### Post by osx424242 on 2009-02-10
> **liferocket said:**
> for give me for sounding like a total Noob, but when it comes to Linux I basically am.  I just installed Ubuntu 8.10 on my Jukebox system (it's in the other room, hooked up to my stereo).  I want to be able to Remote Desktop into it from a WinXP system in the office, so I can control the music.  I tells me what Command to use to do it, but I don't know where to put that command in. please help!

I think what you really want is mpd, [http://mpd.wikia.com/wiki/Music_Player_Daemon_Wiki](http://mpd.wikia.com/wiki/Music_Player_Daemon_Wiki), not Remote Desktop!

Set up mpd on your Jukebox, then use a Windows client on your XP system to control it.

---

### Post by supersonicdarky on 2009-02-10
> **osx424242 said:**
> I think what you really want is mpd, [http://mpd.wikia.com/wiki/Music_Player_Daemon_Wiki](http://mpd.wikia.com/wiki/Music_Player_Daemon_Wiki), not Remote Desktop!

Set up mpd on your Jukebox, then use a Windows client on your XP system to control it.
Exactly what I was goin to suggest, except that it would probably be easier if you set up a web interface.

Unlike remote desktop, this will only take a fraction of the bandwidth.

---

### Post by yeats on 2009-02-10
> Chrissharp123 goes the other way round ie from Ubuntu into Win XP.

@Steve - you're right - my bad :-)

It should be a similar process though - VNC works both ways, though the config in Linux is more "under the hood."

---

### Post by achianese on 2009-02-10
If you would rather do a remote desktop, TightVNC will work as a client in Windows. Just download and install it, selecting only the client portion.

On your Ubuntu machine, go to System - Preferences - Remote Desktop. Under Sharing, check the boxes to allow users to view your desktop and control your desktop. Under Security, check the box requiring a password, and enter your password. 

To log in from Windows, open TightVNC and type the IP address of your Ubuntu box. It will ask for your password and you'll be in.

---

### Post by SteveHillier on 2009-02-11
This contribution from achianese.  Wonderful!  Works like a dream!
Within 5 minutes of reading this post I have a VNC connection to my Hardy host, which included downloading TightVNC, storing it on my server, installing it on Vista, changing my Hardy preferences, and one false start.
Just two comments.  When I typed in the host name in it would not go but worked OK using IP address.  I did have to get the remote host to accept the connection.  That is fine as both machines are side by side but if it was truly remote and without any one present - MMmmmmm.
But good solution anyway.
Many thanks.

Of course there is a setting in preferences - just uncheck the 'Ask you for confirmation' box.  Serves me right for whinging before I sorted it out.  'pologies.

---

### Post by liferocket on 2009-02-11
omg i got it working! i had to uncheck "only allow local connection" and open the port on the router, but now i can control the music from the other room! 

now, another related problem. on the Jukebox system, the one running Ubuntu that I am remoting into.. the Music on there is on another HDD, which is a WindowsXpHome system, using NTFS. I have enabled the related Partitions for network sharing, so Ubunto can open them.  however, after each boot when i go into Computer in Ubuntu and try to open those volumes, i think it says "cannot mount" or something the FIRST time i double click on it, but the second time i try it opens up just fine. does this individually for each partition on the drive.  i'm guessing i need a simple script to tell it to properly mount each Partition on boot... and I have no idea where to insert that script, remember i'm a linux Noob

---

### Post by SteveHillier on 2009-02-11
I did a similar thing the other day.  See this thread.

[http://ubuntuforums.org/showthread.php?t=1064993](http://ubuntuforums.org/showthread.php?t=1064993)

I got some help from other forum members.  If you search the forum for fstab I am sure you will find some better threads.

ps  This method means that the remote locations are mounted on startup and you can access them by moving to the location on /mnt/sharename

---

### Post by liferocket on 2009-02-12
i looked in /ect/mtab, but i did not see anything in there about drives or partitions.

in /etc/fstab, it has things about /dev/sdb1 and sbd2, but nothing about sda which is the physical drive with the music on it. and yes, Windows is on the other drive, but installed on different partitions

---

### Post by argie on 2009-02-12
Do you still have the hostname problem? Try installing nmbd. I'm sorry, but I don't recall which package contains it.

---

### Post by liferocket on 2009-02-12
my only problem is that i put something in the Mount instructions for the partitions that was incorrect. so, i cannot mount them in the GUI, so i cannot change those parameters the way i did the first time.  also, i need them to auto-mount on boot.

---

