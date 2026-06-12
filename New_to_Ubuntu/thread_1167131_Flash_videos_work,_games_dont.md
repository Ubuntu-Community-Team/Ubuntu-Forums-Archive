---
title: "Flash videos work, games dont"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by PuddingKnife on 2009-05-22
I work for a company that teaches people with disabilities workskills and the like, and Ive recently put Ubuntu Jaunty on our community computer.

Ive installed restricted drivers and Youtube videos work just fine, but a lot of our clients play online games such as the ones found at:

[http://www.nabiscoworld.com/games/default.aspx](http://www.nabiscoworld.com/games/default.aspx)

I cant get any of the games there to work on this computer now, and they all worked fine when WinXP was installed.

Can anyone help me figure this out?

---

### Post by XCan on 2009-05-22
It doesn't appear to be working for me either, and I'm using Adobe's Flash 10 64bit. Are they really using the standard flash? In Windows, do you ever get prompted to install some piece of software?

---

### Post by PuddingKnife on 2009-05-22
> **XCan said:**
> It doesn't appear to be working for me either, and I'm using Adobe's Flash 10 64bit. Are they really using the standard flash? In Windows, do you ever get prompted to install some piece of software?

No, we've got 3 computers in our Day Room and Ive only installed Ubuntu on one of them, as a test. Of the 2 XP computers, none of them prompts me to install any software (though I cant say that it hasn't prompted someone before, Im not the IT guy here)

I cant even tell if its a flash or java problem ..

---

### Post by qamelian on 2009-05-22
The site is looking for the Macromedia Shockwave Player 10.1 plugin, rather than the Flashplayer plugin. Since that specific plugin doesn't exist for Linux (to the best of m knowledge), you may be out of luck. There may be a solution, but I don't think Shockwave-specific content has ever been usable on Linux.

**Update:** The only solution I have been able to find involves using wine to install the Windows version of Firefox and the Windows version of the Shockwave player.

---

### Post by Bölvaður on 2009-05-22
These games do not seem to be using flash at all.

They do not show up for me, and firefox is asking me to download plugins.
It requires shockwave 10.1

Not sure if it will work under wine or not.


*added*
man Im slow... I get too easily distracted :(

---

### Post by qamelian on 2009-05-22
> **Bölvaður said:**
> These games do not seem to be using flash at all.

They do not show up for me, and firefox is asking me to download plugins.
It requires shockwave 10.1

Not sure if it will work under wine or not.


*added*
man Im slow... I get too easily distracted :(
It does work under wine, but apparently it doesn't work well in every case. It's fine for some people but glitchy for others. This is also obviously not the ideal solution but at least it is a possible workaround.

---

