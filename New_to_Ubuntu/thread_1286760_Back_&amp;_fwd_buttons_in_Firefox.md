---
title: "Back &amp; fwd buttons in Firefox"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by denizente on 2009-10-09
Hi, am complete newbie, no PC knowledge to speak of just hate Windows.
Installed Ubuntu 9.04 alongside Windows. Firefox back button disabled so I went to address bar & did the following:

about:config. Click the "I'll be careful" button. Then type in "backspace" in the filter. Doubleclick on browser.backspace_action and set it to zero.

Great, that worked. Now I've rebooted after doing some stuff in Windows & both fwd & back have disappeared in Firefox.  I desperately want to get on with Ubuntu without devoting months of my life making it work for me. Any ideas welcome. Many Thanks

---

### Post by XCan on 2009-10-09
That's weird, I have that option as well and my back button still exists. Perhaps you could try and kill your config files? Open Home in Places, and press ctrl+H to show hidden files. Then navigate to /home/username/.mozilla/firefox and rename the dir you see there. This will force FF to start off with a fresh config.

If the above solves your problem, I think it will still be worthwhile to think why it happened in the first place.

---

### Post by fooman on 2009-10-09
maybe a dumb question, but...have you looked in view >  toolbars > customize

look and see if the fwd & back buttons are there.  if they are...just drag & drop them back into the toolbar.

sorry if you've already been there.

---

### Post by lovinglinux on 2009-10-09
See **Solution** [*[COLOR="Red"]**FOT003**[/COLOR]*] from the Troubleshooting section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567&highlight=FOT003).

---

