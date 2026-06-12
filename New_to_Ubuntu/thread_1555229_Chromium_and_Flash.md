---
title: "Chromium and Flash"
date: 2010-08-17
forum: New to Ubuntu
---

### Post by h8uthemost on 2010-08-17
Hey guys,

I'm using Chromium version 5.0.375.99 (51029), and I'm having trouble getting flash to work. Some images and graphics on sites won't show up. And in the images place there's text that says Missing Plugin.

Well, I read somewhere that flash is supposed to be installed with Chromium and all you have to do is enable the plugin. But when I go to the Plugins page of Chromium(which I get there by going into Options>Under The Hood>Content Settings>Plugins>Disable Individual Plugins) there are no plugins listed.

And...when I go to install Adobe Flash, the Adobe page says that flash is already installed for this browser.

I'm not finding much help on what to do so hopefully someone here has came across this and knows how to fix it.

Thank you for any help.

---

### Post by Ozymandias_117 on 2010-08-17
> **h8uthemost said:**
> Hey guys,

I'm using Chromium version 5.0.375.99 (51029), and I'm having trouble getting flash to work. Some images and graphics on sites won't show up. And in the images place there's text that says Missing Plugin.

Well, I read somewhere that flash is supposed to be installed with Chromium and all you have to do is enable the plugin. But when I go to the Plugins page of Chromium(which I get there by going into Options>Under The Hood>Content Settings>Plugins>Disable Individual Plugins) there are no plugins listed.

And...when I go to install Adobe Flash, the Adobe page says that flash is already installed for this browser.

I'm not finding much help on what to do so hopefully someone here has came across this and knows how to fix it.

Thank you for any help.

I've never had it installed automagically, so here is how to do it :P

```
sudo aptitude install flashplugin-nonfree
``` << Just type that in a terminal.

---

### Post by h8uthemost on 2010-08-17
That indeed did do it. I know I read that Chromium came with flash installed. Guess I was wrong.

Well, thank you for your help Ozymandias_117. :)

---

### Post by Ozymandias_117 on 2010-08-17
> **h8uthemost said:**
> That indeed did do it. I know I read that Chromium came with flash installed. Guess I was wrong.

Well, thank you for your help Ozymandias_117. :)

Perhaps it's Google Chrome that has Flash pre-installed. Or it could be that it's only pre-installed for Windows due to FOSS issues.

---

### Post by ECET on 2010-08-17
If you are using 64bit version of ubuntu, that is why your flash isnt working. There's a member on here who has a wonderful "fix" for this....but alas I can't remember where to find it. But it just fools flash into thinking you are running a 32bit system.....hope this helps a little....

---

### Post by Ozymandias_117 on 2010-08-18
> **ECET said:**
> If you are using 64bit version of ubuntu, that is why your flash isnt working. There's a member on here who has a wonderful "fix" for this....but alas I can't remember where to find it. But it just fools flash into thinking you are running a 32bit system.....hope this helps a little....

flashplugin-nonfree does exactly that. :P It puts 32-bit Flash into a wrapper so it can be used by 64-bit. Adobe had a 64-bit version for a while, but they decided to stop supporting 64-bit. (Like that makes any sense >.>)

---

