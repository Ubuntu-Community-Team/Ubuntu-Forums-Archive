---
title: "Amarok won't load my mp3 player??"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by VoXoM on 2009-04-08
I used to transfer my music from my comp to my Samsung YP-U3 using rythmbox but since I installed Ubuntu's newest version, I haven't been able to because an error occurs "Could not create a GStreamer sink element to write to..."

So, instead, I'm considering using Amarok. But Amarok doesn't seem to recognize my mp3 player. When I plug in my mp3 player and try to get it to connect with Amarok, the following error occurs "Malformed URL
(null)"

Can anyone help?
Thanks.

---

### Post by jpoRS on 2009-04-08
Are you following any how-tos or all that?  It is a pretty simple procedure, but there are a few steps you have to take before the first time you connect an MP3 player to Amarok.

jim

---

### Post by alphacrucis2 on 2009-04-08
> **VoXoM said:**
> I used to transfer my music from my comp to my Samsung YP-U3 using rythmbox but since I installed Ubuntu's newest version, I haven't been able to because an error occurs "Could not create a GStreamer sink element to write to..."

So, instead, I'm considering using Amarok. But Amarok doesn't seem to recognize my mp3 player. When I plug in my mp3 player and try to get it to connect with Amarok, the following error occurs "Malformed URL
(null)"

Can anyone help?
Thanks.


If by newest version, you mean 9.04 then that is still a development release, so your gstreamer problem may well be a bug (possibly a known one) . If so, post your info in the Jaunty Testing and Discussion forum under the developement and programming section.

---

### Post by ddrichardson on 2009-04-08
I've had problems with my Samsung since Jaunty - hal seems happy to try and mount it and Rythymbox tries to grab it as an MTP device. Depending on which one gets there first it either works or it doesn't.

I think this might be a fuse issue but make sure you have all the mtp packages installed in Synaptic.

Is it appearing as a mounted device on the desktop?

---

### Post by VoXoM on 2009-04-08
> **jpoRS said:**
> Are you following any how-tos or all that?  It is a pretty simple procedure, but there are a few steps you have to take before the first time you connect an MP3 player to Amarok.

jim
No I haven't. You'd be really nice to point me to a how-to :)

> **alphacrucis2 said:**
> If by newest version, you mean 9.04 then that is still a development release, so your gstreamer problem may well be a bug (possibly a known one) . If so, post your info in the Jaunty Testing and Discussion forum under the developement and programming section.
No, I meant 8.10.

> **ddrichardson said:**
> I've had problems with my Samsung since Jaunty - hal seems happy to try and mount it and Rythymbox tries to grab it as an MTP device. Depending on which one gets there first it either works or it doesn't.

I think this might be a fuse issue but make sure you have all the mtp packages installed in Synaptic.

Is it appearing as a mounted device on the desktop?
Hmm no I don't think. Nothing new on the desktop when I plug it in or out. Also, before 8.10, rhythmbox would automatically start when I'd plug it in. Now I have to open it manually but it doesnt matter anyways cause it won't work using rhythbox anymore anyways.

I also followed a [PulseAudio guide](http://ubuntuforums.org/showthread.php?t=789578) thinking it would maybe fix my gstreamer problem with rhythmbox but it didn't do anything

---

### Post by jpoRS on 2009-04-09
Hmm, they aren't as easy to find as when I needed one.

Here is what I can remember that I had to do.  No guarantees about accuracy, but here goes:

In Amarok, Settings>Configure Amarok>Media Devices.  Add device, select device type (I think that player is MTP, right?) and name it.  You shouldn't have to list a mount point, I didn't anyway.  Click Ok, Apply, and you have finised the "one time only" portion of this (lousy) how-to.

Now you should be able to go down to the "Devices" tab, select "MTP Media Device" (or whatever you selected) and then, with the player plugged in, click the little connect button (lightning bolt with a plug) and after a few seconds you should be ready to roll!

I hope this helps, sorry if I misunderstood your porblem, but that is how you have to set up Amarok to recognize players.

Good luck!
jim

---

### Post by VoXoM on 2009-04-09
> **jpoRS said:**
> Hmm, they aren't as easy to find as when I needed one.

Here is what I can remember that I had to do.  No guarantees about accuracy, but here goes:

In Amarok, Settings>Configure Amarok>Media Devices.  Add device, select device type (I think that player is MTP, right?) and name it.  You shouldn't have to list a mount point, I didn't anyway.  Click Ok, Apply, and you have finised the "one time only" portion of this (lousy) how-to.

Now you should be able to go down to the "Devices" tab, select "MTP Media Device" (or whatever you selected) and then, with the player plugged in, click the little connect button (lightning bolt with a plug) and after a few seconds you should be ready to roll!

I hope this helps, sorry if I misunderstood your porblem, but that is how you have to set up Amarok to recognize players.

Good luck!
jim

I did what you said but when I click on connect it brings up the "Configure Media Device" window. I click on okay and nothing happens. The command is "mount %d" in the pre-connect command.

Also, the problem might be caused by the fact that my comp doesn't seem to recognize my mp3 player as an MTP device. It doesn't show in the "Computer" folder. Though I can see all the songs on it through rhythmbox, the only thing is I can't transfer any songs with rhythmbox because of the gstreamer sink element problem, like mentioned above.

So, is there anything I can do to make my computer realize that it's an MTP device and make it show in the "Computer" folder when I plug it in?

---

### Post by ddrichardson on 2009-04-09
> **VoXoM said:**
> I did what you said but when I click on connect it brings up the "Configure Media Device" window. I click on okay and nothing happens. The command is "mount %d" in the pre-connect command.

Also, the problem might be caused by the fact that my comp doesn't seem to recognize my mp3 player as an MTP device. It doesn't show in the "Computer" folder. Though I can see all the songs on it through rhythmbox, the only thing is I can't transfer any songs with rhythmbox because of the gstreamer sink element problem, like mentioned above.

So, is there anything I can do to make my computer realize that it's an MTP device and make it show in the "Computer" folder when I plug it in?
You can define a set of hal rules but I don't think we're there yet. Make sure mtpfs and mtp-tools packages are installed, plug in the device and from the terminal type:```
mtp-detect
```Then we know its detected OK. Also for it to show in Nautilus you need to have mtpfs installed.

---

### Post by VoXoM on 2009-04-09
> **ddrichardson said:**
> You can define a set of hal rules but I don't think we're there yet. Make sure mtpfs and mtp-tools packages are installed, plug in the device and from the terminal type:```
mtp-detect
```Then we know its detected OK. Also for it to show in Nautilus you need to have mtpfs installed.

mtpfs wasn't installed. So i installed it and now I can put songs on my mp3 through amarok.

I can't believe I wasted a couple hours trying to figure what the problem was... lol

Still tho, the mtp device wont show in nautilus.

---

### Post by ddrichardson on 2009-04-09
It might if you completely quit Amarok. It can't be mounted as a drive and an MTP device at the same time.

---

### Post by VoXoM on 2009-04-09
> **ddrichardson said:**
> It might if you completely quit Amarok. It can't be mounted as a drive and an MTP device at the same time.

Nope... even with amarok closed it doesnt shows anything.

---

### Post by Orographic on 2009-05-26
Thought I should add to this thread as my Samsung YP-U3 was having real problems being recognised in Jaunty after being recognised easily in Intrepid.

Here's what I did and it was very simple in the end but it took me two hours to work it out. 

* Open Rythm Box Music Player first before plugging in the YP-U3 and go to Edit>Plugins and make sure 'Portable Players MTP' is ticked. Then plug in your YP-U3 and it will be recognised as simple as that. When you shut down Rythm Box it seems to unmount the U3 although maybe it isn't mounting via this method anyway? Just make sure you always open Rythm Box first before plugging in this player because if you just insert the player first, it does get recognised but can't be read properly etc.

Note: I spent a lot of time backing up via CloneZilla then installing the programs from Synaptic that were mentioned here in this thread then also Amarok and I could get the player to work but it seemed clunky that way. The method marked above with the asterix seemed to work fine though.

---

### Post by ddrichardson on 2009-05-26
I'd forgotten this thread. I had to upgrade libmtp manually to get Banshee and Rhythmbox to recognise my Samsung and even then hal isn't handling it correctly. I could work around this with a hal entry but I'm kind of busy this week.

---

