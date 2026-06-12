---
title: "can't play audio on VLC or anywhere else...."
date: 2010-03-12
forum: New to Ubuntu
---

### Post by bradmayne04 on 2010-03-12
rI now get an error saying the file is to large. (never heard that one before)  i tried a bunch of different songs.  anyone have an idea????  i put in a screenshot too.

---

### Post by orky7 on 2010-03-12
what is the error from VLC player ??

---

### Post by bradmayne04 on 2010-03-12
failed to connect: stream to large.  click on the screen shot to see it for yourself.  let me know what ya think thanks !

---

### Post by bradmayne04 on 2010-03-12
p.s. rythmm box is working fine!!!

---

### Post by dmillard10 on 2010-03-12
How big IS the file you're trying to play?

Does the file play in something else, say Rhythmbox?

---

### Post by Paddy Landau on 2010-03-12
Looking at your screenshot, it doesn't look like VLC.

VLC has a sort of cone as an icon at the top left corner of the window, and the icon also shows in your panel at the bottom right of your screen.

Try again, ensuring that you really have chosen VLC.

---

### Post by samh785 on 2010-03-12
> **Paddy Landau said:**
> Looking at your screenshot, it doesn't look like VLC.

VLC has a sort of cone as an icon at the top left corner of the window, and the icon also shows in your panel at the bottom right of your screen.

Try again, ensuring that you really have chosen VLC.
Yeah, he's using totem. (Default video player of Ubuntu)

If you want VLC, go into a terminal and type ```
sudo apt-get install vlc

```it will prompt you to enter you password, do so. It should then ask you if you're sure you want to install, type "y" to confirm. After it installs you can open it in Applications --> Sound & Video --> VLC media player.

[s]Have you installed the restricted extras package to allow the playback of non-free media files?[/s]

Edit:
> **bradmayne04 said:**
> p.s. rythmm box is working fine!!!
Ok, so obviously you have installed the restricted extras package :P.

---

### Post by bradmayne04 on 2010-03-13
i do have VLC but the gui is really messed up!  that may have been totem but now i tried vlc and the gui is screwed up.  now that i mention it i'm having a problem w/ the media player in frostwire too and frostwire will not shutdown it just hangs.  could it be a java problem?

---

### Post by Paddy Landau on 2010-03-13
> **bradmayne04 said:**
> i do have VLC but the gui is really messed up!
Please be specific. What does "the gui is really messed up" mean? When you start VLC, what happens? Does your entire screen go funny, or just the VLC window, or what?

A screen shot will help -- but also explain exactly how you got there, for example did you open VLC from the menu, or by opening a music file from Nautilus, or what?

---

### Post by bradmayne04 on 2010-03-14
yeah VLC is all funked up!! I can't take a screen shot at this point because VLC starts off at full screen and the GUI is messed up.  Then i went to "minimal screen" and all i got was a full screen showing a cone.  Though if I try and play video it works fine!! When I try and open it to play music the GUI is  messed up when I go from applications>> sound and video >> VLC.  Does anyone have any idea's???  Thanx in advance!!

---

### Post by Paddy Landau on 2010-03-14
> **bradmayne04 said:**
>  Does anyone have any idea's?
Sorry, I don't know the answer to your problem. I can only tell you what I would try.
I would completely uninstall VLC...

[LIST]
[*]System > Administration > Synaptic Package Manger
[*]Scroll down to VLC > Mark for Complete Removal
[*]Apply
[/LIST]
Then, still in Synaptic Package Manager, reload and reinstall...

[LIST]
[*]Press Reload
[*]Mark All Upgrades
[*]Apply if it's not greyed out
[*]Scroll down to VLC > Mark for Installation
[*]Apply
[/LIST]
I hope that helps.

---

