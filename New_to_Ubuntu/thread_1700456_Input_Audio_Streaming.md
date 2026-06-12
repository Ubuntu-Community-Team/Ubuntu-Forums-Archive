---
title: "Input Audio Streaming"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by AnimaMetallicus on 2011-03-05
Alright,so here it is.
I'm currently trying to use Ardour 2 to record my guitar.
But the matter here is i have just moved to Ubuntu.
On Windows i used to enable "Line In" in the playback control,and everything i play in my guitar comes out to the speaker.
But on Ubuntu,and Linux generally i cannot figure out how.
I tried googling but it seems fate doesn't like me.
Please help this n00b.

---

### Post by maqtanim on 2011-03-05
Click the volume indicator on the right side of the top panel, click the **Sound Preference**. Go to the **Input** tab and select your input device.

---

### Post by AnimaMetallicus on 2011-03-05
maybe you don't understand what i meant.
What i am trying to say here,is not about "let the programs to record the sound" but "stream the input directly to the output in real time"
kinda like the amplifier.

---

### Post by AnimaMetallicus on 2011-03-05
Bump for the love of god...
I need this,people.And i really hope someone can share me some experience about this problem.
I have to say this is the only reason for me to leave Linux.

---

### Post by David.Mac on 2011-04-13
I've got the same problem in Ubuntu 10.10. Can't get any sound from line-in over the speakers. Rythmbox and Exaile work fine. I've de-selected mute in all the controls I can find - nothing

Edit:  Now works. After I searched the rest of the Forum I came across "Gnome Alsamixer. Installed it, and sure enough, the Line-in was muted by default (but not in the other Mixers). De-selected Mute, and all systems on Go. Thanks for a great Forum.
David

---

### Post by spillin_dylan on 2011-04-13
Are you using JACK?  If so, it should be a matter of opening the 'Connect' window in JACK and connecting the system line in to the system audio out.

If you're not using JACK, I can't really help you, but I suggest you give JACK a try.  It kind of adds another layer of complexity, but was designed to work with audio in exactly this way.  It also works very well with Ardour and most other Pro-Audio programs in Linux.

---

