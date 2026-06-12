---
title: "Problem wit 8.04 movie player"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by Total AI on 2010-09-08
[SIZE=4]I have run into a problem with Ubuntu 8.04,I down loaded and set the system up for a person,so far everything works but the movie player,when I downloaded a you tube video,to get the codecs, it says "internal error",I do Ubuntu for folks who want out of M.S[/SIZE], her machine in a Dell dimension 2400,1 gig memory 2.66 mghz processor,it plays a cd video and has all the flash players installed,thanks,AI

---

### Post by Perfect Storm on 2010-09-08
Are you using the default player that comes with Ubuntu? If so, did you install ubuntu-restricted package?

---

### Post by Total AI on 2010-09-08
No,I didn't,where would I find this?Please.and thank you.I didn't think of that thanks,I'll do that. AI

---

### Post by Perfect Storm on 2010-09-08
You can find it in Ubuntu Software Center (using its search function), or by synaptic package manager.

or via the terminal;
```
sudo apt-get install ubuntu-restricted-extras
```

This package will install codecs, flash etc.
Note; it will also install Open Java plugin (icedtea6-plugin), but their might be some stuff it wont work with, so you should grab sun java from Canoncal Partner repositories.


You do it like this.
1. Open Synaptic Package Manager (System --> Administration)
2. In Synaptic Package Manager click the Settings tab ---> Repositories
3. Now go to "Other Software" tab and enable Partner sources.
4. Close Software Sources and click "reload" button.
5. Install sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin

---

### Post by Total AI on 2010-09-09
Ok,I had to take a neighbor to the doc yesterday and I will try this thanks loads AI

---

### Post by Total AI on 2010-09-09
Ok,I went into the terminal,put the command lines in,it downloaded and set everything up,still,I get this when I try to play the movie player,"internal data stream error,boy,this 8.04 is about to eat my lunch

---

### Post by jtarin on 2010-09-09
Is your primary concern just to get Movie Player working or be able to watch YouTube? You could either try to update the player or install something like VLC. YouTube has a tendency to change thigs every once in awhile and its a catch-up game reminiscent of Yahoo messneger and MSN.

---

### Post by Total AI on 2010-09-09
She said she needed the movie player to download school videos for future study,as far as I'm concerned,the player is small stuff,but she is my client and I have to do what she wants,at least try,I run 9.10 on my tower and 10.04 on my laptop,but her antiquated machine won't run the later versions

---

### Post by Total AI on 2010-09-09
Ok,I give up on the player thing,The little girl will just have to take her notes and study from that,maybe,the school will have a different video system than you tube,I was just using that to get the right codecs.I want to thank you very much for your help and hanging in there with me.Have a nice day/evening,AI

---

### Post by jtarin on 2010-09-09
You never did say what version of Movie player you had? Maybe an upgrade would help, but then ther is the chance that it would drag otherupgrades in with it. How is she downloading YouTube videos or is the concern with the browser plugin? If downloaded YouTube then they are .flv which VLC will play and also Xine player.

---

### Post by Jazzy_Jeff on 2010-09-09
Just install VLC media player. I have not found anything it cannot play.

---

