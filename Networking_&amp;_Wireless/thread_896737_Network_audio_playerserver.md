---
title: "Network audio player/server"
date: 2008-08-21
forum: Networking &amp; Wireless
---

### Post by Clochard on 2008-08-21
I'm hoping this is the right place to ask.  I'm looking for some application that I can use in the following scenario:

I have a server with all my media files (MP3s, Ogg, etc).  I have 3 computers on a wired network (100/1000) spread throughout my house.  Those workstations all have sound cards and speakers attached.  I'd like to be able to have a single "thing" play my audio files from the server, and have all my workstations play the audio in a synchronous manner.  I could control this "thing" from any of the workstations, letting me change songs, view currently playing, etc.

I think there are several apps that will let me control the audio on the server, but I can't seem to figure out if there are things that will sync the audio stream across several workstations.  Worst case scenario here is that I have the audio playing on the workstations but not sync'd at all, or lagging slightly.

Anyone know of software designed for this kind of use of a network?

Maybe [PulseAudio ]("http://en.wikipedia.org/wiki/PulseAudio")can do this?

---

### Post by prshah on 2008-08-21
> **Clochard said:**
> 
I have a server with all my media files (MP3s, Ogg, etc).  I have 3 computers on a wired network (100/1000) spread throughout my house.  Those workstations all have sound cards and speakers attached.  I'd like to be able to have a single "thing" play my audio files from the server, and have all my workstations play the audio in a synchronous manner.  I could control this "thing" from any of the workstations, letting me change songs, view currently playing, etc.

You can do this easily from RhytymBox, with the help of the DAAP plugin. On the "server": start RythymBox, click Edit-Plugins-DAAP music sharing-Configure-Share My Music and select your music folder.

On your clients: Start RythymBox, click Music-Connect to DAAP share and select your server.

Note that when I say "server" I just assume you have ubuntu-desktop running, and you are using server in the logical sense, being that where all your MP3, OGGs etc are stored.

There is also an additional plugin in Rhythymbox to enable "remote" (ie, client) control; it's called the "DLNA/UPnP sharing and control support" plugin.

Even VLC can help with streaming video and audio (?).

---

### Post by Clochard on 2008-08-21
So I can launch RB on a workstation, and use it to control the server's RB, which actually plays the audio file on the server.  How does this audio also play on all the workstations then?

I want to have a single audio file played on all 4 workstations simultaneously via the network.  I'm not concerned about sharing libraries, which is what I thought DAAP was all about?

---

### Post by prshah on 2008-08-21
> **Clochard said:**
> So I can launch RB on a workstation, and use it to control the server's RB, which actually plays the audio file on the server.  How does this audio also play on all the workstations then?


The song does not "play" on the server in the sense that you can hear it on the server's speakers; rather, it "plays" it by streaming it to the client that has requested the song.

---

### Post by Clochard on 2008-08-21
That's my understanding too.  But how do I get all 3 workstations to "play" it at exactly the same moment, so all my speakers throughout my house (connected to the workstations) are acting as though they were connected to a single receiver?

I don't want to run from workstation to workstation pushing play, trying to sync them all up .... My house is too big to make this feasible.  I could ask a friend to push play on the other workstations via walky-talky ...

Sorry, these are just silly ideas I had come up with in the first place before I decided to see if there was software that could sync it all up for me.

---

### Post by Clochard on 2008-08-23
Looks like PulseAudio is the trick - I'll see if I can get this working

[http://pulseaudio.org/wiki/FAQ#HowcanIusePulseAudiotostreammusicfrommymainPCtomyLANwithmultiplePCswithspeakers](http://pulseaudio.org/wiki/FAQ#HowcanIusePulseAudiotostreammusicfrommymainPCtomyLANwithmultiplePCswithspeakers)

---

### Post by TwoToneSpirit on 2010-05-26
Did you ever get it working?

---

