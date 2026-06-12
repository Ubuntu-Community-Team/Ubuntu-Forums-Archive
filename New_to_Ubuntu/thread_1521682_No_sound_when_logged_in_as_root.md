---
title: "No sound when logged in as root"
date: 2010-07-01
forum: New to Ubuntu
---

### Post by baguahsing on 2010-07-01
When logged in as root, my sound is muted and can not open software to adjust it.  No problem when I'm logged in as myself.  How do I fix this?

---

### Post by chamber on 2010-07-01
Open a terminal and type alsamixer

Are you able to adjust what is muted now?

---

### Post by ajgreeny on 2010-07-01
But why are you logged in as root?

By default the root user is totally disabled in Ubuntu including the Netbook Remix, and in 5 years of Ubuntu use, I have not needed a root login ever, except for recovery mode, to do anything.

---

### Post by Yanno on 2010-07-01
How did U log in as root graphically???

---

### Post by Don1500 on 2010-07-01
The mods will be here in 5... 4... 3... 2...

1. Do not log in as ROOT.
2. Logging in as anyone but yourself means you will have to set up the sound, flash, and almost anything else you set up before as that other user.
(I'm guessing here but either you are using 9.10 or earlier OR you set up a user called ROOT.)

---

### Post by mikewhatever on 2010-07-01
The fix is simple. Disable root login.

---

### Post by eriktheblu on 2010-07-01
I'm thinking from a user account```
sudo cp -R ~/.* /home/root
```

But yeah, don't see the need for a root account.

---

### Post by KdotJ on 2010-07-01
I agree with the other posters. Why the need for root login? However you managed to do it...

---

### Post by lkjoel on 2010-07-01
First, How did you log in as root?
Second, click on Fix my sound! in my sig.
That will switch from ALSA to OSS.
Also, Check if OSS supports your soundcard.

---

### Post by baguahsing on 2010-07-05
Quite simply I went to administration / users and added a root account. At first, it said that I didn't have the privelages to do this, but when I rebooted, it was there and I can log in as root. I am a newbie, and I was not sure if it was a good idea to give my personal account admin powers so I created the root account. This stems from my ignorance of the structure and security of linux and differences between sudo, root, and administrator. From the tone of the responses I guess that I made a boo boo with creating a root account. Question is should I delete the account? While I'm at it, can anyone tell if there a "safe mode" when you do someting and it screws up your system, like the time I activated the video driver and got a blank grey screen and I ended up reinstalling Ubuntu?  FYI - I'm usnig 10.04 notebook remix on a Toshiba satellite pro 6100.

---

### Post by chillyperson23 on 2010-08-03
sudo passwd root


 hat lets you have access to the root account in ubuntu 10.04 To use it, you have to click other and login as root. 


I got sound working by doing

pulseaudio -D 

And then i had to unmute the sound in alsamixer.  Try adding the command to startup?

---

