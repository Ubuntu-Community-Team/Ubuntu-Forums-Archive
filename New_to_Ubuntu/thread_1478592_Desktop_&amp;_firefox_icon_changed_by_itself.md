---
title: "Desktop &amp; firefox icon changed by itself??"
date: 2010-05-09
forum: New to Ubuntu
---

### Post by duftwone on 2010-05-09
I was using a photograph as my desktop background, and it seems to have changed by itself to a plain gray background. Also, the Firefox desktop shortcut/icon changed from the Firefox logo to a plain rectangle. 
When I tried to use a different Firefox icon to access the internet, it says I'm in offline mode, so I went to File > Offline mode  and unchecked the box (I'm pretty sure I never put a check in the box myself), but that didn't help. Can anyone suggest what the problem might be? Thank you very much.

---

### Post by wojox on 2010-05-09
Did you move the photograph there by changing it's path?

Try launching Firefox from the terminal and see what it says.

---

### Post by ddecator on 2010-05-10
You can also try running Firefox with a new profile to see if your current one has been corrupted for some reason. Just run 'firefox -P' and create a new profile, then select it and launch. If that works, either your profile is corrupt, you need to change the settings, or there are extensions causing issues on your default profile.

Still post the terminal output here, but if you cannot get Firefox to work then you might want to file a bug using 'ubuntu-bug firefox' and I can take a look at the report.

---

