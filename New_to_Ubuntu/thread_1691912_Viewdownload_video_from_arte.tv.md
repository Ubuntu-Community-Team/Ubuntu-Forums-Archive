---
title: "View/download video from arte.tv"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by Mariane on 2011-02-20
Hi, 

I can neither view nor download videos from [http://videos.arte.tv](http://videos.arte.tv)

One example is here:
[http://videos.arte.tv/fr/videos/scandinavie_sauvage-3708692.html](http://videos.arte.tv/fr/videos/scandinavie_sauvage-3708692.html)

I tried seamonkey and firefox with "down them all", it does not work for this site. What I see is a black rectangle with a little revolving symbol (like a "wait" symbol) next to the word "connection". I tried waiting but nothing happens. 

Please help

Mariane

---

### Post by bluebyt on 2011-02-20
Hi,
 Someone make a script to download videos on arte.tv. Maybe you can try that.

[http://www.generation-linux.fr/index.php?post/2009/02/21/Arte-en-voici-en-voila]("http://www.generation-linux.fr/index.php?post/2009/02/21/Arte-en-voici-en-voila")

Bonne chance!
bluebyt

---

### Post by wizard10000 on 2011-02-20
I looked at the page source and that's a Shockwave video.  You can't play Shockwave in Linux - closest you can get is using Crossover Office and run Internet Explorer with a Shockwave plugin or run Windows in a virtual machine.

Hope this helps -

---

### Post by Mariane on 2011-02-20
Oh bother... Maybe I could download it and convert it? 

Mariane

---

### Post by wizard10000 on 2011-02-21
> **Mariane said:**
> Oh bother... Maybe I could download it and convert it? 

Mariane

Probably - but it won't be much fun as mencoder doesn't support Shockwave  ;)

Found this -

[http://help.lockergnome.com/linux/convert-SWF-AVI-format--ftopict396093.html](http://help.lockergnome.com/linux/convert-SWF-AVI-format--ftopict396093.html)

> To accomplish a conversion from *.swf to *avi I succesfully used the 
following workflow: 
First I used a python script called edit.py from the pyvnc2swf 
suite(pyvnc2swf-0.9.3) to convert input.swf to output.flv (yes its a 
flash video movie) 
edit.py -o output.flv input.swf 

Then I used ffmpeg to convert output.flv to output.avi. 
ffmpeg -i output.flv output.avi 

I hope this helps 
KH 

---

### Post by wizard10000 on 2011-02-21
I was able to grab the file with wget and run the python script against it (which complained about no soundcard detected).  Output was about eight frames which VLC did play without converting to avi but all I got was a black flash on the screen in VLC and the video was over - but I think that's encouraging.

---

### Post by Mariane on 2011-02-23
Yes, it's encouraging :) 

Mariane

---

### Post by ron999 on 2011-02-23
> **Mariane said:**
> Hi, 

One example is here:
[http://videos.arte.tv/fr/videos/scandinavie_sauvage-3708692.html](http://videos.arte.tv/fr/videos/scandinavie_sauvage-3708692.html)



Hi
I think there's something wrong with that page.

Try a different one, such as this:- [http://videos.arte.tv/fr/videos/suede_nucleaire_des_sarcophages_en_cuivre_pour_stocker_les_dechets-3435730.html]("http://videos.arte.tv/fr/videos/suede_nucleaire_des_sarcophages_en_cuivre_pour_stocker_les_dechets-3435730.html")

---

### Post by Mariane on 2011-03-02
There always ends up "being something wrong", the videos stay online for a week or two only. 

And an additional problem is that if you are not in France or in Germany you have to use a proxy in France or Germany. Otherwise arte will block your IP. 

I've already spent more time trying to solve this than the length of the video I wanted to watch,  :lol: . 

Mariane

---

### Post by Mariane on 2011-04-23
```

sudo add-apt-repository ppa:arte+7recorder
sudo apt-get update
sudo apt-get install arte+7recorder-5

```

You need version 5 because something is wrong with version 4, this is why I write arte+7recorder-5. 

Then you open it application/multimedia/Arte+7recorder

On first run you have to resize and move the window which opens on fullscreen by default. Underneath it you will find a little "configure" window where you have to choose the download directory and your favorite video player (vlc or totem, etc). It won't work until you do this and then close and relaunch the arte+7recorder program again. 

Later when you open it it opens a window showing all available videos. Double-click on one to see details (when details are available on arte's site). Then click on the + sign and you will see the video added to a list bottom left of the screen. Click on it to select it and then click the "Download" button. 

Then you just have to wait until the "Progress" column shows 100%  :D . 

If like me you cannot watch it straight online because of a bad connection, don't worry if the program stops telling you something is wrong with your connection. Just relaunch the same download and it will start from where it left off. 

Mariane 


PS I don't know about shockwave stuff, I can just say it runs fine.

---

### Post by miikajuuri on 2011-04-25
> Die folgenden Pakete haben unerfüllte Abhängigkeiten:
 arte+7recorder-5 : Hängt ab von: python-beautifulsoup ist aber nicht installierbar
E: Beschädigte Pakete


Danke Marianne. Gibt es einen einfacheren Weg. Ich habe mehrmals versucht all die Scripte zu intalieren. Bin noch nicth so gut mit Linux Matrix vertraut.

---

### Post by miikajuuri on 2011-04-25
> Die folgenden Pakete haben unerfüllte Abhängigkeiten:
 arte+7recorder-5 : Hängt ab von: python-beautifulsoup ist aber nicht installierbar
E: Beschädigte Pakete

bei mir kamm diese Fehlermeldung

---

### Post by Mariane on 2011-05-16
Sorry I cannot reply in German. I think it is telling you that you have missing dependencies and that you should type

```

sudo apt-get install python-beautifulsoup

```

But this is the first time I ever hear of "python-beautifulsoup" (I would have remembered such a name :lolflag: ) so please look it up online first, don't blindly install some script which might make a beautiful soup of your computer. 

Mariane

---

### Post by Ferbantes on 2012-03-31
I have installed the Arte+7recorder and it opens correctly, it shows the list of videos to download.
But then, when I click on the Download button, I get a popup window with the text: "There are problem with your internet connection"
In my download directory I get an flv file with the name of the film that I had selected, but the size is 0.
I live in Sweden, may be that is the problem?

---

### Post by Ferbantes on 2012-04-02
Using the Arte+7recorder application in Ubuntu, works only for Arte Journal and Arte Reportages films. The same result if I play films in Firefox or in Opera.
That means, that Arte permits only those films to be downloaded from countries outside La France and Deutschland.
Is some solution to this?

---

