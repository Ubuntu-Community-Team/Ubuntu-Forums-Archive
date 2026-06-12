---
title: "Noob Display Question"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by geoffray7 on 2009-06-05
I recently was given some old dell computers the local school had planned on pitching. The one i'm working on now had XP pro but I was locked out by passwords and the guest login was blocked....so I figured I'd go with Ubuntu  seeing how I was going to just give the computers  away to people that didn't have computers and I didn't feel like spending $100 plus on xp/vista/etc.. I downloaded Ubuntu, burned it, and installed it fine. The next day I turned on the computer and the display was off a little so I went to system>preference>display and clicked on one of the different sizes. Next thing i know my mouse grew 5 times to big and so did the rest of the stuff. My screen litterally only has the mouse and the 2 control bars. I clicked on display again to change it but I can only see a fraction of what should be on the screen and it won't let me scroll down to change settings. I can't see anything so I can't change anything. However when I'm in guest mode everythings normal. Is there a way to change all the settings in administrator through guest? I can't download or alter things in guest so I'm stuck. I also put the cd in to try and reinstall but it didn't work. I tried doing a boot with the cd at the beggining again but nothing. Any help would be great. Thanks

---

### Post by Penguin Guy on 2009-06-05
Press [COLOR="Green"]Ctrl + Alt + F1[/COLOR].
Type [COLOR="Green"]xrandr -s 1280x1024[/COLOR] (or whatever screen size you have).
Then type [COLOR="Green"]exit[/COLOR] and press [COLOR="Green"]Ctrl + Alt + F7[/COLOR].

If there is an error, write it down and post it back here.

---

### Post by geoffray7 on 2009-06-05
i hit ctrl+alt+F1 and typed xrandr -s 1280x720 (our monitor size) and then hit ctrl+alt+F7 and nothing happened. The only thing I noticed was that after hitting ctrl,alt,F1 there was a message at the top saying IC resources could not be allocated. What should I do now? Is there a way to reboot the os because its not letting me do that either? I just need a free functional os. Thanks

---

### Post by AKK9 on 2009-06-05
After typing in [COLOR=Green]xrandr -s 1280x1024 [COLOR=Black]hit Enter.

Then type [/COLOR]exit [COLOR=Black]and hit Enter again.

Hope this helps.

Also, HI!! I'm new, just got Ubuntu. It's owns.
[/COLOR][/COLOR]

---

