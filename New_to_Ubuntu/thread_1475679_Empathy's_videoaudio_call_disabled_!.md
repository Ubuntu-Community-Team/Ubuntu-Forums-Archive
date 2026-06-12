---
title: "Empathy's video/audio call disabled !"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by Speed Of Light on 2010-05-07
[SIZE="4"]Hi everyone
please a direct answer for this very simple questions:
- Why on earth the menu items of "video call" & "audio call" are always disabled ?!
- Does Empathy really support video/audio calls !
- How can I solve this ?
(I'm using MSN account)
[/SIZE]

---

### Post by Speed Of Light on 2010-05-07
okay I got it:
> MSN support is currently broken due to change Microsoft has done to their server, see [this blog post]("http://kakaroto.homelinux.net/2010/03/amsn-0-98-2-to-be-released-without-audiovideo-support/") for more detail
[source]("http://live.gnome.org/Empathy/FAQ#For_which_protocols_does_Empathy_support_audio_and_video_chat.3F")

so the answers are:
_**- Why on earth the menu items of "video call" & "audio call" are always disabled ?!**_
because it's broken for now.
_**- Does Empathy really support video/audio calls !**_
yes, but not right now.
**_- How can I solve this ?_**
you'll have to wait!

---

### Post by Grakul on 2010-06-13
Any idea when this will become available again (if ever)?

---

### Post by Kimm on 2010-06-13
It will probably take a while, since the protocol needs to be upgraded from what I understand, and MSN support is generally not a priority. You can try to use Emesene, it claims to do video (though not audio I believe), not sure if its affected by this.

---

### Post by YannBuntu on 2010-07-02
As Microsoft changed their MSN protocol in March, it is now impossible to do voice/video calls with this protocol on Linux.

To do voice/video calls with Windows interlocutors, I recommend :
- Ekiga (which exists also on Windows)
- Empathy (with Telepathy PPA , and ubuntu-restricted-extras package, and of course a Jabber account e.g. gmail adress), that can do voice/video calls with Windows Gtak interlocutors
- Skype (which exists also on Windows), but this one is not open-source

---

