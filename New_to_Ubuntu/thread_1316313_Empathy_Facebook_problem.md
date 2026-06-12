---
title: "Empathy Facebook problem"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by Dapilot1 on 2009-11-05
Empathy stopped connecting to Facebook, it says network error. It just all of a sudden stopped, my login info is correct. Any clues on how to get it to connect again?

---

### Post by stoogiebuncho on 2009-11-06
Yeah, facebook changed something and you need to update your pidgin-facebookchat plugin to get it to work again.

You can download the .deb file here: [http://code.google.com/p/pidgin-facebookchat/]("http://code.google.com/p/pidgin-facebookchat/")

You could also wait for the update to come through the pipes, but I'm guessing it will be some time before that happens.

---

### Post by Dapilot1 on 2009-11-06
Works beautifully now, thanks

---

### Post by AndThenWhat on 2009-11-24
Thank you I spent like 30 minutes looking for this.

---

### Post by zeroseven0183 on 2009-11-25
Thank you! Never knew there's a Facebook plugin (although I don't do chats in Facebook).

I can't seem to make it work with Empathy?

---

### Post by lessmemorelove on 2009-11-25
@zero
1) install the deb
2) run following command in terminal: sudo rm /usr/share/telepathy/managers/haze.manager
3) reboot

you should have it then

---

### Post by zeroseven0183 on 2009-11-26
> **lessmemorelove said:**
> @zero
1) install the deb
2) run following command in terminal: sudo rm /usr/share/telepathy/managers/haze.manager
3) reboot

you should have it then

Yes, that did it. Thanks!

---

