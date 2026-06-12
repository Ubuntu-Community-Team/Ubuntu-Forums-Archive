---
title: "What Size to Make Icons for Kubuntu?"
date: 2011-05-16
forum: New to Ubuntu
---

### Post by dniMretsaM on 2011-05-16
What size should I make an icon for the KDE 4 panel? I have a image I want to use as an icon but it won't work so I'm guessing it's too large (it's a .png, so file type is not the issue).

---

### Post by dniMretsaM on 2011-05-16
I got it to work. And it actually had nothing to do with size. Apparently, when selecting a custom icon, if you select a different icon with the same name as an old icon used for the same application, it doesn't change it. So the icon I had been using was icon.jpg. I had a new icon that I wanted to use also called icon.jpg. The old icon had been deleted and this took it's place in the same directory, but when I tried to apply the new icon, it reverted to the old one automatically. And a previous icon (named icon.xpm) which I had used before icon.jpg appeared when I tried to put the new one in with the same name. This is a really weird issue that a may do a bug report for, but it was easily solved by changing the name to Icon.png.

---

