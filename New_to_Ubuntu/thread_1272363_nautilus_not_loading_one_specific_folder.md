---
title: "nautilus not loading one specific folder"
date: 2009-09-22
forum: New to Ubuntu
---

### Post by Sonic Reducer on 2009-09-22
nautilus isn't loading my movies folder, even though ls from the command line shows they are there. i've been loading that folder in nautilus for several minutes and all that has loaded is "movies.txt" and "desktop.ini"

what would cause this problem?

.:EDIT:. i forgot to mention, when i open up VLC and open movies through their dialog (Ctrl + O) it sees the files and loads them just dandy

```
rowdyp@nts-desktop:/data/Movies$ pwd
/data/Movies
rowdyp@nts-desktop:/data/Movies$ ls
A Clockwork Orange.avi   Next Day Air.avi
Defiance.avi             Push.avi
Desktop.ini              Rock 'n' Rolla.avi
District 9.avi           Sphere.avi
Doom.mp4                 The Hurt Locker.avi
Event Horizon.avi        The International.avi
Jarhead.avi              The Last House On The Left.avi
Knowing.avi              The Ruins.avi
Leviathan.avi            The Warriors.avi
Miracle At St. Anna.avi  Watchmen.avi
Movies.txt
```

---

### Post by mcduck on 2009-09-22
Most likely one of the files is corrutped and causes Nautilus to crash when it tries to create a thumbnail for that file.

Testing the files with VLC doesn't really work because VLC is very good at handling corrupted and incomplete files, and also uses it's own codecs instead of Gstreamer.

Try to open the individual files with Totem, for example, to find out which one is causing the problems.

---

### Post by Paddy Landau on 2009-09-22
You can also turn off thumbnails in nautilus to see if that makes a difference.

Edit > Preferences > Preview > Show thumbnails > Never

If that helps, then mcduck could indeed be right.

---

### Post by seshomaru samma on 2009-09-22
do they load in thunar?

---

### Post by Sonic Reducer on 2009-09-22
> **Paddy Landau said:**
> You can also turn off thumbnails in nautilus to see if that makes a difference.

Edit > Preferences > Preview > Show thumbnails > Never

If that helps, then mcduck could indeed be right.

that did the trick. can i rebuild the thumbnail database somehow? i remember on windows i could erase thumbs.db in whatever folder and it'd refresh all the icons

---

### Post by Paddy Landau on 2009-09-23
> **Sonic Reducer said:**
> that did the trick. can i rebuild the thumbnail database somehow? i remember on windows i could erase thumbs.db in whatever folder and it'd refresh all the icons
Well, you do have a directory [FONT=Courier New]~/.thumbnails[/FONT] (note the leading point). However, I would suspect that mcduck is correct and that it won't solve the problem. Still, no harm in trying.

Have you tried mcduck's test in Totem yet? That would be a better start.

---

### Post by Sonic Reducer on 2009-09-24
> **Paddy Landau said:**
> Well, you do have a directory [FONT=Courier New]~/.thumbnails[/FONT] (note the leading point). However, I would suspect that mcduck is correct and that it won't solve the problem. Still, no harm in trying.

Have you tried mcduck's test in Totem yet? That would be a better start.

so... i fixed it?

i didn't do anything, except opening everything with totem (nothing failed to load) then i opened the folder to try moving the .Movies folder (it's my "special" movies folder lol) and voila! everything loaded.

i'm just so good i fix things without even realizing

---

### Post by Paddy Landau on 2009-09-25
> **Sonic Reducer said:**
> i'm just so good i fix things without even realizing
LOL

I'm glad it's all working now.

---

### Post by scorp123 on 2009-09-25
> **Sonic Reducer said:**
>  ```
rowdyp@nts-desktop:/data/Movies$ pwd
/data/Movies
rowdyp@nts-desktop:/data/Movies$ ls

...
... list of stuff you're not supposed to have ...
...
...


```

Up there you basically admit possessing files that you most likely are not supposed to possess .... OK, I'm not your Dad. But you wrote that your location is in California ... and last time I checked that happened to be in the USA? Where they fine people like 750'000$ per illegal copy and throw them into jail for like 10+ years?

Question: What if someone from MPAA, RIAA or FBI stumble over your posting and then take legal action against Canonical Inc. and force them to reveal your IP address to them .... ? They would then go to your ISP and soon find out who you are ...  You know that on the Internet you're never ever anonymous, right?

Again: I'm not your Dad. I have tons of those files too. But then again I am Swiss, I live in Switzerland, and here the law clearly says that it's perfectly legal to download whatever you wish. So unless you live here too I'd suggest you edit that posting above and avoid attracting unnecessary attention by openly posting a list of things that you're not supposed to have?

Just a suggestion.

---

### Post by Sonic Reducer on 2009-09-25
> **scorp123 said:**
> Up there you basically admit possessing files that you most likely are not supposed to possess .... OK, I'm not your Dad. But you wrote that your location is in California ... and last time I checked that happened to be in the USA? Where they fine people like 750'000$ per illegal copy and throw them into jail for like 10+ years?

Question: What if someone from MPAA, RIAA or FBI stumble over your posting and then take legal action against Canonical Inc. and force them to reveal your IP address to them .... ? They would then go to your ISP and soon find out who you are ...  You know that on the Internet you're never ever anonymous, right?

Again: I'm not your Dad. I have tons of those files too. But then again I am Swiss, I live in Switzerland, and here the law clearly says that it's perfectly legal to download whatever you wish. So unless you live here too I'd suggest you edit that posting above and avoid attracting unnecessary attention by openly posting a list of things that you're not supposed to have?

Just a suggestion.

you are correct, you're not my dad, you also don't know me at all and i'd hazard a guess you'd need to scroll up real quick to even remember my login (did i just catch you scrolling?).

not that it's any of your business but i work at a store that sells movies and i get a decent discount. i can provide disks for every one of those avi's

---

### Post by scorp123 on 2009-09-30
> **Sonic Reducer said:**
> i can provide disks for every one of those avi's So these are perfectly legal backups up there which are permitted under "fair use" laws or whatever? Fine then. MPAA, RIAA and all the other content mafiosi can move on then ...

Don't get me wrong. I don't really care so much about you :D  I'd just hate to see Canonical Ltd. or this forum get in trouble because some bunch of lawyers think they have a case and can extort money from here.

Thanks, peace and bye bye.

---

