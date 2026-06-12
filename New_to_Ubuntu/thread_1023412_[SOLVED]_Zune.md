---
title: "[SOLVED] Zune"
date: 2008-12-27
forum: New to Ubuntu
---

### Post by augie2051 on 2008-12-27
Ok before i became a ubuntu fan i was into microsoft and purchased a zune.  Is there a way to make my zune player work with ubuntu?  I like using my zune and have a lot of music that i paid for that i want to continue to use and update.  thanks in advance for any help given.

---

### Post by venator260 on 2008-12-28
I've done some searching on this forum, and the consensus is that, short of having either Windows XP or Vista in a Virtual environment, a Zune will not work with Linux. The closest thing I have seen to native support is that in a thread somewhere a person mentioned that Amarok could connect and delete files, but nothing else.

---

### Post by icyest on 2008-12-28
Sell your zune and buy an ipod from Microsoft's enemy; Apple. It's not right that they do this to you.

I sold my zune on ebay and just started using limewire again to save money. It's just not worth supporting the corporate system if they force you to have Windows ($99) just so you can listen to your music that you already bought.

---

### Post by augie2051 on 2008-12-28
Can you help me creating a virtual box or direct me to a link that will show me?

---

### Post by venator260 on 2008-12-29
Here's the Howto from the Ubuntu Community Documentation. I've never personally used Virtualbox, however. 

[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

---

### Post by riteandritual on 2009-01-01
Well, I have to say I just bought a Zune from ebay... It was cheaper than the Ipods, good quality (so say reviews) and it has radio (a must-have for me - need my npr) ... As we speak I'm setting up windows xp in virtualbox because I gave up windows for good just a couple of months ago, and no way am I going back. 

As long as I can copy over mp3 files, pictures, and make playlists I'll be happy, and I'm sure the linux community will prevail and get some work-around to work. I previously had a Sony NW-HD5 with its SonicStage HELL, so maybe this affects my outlook as well.

The whole point with 30gb-80gb is that you can fill it up once-in-a-while, not every other day. VirtualBox should be sufficient for that. And no way am I buying songs from iTunes, Zune or anyone else... They don't even carry most of the music I like.

---

### Post by pyrofyr on 2009-01-01
Don't bother with an iPod either, your best bet is to go with a third party. If you like large space (30GB+) go with Archos. IF you prefer smaller go with a Cowon.

---

### Post by riteandritual on 2009-01-03
OK, I got Zune and SonicStage perfectly working in Linux! Huzzaaa!  
The actual Zune player I bought from ebay still hasn't arrived yet, but the software works, and I have successfully used SonicStage to manage the music on my NW-HD5 (that is now on ebay, if you're interested ;D ). 

What I did was this: 
- In Synaptic, uninstall VirtualOSE. Go to [Virtualbox website]("http://www.virtualbox.org/wiki/Linux_Downloads") and download the commercial (free for personal use) version and install it. 
- Install XP (last time I hope to use THAT disk!)
- Got the USB working in VirtualBox through help from the Ubuntu forums.
- Made my music folder "shared" in VirtualBox, with read-only capability. 
- Booted up the VirtualBox xp and through the "my computer" I "added new network drive". 

For SonicStage this setup is even better than Windows, because SonicStage likes to track and "authorize" every single mp3 it touches and it can mess up things in the long run when you change computers, share the files etc. With read-only access, I don't have to worry about that. 

I will have to report on how Zune works with this setup when I get the player. If nothing else, Samba is so easy to setup that I can use my wife's Vista to put my music on the Zune player.

On a side note - both the Archos and Cowon look really good, in fact I wanted them, but they're too expensive for me at the moment. My only options were Zune and Creative, because I want FM capability that iPod doesn't have.

EDIT:

It was [this page]("http://ubuntuforums.org/showthread.php?t=492816&page=3") on the forums that helped me get the usb working.

---

### Post by snipatomic on 2009-01-04
I dual boot Vista/Ubuntu and am a fan of Wine. :D
I recently got a 120GB Zune and after a bit of research I found a simple registry hack to use it as an external hard drive (enabling drag-and-drop of files, music, etc without the Zune software in the way...it simply shows up as another drive). 
As I am dual booting there is little practicality in using a virtual machine but I would appreciate a way to access my Zune through Ubuntu. Perhaps something could be applied here much like the Vista/XP registry hack.
Any ideas?

---

### Post by riteandritual on 2009-01-05
CONFIRMED!

I just got my Zune today. Plugged it in. Enabled the USB for it in VirtualBox, Booted XP in the VirtualBox and started up the Zune software...

Synched and even upgraded firmware perfectly... 

Now I can use EasyTag to tag my music, Amarok to get album images for them, and Zune to put them on my mp3 player.

XP in VirtualBox is really fast and works so well I really feel good without dualbooting now lol. And for the record - I like my Zune too (despite it being M$) - I can play Sudoku! :D

---

### Post by superzorro on 2009-01-07
That's great.

I'm having a little trouble though, I'm able to sync but only if I copy the files to the Virtualbox disk.

When I map the Music folder inside ubuntu as a network drive in XP, the music shows up in the Zune software, I can listen to it, edit files, but when it doesn't sync, it states that there is a problem and it can't access the file.

Any advice would be helpful

---

### Post by Frak on 2009-01-07
Zune uses a secret handshake only known by Microsoft. It does not need a driver, as it is an MPD device, but the Zune software and Zune hardware use a secret talk-back as a way to make sure nobody spoofs anything such as the timer (for Zune Pass) or internal workings.

Amarok has support for removing music, but not adding to. This is the farthest they've come.

Kudos with the VirtualBox success.

---

### Post by augie2051 on 2009-01-07
I'm running vista will your idea still work

---

### Post by riteandritual on 2009-01-23
Have you got a shared folder set up on your virtualBox? In virtualbox settings I made my music folder a shared folder with read-only permission (just cause I'm paranoid after bad experiences with Sony). Then in the XP running on my virtualBox, I went to "add new network drive" or something and added the music folder - thus, I have all my music accessible on my virtual XP. 

I will say that I've discovered a caveat: in order to update my music collection (when I redo the tags, for instance, or get new music) I need to "unsynch" my music folder in the Zune software (remove it as a music source), and close and restart the Zune software. Its a pain in the ***, but with 30 gigs, I don't update my music on the player all that often anyway.

Augie - you mean you have vista on virtualbox? I should imagine the process would be the same, although adding a network drive/folder I suppose would be slightly different.

---

### Post by SunnyRabbiera on 2009-01-23
How to get a zune to work for linux:
1: Get your Zune
2: take it outside
3: get a sledgehammer
4: smash repeatedly
5: get a sansa :D

---

### Post by Frak on 2009-01-23
> **SunnyRabbiera said:**
> How to get a zune to work for linux:
1: Get your Zune
2: take it outside
3: get a sledgehammer
4: smash repeatedly
5: get a sansa :D
I like my Zune > my Sansa

---

### Post by riteandritual on 2009-01-23
yeah. although I've heard the sansa have fantastic sound quality for the price... I do love my zune.

---

### Post by SunnyRabbiera on 2009-01-25
> **Frak said:**
> I like my Zune > my Sansa

Yeh but at least the sansa will work on linux without MS being needed and thats where it counts...
No special software, no BS thats why I like sansa

---

### Post by bj0 on 2009-01-27
> **SunnyRabbiera said:**
> Yeh but at least the sansa will work on linux without MS being needed and thats where it counts...
No special software, no BS thats why I like sansa

plus the sansa fuze supports flac, ogg, and has an sd card slot!

---

### Post by riteandritual on 2009-05-10
but it doesn't have a radio!

---

### Post by Arndtwe on 2009-05-10
My Sansa Fuze has a radio... FM only though.

---

