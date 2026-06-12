---
title: "Font install trouble"
date: 2010-03-22
forum: New to Ubuntu
---

### Post by geekosupremo on 2010-03-22
Hey all,

So here's what my issue/problem is. A friend of mine made a font of her handwriting using one of the online services. Which did a very descent job of it. But like most machine created fonts, there are some kerning issues. I thought it would be a fun design challenge to myself to try to "fix" her font.

So I install FontForge, which can open the font just fine. But I wanted to also install the font in the system so I could check out how many of it's kerning pairs look in say OpenOffice before sitting down for any serious editing. And this is where I am a little stuck.

I did some searching on the forum, and didn't seem to find any good solutions to my particular issue. Then I tried the wiki and found this page: [https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts) - which was more informative but sadly did not fix my issue. I also tried just clicking the "install font" button on the font viewer. All of these seemed ineffective. Yeah even the sudo terminal stuff didn't seem to work.

In conclusion, if I have missed something in the documentation please let me know. If there is extra info I can supply to help,please let me know. My goal is understanding as well as a solution.

---

### Post by undecim on 2010-03-22
If you want to add a font, just stick in in the .fonts directory in your home directory (if you don't see the directory, press Ctrl+H to view hidden directories)

You can also put it in /usr/share/fonts/, if you need other users on the system to be able to use it as well.

After doing this, you will need to restart any applications you want to use the font in. If you change the font while an application is running it does no good until you restart that application, because that applications already has the old font loaded.

---

### Post by geekosupremo on 2010-03-22
Thanks for replying.

I checked that folder, and the file was there ... but when I re-opened OpenOffice Wordprocessing, the font did not appear in the font menu. 

I feel like I'm missing something.

---

### Post by Enigmapond on 2010-03-22
You need to update the font cache...

```
sudo fc-cache -f -v
```This will update both of the folders mentioned above and then the application should see it. Whenever you add a new font, do this and this should eliminate that problem.

---

### Post by geekosupremo on 2010-03-24
Enigmapond - 

Okay, I tried that command ... and the font that I installed is still not showing up. could it be that the file type is mal-formed or something?

---

### Post by Enigmapond on 2010-03-25
Could be...it needs to be a true .TTF. I have downloaded 1000's of fonts and just thrown them all into .fonts in my home folder and have never had a problem...maybe something in the way it was made.

---

