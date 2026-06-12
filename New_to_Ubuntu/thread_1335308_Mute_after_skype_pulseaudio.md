---
title: "Mute after skype pulseaudio"
date: 2009-11-23
forum: New to Ubuntu
---

### Post by solomon88 on 2009-11-23
Hi Everyone, I hope this is the right place to post. Its my first one so here goes. 
I updated to Koala a few weeks back and have encountered a few problems, well one really big one to be exact. 
Skype will only let me use pulseaudio in its sound options which is fine until I end a conversation. A few minutes after I finish a conversation on skype any video (youtube, bbciplayer etc) I am running in firefox becomes muted, requiring a restart. Does anyone have any clue as to why this is or how to fix it? this didnt happen when I was running Jaunty. I have become tempted (mostly out of frustration) to remove pulseadio altogether but as a newbie to Ubuntu (been using it a few months)I am cautious. If I remove pulseaudio will other options appear in the 'Sound Options' in Skype after restart.
As an aside, when I turn on the computer, about half the time it is muted in start up. I hope this isnt too much of a problem.
Suggestions, recommendations, questions?
Cheers

---

### Post by Sam on 2009-11-23
If the sound disappear in the middle of the session, this might help```
pulseaudio --kill
pulseaudio --start
```

---

### Post by solomon88 on 2009-11-23
Sound never disappears while in the middle of a skype conversation. However, if I am watching something on firefox, then have a conversation on skype and then return to firefox, the media played will be muted within minutes.Is the code recommended a way to remedy this problem?

---

### Post by Sam on 2009-11-23
By session I meant the time you're using your computer, not the skype conversation. However the code will restart pulseaudio. This may work or not, but you have to try.

---

