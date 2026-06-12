---
title: "Help a noob out. I need to install a theme/conky"
date: 2011-07-29
forum: New to Ubuntu
---

### Post by Selekah on 2011-07-29
So yeah.

I am running Ubuntu 11.04 Natty Narwhal and I have Unity enabled and I've got all my drivers in order. I've downloaded all the updates and such and got the restricted packages to run mp3s and even got the thing that lets me play dvds.

Now I want to install a theme, conky, and if possible a dock.

[http://sunjack94.deviantart.com/art/Gold-And-Grey-Conky-151006149?](http://sunjack94.deviantart.com/art/Gold-And-Grey-Conky-151006149?)

Something like that.

I have the compiz config and the extra plugins but I can't for the life of me figure this out. It says in the instructions for this conky that I just have to double click conky.sh and click run. So I do that and nothing happens.

What I've mentioned above is ALL that I've downloaded plugin/update wise.

Ideally, I want exactly this:

[http://gnome-look.org/content/show.php/Darker+Ice?content=70611](http://gnome-look.org/content/show.php/Darker+Ice?content=70611)

As a theme

[http://gnome-look.org/content/show.php/Conky_Ken?content=134705](http://gnome-look.org/content/show.php/Conky_Ken?content=134705)

as the conky

and thats all really.


I'm just asking how to do this. Everything I need to do it, maybe a bit of terminal advice. Do I need any special programs to run the effects besides compiz? and does compiz need a special configuration? I'm so confused.

I could really use some help guys. Here's hoping.

---

### Post by jerrrys on 2011-07-29
there's like 1000's of themes [here]("http://gnome-look.org/content/search.php") and you cant fine one?  thats pretty sad.

I could not find one either.  so i built it.  and its not so hard. all the tools already exist

interested?.

---

### Post by hookitup on 2011-07-29
i just built one as well, its pretty easy just fallow this guy ^^^^

---

### Post by jerrrys on 2011-07-29
ok hookitup:

lets see it :D

---

### Post by Selekah on 2011-07-29
Alright, so if I'm not going to be told how to implement an existing theme, would you show me how to make my own?

---

### Post by jerrrys on 2011-07-29
it was just a thought

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=modify+edit+an+existing+theme&sa=Search&cof=FORID:9#1046](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=modify+edit+an+existing+theme&sa=Search&cof=FORID:9#1046)

---

### Post by Selekah on 2011-07-29
I'll see what I can do, although my previous question still stands.

---

### Post by hookitup on 2011-08-05
You don't need compiz for conky . Conky is a system monitoring utility. It's very easy to Install just run this ```
sudo apt-get install conky
```then find a configuration file that u like on the web and copy it then run ```
gedit ~/.conkyrc
```And when the text editor opens paste the configuration text you just copyed off the web into it ... Or u can do what I did and just creat my own configuration

 For the .sh file . Download it then right click it and click extract here then the file it creates you need to open it and find the **install.sh** file then right click that and go to properties then permissions tab then click "allow executing file as program" then After that you will double click the install.sh and then click _run_ then _yes_ then let's it do it's thing then it may ask for root password then a little pop up will come saying nothing really just click _ok_  then _unlock_ then _close_ then it will say you are done blah blah blah and the theme should have changed..watch the video below it will make more scene then me explaining it.....

Check these links for conky:
[http://www.junauza.com/2009/03/installset-up-conky-on-ubuntu.html](http://www.junauza.com/2009/03/installset-up-conky-on-ubuntu.html)

for .sh file,,,Fast forward the junk . It's almost the same process but he's making it look like window$ ,, should be the same concept. with the dark theme , not 100% sure if this process works  with the conky , haven't tried it yet
[http://www.youtube.com/watch?v=9T-7BEJpwcI](http://www.youtube.com/watch?v=9T-7BEJpwcI)

---

