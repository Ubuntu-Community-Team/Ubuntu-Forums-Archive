---
title: "Opera Browser wil not show Video"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by Don1500 on 2009-01-23
I switched to Opera a week ago and so far I like it.......But.

When I try to look at video (I'll use Youtube as an example) all I get is a white screen. In fact not even a screen just a blank where the original screen was.
I am using Opera 9.63 with Ubuntu 8.04.
I have Flash 10.0.15.3-1hardy2 installed and it works in Firefox.

Any clue to what I'm doing wrong?

---

### Post by RyanVanDiemen on 2009-01-23
> **Don1500 said:**
> I switched to Opera a week ago and so far I like it.......But.

When I try to look at video (I'll use Youtube as an example) all I get is a white screen. In fact not even a screen just a blank where the original screen was.
I am using Opera 9.63 with Ubuntu 8.04.
I have Flash 10.0.15.3-1hardy2 installed and it works in Firefox.

Any clue to what I'm doing wrong?

I had similar problem in Hardy, didn`t try to solve it because I wasn`t using it as my primary system. So whenever I needed a streming video, I used Firefox.

In ibex everything seems to work just fine after installing ubuntu-restricted-extras package.

---

### Post by cwsnyder on 2009-01-23
Do you have Java installed in Opera and JavaRuntimeEnvironment (JRE) installed on your system?  Youtube also requires Java to run the controls on the video player.

---

### Post by superprash2003 on 2009-01-23
try reinstalling it , opera doesnt seem to recognize it!

---

### Post by sisco311 on 2009-01-23
Check if the plug-in is recognized: [opera:plugins]("opera:plugins")

You may also need to add /usr/lib/mozilla/plugins/ to the plug-in folders.
Tools -> Preferences -> Content -> Plug-in Options -> Change Path -> Add...

---

### Post by Don1500 on 2009-01-23
Don't know what I did, but it's working now. Thanks for the help anyway.

---

